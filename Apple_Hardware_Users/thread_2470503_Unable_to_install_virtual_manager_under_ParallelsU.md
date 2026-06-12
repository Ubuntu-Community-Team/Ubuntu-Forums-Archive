---
title: "Unable to install virtual manager under Parallels/Ubuntu 20.02.2 ARM"
date: 2022-01-01
forum: Apple Hardware Users
---

### Post by kodb on 2022-01-01
Greetings all!
I am currently running Ubuntu 20.04.2 in a Parallels VM so I can do all my linux server work on my M1Pro MacBook.  I am perplexed by the set of errors I am getting.  See below:
```

parallels@ubuntu-linux-20-04-desktop:~$ sudo apt install virt-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dmeventd gir1.2-appindicator3-0.1 gir1.2-gtk-vnc-2.0 gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0
  gir1.2-spiceclientglib-2.0 gir1.2-spiceclientgtk-3.0 ibverbs-providers ipxe-qemu ipxe-qemu-256k-compat-efi-roms
  libaio1 libcacard0 libdevmapper-event1.02.1 libgovirt-common libgovirt2 libgtk-vnc-2.0-0 libgvnc-1.0-0 libibverbs1
  libiscsi7 liblvm2cmd2.03 libnss-mymachines libosinfo-1.0-0 libphodav-2.0-0 libphodav-2.0-common libpmem1 librados2
  librbd1 librdmacm1 libreadline5 libslirp0 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5 libspice-server1
  libusbredirhost1 libusbredirparser1 libva-x11-2 libva2 libvirglrenderer1 libvirt-clients libvirt-daemon
  libvirt-daemon-driver-qemu libvirt-daemon-driver-storage-rbd libvirt-daemon-system libvirt-daemon-system-systemd
  libvirt-glib-1.0-0 libvirt0 libxml2-utils lvm2 mesa-va-drivers osinfo-db python3-distutils python3-libvirt
  python3-libxml2 qemu-block-extra qemu-efi-aarch64 qemu-efi-arm qemu-kvm qemu-system-arm qemu-system-common
  qemu-system-data qemu-system-gui qemu-utils sharutils spice-client-glib-usb-acl-helper systemd-container
  thin-provisioning-tools va-driver-all virt-viewer virtinst
Suggested packages:
  libosinfo-l10n gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libvirt-daemon-driver-lxc
  libvirt-daemon-driver-vbox libvirt-daemon-driver-xen libvirt-daemon-driver-storage-gluster
  libvirt-daemon-driver-storage-zfs numad auditd nfs-common open-iscsi pm-utils radvd systemtap zfsutils samba vde2
  debootstrap sharutils-doc bsd-mailx | mailx python3-guestfs ssh-askpass
The following NEW packages will be installed:
  dmeventd gir1.2-appindicator3-0.1 gir1.2-gtk-vnc-2.0 gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0
  gir1.2-spiceclientglib-2.0 gir1.2-spiceclientgtk-3.0 ibverbs-providers ipxe-qemu ipxe-qemu-256k-compat-efi-roms
  libaio1 libcacard0 libdevmapper-event1.02.1 libgovirt-common libgovirt2 libgtk-vnc-2.0-0 libgvnc-1.0-0 libibverbs1
  libiscsi7 liblvm2cmd2.03 libnss-mymachines libosinfo-1.0-0 libphodav-2.0-0 libphodav-2.0-common libpmem1 librados2
  librbd1 librdmacm1 libreadline5 libslirp0 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5 libspice-server1
  libusbredirhost1 libusbredirparser1 libva-x11-2 libva2 libvirglrenderer1 libvirt-clients libvirt-daemon
  libvirt-daemon-driver-qemu libvirt-daemon-driver-storage-rbd libvirt-daemon-system libvirt-daemon-system-systemd
  libvirt-glib-1.0-0 libvirt0 libxml2-utils lvm2 mesa-va-drivers osinfo-db python3-distutils python3-libvirt
  python3-libxml2 qemu-block-extra qemu-efi-aarch64 qemu-efi-arm qemu-kvm qemu-system-arm qemu-system-common
  qemu-system-data qemu-system-gui qemu-utils sharutils spice-client-glib-usb-acl-helper systemd-container
  thin-provisioning-tools va-driver-all virt-manager virt-viewer virtinst
0 upgraded, 70 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.3 MB/29.7 MB of archives.
After this operation, 414 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 librados2 arm64 15.2.13-0ubuntu0.20.04.1
  404  Not Found [IP: 91.189.88.142 80]
Err:2 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 librbd1 arm64 15.2.13-0ubuntu0.20.04.1
  404  Not Found [IP: 91.189.88.142 80]
Err:3 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt0 arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:4 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt-clients arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:5 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt-daemon-driver-qemu arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:6 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt-daemon arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:7 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt-daemon-driver-storage-rbd arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:8 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt-daemon-system-systemd arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:9 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 libvirt-daemon-system arm64 6.0.0-0ubuntu8.11
  404  Not Found [IP: 91.189.88.142 80]
Err:10 http://ports.ubuntu.com/ubuntu-ports focal-updates/universe arm64 mesa-va-drivers arm64 20.2.6-0ubuntu0.20.04.1
  404  Not Found [IP: 91.189.88.142 80]
Ign:11 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 qemu-efi-aarch64 all 0~20191122.bd85bf54-2ubuntu3.2
Ign:12 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 qemu-efi-arm all 0~20191122.bd85bf54-2ubuntu3.2
Err:11 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 qemu-efi-aarch64 all 0~20191122.bd85bf54-2ubuntu3.2
  404  Not Found [IP: 91.189.88.142 80]
Err:12 http://ports.ubuntu.com/ubuntu-ports focal-updates/main arm64 qemu-efi-arm all 0~20191122.bd85bf54-2ubuntu3.2
  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/c/ceph/librados2_15.2.13-0ubuntu0.20.04.1_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/c/ceph/librbd1_15.2.13-0ubuntu0.20.04.1_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt0_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt-clients_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt-daemon-driver-qemu_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt-daemon_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt-daemon-driver-storage-rbd_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt-daemon-system-systemd_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/libv/libvirt/libvirt-daemon-system_6.0.0-0ubuntu8.11_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/universe/m/mesa/mesa-va-drivers_20.2.6-0ubuntu0.20.04.1_arm64.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/e/edk2/qemu-efi-aarch64_0~20191122.bd85bf54-2ubuntu3.2_all.deb  404  Not Found [IP: 91.189.88.142 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/pool/main/e/edk2/qemu-efi-arm_0~20191122.bd85bf54-2ubuntu3.2_all.deb  404  Not Found [IP: 91.189.88.142 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

I have already tried every iteration of "sudo apt/apt-get update/clean/autoclean etc" that I know (with correct syntax)
Any ideas or is this simply an ARM limitation as to not having the packages to support?

Thanks and have a Happy New Year!

Bob

---

