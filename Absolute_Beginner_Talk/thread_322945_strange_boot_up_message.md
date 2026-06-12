---
title: "strange boot up message"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2006-12-21
I've got 6.06 64bit installed and running but the strange thing is that when I boot up, after I choose Ubuntu from the Grub menu, everything stops with this:

"/bin/sh: cant access tty; job control turned off"

If I simply type "exit", the system will boot normally but I'd like to fix whatever is causing this so Ubuntu will boot normally. I couldn't find much on these forums for this error but someone  
suggested to another user with this problem to "remove the tty" but nothing about what tty is or how to remove it (or even if its safe).

Anyone have insight on this and what I need to do to correct it?
Thanks

---

### Post by compwiz18 on 2006-12-22
Mine used to do that - the problem is that you when you installed Ubuntu, you had some sort of external memory device plugged in that is no longer there.  This may be a hard drive, memory stick, or something else.  The solution: **sudo gedit /etc/fstab** and find the line that references your gizmo that isn't plugged in, and put a # in front of it (literally the character # - this is a comment, and will make the line not do anything).  If something else breaks, then just remove the # from the line, and you are back to the original.

If you aren't sure what line to #, post your /etc/fstab file here and I'll help you.

---

### Post by atarileaf on 2006-12-22
Thanks, I'll go through that file and see if I can find the culprit although I didn't have anything like a memory stick or any other kind of device plugged in at install that isn't there now.

---

### Post by atarileaf on 2006-12-22
Ok Compwiz, here is my list, copied and pasted as is. Thanks for your help!

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=0d495912-46f1-4bd0-bc9c-11359cc79c76 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=52e8bc6d-dab4-4c9d-b6ea-d9e3fb8caff8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


---

### Post by compwiz18 on 2006-12-22
Try putting a # in front of the last line - it looks a little funky...apparently you are telling it to mount /dev on /media/floppy0 which is incorrect.  If you have a floppy drive, I think GNOME should mount it automatically without needing /etc/fstab to do it.

---

### Post by atarileaf on 2006-12-24
Hi again. I followed your instructions and still I get this boot error message. ](*,) ](*,) ](*,) 

Anything else perhaps I could try :???:

---

### Post by Sef on 2006-12-24
> sudo gedit /etc/fstab

When using sudo to start a graphical program (e.g., gedit, or firestarter), use gksudo.  Hence the command should read like this: gksudo gedit/ etc/fstab.  Otherwise you could find yourself not being able to log in.

---

