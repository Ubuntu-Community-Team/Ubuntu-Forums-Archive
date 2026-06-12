---
title: "MacBook Pro Live CD does not work"
date: 2007-06-01
forum: Apple Intel Users
---

### Post by speedemonV12 on 2007-06-01
hi, im on a macbook pro core 2 duo, and im trying to get ubuntu going.. but i cant get the live cd to boot... everything goes fine, it starts the start up process, and then at the end of it, it closes, and says it could not load the X window environment. Is there anything that I can do to fix this? 

I know that there is an alternate installer, but if i use that to install ubuntu, and then i go to boot it up, will i still get the same problem? 

im trying to boot 7.04.


thanks!

---

### Post by tchorix on 2007-06-01
Hi speedemonV12

You don't really need the alternate installer.After rebooting with the live CD, then you see the problem that xserver will not launch. So you will just have access to a console. There you can install the ATI restrictive drivers and launch xserver. There you can install Ubuntu without any problem, but you will have to repite the process of installing the drivers in your definitive instalation. Follow the instructions that appear over here:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

at least it worked for me.
cheers
Tchorix

---

### Post by ronocdh on 2007-06-01
> **speedemonV12 said:**
> hi, im on a macbook pro core 2 duo, and im trying to get ubuntu going.. but i cant get the live cd to boot... everything goes fine, it starts the start up process, and then at the end of it, it closes, and says it could not load the X window environment. Is there anything that I can do to fix this? 

I know that there is an alternate installer, but if i use that to install ubuntu, and then i go to boot it up, will i still get the same problem? 

im trying to boot 7.04.


thanks!
Check the link in my sig. Long and short of it is I think you should use the alternate CD; only difference is that you'll get to install before you have to deal with the X failure.

If you don't mind dealing with it right away, then do so (with the live, non-alternate CD). At least that way you'll have a GUI installer, rather than the text-based one which the alternate CD has.

---

### Post by ronocdh on 2007-06-01
> **tchorix said:**
> Hi speedemonV12

You don't really need the alternate installer.After rebooting with the live CD, then you see the problem that xserver will not launch. So you will just have access to a console. There you can install the ATI restrictive drivers and launch xserver. There you can install Ubuntu without any problem, but you will have to repite the process of installing the drivers in your definitive instalation. Follow the instructions that appear over here:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

at least it worked for me.
cheers
Tchorix
Kudos on your quick draw!

---

### Post by speedemonV12 on 2007-06-01
ok thanks for that link.. it is very helpfull...

sort of off topic, does anyone know of a quide to set up refit, and then grub when installing ubuntu.. i have found some guides, but I already have windows and OS X installed via bootcamp... i created a third partitin using ipartition. Can i just follow the regular guides, and jump to the part about installing ubuntu?

---

### Post by ronocdh on 2007-06-01
> **speedemonV12 said:**
> ok thanks for that link.. it is very helpfull...

sort of off topic, does anyone know of a quide to set up refit, and then grub when installing ubuntu.. i have found some guides, but I already have windows and OS X installed via bootcamp... i created a third partitin using ipartition. Can i just follow the regular guides, and jump to the part about installing ubuntu?
If you are able to nondestructively add another partition to your system, yeah, you should be all set! I remember that after I had OS X and WinXP dual booting nicely, I repartitioned from within OS X to add a third partition, and it trashed my XP installation. No sweat, I just reinstalled that and then added Ubuntu, but it was an extra step.

Please post back whether you are able to do this. As I said, if you are able to add that third party trouble-free, then you're in the clear to proceed with the Ubuntu triple boot setup guides.

---

### Post by speedemonV12 on 2007-06-01
ok thanks.. i should be installing within the next 4-3 days.. i will let you know how things go. thanks for the help

---

