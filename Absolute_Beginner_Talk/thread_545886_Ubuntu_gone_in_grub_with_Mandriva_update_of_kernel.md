---
title: "Ubuntu gone in grub with Mandriva update of kernel"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-09-08
Hi,

I updated to the latest kernel in Ubuntu- well at least the download manager said that it was available and I said download.
I did have a triple boot system.
I also updated the Mandriva Kernel also.
I have two SATA drives
XP on one, the two linux on the other.

At boot, the grub now gives me

Mandriva spring linux 2007
Madriva Linux safe mode
Windows Xp
Linux = 2.6.17-14
Linux = 2.6.17-15

The yellow penguin appears, so its mandriva and then the graphics fails - can't get past go.


Originally the grub gave me

Mandriva spring linux 2007
Madriva Linux safe mode
Windows Xp
Ubuntu
Ubuntu safe

I've lost Ubuntu - which also had a kernel upgrade to 2.6.15-29

To be replaced with the two choices of.

Linux = 2.6.17-14
Linux = 2.6.17-15

The mandriva gives me a failed graphics.
Xp boots and is Ok.

Has the new mandriva kernel screwed things up?
How can I get the ubuntu boot back?
How can i get mandriva back?

I haven't tried the safe mode yet - but all three mandriva choices fail the graphics and go isn't an option.

HELP!!!!!!!
I want Ubuntu back.

I know that the grub is attached to mandriva so I have to remedty that first - right now stuck

Thanks
Bill

---

### Post by overdrank on 2007-09-08
> **wapfu said:**
> Hi,

I updated to the latest kernel in Ubuntu- well at least the download manager said that it was available and I said download.
I did have a triple boot system.
I also updated the Mandriva Kernel also.
I have two SATA drives
XP on one, the two linux on the other.

At boot, the grub now gives me

Mandriva spring linux 2007
Madriva Linux safe mode
Windows Xp
Linux = 2.6.17-14
Linux = 2.6.17-15

The yellow penguin appears, so its mandriva and then the graphics fails - can't get past go.


Originally the grub gave me

Mandriva spring linux 2007
Madriva Linux safe mode
Windows Xp
Ubuntu
Ubuntu safe

I've lost Ubuntu - which also had a kernel upgrade to 2.6.15-29

To be replaced with the two choices of.

Linux = 2.6.17-14
Linux = 2.6.17-15

The mandriva gives me a failed graphics.
Xp boots and is Ok.

Has the new mandriva kernel screwed things up?
How can I get the ubuntu boot back?
How can i get mandriva back?

I haven't tried the safe mode yet - but all three mandriva choices fail the graphics and go isn't an option.

HELP!!!!!!!
I want Ubuntu back.

I know that the grub is attached to mandriva so I have to remedty that first - right now stuck

Thanks
Bill

Hi you can try and reinstall the grub with the live cd 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or if you don't have the live cd then you can try this 
[http://ubuntuforums.org/showthread.php?t=542683](http://ubuntuforums.org/showthread.php?t=542683)
Good luck!

---

### Post by louieb on 2007-09-08
Welcome to GRUB, kernel  updates, and multiple distributions. 
The long term fix is to let each distro use its own GRUB menu either by chainloading or using the configfile option.  

You say you can boot windows. Do you have [Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html") installed on XP?  You can use that or a live CD to edit your menu.lst files. If you use XP go here [http://www.fookes.com/](http://www.fookes.com/) and get Note Tab lite . Notepad does not like unix text files. 

Don't really have enough to go on to give specific instructions on what edits are needed. But if you go here. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) 
Herman has all you would  need to know about GRUB and dual booting.  Look at the [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") too.

---

### Post by Warren Watts on 2007-09-08
After recently experiencing problems with kernel updates modifying my menu.lst file, I have started making backup copies of menu.lst before I allow any kernel updates.  The Ubuntu kernal update last week re-wrote my menu.lst on a dual boot Ubuntu/Wolvix computer I have, completely removing  the entry for Wolvix.  Luckily I had been messing around with another aspect of GRUB and had made a backup for that, so I was able to just copy the Wolvix entry back into menu.lst.

---

### Post by wapfu on 2007-09-08
Thanks Guys,
Well it seems the latest kernel upgrade for both distributions has shot the nvidia graphics cards out the back door.
I'll try the 

Hi you can try and reinstall the grub with the live cd 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or if you don't have the live cd then you can try this 
[http://ubuntuforums.org/showthread.php?t=542683](http://ubuntuforums.org/showthread.php?t=542683)

First and see what happens.
Had to modify the mandriva grub menu list to get ubuntu when I installed it, so to get back ubuntu so i'll try the reinstall ubuntu grub.

Thanks
Catch you back if all fails.

Kind Regards
Bill

---

### Post by wapfu on 2007-09-09
Good News.
I tried the supergrub and was able to boot into Ubuntu 2.6.20-16.29 OK.
No problems with graphics - so the kernel upgrade is OK.
Ubuntu still Rocks!!!!!!!!!! - yeah for that.

Using the super grub I reinstalled the MBR - it said it was successful - however.
I still get the Mandriva grub and all its limited options and no Ubuntu.
So i've lucked out so far - but using the super grub on the live CD I can still get Ubuntu.
The mandriva grub says 1.5 and supergrub said it had restored Ubuntu 1 to the MBR.
Whats happened?

Ubuntu Reigns - still the superior distribution.
What to do about Mandriva though.

Kind Regards
Bill

---

### Post by louieb on 2007-09-09
Until you get it sorted out. Put a configfile entry in the other menu.lst. Example below: Just have to change the (hd#,#)  part to point it the Ubuntu / partition.

```
title        Ubuntu 
configfile   (hd0,5)/boot/grub/menu.lst
```More here [http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)

---

### Post by wapfu on 2007-09-10
Many Thanks Louieb.

Best reagrds
bill

---

### Post by wapfu on 2007-09-11
Hi Louieb,
works just fine.
Added the
title        Ubuntu 
configfile   (hd1,0)/boot/grub/menu.lst

Yeah - rocks.

Many many thanks.
Bill

---

### Post by louieb on 2007-09-11
Alright. :)You say you tried the super grub disk to get Ubuntu's GRUB to start 1st.  Well Super Grub can be confusing.  I could not have helped, But now that I know where Ubuntu is installed you can do this. 
In Ubuntu open a terminal  window. 
```
**sudo grub** 
```Now to confirm and change the PC to boot to Ubuntu's GRUB

```
find /boot/grub/stage1
```This should list (hd1,0) and wherever Mandriva is installed.  
Tell GRUB to use the Ubuntu's install partition.
```
root (hd1,0)
```Change the bootloader pointer in the 1st hard drives MBR to load Ubuntu's GRUB . 
```
setup (hd0)
```Your done.
```
quit
```If you want to keep booting Mandriva put a configfile option in Ubuntu's menu.lst.

---

