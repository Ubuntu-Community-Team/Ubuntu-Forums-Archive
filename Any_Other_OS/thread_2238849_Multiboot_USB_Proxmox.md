---
title: "Multiboot USB Proxmox"
date: 2014-08-10
forum: Any Other OS
---

### Post by bkvaluemeal on 2014-08-10
I'm trying to add the Proxmox ISO to grub2 that I'm running on a flash drive, but don't really know what I'm doing. How do I make it work?

This is what I've got:
```
set timeout=-1
set default=0


submenu 'Ubuntu' {
	menuentry "Ubuntu Server 14.04.1 64bit" {
		set iso="/ubuntu-14.04.1-server-amd64.iso"
		loopback loop $iso
		set gfxpayload=keep
		linux   (loop)/install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed iso-scan/filename=$iso quiet --
		initrd  (loop)/install/initrd.gz
	}
}


menuentry 'Proxmox VE 3.2' {
	set iso='/proxmox-ve_3.2-5a885216-5.iso'
	loopback loop $iso
	linux    (loop)/boot/isolinux/linux26 iso-scan/filename=$iso silent --
	initrd   (loop)/boot/isolinux/initrd.img
}


menuentry ' ' {
	set root= 
}


menuentry 'DBAN' {
	set iso='/dban.iso'
	loopback loop $iso
	linux (loop)/DBAN.BZI nuke='dwipe' iso-scan/filename=$iso silent --
} 


menuentry 'Memtest 86+' {
	linux16 /memtest86+.bin
}
```

Edit: Figured it out, but it's just white text on black. The GUI isn't there.

---

