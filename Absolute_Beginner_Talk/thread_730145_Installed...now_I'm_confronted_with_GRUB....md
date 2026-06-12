---
title: "Installed...now I'm confronted with GRUB..."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Pickers on 2008-03-20
Okay I'm trying (oh god how I've been trying...) to install ubuntu onto my PC. Now I'm more than likely being a little stupid and making silly mistakes, however I've ran into a problem, but a first a little background...

I'm trying to install ubuntu 7.10 onto my 2.5" HDD that I salvaged from my now deceased laptop. The HDD is mounted within a external case that runs off USB. I have two other internal HDDs one with XP, the other I'm currently using for data storage.

The installation (from CD) goes fine, I have fiddle with the Live CD OS and I go through the motions, once it's installed I reboot and then bam! I'm confronted with the GRUB command line interface. So...now what do I do here? Has the installation not worked, does Unbuntu not like being installed on my external HDD. Or has it worked and do I now need to enter some commands to get the bloody thing to work?

Cheers!

---

### Post by Moop on 2008-03-20
For some reason your x server isn't starting. Try running 
```
sudo dpkg-reconfigure xserver-xorg
``` after you log in from the terminal.

---

### Post by louieb on 2008-03-20
So I'm guessing when you boot you get something lie this:
```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> 


```

1 st question what happens when you unplug the usb drive? 
Should get a grub error or it should boot to XP.
If you get a grub error. I'd get it to boot XP with usb detached. 
You do that by replacing the GRUB code in the MBR of your XP drive. 
If you have an XP CD it can do it. If not the [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") can do it too.
Heres a good explanation of how to do it either way. [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

 Once you get XP booting then we can go through the steps to get the PC to boot Ubuntu on the usb drive.

---

