---
title: "Dual boot, XP/ubuntu, two hard drives"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by bourne- on 2006-10-10
Hey guys whats up. I am not totally new to the linux world. I  just recently got ride of a xp/fedora core 4 dual boot. However I never really used fedora. In that setup I have both xp and fedora on one HD and it was partitioned and I used GRUB as my boot loader.
My ubuntu dual system will be different. I bought a new HD. So now I would like to have one HD with XP on it and one with ubuntu on it. My biggest question is in the the boot loader. I have read a bunch of different ways to do this. This time I would like GRUB to have its own little partition but I am not sure how to do this. I was going to try and use windows as the boot manager but that process seems way to complicated!!
Questions:
1. How do I create the serperate partition for GRUB?
2. How do I install to that partition?
3. If I make this small partition for GRUB does that take up a      drive letter?

thanks in advance
todd

ps. I must add that I am going to do this completely from scratch. I will be formatting both hd's so they will both be blank!!

---

### Post by bulldog on 2006-10-10
Wouldn't make a separate partition for your GRUB.

What I should do and done already is this.

Let windows completely original.

Make your second hdd the **first** bootdevice in your BIOS if possible.

When you install Ubuntu it will install GRUB on the same hdd and makes a entry for windows too.

Now if GRUB fails for what reason you can switch the bootdevice and start your windows from it's own loader.

Edit:If you use the alternate cd instead of the live cd,you have the choice where you want to install GRUB.
So if you can't make your second hdd master boot device I should use the alternate.

There are more options to acomplish this,but this is the easy way :D

---

### Post by gn2 on 2006-10-10
> **bourne- said:**
> Hey guys whats up. I am not totally new to the linux world. I  just recently got ride of a xp/fedora core 4 dual boot. However I never really used fedora. In that setup I have both xp and fedora on one HD and it was partitioned and I used GRUB as my boot loader.
My ubuntu dual system will be different. I bought a new HD. So now I would like to have one HD with XP on it and one with ubuntu on it. My biggest question is in the the boot loader. I have read a bunch of different ways to do this. This time I would like GRUB to have its own little partition but I am not sure how to do this. I was going to try and use windows as the boot manager but that process seems way to complicated!!
Questions:
1. How do I create the serperate partition for GRUB?
2. How do I install to that partition?
3. If I make this small partition for GRUB does that take up a      drive letter?

thanks in advance
todd

ps. I must add that I am going to do this completely from scratch. I will be formatting both hd's so they will both be blank!!

1.Not required, Ubuntu will load it in it's proper place for you.

See this thread for more info: [http://www.ubuntuforums.org/showthread.php?t=274444](http://www.ubuntuforums.org/showthread.php?t=274444)

To do it this way you can install either OS in any order on either drive, but the other drive must be unpowered.
Windows likes to be Master if on IDE channel.

---

### Post by equal on 2006-10-10
Bulldog's suggestion is definitely the way to go. That's a great idea.

---

### Post by bourne- on 2006-10-10
Ok sounds good, So can I just get the process straight before attempting this?

steps
1. Format and reinstall windows on first hard drive
2. diconnect that hard drive
3. Connect other Hard drive that will host ubuntu
4. Install ubuntu and leave grub loader on that hard drive.
5. One ubuntu boots up itself, shut computer down and reconnect windows hard drive.
6. Reboot computer, and I am assuming at this point GRUB will detect the windows partition and take over the booting process? without over writing windows boot loader?

Does this sound right?

And thanks for the quit response I very much appreciate it!

---

### Post by mahy on 2006-10-10
> **bourne- said:**
> 
Questions:
1. How do I create the serperate partition for GRUB?
2. How do I install to that partition?
3. If I make this small partition for GRUB does that take up a      drive letter?


Uhm, partition just for GRUB... never heard of it. Are you sure it's necessary and/or the best way to do it? The only thing i'm sure of is that is doesn't take up a letter in windows (that's what you meant, huh?). Linux partitions don't do it either.

I'd just put the windows disk as a primary device and linux disk as a secondary one. GRUB in the MBR of the first disk will do the trick; i'm not sure what else you expect to get...

Mahy

---

