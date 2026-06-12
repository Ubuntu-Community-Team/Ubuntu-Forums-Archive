---
title: "yaboot.conf"
date: 2005-09-03
forum: Apple PPC Users
---

### Post by osxus3r on 2005-09-03
I have installed Ubuntu on my mac mini and everything is fine. I edited /etc/yaboot.conf file so it has just one entry for linux, 
```

image=/boot/vmlinux
	label=customLinux
	read-only
	append="quiet splash"
```

However, after rebooting I can still choose 'old' and there is 'Linux' instead of my entry 'customLinux', how come?? any suggestions?

---

### Post by sulobanks on 2005-09-03
Did you run ybin after changing yaboot.conf?

---

### Post by osxus3r on 2005-09-03
[QUOTE=sulobanks]Did you run ybin after changing yaboot.conf?[/QUOTE]
 no, because I changed it from mac os, because Ubuntu wouldn't boot anymore.

---

### Post by stuporglue on 2005-09-24
Maybe you can use a live cd to rescue yourself. 

Boot from the live CD and mount the Ubuntu disk install. Copy the yaboot.conf file from /where/you/mounted/ubuntu/etc to /etc (ie. the /etc of the live session) then run ybin. If the live CD doesn't have ybin on it, there's a way to do it with chroot...

---

### Post by patrickp on 2005-09-26
hi,

there is another way

boot with the ubuntu cd

chroot

and then do your changes in yaboot.conf
when u finish type mkofboot -v 

this works

patrick

---

### Post by stuporglue on 2005-09-27
Easier way here.

Just hold down option while booting untill you get a graphical boot menu. Pick the penguin, then boot into Linux. Don't forget to run ybin afterwards.

---

