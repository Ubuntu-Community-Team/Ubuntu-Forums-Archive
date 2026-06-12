---
title: "Update woes"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Araj on 2007-10-30
I upgraded from FF to GG and got an error message half way through the installation routine saying it couldn't commit all the changes.

The system seems to boot into (K)ubuntu fine except:

(1) The NTFS partition I could access happily in FF doesn't mount any more. I had it set to mount to /media/windows at bootup. When I click on the partition in the new Dolphin file manager it gives the message "The mount point 'media/windows' is already occupied" - but I can't access any data.

(2) My keyboard layout seems to have gone back to default and I can't change it as System Settings (KDE/Kubuntu) is out of action (error message)

(3) My Thinkpad refuses to turn off or reboot from "log out" - I have to hold down the power switch.

What's my best option? Wipe everything and clean install GG, or is there an easy way to fix these problems?

Many thanks for any help

---

### Post by haldean on 2007-10-30
try running ```
update-manager -cd
``` in the terminal... the update tool should come up and say something about an incomplete upgrade. press "complete upgrade" (or something like that) and it should finish the upgrade and fix your problems!

---

### Post by Araj on 2007-10-30
Sounds good! I'll try that later - my laptop is at home.

---

### Post by mirontoli on 2007-10-30
Hi, I have the same problem: After upgrading from FF to GG it can't mount FAT32 discs: my USB stick and a FAT32 partition on my hard drive. I hope I can fix it with update-manager -cd

---

### Post by Araj on 2007-10-30
Thanks for the tip. Turns out I didn't have update-manager but the system nicely gave me a message telling me how to install it and then it ran through fine. System Settings are now available so I reconfigured my keyboard, which makes things a lot easier. The mount problem didn't get fixed,  but I noticed that in Dolphin, the partition said it was sda2 and not hda2, which was what the system previously called it, so I edited fstab and changed the h to an s and now it's mounted.

The remaining issue is that I can't shutdown - at least I think not. I left it trying to shut down for 10 minutes and then gave up waiting. Any ideas?

---

### Post by Seisen on 2007-10-30
I think they mean ```
update-manager -c -d 
```

---

### Post by haldean on 2007-10-30
```
update-manager -cd
```does the same as
```
update-manager -c -d
```;)

---

### Post by Araj on 2007-10-30
No ideas why shutdown doesn't work?

---

### Post by haldean on 2007-10-30
A few other people have had that problem as well. Check [url]http://ubuntuforums.org/showthread.php?p=3661207#post3661207
[/url] and see if it works for you.

---

### Post by Araj on 2007-10-31
Thanks for the link to the thread, but no joy - it makes no difference.

When I want to turn off, the screen goes blank except for the mouse, then the mouse disappears and the system hangs. The Kubuntu logo screen with the progress bar doesn't appear at all.

---

### Post by Araj on 2007-11-03
Gone back to Feisty :(

---

