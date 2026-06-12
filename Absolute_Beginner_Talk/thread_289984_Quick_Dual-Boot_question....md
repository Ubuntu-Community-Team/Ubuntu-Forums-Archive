---
title: "Quick Dual-Boot question..."
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by unexpected on 2006-10-31
Okay, so I'm about to install Ubuntu on a secondary hard drive, with XP as my primary partition. Ubuntu is going to take up the entire hard drive.

I'm at the installation screen, and have let Ubuntu automatically erase and configure this hard drive. It takes me to the "Ready to Install" Screen, and it tells me grub will be installed to (hd0).

do I want this? I searched the forums, and some people say don't install into the MBR of the first hard drive. Is this going to happen with this setup? Is it okay?

Ideally, I just want a screen that tells me if I want to boot into Ubuntu or Windows, with Windows being the default. Will this happen if I just go as is? or is there a better way?

---

### Post by petersjm on 2006-10-31
I've never booted off two HDs before, but in its simplest terms, Grub is the screen that asks you which OS you want to boot from. Installing it on hd0, though, when Ubuntu is on hd1 might cause some errors, but you had better wait for someone who knows what they're talking about first!

---

### Post by bulldog on 2006-10-31
Install GRUB on (hd1) and make this the primary bootdevice if you can.
You can make windows your primary boot by altering your menu.lst.
This way you can boot windows without GRUB if there should be any problem with it by switching the bootdevice in your BIOS.

If you can't set the second hdd as your primary bootdevice you can install GRUB on your first drive (hd0) without any problem.
To make windows your default OS you have to alter the menu.lst.

I prefere the first option though,if it's possible with your hardware.

Post back which one you choose,so I can help you with your menu.lst.

---

### Post by unexpected on 2006-10-31
aahh...

so the reason that it should not be installed on the MBR of hd0 is so that the windows drive can remain 'pristine'. That makes sense. Okay, I'm pretty sure I can make the 2nd drive the primary boot device...I have two SATA drives so, i'll just flip the order in the BIOS. I'll post back when I need help configuring Windows to be the default.

Thanks!

---

### Post by Rhubarb on 2006-10-31
Ok, it can be done, but it's a bit difficult to explain ... So I'll make it as simple as possible:

If you've got 2 Serial ATA hard disks (they're connected by a small often red cable), then you can easily do what bulldog says.
Your menu.list is hiding in:
/boot/grub/menu.list

You'll need to have a look through the forums here to work out how to tinker with it depending on your setup.

If you've got 2 normal ATA hard disks, then your best bet is to set them up as primary master and secondary master, with your CD ROM drive as a slave (primary or secondary, it doesn't matter).

It might be a good idea to disconnect your windows hard drive when installing ubuntu, just to make sure you don't accidentially wipe it / install grub onto it.

Doing it this was, as bulldog so rightfully points out, is so your windows drive can be completely untouched.  All you have to do is to enter the BIOS to select which drive will be used to boot up on.

---

### Post by Rhubarb on 2006-10-31
Ooops, didn't read your last reply there unexpected .... I guess I hadn't expected it!

No seriously now, just disconnect your windows drive, install ubuntu.
You won't have to worry about messing around with your grub menu.list

Enjoy!

---

### Post by bulldog on 2006-10-31
> **unexpected said:**
> aahh...

so the reason that it should not be installed on the MBR of hd0 is so that the windows drive can remain 'pristine'. That makes sense. Okay, I'm pretty sure I can make the 2nd drive the primary boot device...I have two SATA drives so, i'll just flip the order in the BIOS. I'll post back when I need help configuring Windows to be the default.

Thanks!

If you have two Sata disks then it changes a little :D 
Make the hdd where you install Ubuntu your master boot device and install GRUB on this hdd (hd0).
Let this one set as master so your windows keeps clean.

Now you have to map your hdd's in menu.lst in order to boot windows from GRUB.
Don't unplug your windows hdd.

---

### Post by unexpected on 2006-10-31
crap...I already installed it and made it hda1. I don't mind reinstalling it, but i'm getting two different opinions...

Rhubarb, if I disconnect my windows hard drive and reinstall, how will GRUB know that I have a Windows partition?

---

### Post by Rhubarb on 2006-10-31
> Now you have to map your hdd's in menu.lst in order to boot windows from GRUB.
Don't unplug your windows hdd.

Hmmm, yeah you could do it that way, it'd certainly be a lot easier than entering the BIOS everytime you want to use a different OS.
So Don't unplug your windows hdd.
You will have to edit that menu.list to make windows load by default (why?).

---

### Post by bulldog on 2006-10-31
> **unexpected said:**
> crap...I already installed it and made it hda1. I don't mind reinstalling it, but i'm getting two different opinions...

