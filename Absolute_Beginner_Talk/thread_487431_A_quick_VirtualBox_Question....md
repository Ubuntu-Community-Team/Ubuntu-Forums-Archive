---
title: "A quick VirtualBox Question..."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-06-29
I'm getting this:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

How do I change those permissions?

---

### Post by meney on 2007-06-29
Not too sure, but perhaps running the command that you need to using sudo. Or open up System -> Admin -> Users and Groups at the bottom of the list, and try adding you account to that particular group? Hope it helps :)

---

### Post by toasty_ghosty on 2007-06-29
thank you. That I believe solved the problem. And I have to say as someone relatively new to the linux community, everyone on this forum has given me a huge amount of help. Thanks.

---

### Post by meney on 2007-06-29
Thats what were here for :D

You are most welcome and enjoy using linux!

---

### Post by toasty_ghosty on 2007-06-29
One last thing before I retire to get some rest. How do I enable usb ports while using XP on VirtualMachine. It does not seem to want to work.

---

### Post by HotShotDJ on 2007-06-29
> **toasty_ghosty said:**
> One last thing before I retire to get some rest. How do I enable usb ports while using XP on VirtualMachine. It does not seem to want to work.On right hand panel of VirtualBox (Before you start windows!) scroll down until you see "USB Controler" and then click on it. Tick the box next to "Enable USB Controler".  There should be no need to mess with the filters right now.

NEXT, you need to add the following line to your /etc/fstab file ... replace devgid=1001 with the actual group id number for your vboxusers group.  THIS IS IMPORTANT or you will have problems!
```
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
```
Reboot your system and you should be good to go.

---

### Post by toasty_ghosty on 2007-06-29
I know I'll seem like a total loser asking this, but what file, I can't seem to find it.

---

### Post by HotShotDJ on 2007-06-29
> **toasty_ghosty said:**
> I know I'll seem like a total newb asking this, but what file, I can't seem to find it.It is not in your home directory.  Open a terminal and type ```
gksudo gedit /etc/fstab
``` and then edit as I showed you above. Its easy.  (you'll get used to this stuff, I promise ;) )

---

### Post by toasty_ghosty on 2007-06-29
This is all I'm getting. I can't seem to find the code:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e30648cc-c5d3-4594-8292-4311e55ac6a5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=354ecfcd-b8a5-4daf-95a8-d3a186a56e88 /usr/local      ext3    defaults        0       2
# /dev/sda2
UUID=918df669-9ab1-42a7-942c-ba0e2eea26bc none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by HotShotDJ on 2007-06-29
> **toasty_ghosty said:**
> This is all I'm getting. I can't seem to find the code:
Well, of course not, you haven't added it yet. :)  Cut and Paste the line I showed you to the end of the file and then save it. **Just make sure you change the devgid= line to the proper id number!!! **

---

### Post by toasty_ghosty on 2007-06-29
Alright. I posted the line, checked the number, it happened to be the same, yet it still doesn't want to work. Any ideas?

---

### Post by HotShotDJ on 2007-06-29
Did you reboot?  The usbfs needs to be remounted.

---

### Post by toasty_ghosty on 2007-06-29
I crtl alt backspaced. Not rebooted. Thank you for all your help. Especially at 337 am. at least my time.

---

### Post by HotShotDJ on 2007-06-29
Does it work now?  And your quite welcome. :)

---

### Post by toasty_ghosty on 2007-06-29
Yes. At least to an extent. It recognized the drive but I received an error in XP right after I tried to transfer a file to the XP desktop. While transferring it said it was unable to write from the drive (usb jumpdrive) I think it may have just been a windows problem though. Thanks again though. I'll save this for tomorrow. I need to go to bed. I said only 5 more minutes about 2 and a half hours ago. Thanks for all the help.

---

