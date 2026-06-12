---
title: "[SOLVED] System hangs on shutdown"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by spideygal on 2007-11-19
I have read through  all links however some links in suggested threads do not work so I do not have the answer.

[http://ubuntuforums.org/showthread.php?t=310928](http://ubuntuforums.org/showthread.php?t=310928) is a dead link that does not show the fix.

I have an older system that I believe requires the apm force shutdown but somehow when I added it it did not work.

Also I saw some for editing lilo.conf but I do not have that I assume that is for another distro..

Any help greatly appreciated.

Celeron 733 with 384 mb or ram running Feisty 7.04 and it has to be powered off by the power button.

Thank you.

---

### Post by plucky on 2007-11-19
Hi spideygal,

Check out this link

[http://ubuntuforums.org/showthread.php?t=513224]("http://ubuntuforums.org/showthread.php?t=513224")

Also check your bios to see if ACPI is supported as you might have to disable ACPI at startup and enable APM

To do this you will have to edit menu.lst

```
gksudo gedit /boot/grub/menu.lst
```

and add

> acpi=off apm=on

to th end of this line

> kernel		/vmlinuz-2.6.22-14-generic root=UUID=c65f00cc-bb55-4e82-acea-922fe8e691c6 ro quiet splash  

Hope this helps
Plucky

---

### Post by yogo on 2007-11-19
deleted

---

### Post by spideygal on 2007-11-19
Was using someone else's pc

Thanks Plucky,

I did this (below) earlier but did not complete the mission


sudo gedit /etc/modules

add a new line with the following statement:

apm power_off=1

save and re-boot

I should have done this since I did not re-boot

sudo update /etc/modules

Seems to be working now, I was not able to get into bios. to check for acpi settings.

I assume everything is copasetic so I will mark it solved.

---