Rhubarb, if I disconnect my windows hard drive and reinstall, how will GRUB know that I have a Windows partition?

If you have the live ubuntu cd and a windows cd it's easely to be corrected.
But if it works you can leave it this way,and when you install windows again you can correct things.

---

### Post by Rhubarb on 2006-10-31
> **unexpected said:**
> Rhubarb, if I disconnect my windows hard drive and reinstall, how will GRUB know that I have a Windows partition?

Ahhhhhghghghh, maybe I should just shut up.  Too many cooks spoil the broth.
If you do disconnect your windows drive when you install ubuntu, you'll have to edit the menu.list manually to get windows to appear in the grub boot loader.

Just make sure your Ubuntu - destined hard drive is the one that is set to boot in the BIOS, then just install Ubuntu.
Grub will (should) automatically find windows on the other hard disk.

---

### Post by bulldog on 2006-10-31
> **Rhubarb said:**
> Hmmm, yeah you could do it that way, it'd certainly be a lot easier than entering the BIOS everytime you want to use a different OS.
So Don't unplug your windows hdd.
You will have to edit that menu.list to make windows load by default (why?).

In GRUB is Ubuntu set as the default bootoption.

If you want windows as the default you have to count your entrys in menu.lst, the recovery too, start counting with zero,one,two and so on.
If you get to windows,lets say 5, you have to change this section of the menu.lst,```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		2

```here is default a zero and change it into 5

Now will windows boot by default.

---

### Post by unexpected on 2006-10-31
Well, I wouldn't call it "working" per say. I can't figure out how to make the 2nd hard drive the primary boot device. ](*,) 

Things used to be easier when you just had to switch the jumper cables...

---

### Post by bulldog on 2006-10-31
> **unexpected said:**
> Well, I wouldn't call it "working" per say. I can't figure out how to make the 2nd hard drive the primary boot device. ](*,) 

Things used to be easier when you just had to switch the jumper cables...

You should have an option in your BIOS,just take a look and search for something as bootorder.

I have a MSI MoBo and I have to search too :D 

Have you an option when you boot to push F11 or something to change your bootdevice on the fly?
It's displayed at the bottom of your bootscreen,push DEL to open BIOS,push ??? to open bootoptions or something like that?

---

### Post by unexpected on 2006-10-31
What are the ramifications of just switching the cables in the computer, so that the new hard drive maps to the primary boot hard drives slot, and the old hard drive becomes the secondary one?

---

### Post by bulldog on 2006-10-31
> **unexpected said:**
> What are the ramifications of just switching the cables in the computer, so that the new hard drive maps to the primary boot hard drives slot, and the old hard drive becomes the secondary one?

Nothing I suppose,but altering the BIOS is much easier to do.

You can give it a try and see if Ubuntu will boot.
Windows will definitly not boot without mapping the drives in your menu.lst.

If you give it a go I'll look up the mapping and post it.

Okay the mapping!
Open your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
Alter your windows entry as follows,```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1
```

Save the file and close it.
Windows likes to be on your first hdd,and by mapping your hdd's it thinks it is.
So when you did this you make your Ubuntu hdd the default bootdevice,presuming GRUB is on this hdd.

If GRUB is on your windows hdd then don't do the mapping!!

---

### Post by unexpected on 2006-10-31
yea, I've looked for it in the BIOS settings, but for some reason, the Dell BIOS, in the boot order, only includes a generic "Onboard SATA Device" - it doesn't include specific hard drives, and that option boots to Windows.

---

### Post by Rhubarb on 2006-10-31
I'll shut up now.  Am going to bed now, 'nite ;-)
bulldog'll help you out there (thanks).

---

### Post by bulldog on 2006-10-31
> **unexpected said:**
> yea, I've looked for it in the BIOS settings, but for some reason, the Dell BIOS, in the boot order, only includes a generic "Onboard SATA Device" - it doesn't include specific hard drives, and that option boots to Windows.

Well you have to experiment a little then :D 

It's not a big thing though,only it can make life easier when things go wrong.
You can safely set GRUB on your windows MBR nothing wrong with that.

I'm let my dog out in rain and storm now,be back in 15 minutes.
If you have no more questions Ill be going to sleep then.
You can give me a PM though,but I'll read it over about 17 hours,if you need more help with anything.

---

### Post by unexpected on 2006-10-31
Aight, I gave it a go, and it definitely didn't like it. GRUB loaded up, but it "couldn't load partition" and when I selected Windows, it just hung at "Starting Up"

---

### Post by unexpected on 2006-10-31
Yeah, I think I'm just going to set the MBR to hd0. Thanks for your help though!

---

