---
title: "Problem with Samba"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by pbb on 2006-01-06
I've connected my Ubuntu computer to a Windows XP-shared folder on another computer. This connection shows up on my desktop.

However, if I now want to open files from that share, for example in OpenOffice, the Open dialog doesn't allow to let me go beyond the File System level (/), while the desktop is one level higher. Also under /home/peter/Desktop, I cannot find the conenction to the Windows share.

Nautilus allows me to browse the share, but how do I access it from applications? Is Samba something that is supported by Nautilus, but not by applications in general?

---

### Post by bluefrog on 2006-01-06
nautilus access the shares but do not mount them. if you want to access them from an application you will need to mount them first

james

---

### Post by pbb on 2006-01-06
Okay, thanks! That is actually clear to me :-)

And to keep the mount after a reboot, do I add a line to /etc/fstab ? What would the format of this line be?

---

### Post by bluefrog on 2006-01-06
google for it..

something like //IP/share  smbfs ...

james

---

### Post by Zimmer on 2006-01-06
[QUOTE=pbb]I've connected my Ubuntu computer to a Windows XP-shared folder on another computer. This connection shows up on my desktop.

However, if I now want to open files from that share, for example in OpenOffice, the Open dialog doesn't allow to let me go beyond the File System level (/), while the desktop is one level higher. Also under /home/peter/Desktop, I cannot find the conenction to the Windows share.

Nautilus allows me to browse the share, but how do I access it from applications? Is Samba something that is supported by Nautilus, but not by applications in general?[/QUOTE]
Hello,
Have a look here for general Samba issues  posts #5 - #9
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)
and this
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
This will link to the Samba information which may help you acces Samba from within applications.( I have not tried this yet)
Personally I always copy files from a remote network location before opening them in an application, then save locally and copy back any altered file (paranoia!)

Regards

---

### Post by pbb on 2006-01-06
Thanks! That wiki-page was what I was looking for. It seems to work now (I've learned to not celebrate too early when using Linux ;-))
Thanks again

---