### Post by bulldog on 2006-10-10
I'm not entirely sure if this would work:6. Reboot computer, and I am assuming at this point GRUB will detect the windows partition and take over the booting process? without over writing windows boot loader?

You should use the Ubuntu hdd as bootdevice otherwise you won't see GRUB :D 


But no problems you only have to add the bootloader for windows at your menu.lst.

And I think you should manually put your windows partitions in your fstab,but that is fixed in 10 minutes.

**EDIT** turn this around!!
[Quote]
I'd just put the windows disk as a primary device and linux disk as a secondary one. GRUB in the MBR of the first disk will do the trick; i'm not sure what else you expect to get...

I tell you.
If you do a reinstall of windows it won't harm your GRUB.
If you do a reinstal of Ubuntu it won't harm your windows.

Thats why.

---

### Post by bourne- on 2006-10-10
> **bulldog said:**
> I'm not entirely sure if this would work:6. Reboot computer, and I am assuming at this point GRUB will detect the windows partition and take over the booting process? without over writing windows boot loader?

You should use the Ubuntu hdd as bootdevice otherwise you won't see GRUB :D 


But no problems you only have to add the bootloader for windows at your menu.lst.

And I think you should manually put your windows partitions in your fstab,but that is fixed in 10 minutes.

**EDIT** turn this around!!
> 
I'd just put the windows disk as a primary device and linux disk as a secondary one. GRUB in the MBR of the first disk will do the trick; i'm not sure what else you expect to get...

I tell you.
If you do a reinstall of windows it won't harm your GRUB.
If you do a reinstal of Ubuntu it won't harm your windows.

Thats why.


