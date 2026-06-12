---
title: "Ubuntu Install stops at 15%"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by johnz1 on 2006-09-27
Hello all,

Yesterday I acquired a IBM ThinkPad 600X (PIII 500MHz, 256MB, 11GB HDD). Last night I tried to install Ubuntu 6.06.1 and had problems. 

I booted to the CD and got into the Ubuntu GUI. I successully ran the Gnome Partition Editor and formated the hard drive to ext3. Then I ran Install. At Step 5, I selected "Erase entire disk: IDE1 master (hda) - 12.1GB IBM-DJSA-220." After hitting "Install" at Step 6, it proceeds to a "Installing System" window. So far so good. The install gets to 15%, where it is "Detecting file systems...", and it never proceeds. I got tired of waiting, so I went to sleep and left the system on all night. When I awoke, it was still sitting at 15%.

I tried installing Ubuntu two more times today. Same result.

Any ideas as to what the problem is?

Thank you for any help

---

### Post by hellmet on 2006-09-27
well, see if there are errors on the Windows drive if there are any.
second..u cud try the alternate cd..
This is becoming a serious bug now..
Every other beginner thread..is about the install getting stuck..
has the bug been filed?

---

### Post by wpshooter on 2006-09-27
Johnz1:

Does your computer have any other O/S or information on it that you need to keep or are you only going to be putting Ubuntu on it ???

---

### Post by johnz1 on 2006-09-27
No, I am trying to format the entire drive and ONLY run Ubuntu.

The system came with XP on it, but it wouldn't boot up. It wouldn't get past the boot screen with a black background, windows logo in the middle, and blue progress meter under the logo.

I dont have experience with Ubuntu, but I thought the Gnome Partition Editor would indeed format the drive and remove all information about previous OS's.

Should I use a different tool to format the drive to ext3 and try installing again, or should I pursue the Alternate CD?

---

### Post by Dinerty on 2006-09-27
Try the alternate CD mate, quite a few people have problems with the Desktop LiveCD.

gnome partition editor can play up some times, I had same problems when formating my hdd. In the end I used GParted Live CD, worked a treat.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by blx_286 on 2006-09-27
> **johnz1 said:**
> Hello all,

Yesterday I acquired a IBM ThinkPad 600X (PIII 500MHz, 256MB, 11GB HDD). Last night I tried to install Ubuntu 6.06.1 and had problems. 

I booted to the CD and got into the Ubuntu GUI. I successully ran the Gnome Partition Editor and formated the hard drive to ext3. Then I ran Install. At Step 5, I selected "Erase entire disk: IDE1 master (hda) - 12.1GB IBM-DJSA-220." After hitting "Install" at Step 6, it proceeds to a "Installing System" window. So far so good. The install gets to 15%, where it is "Detecting file systems...", and it never proceeds. I got tired of waiting, so I went to sleep and left the system on all night. When I awoke, it was still sitting at 15%.

I tried installing Ubuntu two more times today. Same result.

Any ideas as to what the problem is?

Thank you for any help

This may not be your prob, but I thought I would throw it out there [http://ubuntuforums.org/showpost.php?p=1523386&postcount=6](http://ubuntuforums.org/showpost.php?p=1523386&postcount=6)

You might also try reseating your memory or try the alternate cd.

Edited to add another thought. You could go to [http://ubcd4win.com/]("http://ubcd4win.com/") and download it and burn it to cd. It will create a bootable diagnostic cd and you can check your hard drive for bad sectors.

---

### Post by xpod on 2006-09-27
Try just running the installer and pointing it towards the whole unallocated hd and letting it do it all itself:D

---

### Post by johnz1 on 2006-09-27
Reseated the memory.
Used Gparted LiveCD to make the hdd one big, unallocated disk.
Ran Ubuntu install again and selected "Erase entire disk" again.

Same result: stuck at 15% (detecting file systems...)


anything else to try?

---

### Post by elpuerco on 2006-09-27
I had a similar problem when trying to install from the Ubuntu liveCD on more than one computer.

I then used the Kubuntu alternative cd and installed it flawlessly on four different computers.

Give it a go....;)

---

### Post by Dinerty on 2006-09-27
Your ram is quite low for Ubuntu and this maybe causing some problems, how about trying Xubuntu?

[http://www.xubuntu.org/](http://www.xubuntu.org/)

It's meant for lower end systems

---

### Post by GreenHawkIA on 2006-09-27
My issue when I've had this happen (multiple installs), has always always always been burning the install CD.  Did you order a CD (a pressed one) or burn it yourself?  If you did burn it yourself - do it again at a low speed 2x or so, and then check it with the disk checker on the CD (boot from the CD, it should be an option on the first menu you see), make sure it all checks out.  Then install.
Hope this helps.

---

### Post by Imsati on 2006-09-27
I had the same problem with my laptop (an old Inspiron 7000 running 256 MB memory and a P2 @ 333 Mh), only it would get stuck around 90% and hang indefinately.

I tried Xubuntu on it and it worked flawlessly (or as flawlessy as a P2 could be).

Give it a go with that, Like Dinery suggested--it'll be better.

---

### Post by johnz1 on 2006-09-27
Just tried Xubuntu. Unfortunately, I got the same results. Installation never got past 15%.
Also, I checked the CD in the menu to make sure its a good burn.

Anything else I can try to get this to work?

---

### Post by johnz1 on 2006-09-28
Here's a couple error messages that I get when Ubuntu/Xubuntu is loading, before it gets into the interface.

"IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!"

This one repeats for about two full screens:
"cs;pcmcia_socket1:time out after reset"


Hopefully this can shed some light onto the problem.

---

### Post by Dr. Dweebis on 2006-09-28
I had the same problem on a desktop.  My biggest problem (I think) was that the CD would go to sleep.  I kept it spinning by playing with the live CD (just opening different apps, stuff like that) and after a pause at 15%, it started loading up, and now it works fine.

Other than that - I did the same stuff - reseated memory, checked all the hardware plugs again.

Good luck - 

Dweebis




> **johnz1 said:**
> Just tried Xubuntu. Unfortunately, I got the same results. Installation never got past 15%.
Also, I checked the CD in the menu to make sure its a good burn.

Anything else I can try to get this to work?

---

### Post by johnz1 on 2006-09-28
Thanks for the idea Dr. Dweebis, but it didnt work. I ran every single app and it still just sat at 15%.

Thanks to everyone for the ideas and help.

I'll keep trying...

---

### Post by ian.l on 2006-09-28
I recommend using gdisk or fdisk to clean the partitions from the disk, then try installing again. Trying an alternate Ubuntu CD or an alternate distro altogether (Suse/Fedora) would be worth a try. If the problem is consistent across different distros it may be a hardware issue.

---

### Post by nickppv2000 on 2008-03-06
Had same problem, tried to change HDD but it really doesn't help. After that I take out one plank of memory and pass this 15% wall. Not sure what does it means but it works for me :)

---

