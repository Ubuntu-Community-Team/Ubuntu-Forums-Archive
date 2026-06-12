---
title: "Help"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by squeezycheese on 2007-05-16
I installed ubuntu edgy the version one before latest, with a drive partition 60-40 with 60 being ubuntu, 40 being Windows Vista. It installed fine and on the reboot I could get into ubunty easilly. However When i attempt to get into Vista it pretends to load then goes to a black screen which hasnt changed for over an hour.

Is there anyway of recovering what I had before I installed and then going in for a second try and if so, how?

Many thanks

---

### Post by Ptero-4 on 2007-05-16
My friend. You´re so screwed. Vista won´t boot through grub (known issue that happens because Vista doesn´t use boot.ini as bootloader (as NT/2k/XP did)) and your data is surelly locked by BitLocker (which M$ surelly enabled remotelly on you).

---

### Post by squeezycheese on 2007-05-16
So what should I do?

---

### Post by starcraft.man on 2007-05-16
> **squeezycheese said:**
> I installed ubuntu edgy the version one before latest, with a drive partition 60-40 with 60 being ubuntu, 40 being Windows Vista. It installed fine and on the reboot I could get into ubunty easilly. However When i attempt to get into Vista it pretends to load then goes to a black screen which hasnt changed for over an hour.

Is there anyway of recovering what I had before I installed and then going in for a second try and if so, how?

Many thanks

Hmmm, ok, sounds like you simply have a problem with your GRUB. Just to make sure you didn't actually overwrite Vista can you post the output of this terminal command (Applications> Accessories > Terminal):

```
sudo fdisk -ls
```

Just copy and paste it all here in the code tags.

Assuming vista is still there, all ya need is to restore GRUB. You can find a good guide to it [here.]("http://users.bigpond.net.au/hermanzone/p15.htm") Scroll down till you find the section reinstalling GRUB :) 

In the event that you need a really quick no messing around solution cuz theres something important you have to do on windows, try the [GAG]("http://gag.sourceforge.net/") bootloader and read the documentation, its rather simple to use :)

Hope that helps.

Edit: Ptero are you sure that bit locker gets enabled? I thought you manually had to activate it... and even then GAG should fix this if its an error with GRUB I believe.

---

### Post by squeezycheese on 2007-05-16
Will try now. Thanks.

---

### Post by LaRoza on 2007-05-16
If you resized the Vista partition with something other than Vista's own tools, you probably corrupted Vista.

You would need to reinstall it if this is the case. (Then you would need to fix Grub)

---

### Post by squeezycheese on 2007-05-16
Re install vista or ubuntu?

Oh and it is fiesty not edgy if that makes a difference

---

### Post by LaRoza on 2007-05-16
If Vista was corrupted you would need to reinstall Vista. 

Feisty may have been able to properly alter the Vista partition, but I am not sure. Try the simplest solutions first, then work your way up to a reinstall.

---

### Post by starcraft.man on 2007-05-16
> **squeezycheese said:**
> Re install vista or ubuntu?

Oh and it is fiesty not edgy if that makes a difference

Did you try GAG? Its the simplest litmus test, if Windows is functional it should boot to it (I have almost never heard any trouble with people using GAG), otherwise I'd say the partition is a write off and you'd have to reinstall vista and then restore GRUB/GAG as listed above.

---

### Post by squeezycheese on 2007-05-17
Tis all sorted now. Re installed Vista :( complete restart. Lost all data.

I am getting a friend into looking at where I messed up and he will hopefully get the partitioning right.

Thanks for all your help.

:guitar:

---

### Post by Ptero-4 on 2007-05-18
[QUOTE=starcraft.man]Edit: Ptero are you sure that bit locker gets enabled? I thought you manually had to activate it... and even then GAG should fix this if its an error with GRUB I believe.[/QUOTE]
There was this stuff going about Vista because M$ changed the Vista bootloader and added this BitLocker thing, the tinhg with thme is that a big bunch of linux and mac users were saying that M$ added Bitlocker as a way to keep you from being able to access files stored in a Vista partition from Linux/OSX and that the bootloader was changed to screw the bootloaders that relied in the old boot.ini bootloader.

---

