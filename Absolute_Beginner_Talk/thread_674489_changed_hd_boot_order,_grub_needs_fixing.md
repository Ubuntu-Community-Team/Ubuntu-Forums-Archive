---
title: "changed hd boot order, grub needs fixing"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by anitract on 2008-01-21
I just installed Ubuntu today.  After the install, I ended up switching the HD boot order in my system bios.  Now, when grub loads it is referencing an incorrect location: (hd1, 1).

The correct location should be (hd0,1).

Ok, so I can edit it in grub and then boot into the OS - no prob.  But I'd like to fix it so I don't have to do this on every reboot.

Did some digging and thought I found a solution. I just altered /boot/grub/menu.lst so that (hd0,1) is being referenced.  It worked on my next reboot!  

But I spoke to soon.  I then did a system update and for some reason when I rebooted grub was trying to reach hd1 again.  What gives?  Getting into the OS it looks like my previous change was overwritten.  What do I need to do here to make this permanent?

I noticed device.map shows:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

...but since I swapped the boot order, sdb should be hd0.  Can I just edit this file?

---

### Post by dstew on 2008-01-21
When you update your kernel, grub updates its menu using the **#groot** line in menu.lst. Change the **#groot** argument to (hd0,1) and do **sudo update-grub** on the command line. Next time you update, it will use the correct grub root. Try this first. If no joy, edit /boot/grub/device.map as you suggest. See the [update-grub man page.]("http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz")

---

### Post by anitract on 2008-01-21
Alright...easy enough. :)  I made the change - we'll see what happens next update.  Thanks for the help!

One odd thing I noticed is that when I restarted my system, it hung almost immediately on the Ubuntu loading screen when it was coming back up.  I had to Ctrl-alt-delete to reset.  Did it again.  The 3rd time I was able to get back into my system.

I had noticed this behavior after I had installed the nvidia drivers and rebooted as well.

Are there any sort of error logs I can look at to determine why this is?

So far as I can tell it happens any time instigate I reboot from within the OS.

---

### Post by dstew on 2008-01-22
Yes, there are error logs in the /var/log directory. Logs to look at include boot and syslog. Also, the command **dmesg** gives the most recent system messages.

---

