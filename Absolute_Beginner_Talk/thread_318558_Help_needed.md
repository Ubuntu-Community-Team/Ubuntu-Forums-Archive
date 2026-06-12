---
title: "Help needed"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by fjw1982 on 2006-12-14
Hi everyone

I have a problem.

I just installed ubuntu 6.10 on a external hard drive connected to my laptop. Everything went fine until I started ubuntu for the first time. I type in my user name, not my real name!, and my password and nothing happens. All I can see is the standard ubuntu wallpaper.

Second, I disconnected the external hard drive to start windows xp and I get an error message when I boot.

"Grube loading... or somthing like that

ERROR 21"

Does this mean I can't take my laptop with me unless my external hard drive i with me at the same time? I just cant start windows xp unless the external hard drive where ubuntu is installed is connected.

I know I'm just a "nOOb" so please take that in to consideration... :)

Thanks in advance...

---

### Post by bernied on 2006-12-14
Regarding your second problem, when you installed ubuntu, you installed a bootloader called 'grub'. This is in two stages, the first is on the master boot record of your first hard-drive, this is where bios looks to start loading an operating system. Grub Stage 1 loads grub stage 2, which in your case is on the external hard-drive. Grub stage 2 gives you a boot menu and loads the operating systems.

To be able to start windows without your external drive attached, you will need to restore your original master boot record. You can do this with your Windows Recovery CD, or possibly the install CD. Failing that, you can use an open source alternative, like FreeDOS. The command you need is fixmbr. Google that for options, and check windows web sites.

To then use your external hard drive for an operating system, I recommend that you change the boot order in your bios setup, so that usb drives are first on the list. Then you would have to set up grub on the master boot record of the external drive. If this is not possible, then you need some other way of booting the external drive. You could have:
- a boot partition on the onboard hard drive
- a boot floppy disk
- a boot CD

As for your first problem, it may be related, though perhaps not. If you get to the point where you login, then quite a lot is working well. This could just be a problem with desktop settings. But maybe better to fix the boot setup first?

You need to take these things a step at a time. An operating system is not a simple thing, even Windows.

---

### Post by xyz on 2006-12-14
Try restoring GRUB "the simple way":
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
Using the Ubuntu Install CD!!

---

### Post by fjw1982 on 2006-12-14
Thank you very much.

I just found this site addressing the problem!

[http://www.users.bigpond.net.au/hermanzone/p18.htm]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by xyz on 2006-12-14
> **fjw1982 said:**
> Thank you very much.

I just found this site addressing the problem!

[http://www.users.bigpond.net.au/hermanzone/p18.htm]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Excellent!!!**Hermanzone**
Let us know how you get along...

---

### Post by fjw1982 on 2006-12-14
Everything fixed. 

I just ran mbrfix.exe found on here:

[http://www.sysint.no/en/Download.aspx]("http://www.sysint.no/en/Download.aspx")

I have now formated my external HD and I'm going to try to install Ubuntu again. This time on a partition that actually is ON my laptop :)

Thank you for your help!

---

### Post by bernied on 2006-12-14
Take care with all that partition resizing nonsense. It is easy to destroy your windows install.

For the future, you can put linux on external drives, it's just a bit more fiddly.

---