Well I am just piecing the process together from the thread that gn2 gave me.
[http://www.ubuntuforums.org/showthread.php?t=274444]("http://www.ubuntuforums.org/showthread.php?t=274444")
The guy kind of has the same setup as me. And he was told to disconnect the windows hd. But where I get confused now is how to boot. They say use f8 to choose between between windows or ubuntu. But to my knowledge pressing f8 takes you to safe mode options? I am a little lost.

---

### Post by gn2 on 2006-10-10
> **bourne- said:**
> Ok sounds good, So can I just get the process straight before attempting this?

steps
1. Format and reinstall windows on first hard drive
2. diconnect that hard drive
3. Connect other Hard drive that will host ubuntu
4. Install ubuntu and leave grub loader on that hard drive.
5. One ubuntu boots up itself, shut computer down and reconnect windows hard drive.
6. Reboot computer, and I am assuming at this point GRUB will detect the windows partition and take over the booting process? without over writing windows boot loader?

Does this sound right?

And thanks for the quit response I very much appreciate it!

Regarding your point 6, with The method I suggest, when you install Ubuntu and Grub on the same drive with Windows disconnected, Grub will never know about Windows unless you tell it. Your Windows is booted by the MBR as if it was a single booted PC.

Boot selection is done through selecting from the BIOS boot device selection screen, brought up by F8 (or whatever button for your BIOS version)

Each OS booted by it's own loader on it's own drive.
Keeps it simple for updates and re-installs. 
Each OS is entirely independent.

Access to files across drives can be configured later.

---

### Post by bulldog on 2006-10-10
> **gn2 said:**
> Regarding your point 6, with The method I suggest, when you install Ubuntu and Grub on the same drive with Windows disconnected, Grub will never know about Windows unless you tell it. Your Windows is booted by the MBR as if it was a single booted PC.

Boot selection is done through selecting from the BIOS boot device selection screen, brought up by F8 (or whatever button for your BIOS version)

Each OS booted by it's own loader on it's own drive.
Keeps it simple for updates and re-installs. 
Each OS is entirely independent.

Access to files across drives can be configured later.

Well mine is easyer!!:D 

Make your Ubuntu master and install GRUB on this hdd.
It will detect windows on your second hdd and make an entry in GRUB for windows,no hazzle with bios or what ever.

Windows wil allways start on itself with its own bootloader and only in case of GRUB trouble you have to go to the BIOS to switch the devices.

You only have to map your windows entry in menu.lst because windows like to be on the first hdd,but it is easy to fool windows by mapping.

---

### Post by bourne- on 2006-10-10
> **gn2 said:**
> Regarding your point 6, with The method I suggest, when you install Ubuntu and Grub on the same drive with Windows disconnected, Grub will never know about Windows unless you tell it. Your Windows is booted by the MBR as if it was a single booted PC.

Boot selection is done through selecting from the BIOS boot device selection screen, brought up by F8 (or whatever button for your BIOS version)

Each OS booted by it's own loader on it's own drive.
Keeps it simple for updates and re-installs. 
Each OS is entirely independent.

Access to files across drives can be configured later.


OOH I see. So if I want to say run windows. I need to go into the bios and make sure that the hard drive which houses windows in the first HD to be booted. And vice versa for ubuntu? So essential your bios becomes your boot manager...persay

---

### Post by bulldog on 2006-10-10
> **bourne- said:**
> OOH I see. So if I want to say run windows. I need to go into the bios and make sure that the hard drive which houses windows in the first HD to be booted. And vice versa for ubuntu? So essential your bios becomes your boot manager...persay


If you think that's the way to go,just do so.

Otherwise read my post.:D

Example of the mapping```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by gn2 on 2006-10-10
> **bourne- said:**
> OOH I see. So if I want to say run windows. I need to go into the bios and make sure that the hard drive which houses windows in the first HD to be booted. And vice versa for ubuntu? So essential your bios becomes your boot manager...persay

Not exactly, you don't need to go into the BIOS and change the order each time, just press the key that brings up the Boot Device list. F8 on my MSI board desktop PC, and F2 on my Toshiba Laptop for example.

You can go into the BIOS and change the boot order so that the desired default OS boots first.

Then you only need to bring up the Boot Order Device List to boot the other OS.

---

### Post by bulldog on 2006-10-10
To choose which OS has to be launched is very easy to set in the menu.lst.

But it's your choice how you want to do it.

---

### Post by bourne- on 2006-10-10
> **gn2 said:**
> Not exactly, you don't need to go into the BIOS and change the order each time, just press the key that brings up the Boot Device list. F8 on my MSI board desktop PC, and F2 on my Toshiba Laptop for example.

You can go into the BIOS and change the boot order so that the desired default OS boots first.

Then you only need to bring up the Boot Order Device List to boot the other OS.

Ok well for my system I am pretty sure that if I presss F8 I will get the safe mode options. ubuntu and windows must get added to that screen then?

[quote="bulldog"]
If you think that's the way to go,just do so.

Otherwise read my post.

Example of the mapping
Code:

### END DEBIAN AUTOMAGIC KERNELS LIST # This is a divider, added to separate the menu items below from the Debian # ones. title Other operating systems: root # This entry automatically added by the Debian installer for a non-linux OS # on /dev/hda1 title Microsoft Windows XP Professional map (hd0,0) (hd1,0) map (hd1,0) (hd0,0) rootnoverify (hd1,0) savedefault makeactive chainloader +1

[/quote]

Um sorry man that is waaay over my head. What exactly are you describing there?

---

### Post by bulldog on 2006-10-10
You have to decide which way you choose.

If you go my way I explain all to you what you need to do.

Otherwise I suppose GN2 will help you.

You can't use both ways.

---

### Post by bourne- on 2006-10-10
> **bulldog said:**
> You have to decide which way you choose.

If you go my way I explain all to you what you need to do.

Otherwise I suppose GN2 will help you.

You can't use both ways.

Oh wait sorry man I am sorry I just read over your other posts. That line of code is something that you add to the GRUB manager to recognize windows right? But it still allows windows to retain its bootloader without chaing it right?

---

### Post by bulldog on 2006-10-10
> **bourne- said:**
> Oh wait sorry man I am sorry I just read over your other posts. That line of code is something that you add to the GRUB manager to recognize windows right? But it still allows windows to retain its bootloader without chaing it right?

Yes to all.

You only need to make your Ubuntu the master hdd.
So you can boot GRUB and choose to launch windows or Ubuntu or even make one of them default OS.

In case of GRUB fails you can simply change the boot device in your BIOS and windows will start with it's own loader.


Reinstalling GRUB is 5 minutes with the live cd.

Reinstalling will not affect your windows.
Reinstalling windows will not affect Ubuntu.
No fidling with F8 or what ever,save as a house,you'll have always one of the two that will boot on it's own.
Don't unplug your windows hdd just make it the secundary one,so will your fstab be up to date and you can read your NTFS partitions.

Is the safest way in my opinion,and the easyist way.

Edit:
Maybe you should create a small FAT32 partition to exange stuff between windows and Ubuntu if you need so.

---

### Post by gn2 on 2006-10-10
> **bulldog said:**
> To choose which OS has to be launched is very easy to set in the menu.lst.

That's true, but it just isn't necessarily necessary.

---

### Post by bourne- on 2006-10-10
> **bulldog said:**
> Yes to all.

You only need to make your Ubuntu the master hdd.
So you can boot GRUB and choose to launch windows or Ubuntu or even make one of them default OS.

In case of GRUB fails you can simply change the boot device in your BIOS and windows will start with it's own loader.


Reinstalling GRUB is 5 minutes with the live cd.

Reinstalling will not affect your windows.
Reinstalling windows will not affect Ubuntu.
No fidling with F8 or what ever,save as a house,you'll have always one of the two that will boot on it's own.
Don't unplug your windows hdd just make it the secundary one,so will your fstab be up to date and you can read your NTFS partitions.

Is the safest way in my opinion,and the easyist way.

Edit:
Maybe you should create a small FAT32 partition to exange stuff between windows and Ubuntu if you need so.

Ok well I like the sounds of your way. It sounds like it will give me everything I want. Thanks to both you and gn2 though for your suggestions. 

So now I just need to go ahead and install both os's. So you say that the ubuntu drive must be the master drive and first in the boot process? 
Steps I am gonna take

1. format current HD for with windows and fat32 partitions
2. Format new HD with ubuntu and during process tell installer to leave GRUB on the current HD (will there be an option for me to tell ubuntu to install grub on the same partition as ubuntu?)
3. Come back here and get you to help me tell grub how to boot windows and ubuntu

That sound about rigt? I know I am probably missing something so I am sorry!!

---

### Post by bulldog on 2006-10-10
> **gn2 said:**
> That's true, but it just isn't necessarily necessary.

Nice said :D 

No it isn't but you **can** that's what counts.

---

### Post by gn2 on 2006-10-10
> **bourne- said:**
> Ok well for my system I am pretty sure that if I presss F8 I will get the safe mode options. ubuntu and windows must get added to that screen then?

There will be a button to press at boot time which when pressed brings up a list of your bootable devices. 
You need to find what this is. 
It is usually displayed on the splash screen at boot.

On the list will be your Hard Drives, CD ROM, and Floppy (if fitted)

Use arrows to highlight the one you want and hit "Enter" and the OS on that drive will boot.

If you take this solution, you won't need any help.

---

### Post by bulldog on 2006-10-10
> **bourne- said:**
> Ok well I like the sounds of your way. It sounds like it will give me everything I want. Thanks to both you and gn2 though for your suggestions. 

So now I just need to go ahead and install both os's. So you say that the ubuntu drive must be the master drive and first in the boot process? 
Steps I am gonna take

1. format current HD for with windows and fat32 partitions
2. Format new HD with ubuntu and during process tell installer to leave GRUB on the current HD (will there be an option for me to tell ubuntu to install grub on the same partition as ubuntu?)
3. Come back here and get you to help me tell grub how to boot windows and ubuntu

That sound about rigt? I know I am probably missing something so I am sorry!!

Almost:D 

First install windows and switch the hdd to secundary afterwards.

Install Ubuntu on the master hdd and don't unplug the other hdd.
So will GRUB detect windows and make an entry in GRUB for it.

If done,and be sure you do it this way,Ubuntu master,windows slave device.

Now you can start Ubuntu by GRUB **not** windows yet.

That's done by mapping the hdd's in your menu.lst afterwards.

You can load windows however by switching your boot devices in your BIOS,if you have trouble to get back here with ubuntu :D 

I tell you what to do when you have installed both OS's.,but can do now if you want to.

Edit:
2. Format new HD with ubuntu and during process tell installer to leave GRUB on the current HD (will there be an option for me to tell ubuntu to install grub on the same partition as ubuntu?)

If you have a master IDE and a slave IDE it's very important to install Ubuntu on the master and windows on the slave because you have no choice where you install GRUB if you use the live cd.

If you use the alternate cd you have the choice where to put GRUB,it's a bug in the live cd.

You can install windows with the other hdd unplugged however,but when you install Ubuntu plug all the devices in because they get detected by Ubuntu during install.

---

### Post by bulldog on 2006-10-10
> **gn2 said:**
> There will be a button to press at boot time which when pressed brings up a list of your bootable devices. 
You need to find what this is. 
It is usually displayed on the splash screen at boot.

On the list will be your Hard Drives, CD ROM, and Floppy (if fitted)

Use arrows to highlight the one you want and hit "Enter" and the OS on that drive will boot.

If you take this solution, you won't need any help.

No you need no help,but it gets annoying to wait and have to switch the drives every time you boot.

It's as safe as mine,but not as easy in all day use in my opinion.
It's better when you do a major install operation to do it right in one time.

---

### Post by gn2 on 2006-10-10
> **bulldog said:**
> 
but you **can** that's what counts.

Absolutely and completely agree with you on this point.

As you will have noticed I post on the dual-boot-dual-drive quite a bit.

The reason for this is that the "F8" method totally avoids all the difficulties that people continue to have with the standard method. 

There's no doubt that you know your stuff with Linux, much more than me, I just like simple solutions.

---

### Post by bulldog on 2006-10-10
> **gn2 said:**
> Absolutely and completely agree with you on this point.

As you will have noticed I post on the dual-boot-dual-drive quite a bit.

The reason for this is that the "F8" method totally avoids all the difficulties that people continue to have with the standard method. 

There's no doubt that you know your stuff with Linux, much more than me, I just like simple solutions.

You can easely change to my solution by reinstalling grub and make your Ubuntu drive the master boot device.

You can see what I mean then.
You can start Windows or Ubuntu through GRUB or make one of them the default OS.

And your windows boot is not affected by this,you can always safely boot into windows by your F8.

---

### Post by gn2 on 2006-10-10
[QUOTE=bulldog;1601751]it gets annoying to wait and have to switch the drives every time you boot.
QUOTE]

Drives don't need switched, after both OS's are installed on their own drives, both drives are left connected and powered.

In my experience it doesn't take any longer to re-boot by either method.

Doubt it's annoying to press F8?

---

### Post by bulldog on 2006-10-10
> **gn2 said:**
> [QUOTE=bulldog;1601751]it gets annoying to wait and have to switch the drives every time you boot.
QUOTE]

Drives don't need switched, after both OS's are installed on their own drives, both drives are left connected and powered.

In my experience it doesn't take any longer to re-boot by either method.

Doubt it's annoying to press F8?

No I suppose not,but you must have that possebility to change the drives,not everyone has it.

I have a master IDE and a Sata which could be master aswell slave at my desire.

So I haven't unplug anything,only make my choice once in the BIOS and there I go.

---

### Post by bourne- on 2006-10-10
> **bulldog said:**
> Almost:D 

First install windows and switch the hdd to secundary afterwards.

Install Ubuntu on the master hdd and don't unplug the other hdd.
So will GRUB detect windows and make an entry in GRUB for it.

If done,and be sure you do it this way,Ubuntu master,windows slave device.

Now you can start Ubuntu by GRUB **not** windows yet.

That's done by mapping the hdd's in your menu.lst afterwards.

You can load windows however by switching your boot devices in your BIOS,if you have trouble to get back here with ubuntu :D 

I tell you what to do when you have installed both OS's.,but can do now if you want to.

Edit:
2. Format new HD with ubuntu and during process tell installer to leave GRUB on the current HD (will there be an option for me to tell ubuntu to install grub on the same partition as ubuntu?)

If you have a master IDE and a slave IDE it's very important to install Ubuntu on the master and windows on the slave because you have no choice where you install GRUB if you use the live cd.

If you use the alternate cd you have the choice where to put GRUB,it's a bug in the live cd.

You can install windows with the other hdd unplugged however,but when you install Ubuntu plug all the devices in because they get detected by Ubuntu during install.


Well I have two sata drives...I hope thats not a problem. Sweet ok well I am going to attempt this then. So I should be back later. Will you still be around bulldog?

---

### Post by bulldog on 2006-10-10
> **bourne- said:**
> Well I have two sata drives...I hope thats not a problem. Sweet ok well I am going to attempt this then. So I should be back later. Will you still be around bulldog?

That's much easyer,why didn't you say so.

You can decide in BIOS which is the boot device.

No problems with that.:D :D
I will be here for two hours.

---

### Post by gn2 on 2006-10-10
> **bulldog said:**
> [QUOTE=gn2;1601789]

No I suppose not,but you must have that possebility to change the drives,not everyone has it.

I have a master IDE and a Sata which could be master aswell slave at my desire.

So I haven't unplug anything,only make my choice once in the BIOS and there I go.

I have two IDE's and Linux is on the slave drive with it's own Grub and boots as default OS from being first in boot list.

You can have Windows on SATA and Linux+grub on IDE slave with the IDE master connector not plugged in to any drive.

I'm not aware of any BIOS that doesn't have an option to bring up a boot device list?

---

### Post by gn2 on 2006-10-10
Windows on Master

Ubuntu & Grub on Slave (with master drive  disconnected at install time.)

---

### Post by bourne- on 2006-10-10
> **bulldog said:**
> That's much easyer,why didn't you say so.

You can decide in BIOS which is the boot device.

No problems with that.:D :D
I will be here for two hours.

Sorry man I didn't realize that it would be relavent. I am starting the reformant now. I have a laptop as well so I will nto be without access to this site incase something goes wrong along the way. GN2 man thanks alot for all your help!! I really appreciate you guys giving me a hand. Hopefully when I am done this I can help some other people out. Or even make a tutorial for dummies like me lol

But I will go start the process now.

---

### Post by bulldog on 2006-10-10
Okay,in case I'm gone when you come back I have made a Howto what you should do.

Boot Ubuntu and open a terminal and type,or copy/paste,
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
So you have a copy if something goes wrong.

To set the copy back type,```
sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
```
Only if something goes wrong ofcourse!!

Now we open the menu.lst to alter it,
```
gksudo gedit /boot/grub/menu.lst
```
This opens your menu.lst where your Ubuntu kernels and your windows should be.
Now scroll to the end and you should see your windows entry,which we gonna alter to the following,```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1
```

Only add the two lines with map before them and rootnoverify into your windows loader.
Leave the rest as it is,so it looks like the one above in general.
Make sure you safe the file and you're done.

Now you can choose which OS you want to start with GRUB **and** if GRUB fails you can change the boot device in your BIOS to boot into windows without using GRUB.

To make Windows your default OS instead of Ubuntu you have to alter the following line in your menu.lst,```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```
You start counting entry's in your menu.lst and start counting with 0,1,2,3 and so on.
If windows is the fourth entry for example you change the default zero to 4.
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
```
The time before the actual booting begins is standard 10 seconds and you can make it 5 or 25 but don't make it zero because you have not a change to chance your desired OS,only by altering your menu.lst again.[3 seconds is fine to set]

If you need more guidance I'll be back tomorrow,just ask here and I'll find it and try to answer your questions.

Goodluck.

---

### Post by bulldog on 2006-10-10
> **gn2 said:**
> [QUOTE=bulldog;1601809]

I have two IDE's and Linux is on the slave drive with it's own Grub and boots as default OS from being first in boot list.

You can have Windows on SATA and Linux+grub on IDE slave with the IDE master connector not plugged in to any drive.

I'm not aware of any BIOS that doesn't have an option to bring up a boot device list?

Well I'm 54 years young :D and I know plenty PC's that haven't.
If you have a recent PC you should have it,but most people shouldn't know it's there :D

---

### Post by bourne- on 2006-10-10
Thank you very much for posting that. I may be a while. I just had a little problem getting my system to boot from the windows XP cd, It for some reason doesn't like linux. I had to first delete my old linux partition before I could get it to boot from the XP cd. But all is well now and I am just getting ready to reinstall XP

---

### Post by bourne- on 2006-10-10
um well that sucks lol. 
well i finished installing both os's and everything went by smoothing
however i never got an option of were to install GRUB
when I restarted the computer after finishing ubuntu install it just went right to the GRUB window. And both ubuntu and windows boot fine. So um? Where did I go wrong? Is there anyway to check where GRUB actually installed itself?

---

### Post by gn2 on 2006-10-10
Guess you didn't have the Windows drive unplugged when you installed Ubuntu and Grub?

Reason for unplugging Windows drive during Ubuntu install is that Grub can then only install to the Ubuntu drive.

I'm sure Bulldog will get you sorted, he's an expert at this type of thing.

---

### Post by gn2 on 2006-10-10
> **bulldog said:**
> [QUOTE=gn2;1601857]

Well I'm 54 years young :D and I know plenty PC's that haven't.
If you have a recent PC you should have it,but most people shouldn't know it's there :D

And are these PC's that can't give a boot device list capable of effectively running XP?

---

### Post by bourne- on 2006-10-10
> **gn2 said:**
> Guess you didn't have the Windows drive unplugged when you installed Ubuntu and Grub?

Reason for unplugging Windows drive during Ubuntu install is that Grub can then only install to the Ubuntu drive.

I'm sure Bulldog will get you sorted, he's an expert at this type of thing.

perfect. I thought i wasn't supposed to disconnect it. Oh well. I have bigger fish to fry right now. I still need to somehow get my wireless network card working.

---

### Post by bulldog on 2006-10-11
> **bourne- said:**
> um well that sucks lol. 
well i finished installing both os's and everything went by smoothing
however i never got an option of were to install GRUB
when I restarted the computer after finishing ubuntu install it just went right to the GRUB window. And both ubuntu and windows boot fine. So um? Where did I go wrong? Is there anyway to check where GRUB actually installed itself?

You had to make the Ubuntu drive the master bootdevice to get GRUB install on that hdd.
Have it told many times :D ,and I told GRUB will not ask on the live cd but install on the master by default.

But no harm done anyway.

You can check where GRUB is installed by trying to boot your windows hdd,if the windows loader is present,GRUB is installed on the right hdd,if not we have to replace it with the live cd.

If you want to do that give a shout,it's 10 minutes of your time.

Glad that every thing worked out with the install of two OS's,and welkom to Ubuntu.:D

---

### Post by bourne- on 2006-10-11
Dammit I think I forgot the very important step of switching the master hd's around dammit. Yeah I might try and switch it around. I would really like them to be completely seperate! And thanks for the welcome, although it isn't all peaches and cream, trying to get my wireless card to work is proving to be impossible.

thanks for all your help though I really appreciate it!!

todd

---

### Post by heroinbob on 2006-10-11
I can't get grub to recognize xp. I've tried this method a few times, but to no avail. I have also tried editing the grub list but that didn't work either. Something to do with the windows mbr?

---

### Post by bourne- on 2006-10-11
Well as it turns out I actually did install it correctly. I just forgot that I had. I just deleted my ubuntu install (going to reinstall fresh to see if I can get my wireless card to work). After I deleted my ubuntu partition and all its accompanying partitions I set the windows HD as the primary and tried booting the system and windows booted up fine.

So thanks again for all your help I really appreciate it!!
Hopefully I can get my wireless card working or I might have to try a different distro

---

### Post by confused57 on 2006-10-11
> **heroinbob said:**
> I can't get grub to recognize xp. I've tried this method a few times, but to no avail. I have also tried editing the grub list but that didn't work either. Something to do with the windows mbr?
In Ubuntu, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L"

then

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first

Post the output of these commands and someone should be able to help you...for the second command, you just need to post the entries used to boot your OSes.

---

### Post by SaltyMcCracker on 2006-10-16
Ok, 
I set my ubuntu drive to master, and unplugged the windows drive.  Then installed Ubuntu.  Now, before I plug back in the other drive I need to do the following?

1) Set drive to slave (gotta find the jumper settings online somewhere).  
2) Boot to ubuntu
3) Open up terminal
4)???  Do I just do what you had Bourne do?

---

### Post by confused57 on 2006-10-16
> **SaltyMcCracker said:**
> Ok, 
I set my ubuntu drive to master, and unplugged the windows drive.  Then installed Ubuntu.  Now, before I plug back in the other drive I need to do the following?

1) Set drive to slave (gotta find the jumper settings online somewhere).  
2) Boot to ubuntu
3) Open up terminal
4)???  Do I just do what you had Bourne do?

See this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

