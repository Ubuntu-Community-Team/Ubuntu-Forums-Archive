---
title: "Add terminal command at startup"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-19
I'm using captive drivers to mount my ntfs partitions. How can I add the following command to startup? I tried to do this at sessions but it didn't work. ```
sudo mount -t captive-ntfs /dev/hda1 /media/windows && sudo mount -t captive-ntfs /dev/hda5 /media/d && sudo mount -t captive-ntfs /dev/hda6 /media/e

```

---

### Post by Crosbie on 2006-07-19
My quick suggestion is to check out the awesomely-named 'bum' or Boot-Up Manager, which I think will allow you to add this sort of thing to your boot sequence with a GUI-driven tool.  It should be findable via Synaptic.

You may need expert/command-line help to do this, though.

---

### Post by frodon on 2006-07-19
This is a mount command and there's a file called "fstab" which contain all the mount command you want to execute on startup.
So open the fstab file : ```
sudo gedit /etc/fstab
```
And add a lines like that : ```
/dev/hda1 /media/windows captive-ntfs defaults,umask=0222  0 0
/dev/hda5 /media/d captive-ntfs defaults,umask=0222  0 0
/dev/hda6 /media/e captive-ntfs defaults,umask=0222  0 0
```Then reboot.

---

### Post by FuzZy2006 on 2006-07-20
I did as you said. Before, instead of 0222 it was none. Now, I've got a really big problem: when I am booting linux, it stops at checking all filesystems. Pls help.

---

### Post by frodon on 2006-07-20
I don't use captive so i can't help you more on this point but there's other threads in the forum with similar problems : 
[http://ubuntuforums.org/showthread.php?t=198618](http://ubuntuforums.org/showthread.php?t=198618)
[http://ubuntuforums.org/showthread.php?t=201445](http://ubuntuforums.org/showthread.php?t=201445)
[http://ubuntuforums.org/showthread.php?t=198618](http://ubuntuforums.org/showthread.php?t=198618)

Hope you'll find a solution.

---

### Post by FuzZy2006 on 2006-07-20
thx a lot. it works now. i should have searched

---

