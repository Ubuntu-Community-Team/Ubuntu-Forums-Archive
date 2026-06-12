---
title: "Macbook Pro 3,1 and Ubuntu 14"
date: 2014-09-03
forum: Apple Hardware Users
---

### Post by brandonbyrum on 2014-09-03
I have a mid 2007 Macbook Pro 3,1 that isn't supported by Apple anymore. In an attempt to keep it running and save me a few hundred bucks I'm starting to explore the option of installing Linux on it.  Im a total newbie to Linux.  The machine is already set up to dual boot Win XP and OSX. Here are my questions. 

1. Will the Macbook Pro 3,1 handle the latest version of  Ubuntu? Ive always heard that Linux distro's are not power/memory/cpu hungry.
2. The Windows partition can be erased, it is no longer needed. Could Ubuntu be installed there?

---

### Post by moore.bryan on 2014-09-03
> **brandonbyrum said:**
> 1. Will the Macbook Pro 3,1 handle the latest version of  Ubuntu? Ive always heard that Linux distro's are not power/memory/cpu hungry.
Not to be flippant, but the short answer is "maybe." There *can* be issues with nVidia cards & Linux, but there are plenty of walkthroughs around and really helpful mates on the forum.

[quote=brandonbyrum]2. The Windows partition can be erased, it is no longer needed. Could Ubuntu be installed there?[/QUOTE]
Yup... Ubiquity--the Ubuntu install program--can help you go through that during the partitioning phase.

The specs of your particular Mac are really important in determining whether to go with the most recent release or one of the older--but still supported--long-term releases.

---

### Post by este.el.paz on 2014-09-03
> **brandonbyrum said:**
> I have a mid 2007 Macbook Pro 3,1 that isn't supported by Apple anymore. In an attempt to keep it running and save me a few hundred bucks I'm starting to explore the option of installing Linux on it.  Im a total newbie to Linux.  The machine is already set up to dual boot Win XP and OSX. Here are my questions. 

1. Will the Macbook Pro 3,1 handle the latest version of  Ubuntu? Ive always heard that Linux distro's are not power/memory/cpu hungry.
2. The Windows partition can be erased, it is no longer needed. Could Ubuntu be installed there?

@bb:

I'll add my $.05 . . . I was under the impression that any intel mac would be "easy" to get linux running, but on a recent thread here a gentleman had problems getting perhaps 14.04 to even boot the live desktop on an '08 MBPro . . . but he did get it going on an iMac I believe . . . .  So as m.b says, it is "case by case" . . . .  I've had my '10 MBPro with dual boot and now triple boot . . . I'm using rEFInd as an interface between what is probably "EFI" boot in your apple and the usual "BIOS" boot of most PC's and linux . . . finding it on sourceforge or from "rodbooks" will provide instruction on how to install . . . .  I ****don't*** recommend the "Bootcamp" option, try just using OSX DU . . . to prepare the partition.

But, having now spent a couple of years messing with various linux distros and getting the "flavor" or taste of the various forums, for the most part it's a better strategy to actually try something . . . and report here with the problems . . . while also searching google with your question/issue . . . linux is a DIY philosophy, rather than asking, "Can I do this?" . . . show "This is what I've done . . . ."  : - )  Of course it's always advised that you back up your OSX system ***before*** doing anything serious . . . but then, explore . . . play with it--there is always OSX if you need to do something, I'm still using 10.6.8 on my MBPro, extensively.

e.e.p.

---

### Post by brandonbyrum on 2014-09-03
Thank you for your responses. I guess the only thing to do is download and install. 
> The specs of your particular Mac are really important in determining  whether to go with the most recent release or one of the older--but  still supported--long-term releases.
I will gather the specs of the machine so you can advise what version should be used.

---

### Post by este.el.paz on 2014-09-03
> **brandonbyrum said:**
> Thank you for your responses. I guess the only thing to do is download and install. 

I will gather the specs of the machine so you can advise what version should be used.

@bb:

First simply try to download and boot a "desktop" version and see if you can test out the system, booting a DVD with the c key held down, etc -- before installing . . . see how that process goes--and as m.b says, probably better to use the LTS . . . which would be 12.04 or 14.04 . . . personally the XFCE or Xubuntu flavor has been the most stable for me on my MBPro . . . .  If it seems to be booting up OK, then when you have a half an hour, try the install . . . .

e.e.p.

---

### Post by brandonbyrum on 2014-09-03
One last question, I know im bugging the hell out of you. I cant burn a DVD, can the same thing be accomplished with a a usb drive?

---

### Post by este.el.paz on 2014-09-03
> **brandonbyrum said:**
> One last question, I know im bugging the hell out of you. I cant burn a DVD, can the same thing be accomplished with a a usb drive?

Yes it can, many people prefer that, but I have no experience with that . . . it might be do-able from DU in OSX? . . .  it needs to be a bootable file??? which probably is not the same as drag and dropping the file onto the drive, etc.  In Ubuntu or linux there are apps to do it, which I have, but haven't played with . . . some people recommend "unetbootin"???  which works only in windows, so if you still have windows you could try to make the bootable usb from the iso . . . .  But, you would have to find the details of booting the usb drive on google or someone else here . . . I don't know if the c key thing works for any boot-able drive, etc . . .

e.

---

### Post by moore.bryan on 2014-09-04
Getting a bootable usb for Mac can be a pita because of what Macs need on it... even using OSX I was never able to get one working, but there are some great tutorials out there to help out.

---

