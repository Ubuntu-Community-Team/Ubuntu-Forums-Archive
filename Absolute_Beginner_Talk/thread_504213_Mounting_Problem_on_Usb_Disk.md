---
title: "Mounting Problem on Usb Disk"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by FotiX on 2007-07-18
I am using Ubuntu Feisty. Everything with mounting my external usb disk runs fine except from one thing. Everytime I unplug it or restart, the usb-disk doesn't unmount. So the next time I plug it in the disk mounts as (diskname)_ and so on.

You can see for yourselves:
[[IMG]http://img170.imageshack.us/img170/8505/screenshotvk5.th.jpg[/IMG]](http://img170.imageshack.us/my.php?image=screenshotvk5.jpg)

How can I fix this?

---

### Post by deadlikeoscar on 2007-07-18
So what you are saying is that the drive doesn't unmount and every time you remount it, it adds another entry that is filename_ and then filename__ and so on so it keeps adding an _ (underscore) everytime? Are you right clicking on the drive and selecting to unmount it before you pull it out? Does rebooting remove those entries?

---

### Post by FotiX on 2007-07-18
I think that it should unmount by itself like it does in Kubuntu. Rebooting doesn't remove these entries, unfortunately. Anyway, i could make do if someone would tell me how to remove these entries. :D

---

### Post by aitorcalero on 2007-11-15
Have you been able to resolve this issue? I have the same problem too!!!

I've just found a solution:

[http://www.linuxquestions.org/questions/linux-newbie-8/hotplug-mounting-to-different-different-directories-599359/]("http://www.linuxquestions.org/questions/linux-newbie-8/hotplug-mounting-to-different-different-directories-599359/")

Just only need to remove all of the underscore directories

---

