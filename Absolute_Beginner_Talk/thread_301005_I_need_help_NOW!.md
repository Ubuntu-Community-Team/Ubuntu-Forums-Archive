---
title: "I need help NOW!"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Entase on 2006-11-16
Please, I installed Ubnutu 6.06 last night on my brothers computer, when I installed it, I chose to partition the HD, and it installed, I was under the impression that one could choose which OS you wanted to boot, (by pressing esc. at boot, and accessing Grub) the problem is that windows isnt there, all thats there is Ubunutu, Ubuntu Safe Mode and something, else( thats not Windows) please help me, I need a literally step-by-step guide to fixing my problem, and being able to choose which OS to boot, seriously dont leave anything out, please not a single step, I mean like, for example, ( Click applications, highlight X, and select) please I need it that detailed, this is a serious problem that I need fixed today, please and thanks.


Entase

---

### Post by xpod on 2006-11-16
Me thinks your thread title is more likely to get you NO help m8

---

### Post by meng on 2006-11-16
Question 1, which you need to tell us before anything else: did you overwrite Windows or did you preserve a Windows partition? If you overwrote Windows, then grub won't find any other OS choices. If you're not sure of the answer, go to System > Admin > Disks and tell us what partitions are present on the hard drive there.

---

### Post by Entase on 2006-11-16
Sorry about the title, but I think you get the point, okay, im not on the computer with Ubuntu on it right now, and wont be able to get on later ,so can you just give me both ways, Im sure what you mean by no other OS choices, like in Grub, because in Grub, theres only Ubuntu, and Ubuntu Safe mode

---

### Post by xpod on 2006-11-16
Sorry m8.
It dont bother me at all.I actually like some of the less formal titles:D 

A lot of folks though prefer informative titles as apose to some of the funnier ones.

Good luck regardless

---

### Post by meng on 2006-11-16
Both ways? If you overwrote (i.e. deleted) Windows, then you'll have to reinstall Windows. If you didn't overwrite Windows, then you need to manually configure your grub menu.lst.

It's going to be difficult for me to write detailed instructions as you requested without knowing some specifics. And to write TWO sets of detailed instructions when you only will need ONE (we just don't know which one yet) is something I'm not prepared to do - it would take me an hour I think. I'm happy to help you, but there are limits!

---

### Post by jhenager on 2006-11-16
Grub comes up automatically, and Windows isn't listed, it is possible that you overwrote it.
Just a heads up to help you get prepared if that's what happened.
I hope there wasn't any irreplaceable data on the computer. This is why you do backups. I would recommend the Live CD in the future. Good luck.

---

### Post by Entase on 2006-11-16
If i didnt overwrite Windows, should I be able to access my files from Windows?

---

### Post by Henry Rayker on 2006-11-16
There are no both ways. If you installed over the Windows partition, it is gone. Reinstall Windows to get it back.

The other way, it will depend on what partitions are present. This information will come from System > Admin > Disks as was pointed out.

Additionally, demanding help "NOW!" is hardly proper etiquette for a voluntary support forum. None of us here are paid and only help to be kind. How would you like it if I showed up at your house (completely unannounced) and said, "I need food NOW!"

EDIT: if you didn't overwrite your partition, yeah, you should be able to access your files from windows...you should be able to access them in Ubuntu too, if the partition is mounted. A disk should show up on the desktop.

My personal feeling is that you did bork the Windows install.

---

### Post by meng on 2006-11-16
> **Entase said:**
> If i didnt overwrite Windows, should I be able to access my files from Windows?
Yes. Since you're not at your computer now, don't fret, when you are at the computer and you get the information, post then and help will be on the way.

---

### Post by Entase on 2006-11-16
Okay, say for example, I have World Of Warcraft on the computer, ( which I do) hould it come up, I didnt overwrite Windows?

---

### Post by meng on 2006-11-16
I would think so.

---

### Post by Henry Rayker on 2006-11-16
Well, it will depend on what you mean by, "should it come up".

---

### Post by meng on 2006-11-16
I'm beginning to think this is a little silly. It's rather a waste of time speculating on what might be if you're not actually in front of your computer. Let's all worry about the problem when we're in a position to learn some specifics/

---

### Post by Entase on 2006-11-16
Guys, seriously I BEGGING you, some dude said something about loading up console and inpitting something in the console regarding being able to boot windows from grub, can anyone help me out with that?

---

### Post by meng on 2006-11-16
Who said that about the console? I can't find it in this thread. Are you talking about a different thread? Or IRC? Or IM?

I've had enough of this. Sorry I couldn't help, but if I'm going to be spending time here I'd like to offer advice to members who can actually benefit from it.

---

### Post by Zeerak on 2006-11-16
Okay I was reading this thread hoping to learn something... Sadly due to lack of specifics I couldn't.

If you want help, which you seemingly do, then go on the computer with ubuntu, boot it up and tell us what you see when you go System > Admin > Disks

---

### Post by Entase on 2006-11-16
This is exactly what he said about the console, can someone please explain this to me step-by-step please?

This is incorrect, he says that he see's GRUB, but doesnt see XP on the grub list. This means that grub must be installed on the master drive in order for it to be booted at startup (if grub was on the slave, windows would simply be booting up)

Anyway, there is a simple solution to your problem:

*SImply add the windows xp entry to you Grub list 

==Instructions==

*load up ubuntu, go to console, and do the following:

sudo gedit /boot/grub/grub.conf

add the folowing:

