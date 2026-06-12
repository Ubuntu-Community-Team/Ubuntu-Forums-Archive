---
title: "Windows not starting after installing Ubuntu"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by cramactive on 2007-04-02
I have a new VAIO laptop which came preinstalled with Vista. Through Vista, I created a 20GB empty partition and installed Ubuntu. Everything went well, I could even see my Windows partion and files from Ubuntu.

The problem was I couldn't actually boot into windows. (It wasn't in the GRUB). So, I followed direction to update my grub setup by adding the following:

title Windows Vista

root (hd0,0)

makeactive

chainloader +1 

This worked and I could see Windows Vista in the grub. However, when I try and boot into Windows it thinks I end up in system recovery land. I did all the recovery operation and ended up with the same issue, except now I have a fresh install which I can see the directories from Ubuntu but booting into Windows still thinks it has a problem.

So, I use the recovery disks I made for the Sony. (They do not include a Vista disk). This brings me to a screen where I can diagnose or restore the system. Trying to re-install windows begins to work, but then I get an error saying "Windows could not update the boot configuration" and it shuts down.

In the system recovery menu there is an option for the command prompt so I think I can get into the inner workings of Vista, I just don't know what to do.

Any help would be much appreciated...

Thank you so much

---

### Post by zvacet on 2007-04-02
[http://ubuntuforums.org/showthread.php?t=371530&highlight=vista]("http://ubuntuforums.org/showthread.php?t=371530&highlight=vista")

---

### Post by cramactive on 2007-04-02
Thank you, but that is the article that I got the original direction from. Problem is, grub can recognize Vista it just will not start. Trying to reinstall Vista results in an error that it can't configure the boot configuration. So, I cant launch windows to tell the computer to use windows boot manager.

---

### Post by zvacet on 2007-04-02
[http://ubuntuforums.org/showthread.php?t=358241&highlight=vista+install]("http://ubuntuforums.org/showthread.php?t=358241&highlight=vista+install")

[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx")

---

### Post by Neobuntu on 2007-04-02
I think you have perhaps set your GRUB Vista boot selection to a recovery partition of the computer instead.

---

