---
title: "Ubanutu Multiple Boot Manager"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by KLoWnTaZ on 2006-07-08
I have 3 partitions.
Ubanutu 
Win XP Media
Vista Beta

However My mbs screen shows this...
Ubuntu (Ver)
Ubuntu Recovery
Ubuntu (Ver)
Ubuntu Recovery
Other OS's:
Windows Meda Edition

Now my question is How do I get rid of the duplicate Ubanutu's in the Boot manager and have the Boot manager list both of the windows OS's?

---

### Post by tonyr on 2006-07-08
The boot list you see is generated from the file **/boot/grub/menu.lst**.
You will need to edit this file manually as root.  One way to do that
is to ALT+F2, and type into the dialog window that pops up
```

gksudo gedit /boot/grub/menu.lst

```
Another dialog will ask for a password. Enter **your** password.
There are sections in this file for each bootable OS.  Each section starts
with a **title** line.  It sounds to me like you have duplicate sections.
If you do, you should be able to safely remove the second copy.

If you need more detail, I can post my **/boot/grub/menu.lst**
with highlights, but the links I include below also have examples.

Multi-booting Vista seems to be problematical, although many other people
are doing/trying it.  Here are a couple of examples that contain
interesting discussion and other links.
[http://www.ubuntuforums.org/showthread.php?t=207870](http://www.ubuntuforums.org/showthread.php?t=207870)
[http://www.ubuntuforums.org/showthread.php?t=207530](http://www.ubuntuforums.org/showthread.php?t=207530)

---

### Post by Sonofmoog on 2006-07-08
Your Ubuntu entries are not duplicates.  If you check the (ver) information carefully, you should see they are slightly different.  These are different kernels, and if hard drive space is not an issue I recommend keeping both.  This way if your working kernel is ever hosed, you have a backup that will allow you to boot and recover your system.

---

### Post by KLoWnTaZ on 2006-07-08
> **Sonofmoog said:**
> Your Ubuntu entries are not duplicates.  If you check the (ver) information carefully, you should see they are slightly different.  These are different kernels, and if hard drive space is not an issue I recommend keeping both.  This way if your working kernel is ever hosed, you have a backup that will allow you to boot and recover your system.

They are Identical It was a goof of mine I double installed...

---

