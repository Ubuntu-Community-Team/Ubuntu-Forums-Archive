---
title: "Dual Boot XP with only ubuntu currently installed"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by c_x on 2006-08-05
Now I have this:
. Ubuntu 6.06 on an ext3 partition
. A free ntfs partition
. VMware workshop

I want:
. Install win xp and use ubuntu boot manager
. Sometimes run xp "natively"
. Sometimes run xp via VMware in ubuntu

Is this possible, and how?

Thanks in advance!

---

### Post by louis_nichols on 2006-08-05
it is possible. what you should do is to first install xp on the ntfs partition. unfortunatelly, XP will rewrite your MBR without asking, so right after that it will boot only win xp, but you can fix this. to do it, you boot the dapper install cd, open a terminal window and start grub with

```
sudo grub
```
then the grub screen will appear. in this, you issue the command for root partition, to set it on the ubuntu partition, like this
```
root (hd0,x)
```
where x is the ubuntu partition. To find it, you can use the command
```
geometry (hd0)
```
after this, I'm not sure weher you also have to issue the command configfile, but you should, to be safe:
```
configfile (hd0,x)/boot/grub/menu.lst
```
where x is the same like above, unless you use a separate partition for the boot folder.
the last thing is to install grub with
```
setup (hd0)
```
and this is pretty much it. Then you'll only be able to boot Ubuntu from the grub menu, but after this you just need to add the xp install in menu.lst and you're good to go.

as for vmware, it can be done and is a whole different thing. You just install vmware in ubuntu and then xp in vmware. It can't be the same xp on your ntfs drive, if that's what you're thinking. Mind you, legally you'll need 2 p licences for this. lol

---

### Post by c_x on 2006-08-05
Whoa! Thanks a lot for the detailed information!

---

### Post by annda on 2006-08-05
you might consider reformatting your NTFS partition to FAT first in case you want to write to it under Ubuntu.

---

### Post by c_x on 2006-08-05
*"as for vmware, it can be done and is a whole different thing. You just install vmware in ubuntu and then xp in vmware. It can't be the same xp on your ntfs drive, if that's what you're thinking. Mind you, legally you'll need 2 p licences for this. lol"*
I read somthing at [http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html](http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html) very fast, but i probobly misunderstood it.
[I]
"you might consider reformatting your NTFS partition to FAT first in case you want to write to it under Ubuntu."[/I]
Yeah, thats seems like a good idea!

Before I do the xp installing is there a last way to improve speed in vmware? is win2000 faster?
How about win4lin, is that better then vmware?

I really want to stick with ubuntu only, but the 2 program i use most often besides azureus and firefox is photoshop cs2 (no gimp is not that good) and flash 8.
If I install windows on it's own partition i'm afraid that i will boot it the most :(

---

### Post by louis_nichols on 2006-08-06
you may wanna try installing photoshop under wine. I know I installed photoshop 6 once and it was working great! almost flawlessly. Just a minor GUI bug, but it didn't bother me once I learned how to avoid the situation.

---

