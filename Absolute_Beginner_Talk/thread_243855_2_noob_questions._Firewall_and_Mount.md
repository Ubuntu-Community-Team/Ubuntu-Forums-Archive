---
title: "2 noob questions. Firewall and Mount"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by uBo on 2006-08-25
Hi,

I use Ubuntu for a month already. Very cool, my windows partition is just gathering dust.

I have two questions though.

1. I use my windows partition from ubuntu and have the following strange problem.

When I open nautilus for the first time and doubleclick on the windows partition nothing happens. Then I have to doubleclick on the linux one, go back and then select the windows one. Only after this operation I am able to access the windows partition. It is quite frustrating. Any ideas? I think back then I added some script to mount windows as a removable drive...

2. I am not sure Firestarter is running after bootup. I havent put any script in the session window, but have selected start_firewall_on_boot at the Configuration editor. I do not see any process listed on the System monitor, so I assume it is not runnig.
But when I scan my ports with some of those online scanners, everything is closed and blocked. Apart drom that on Shutdown it always lists "Closing Firestarter firewall" or something like that. So what do tou say, is it running or not?

Thanks for the help!

uBo

---

### Post by bogoliubov on 2006-08-25
Hello. I'm sorry but I don't have any answer for your first question. As for the second, I think that what Firestarter (or any other linux firewall for that matter) do is to edit the "iptables", which is a file containing what ports to open and so on...
So even though you can't see firestarter, the firewall should be ok.
But you can also check fs-security.com

---

### Post by uBo on 2006-08-25
thanks bogoliubov!

i thought so, because al my ports were hidden anyway. that is cool.


my question No1. still remains. 
Please help here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

so my **/dev/sda1** is not included there. but is still visible and accessible under /media/windows, but only when I do the trick described in the original post.

---

### Post by taurus on 2006-08-25
If you want to mount your Windows automatically at boot, then just add this line to the end of your /etc/fstab...

```

gksudo gedit /etc/fstab <-- edit your /etc/fstab

```

```

/dev/sda1   /media/windows   ntfs   defaults,umask=0222   0   0

```

---

