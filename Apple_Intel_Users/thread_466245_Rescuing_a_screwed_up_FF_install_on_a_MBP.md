---
title: "Rescuing a screwed up FF install on a MBP"
date: 2007-06-06
forum: Apple Intel Users
---

### Post by ThufirHawat on 2007-06-06
I installed originally on my 2.33GHz C2D MBP Win XP with Boot Camp, then I overwrote the additional Win XP partition with Feisty Fawn.
Thanks to many of you I have been able to install the ATI drivers and got a usable system, which I updated and was beginning to use.
Having at home a WPA2 WIFi network, I started delving into madwifi and got nowhere.
Also, by some unfortunate coincidence, I screwed up, while fiddling with madwifi, my Ubuntu installation.
I took my alternate Ubuntu CD and thought to rescue my installation. No way...
I am now left with an unusable (it does not boot) Ubuntu, a ridiculous swap partition I added when overlooking an ambiguous command, and a rather unhappy FF user (me...).

The 25'000 EUR (or $ or £) question is the following:

knowing that I have ReFIT that works pretty well, knowing that I have the following partitions:
91 GB [Mac OS X, do not wish to touch], 
18.36 GB [screwed -up Ubuntu, to be re-formatted],
161.8 MB [swap, please don't laugh..., to be re-formatted],

how can I re-partition the disk in a suitable way, without a swap partition (i have 2 GB RAM), without touching my Mac OS X, without re-installing WinXP and without screwing-up big time again?

This Ubuntu trip is teaching me humility, if not much else...

Thanks folks!

---

### Post by ronocdh on 2007-06-06
I would load the Ubuntu installer disc (I prefer the alternate, but use the live/desktop one as long as you don't mind setting up the fglrx driver) and erase the swap and old Ubuntu partitions. Erase them, click Apply, then you might want to format them as FAT32 and Apply, also. I'm not sure whether the FAT32 is necessary, but perhaps it'll make it easier for OS X to understand the freespace.

Then in OS X you should partition the drive again how you want it. You will lose all Windows and Ubuntu data, but I think you've come to terms with that already. At least by partitioning from within OS X, you know your OS X will remain happy and safe. You might also consider trying to boot from the OS X installer disc and partitioning via Disk Utility, if that's possible... I would personally use the terminal in an OS X native boot session and the **sudo diskutil resizeVolume** command.

---

### Post by ThufirHawat on 2007-06-06
> **ronocdh said:**
> I would load the Ubuntu installer disc (I prefer the alternate, but use the live/desktop one as long as you don't mind setting up the fglrx driver) and erase the swap and old Ubuntu partitions. Erase them, click Apply, then you might want to format them as FAT32 and Apply, also. I'm not sure whether the FAT32 is necessary, but perhaps it'll make it easier for OS X to understand the freespace.

Then in OS X you should partition the drive again how you want it. You will lose all Windows and Ubuntu data, but I think you've come to terms with that already. At least by partitioning from within OS X, you know your OS X will remain happy and safe. You might also consider trying to boot from the OS X installer disc and partitioning via Disk Utility, if that's possible... I would personally use the terminal in an OS X native boot session and the **sudo diskutil resizeVolume** command.

Hmm, thanks, ronocdh, but I am afraid my MBP no longer loads the Ubunt installer, i.e. even with the alternate installer (for AMD64/Intel) nothing happens, as the keyboard seems frozen and I have no access to any key or arrow.
I am therefore unable to delete the partitions to be eliminated. 
Looks like I am stuck on that...

---

### Post by ronocdh on 2007-06-07
> **ThufirHawat said:**
> Hmm, thanks, ronocdh, but I am afraid my MBP no longer loads the Ubunt installer, i.e. even with the alternate installer (for AMD64/Intel) nothing happens, as the keyboard seems frozen and I have no access to any key or arrow.
I am therefore unable to delete the partitions to be eliminated. 
Looks like I am stuck on that...
Unable to do it via the Ubuntu disc perhaps, but what about booting from the OS X disc and removing the partitions in Disk Utility like that?

---

### Post by ThufirHawat on 2007-06-07
> **ronocdh said:**
> Unable to do it via the Ubuntu disc perhaps, but what about booting from the OS X disc and removing the partitions in Disk Utility like that?

I tried that too, but it does not work, because it considered them volumes, not just partitions.
So what I did was ( I am paranoid as most OS designers) erase the disk after the back-up and re-start from scratch.

By now I am getting more knowledgeable about this, of course, and it worked.
How to do the whole thing?

Let me list what I have learned from you, ronocdh, and from some other gentlebeings.

*DISCLAIMER: in spite of the weird belief of the Linux users' community, there are no magic recipes to provide, and thousands of messages and web pages are lost by providing ultra-detailed informations which have a very short life expectation...*

**[SIZE="3"]HOW TO CREATE A DUAL-BOOT MacBook Pro (2.33 GHz, C2D CPU), in June 2007, using FF 7.04[/SIZE]**

**a.** install BootCamp and partition your disk with it, leaving whatever for your Linux system.
    Leaving less than 10 GB for Linux is probably a bad idea.
**b.** use the Ubuntu CD which can be identified as follows: Alternate (that is text only, not the live installer) AMD 64 (never mind, this is the right one). 
If you have enough RAM, i.e. at least 2GB, do not add any swap partition. 
Once installed with the text-based installer in the Linux partition of your HD, you will have to make up for various shortcomings of Ubuntu, namely:
1. update your installation, by being connected to an Ethernet network (nothing else will do-believe me) somewhere and executing the following commands [detail them];
2. using the synaptics package manager, install the qsynaptics package, as it contains a slightly better trackpad emulation that the unusable pathetic shameful crap that comes standard with the Ubuntu distribution and shouldn't be there;
3.  install the closed ATI drivers, otherwise forget about using Gnome, by using the following terminal commands [list them];
**c. **only at this point, install rEFIt, which allows to choose the boot OS, as if you do it beforehand you will not be able to use the text-based Ubuntu installer [the fact that the rEFIt developers just shove the responsibility to Apple seems to me very undignified, and not technically defendable]
**d.** install hubackup using the synaptics package manager and promptly thereafter make two copies of your Linux partition onto reliable, GPT formatted, hard disks;
**e.** to get wireless then ……[still to be written]

There, it isn't rocket science, and it will probably last only between 4 and 10 months, before getting hopelessly obsolete...
Given that you are probably one of the leading GIC (Gurus In Charge), perhaps you'd care to tell me what did I miss...

---

### Post by ronocdh on 2007-06-07
> **ThufirHawat said:**
> **a.** install BootCamp and partition your disk with it, leaving whatever for your Linux system.
    Leaving less than 10 GB for Linux is probably a bad idea.
No, I disagree. In fact, my Ubuntu installation is currently installed on a 6GB partition. This is because the only thing I need space for is essentially applications, as I store all my data (media and documents) on my OS X volume and share across them. Alternately I could place them on my FAT32 WinXP party, but you're only talking dual booting here.
> **b.** use the Ubuntu CD which can be identified as follows: Alternate (that is text only, not the live installer) AMD 64 (never mind, this is the right one).
To be totally clear, the AMD64 disc can (and I believe *should*) be used by those with Core2 Duo processors, but the 32-bit (or i386) build will work, too, just with reduced processor performance. Also, the "alternate" installer disc is used for its text-based interface, which means the user doesn't have to deal with the X server fail until after Ubuntu is installed on the drive and attempts to boot into it. The live CD would still work, but you'd have to install the fglrx driver before even attempting to install.
> If you have enough RAM, i.e. at least 2GB, do not add any swap partition.
I've run Feisty on 1GB with no swap partition. In general, on these laptops I'd recommend not using a swap partition and creating a swapfile instead. This can be done at any point after the installation; I have many times just not even done this, as Ubuntu runs pretty light IMO and it's not necessary, given my computing habits.
> 1. update your installation, by being connected to an Ethernet network (nothing else will do-believe me) somewhere and executing the following commands [detail them];Yes, this is vital! DHCP-enabled ethernet will get you online out of the box, but wireless will not work. For the Atheros chipsets, I recommend using Madwifi; [here's a post]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") about getting that set up. Alternatively there's always ndiswrapper, which gets a lot of people running, but it's a kludge and not open source, so I encourage you to try Madwifi first.
> 2. using the synaptics package manager, install the qsynaptics package, as it contains a slightly better trackpad emulation that the unusable pathetic shameful crap that comes standard with the Ubuntu distribution and shouldn't be there;
This is also possible via the terminal command **sudo apt-get install qsynaptics** or **sudo apt-get install gsynaptics** (preferences vary). However, beyond this stage you'll need to edit your xorg.conf file to enable this driver. To do this, use the terminal command: ```
sudo gedit /etc/X11/xorg.conf
```Then, under the section for your trackpad, add:```
Option     "SHMConfig"     "true"
```Then (last step!) add the command "qsynaptics" (or "gsynaptics," if that's what you've chosen) to your startup items. This option is under Settings>Preferences (or Admin?)>Session, IIRC.
> 3.  install the closed ATI drivers, otherwise forget about using Gnome, by using the following terminal commands [list them];
I believe you want the following: 
```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
Additionally it may be necessary to run **sudo dpkg-reconfigure xserver-xorg** and manually add the resolutions you wish to appear in the Ubuntu Screen Resolutions panel. (For example, the native resolution for the 15" MBP is 1440x900.)
> **c. **only at this point, install rEFIt, which allows to choose the boot OS, as if you do it beforehand you will not be able to use the text-based Ubuntu installer [the fact that the rEFIt developers just shove the responsibility to Apple seems to me very undignified, and not technically defendable]
This is news to me. I'm pretty sure I've left rEFIt installed while wiping Ubuntu and reinstalling. I think you may be mistaken about this (perhaps you ran into a coincidental glitch), but I am willing and eager to stand corrected. Hopefully this has helped you. Thanks for always being patient, Thufir! You seem very dedicated to learning Ubuntu, and I admire it. =) Hope to see you around here more often.

---

### Post by ThufirHawat on 2007-06-08
That  I am not the only chap with a keyboard problem with rEFIt may be seen through this:
[http://refit.sourceforge.net/doc/c4s3_keyboard.html](http://refit.sourceforge.net/doc/c4s3_keyboard.html)
There is in my case a perfect repeatability, i.e. refit ON, keyboard disabled; refit OFF, keyboard working, so I may draw my own conclusion, which is that the rEFIt developers actually haven't bothered to investigate the interaction of their boot loader with the keyboard driver.
As for the rest, thank you ronocdh-I owe much to your patient and clear instructions! Much obliged.
I think that by next week I should be able to add most of your corrections, complete the WiFi bit (I am still not entirely convinced: the madwifi procedure you point at no longer works, as some URL is now dangling).
Next week I am attending an Open Source conference in Amsterdam, so I will work on this a bit more once back.

---

### Post by ronocdh on 2007-06-08
> **ThufirHawat said:**
> That  I am not the only chap with a keyboard problem with rEFIt may be seen through this:
[http://refit.sourceforge.net/doc/c4s3_keyboard.html](http://refit.sourceforge.net/doc/c4s3_keyboard.html)
There is in my case a perfect repeatability, i.e. refit ON, keyboard disabled; refit OFF, keyboard working, so I may draw my own conclusion, which is that the rEFIt developers actually haven't bothered to investigate the interaction of their boot loader with the keyboard driver.
As for the rest, thank you ronocdh-I owe much to your patient and clear instructions! Much obliged.
I think that by next week I should be able to add most of your corrections, complete the WiFi bit (I am still not entirely convinced: the madwifi procedure you point at no longer works, as some URL is now dangling).
Next week I am attending an Open Source conference in Amsterdam, so I will work on this a bit more once back.
I agree that the problem is universal; I literally have never heard of a person trying rEFIt on the MBP C2Ds who didn't have this problem. However, I have had pretty good results with developing a "keyboard voodoo," which admittedly was initially entirely improvised, but has now become rather standardized. :D Sorry if I came across as nihilistic on that point....

I've tested the link I gave you, pointing to widemos's post, and it works for me. However, here it is again without formatting: [http://ubuntuforums.org/showthread.php?t=429641](http://ubuntuforums.org/showthread.php?t=429641)

But please keep in mind that Madwifi seems to fail on the 2.6.20.16 kernel, so you'll have to boot from .15 for it to work. [More on that here]("http://ubuntuforums.org/showthread.php?t=460493").

---

### Post by pfistech on 2007-06-15
> **ThufirHawat said:**
> That  I am not the only chap with a keyboard problem with rEFIt may be seen through this:
[http://refit.sourceforge.net/doc/c4s3_keyboard.html](http://refit.sourceforge.net/doc/c4s3_keyboard.html)
There is in my case a perfect repeatability, i.e. refit ON, keyboard disabled; refit OFF, keyboard working, so I may draw my own conclusion, which is that the rEFIt developers actually haven't bothered to investigate the interaction of their boot loader with the keyboard driver.
I'm sorry, but I feel I have to respond to this allegation. First off, there is no "the rEFIt developers", there is just me, and I have a well-payed day job that comes first.

Now, for rEFIt's interaction with the "keyboard driver". rEFIt runs inside the EFI environment. (U)EFI is a new firmware standard supposed to replace BIOS. It has very nice, documented, high-level C APIs. Those APIs is all that rEFIt uses, and it's several layers removed from the actual keyboard driver and hardware.

If you boot the Ubuntu CD, you're booting a BIOS-based operating system. To make that happen, a special part of the firmware kicks out most of the EFI stuff and loads BIOS-compatible firmware components instead, then runs a standard BIOS boot process. All that rEFIt does is to call that special part of the firmware, and the only information passed is the string "HD", "CD"  or "USB". At that point, rEFIt stops running, and is removed from memory along with most of EFI.

The problem you're having occurs quite a bit later, after the BIOS emulation has loaded a Linux boot loader from the CD. It's very hard to see how rEFIt would influence that, given that it's no longer running, has only talked to the driver through regular APIs, and hasn't talked to the hardware at all. The issue has been investigated, and while it initially appeared to happen only when rEFIt was loaded, it was later found to happen also when you bypass rEFIt, and to be non-deterministic in both cases.

If you have suggestions how I'm supposed to "fix" this or further investigate it, please go ahead.

---

### Post by ThufirHawat on 2007-06-15
> **pfistech said:**
> I'm sorry, but I feel I have to respond to this allegation. First off, there is no "the rEFIt developers", there is just me, and I have a well-payed day job that comes first.

Now, for rEFIt's interaction with the "keyboard driver". rEFIt runs inside the EFI environment. (U)EFI is a new firmware standard supposed to replace BIOS. It has very nice, documented, high-level C APIs. Those APIs is all that rEFIt uses, and it's several layers removed from the actual keyboard driver and hardware.

If you boot the Ubuntu CD, you're booting a BIOS-based operating system. To make that happen, a special part of the firmware kicks out most of the EFI stuff and loads BIOS-compatible firmware components instead, then runs a standard BIOS boot process. All that rEFIt does is to call that special part of the firmware, and the only information passed is the string "HD", "CD"  or "USB". At that point, rEFIt stops running, and is removed from memory along with most of EFI.

The problem you're having occurs quite a bit later, after the BIOS emulation has loaded a Linux boot loader from the CD. It's very hard to see how rEFIt would influence that, given that it's no longer running, has only talked to the driver through regular APIs, and hasn't talked to the hardware at all. The issue has been investigated, and while it initially appeared to happen only when rEFIt was loaded, it was later found to happen also when you bypass rEFIt, and to be non-deterministic in both cases.

If you have suggestions how I'm supposed to "fix" this or further investigate it, please go ahead.


Didn't mean to slander anbody. Wasn't aware it occurs without rEFIt as well, though it never occurs with me when rEFIt is not present.

How to investigate: in the good old times when I was developing VAX/VMS real-time device drivers (quite a few years ago) I would have done the following:

1. Got myself a small RAM resident dump utility capable of relocating itself;
2. With a symbolic debugger stepped through the boot code until I find where it screws up;
3. Taken a snapshot of the stack, the shared variables and a dump of the wired physical RAM then;
4. Repeat without rEFIt.

Your description is quite clear, but it still leaves the door open at least to the
 following possibilities:

a. your clean-up is not complete and you leave some memory messed up before exiting (have seen this occur many times in my career);
b. the EFI interface may contain a timing mistake, which is not your fault (ditto);
c. your code does not contain ultra-cautious provisions (superfluous boundary check, index constraining, etc.), so that some overflow may occur, especially if the compiler is too permissive.

---

