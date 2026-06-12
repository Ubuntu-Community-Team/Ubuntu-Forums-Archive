---
title: "Two problems"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by dux on 2006-06-04
Hey guys. I'm now typing from inside Ubuntu! :) Nice and shiny. But I've got two problems.

Firstly, I have a Dell 2005 FPW (widescreen) but I can't seem to select widescreen in the resolution options. I'd really like the few extra inches I enjoyed under XP, I'm always being told a few inches make a big difference....that's another story I think. I ran a search but all the solutions make my little newbie brain bleed. Can anyone point me in the right direction?

Secondly, my XP install is on a different partition to my Ubuntu install and GRUB doesn't seem to have picked it up. This means that, to change what I boot into, I have to manually edit boot priorities in the BIOS. Is there a way to get GRUB to recognise XP on my other HDD?

Thanks in advance for the help,
Stu.

---

### Post by smile-its-smiley on 2006-06-04
you need to have your windows xp hdd in fat32 not in ntfs because grub doesnt support ntfs

---

### Post by taurus on 2006-06-04
First, welcome to Ubuntu.

What video card do you have?  If you have either nVidia or ATI, you may want to install the right driver for it first before you try to configure your monitor...

If GRUB doesn't pick up your XP during the installing process, you can always add it in by hand...  Assuming that your XP is on the first HD, open a terminal, Applications -> Accessories -> Terminal and, and type
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak <-- back it up first...
sudo gedit /boot/grub/menu.lst <-- edit it

```
Now, scroll all the way dow the the bottom and add
```

title Windows XP
root (hd0,0)
makeactive
chainloader +1

```

---

### Post by dux on 2006-06-04
Hi. I've got an Nvidia card (6600GT), I'm just checking the site now for how to install these drivers :). Will that method you just suggested work even though my XP drive is NTFS or, like smile said, does it have to be Fat32 to work?

---

### Post by taurus on 2006-06-04
[QUOTE=dux]Hi. I've got an Nvidia card (6600GT), I'm just checking the site now for how to install these drivers :). Will that method you just suggested work even though my XP drive is NTFS or, like smile said, does it have to be Fat32 to work?[/QUOTE]
Not sure exactly what he meant because GRUB can boot XP fine even if it's NTFS filesystem...  And for your nVidia card, check out this link to install nVidia driver for it.

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by dux on 2006-06-04
Drivers are all installed now and everything is running much faster, thanks :). Still no luck on the widescreen front. I tried adding in 1650 x 1080 to xorg.conf manually, but that didn't seem to do anything at all.

---

### Post by taurus on 2006-06-04
[QUOTE=dux]Drivers are all installed now and everything is running much faster, thanks :). Still no luck on the widescreen front. I tried adding in 1650 x 1080 to xorg.conf manually, but that didn't seem to do anything at all.[/QUOTE]
For the wide screen thing, check out this post...

[http://ubuntuforums.org/showthread.php?t=169758&highlight=wide+screen](http://ubuntuforums.org/showthread.php?t=169758&highlight=wide+screen)

---

### Post by IYY on 2006-06-04
Adding it to xorg.conf should do the trick. Show us your xorg.conf file.

---

### Post by dux on 2006-06-04
I killed my xorg.conf by mistake when running the config and the UI refused to load, so I replaced it with the backup using the command line. Then ran the sudo dpkg-reconfigure again, and got it working. I was quite impressed with myself, being able to do that after less than a day using Ubuntu :). Thanks for the help.

Grub still isn't working right though, the XP hardrive is now set to my secondary drive because otherwise it boots straight to XP at startup. The XP option on Grub however refuses to work, I assume because it's looking at the wrong HDD. How do I change this: ```
title Windows XP
root (hd0,0)
makeactive
chainloader +1
``` to point to the other HDD (which is SATA, unlike the current primary which is IDE, if that makes any difference)

---

