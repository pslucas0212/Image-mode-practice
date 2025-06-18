# Image Mode Practice

Image Mode examples on a RHEL 10 VM running in VMWare Fusion

### Set up virtualization to use QUCOW2 images
Install Virtualization Packages
```
# dnf -y install qemu-kvm libvirt virt-install virt-viewer
...
Complete!
```

Start and Enable libvirt services
```
# for drv in qemu network nodedev nwfilter secret storage interface; do
  sudo systemctl start virt${drv}d{,-ro,-admin}.socket
  sudo systemctl enable virt${drv}d{,-ro,-admin}.socket
done
```

Check system readiness
```
virt-host-validate
```

Manage VMs without Root privileges
```
# sermod -aG libvirt $(whoami)
# newgrp libvirt
```
