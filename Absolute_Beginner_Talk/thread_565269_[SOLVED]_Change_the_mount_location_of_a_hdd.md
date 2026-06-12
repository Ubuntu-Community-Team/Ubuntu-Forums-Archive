---
title: "[SOLVED] Change the mount location of a hdd"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-10-02
How do you change the mount location of a hard drive? I've just reinstalled Kubuntu but the hard drive I was using for /home in my last installed is now mounted at /media/hdb1.

Does anyone know how to change this?

---

### Post by Jaearess on 2007-10-02
Alt+F2, then type "gksu gedit /etc/fstab" and press enter.

Find the line that looks similar to this (ignore the numbers and letters after UUID, as this will be different on your computer.):

```

UUID=1e1a248c-1e98-4499-8266-d7da324713df /media/hdb1 ext3    defaults        0       2

```

Change the "/media/hdb1" to "/home". Save the file, then reboot.

That should fix it.

---

### Post by NovaAesa on 2007-10-02
That didn't end up working. When I restarted, i got to the login screen and typed in my password, but before KDE could load, it came up with a small dialogue box saying that something was wrong and I needed to check my installation.

I booted in recovery mode and changed the file back to what it was origninally.

Any other ideas?

---

### Post by NovaAesa on 2007-10-02
The error message the came up was exactly as follows:

> Could not start kstartupconfig. Check your installation.

---

### Post by conehead77 on 2007-10-02
i think it should be /home/myharddrive

edit: the more i think about it it seems to be obvious that you cant mount sthg at the place where your home directory is, so i guess /home/myharddrive will do the trick (didnt try it though)
edit2: also i dont know if you need to create the "myharddrive"-directory first. i know you have to when mounting manually, not sure what its like with fstab

---

### Post by NovaAesa on 2007-10-02
Well that worked :). The problem is that it's not really mounted in the right location. On the hard drive, I had a directory called peter (which is my user name btw), and within that I had all my personal files. What I really want is to have the directory 'peter' under the directory /home.

This should be possible right? I had it like this in my last install, but that was because I had made that mount point during the install process. When installed last, I must have forgotten to put the mount point in during the partitioning part of the install.

So does anyone know how to mount it at /home ? I can do a reinstall if that's what it takes.

---

### Post by NovaAesa on 2007-10-02
After a reinstall (making sure to set the mount point carefully this time :)) it works.

After reinstalling, I found an option under K -> System Settings -> Advanced Tab -> Disk & File Systems from which I think I may have been able to change the mount point (just in case anyone every has the same problem).

Thanks for the help everyone

---

