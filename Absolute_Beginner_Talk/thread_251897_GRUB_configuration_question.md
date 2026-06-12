---
title: "GRUB configuration question"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by wetsawdust on 2006-09-06
I just installed Ubuntu 6.06 on my pc on a newly installed hard drive.  The old hard drive is still in there with my old installation of windows XP, however GRUB loads Ubuntu automatically, instantly.  How do I configure it so that it reckognizes the XP drive and prompts me to make a choice upon startup?

---

### Post by Apple 101 on 2006-09-06
How are your drives connected to your computer?

---

### Post by KashKhan on 2006-09-06
[COLOR="Blue"]well well well, i think you must have asked someone before you tried to install Ubuntu with Windows.To the best of my understanding, you wanted to make your pc Dualboot and ended up losing Windows OS on your hard drive due to grub configeration.I have installed Windows and Ubuntu on my Dell notebook.When i start up my notebook, it gives me option either to use Windows or Ubuntu and so far i have no problem at all.
I think you must make two partitions of your hard drives, one for Ubuntu and the second one of windows. The partition for Ubuntu works only if you its formated through Ubuntu's hard drive which it does automatically when you reboot the system from Ubuntu's bootable cd and direct it to the slected partition.
As to solution for your problem, i would suggest you to make a clean format of your hard drive and install first windows and then Ubuntu on seprate parts of hard drives.Hopefully then you will have options to opt for an opereting system every time you turn on your pc.[/COLOR]
Regards,
KashKhan

---

### Post by ciscosurfer on 2006-09-06
wetsawdust, check these three links:
[https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28grub%29)
[https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/BootFloppy?highlight=%28grub%29)
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

---

### Post by lha on 2006-09-06
> **wetsawdust said:**
> I just installed Ubuntu 6.06 on my pc on a newly installed hard drive.  The old hard drive is still in there with my old installation of windows XP, however GRUB loads Ubuntu automatically, instantly.  How do I configure it so that it reckognizes the XP drive and prompts me to make a choice upon startup?

If you have only two ide hard drives, the following should do the trick:

Open terminal (Applications->Accessories->Terminal) and type```

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```
and paste the following lines in the very end of that file.
```
title Windows
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
Then replace lines
```
timeout         3
```
(the number may be different) and
```
hiddenmenu
```
with
```
timeout         10
```
and
```
#hiddenmenu
```

---

