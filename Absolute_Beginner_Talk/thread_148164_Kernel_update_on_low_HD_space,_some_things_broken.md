---
title: "Kernel update on low HD space, some things broken"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Zeroangel on 2006-03-21
OK, I tried to do a kernel update with 75MB of free space. The download said 22MB so I thought that it would be safe to do (because it would overwrite the new kernel, right?), but I guess I was wrong. 

I ran the update but now I have 0MB of hard drive space, I cannot use some commands (like cd) during sudo because linux says that it cannot find the command, and every time I try to run a gksudo program like nautilus or synaptic it says that it cannot copy 'the users Xauthorization file'

'df' outputs the following:```
/dev/hda1              2735516   2633840         0 100% /
varrun                  257516        80    257436   1% /var/run
varlock                 257516         4    257512   1% /var/lock
udev                    257516       132    257384   1% /dev
devshm                  257516         0    257516   0% /dev/shm
/dev/hdb1              4150700   3483084    456768  89% /home/dave
``` 
And when when I have already removed opt/firefox, ran the commands 'sudo apt-get clean' and 'sudo localpurge' but none of those methods grant any extra space to /

And I do not want to reboot because if the kernel is broken, then I might have to reinstall ubuntu from scratch. What should I do?

---

### Post by Zeroangel on 2006-03-21
Please do not ignore this post. This isnt some bull about not getting Nautilus' FTP working or this little bug that i'm experiencing in Firefox, or a wallpaper that i'm looking for. I could lose my system and have to redo about 30+ hours of tweaks and customization.

It might've been because of my own idiocy, but still...

---

### Post by Zeroangel on 2006-03-21
I think the problem has to do with the additional partitions created after the update, varrun and varlock.

I have managed to successfully umount the varlock partition but I cannot umount the varrun partition because I get an error that the device is busy. I tried -f but still no go.

Edit: Nevermind. I managed to unmount varrun using the -l switch. Yet I cannot access any of the gksudo (aka System > Admin) tools because there is no space on root.

Gonna try some more drastic things soon like moving large folders out of my root partition and into my home partition then symlinking it.

---

### Post by Zeroangel on 2006-03-21
Problem solved, worked around by moving /usr/share/doc to my home folder. I don't think I will ever again think 'Linux is not documented enough' given that I just had to move a thick 100+MB slab of documents out of my root partition. :D

Kind of choked that nobody helped me re: this. Especially given that I try to help others that are newer then myself when I can. :-?

---

