---
title: "PowerPC dual G4 will not upgrade to an smp kernel"
date: 2006-10-24
forum: Apple PPC Users
---

### Post by dister520 on 2006-10-24
I recently decided to install dapper on my dual G4. I wanted to use a kernel that supported SMP. Using synaptic i installed the latest kernel, and modified my yaboot config, shown below:
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
boot=/dev/hda2
device=/pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux-2.6.15-25-powerpc-smp
	label=new
	read-only
	initrd=/boot/initrd.img-2.6.15-25-powerpc-smp
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

uname -r displays the following: 2.6.15-26-powerpc

how can i utlize both of my processors? Your help will be wonderful:mrgreen: 
D

---

### Post by taurus on 2006-10-24
Move to PPC section.

---

### Post by catlett on 2006-10-24
The smp is no longer listed. It use to be 2 packages but now it is just one. For instance I have intel so I use the 686 kernel. With the 2.4 kernel it would say 686-smp but now it is just 686. As long as you installed the power pc -smp in synaptic (synaptic will still list the smp) it is enabled. This is a long way to say you have smp support.
This is my output 
```
catlett@ubuntu:~$ uname -r
2.6.15-27-686
```
The smp just isn't listed any more.

---

### Post by dister520 on 2006-10-24
Ill see if i have powerpc-smp, and post back my results shortly

thanks
D

---

### Post by dister520 on 2006-10-25
so i started going to the repository, and downloaded the power pc smp and kernel 2.6.15.27-smp. After which it installs but doesnt update the yaboot.conf. So that was updated, and than restarted. I still boot into kernel
2.6.15-26-powerpc

---

### Post by dister520 on 2006-10-30
After a week i am unable to get smp support. If there is a how-to please point it to me
thanks
D

---

### Post by stmiller on 2006-10-31
Apple PPC Users> "Sticky: Warning: Dual processor kernel"

[http://ubuntuforums.org/showthread.php?t=185565](http://ubuntuforums.org/showthread.php?t=185565)

This is out of date, but may help.

Post your /etc/yaboot.conf

You can edit that, then type

sudo ybin -v

to write changes.

---

### Post by dister520 on 2006-12-14
Problem was yaboot.conf was not updating. Once it updated all is well:mrgreen:

---