title Windows XP Professional
rootnoverify (hd0,0)
chainloader +1

this means hd0 partition0 (hd0,0), change these to your values.

You will also see something like this:

default=0 

0 being the first option, then 1 then 2, set this to whatever one you want to be highlited when grub loads.

Hope this helps

---

### Post by lyceum on 2006-11-16
Run your windows XP disk in system recovery. If it can't find Windows, it is not there. If there is no grub, there is no Windows. How did you set up the partition? Did you tell it too loog for the largest empty space, or did you tell it to errase everythng? At this point, I hope you brother knowes what you were doing and has a back up of XP somewhere.

---

### Post by Entase on 2006-11-16
how do i access the console?

---

### Post by TheWizzard on 2006-11-16
> **Entase said:**
> Guys, seriously I BEGGING you, some dude said something about loading up console and inpitting something in the console regarding being able to boot windows from grub, can anyone help me out with that?

please understand that people here really want to help you, but they'll need some essential information. 

first brows the menu and search for something like konsole or terminal. you'll get something that lokks like a DOS prompt.
now enter:
```
sudo fdisk -l
```
typ your password
copy-past the result for us to read.

---

### Post by Henry Rayker on 2006-11-16
> **Entase said:**
> 
==Instructions==

*load up ubuntu, go to console, and do the following:

sudo gedit /boot/grub/grub.conf

add the folowing:

title Windows XP Professional
rootnoverify (hd0,0)
chainloader +1

this means hd0 partition0 (hd0,0), change these to your values.


Okay, when it boots into Ubuntu, you need to open a terminal. Terminal is the command line interface; I believe it is in Applications > Accessories > Terminal or something similar (I'm not at my Ubuntu system either).

Next, type "sudo gedit /boot/grub/grub.conf"
It will ask for your password.....give it.

Add the following to the bottom:
title Windows XP Professional
rootnoverify (hd0,0)
chainloader +1

However, where it says (hd0,0)

WE NEED THE INFORMATION WE HAVE ASKED FOR ABOUT 4 TIMES NOW! System > Administration > Disks

---

### Post by darrenm on 2006-11-16
Can you click Applications > Accessories > Terminal

Then in the window that pops up type ```
sudo fdisk -l
```, it will ask for a password. This is the password you chose when installing Ubuntu.

It should output something like the following
```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19269   154778211   83  Linux
/dev/hda2           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/hdb2           12749       24321    92960122+  83  Linux
```
If you see NTFS there anywhere you should be ok. If you can copy and paste what it says or try and write it down as accurately as possible then everyone will be waiting to help you out. Until you provide some specifics and not just ignore what people are asking you to do then you will be stuck.

---

### Post by Entase on 2006-11-16
Okay, I will repst later tonight with the information on the Disks, and whatI get from the Terminal, thanks guys.


Entase

---

### Post by lapsey on 2006-11-16
> **Henry Rayker said:**
> WE NEED THE INFORMATION WE HAVE ASKED FOR ABOUT 4 TIMES NOW! System > Administration > Disks

what good is that when 'Disks' doesnt appear on vanilla edgy's administration menu?

---

### Post by TheWizzard on 2006-11-16
> **Henry Rayker said:**
> Okay, when it boots into Ubuntu, you need to open a terminal. Terminal is the command line interface; I believe it is in Applications > Accessories > Terminal or something similar (I'm not at my Ubuntu system either).

Next, type "sudo gedit /boot/grub/grub.conf"
It will ask for your password.....give it.

Add the following to the bottom:
title Windows XP Professional
rootnoverify (hd0,0)
chainloader +1

However, where it says (hd0,0)

WE NEED THE INFORMATION WE HAVE ASKED FOR ABOUT 4 TIMES NOW! System > Administration > Disks

please don't shout. and try to solve problems using the terminal. i'm sure the result of fdisk -l helps us a lot more than a description of what the guy sees when he does System > Administration > Disks. besides, this is gnome specific and doesn't help people with other desktop environments.

---

### Post by Henry Rayker on 2006-11-16
That's weird...because Disks appeared on mine from initial install. It didn't on Dapper, but I'm certain it did on Edgy; I didn't want it there.

As for shouting, when someone demands help "NOW!" and wants multiple step by step walkthroughs of how to do something, without giving us any information that we have asked for, I think it is justified. It was requested a couple of times prior and I just figured he couldn't see it or something.

However, at this point, I'll bow out and let you guys handle this.

---

### Post by Entase on 2006-11-16
okay, in the terminal what exactly do I type to bring up the HD thingy?

---

### Post by Entase on 2006-11-16
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29668   238308178+  83  Linux
/dev/sda2           29669       30401     5887822+   5  Extended
/dev/sda5           29669       30401     5887791   82  Linux swap / Solaris

heres from terminal ,and what do you need from Disks?

---

### Post by BarfBag on 2006-11-16
> **Entase said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29668   238308178+  83  Linux
/dev/sda2           29669       30401     5887822+   5  Extended
/dev/sda5           29669       30401     5887791   82  Linux swap / Solaris

heres from terminal ,and what do you need from Disks?

Dude - you're sunk.  You erased your Windows partition.  All the data is gone for good.  All you can do now is reinstall XP.  None of your data will be there, but he'll have Windows again.

---

### Post by meng on 2006-11-16
This partition table tells us that you installed Linux over Windows. If you want Windows back, you are going to have to reinstall it. Your Windows data should be considered lost.

---

