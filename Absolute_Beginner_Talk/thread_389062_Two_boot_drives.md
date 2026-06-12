---
title: "Two boot drives"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by hwodin on 2007-03-20
I think I have a simple question....maybe not. All I want to do is boot to XP home located on different drives, one older, one newer but both with SP2

Just built new computer (first time builder) I installed three hard drives, drive H is a new boot disk with XP home, drive C is a storage disk from old computer and disk L is the older boot disk with XP home (reformatted within the past year). The MB assigned the drive letters, not me.

H and C are slave and master on Primary IDE, L is Master attached to a PCI card.

I want to boot from L. Boot sequence does not recognize L but it does offer the option of booting from OTHER DEVICE so I disable all drives (including H,C and two dvd drives) but it still boots to the new H drive.

The bios does not recognize drive L (I guess cause its attached to the PCI card?). My thinking is that if I set up L directly to MB and switch one of the DVD drives to the PCI card it will work.

If I do that then I think the MB will recognize drive L and allow me to set it up in the boot sequence the same way that the new drive works.

I don't know what I should worry about BUT I am sure that I don't know what will go wrong. For instance, what happens to the drive letters? will it sort itself out automatically??

HELP

---

### Post by hwodin on 2007-03-20
Two boot drives 

--------------------------------------------------------------------------------
I think I have a simple question....maybe not. All I want to do is boot to XP home located on different drives, one older, one newer but both with SP2

Just built new computer (first time builder) I installed three hard drives, drive H is a new boot disk with XP home, drive C is a storage disk from old computer and disk L is the older boot disk with XP home (reformatted within the past year). The MB assigned the drive letters, not me.

H and C are slave and master on Primary IDE, L is Master attached to a PCI card.

I want to boot from L. Boot sequence does not recognize L but it does offer the option of booting from OTHER DEVICE so I disable all drives (including H,C and two dvd drives) but it still boots to the new H drive.

The bios does not recognize drive L (I guess cause its attached to the PCI card?). My thinking is that if I set up L directly to MB and switch one of the DVD drives to the PCI card it will work.

If I do that then I think the MB will recognize drive L and allow me to set it up in the boot sequence the same way that the new drive works.

I don't know what I should worry about BUT I am sure that I don't know what will go wrong. For instance, what happens to the drive letters? will it sort itself out automatically??

HELP

---

### Post by Yoooder on 2007-03-20
Well you've certainly thrown all standards to the wayside :-) it took me about 3 reads to understand your setup.

First, one question:  Are you even running Ubuntu, or Linux at all?  If you're just running Windows, and not Linux at all, then you will likely have a lot of difficulty getting it's bootloader configured as needed.

Firstly, you really should try and get your boot drives attached to the same controller (either your motherboard IDE connectors, or your PCI IDE connectors).  I would personally put them both on the motherboard controller so that you can use your regular BIOS to boot to them.

If you use your add-in controller, it should have it's own BIOS of sorts, which should prompt you to press a key to configure it after your regular BIOS POST.

Once you get your setup somewhat more normalized you should be able to follow a GRUB/LILO tutorial (if you're running Linux anywhere) and get things setup.  If not, you can use a Linux bootdisk to install GRUB or LILO and use it to boot your Windows partitions, or you can try to figure it out with the NT Bootloader.

---

### Post by kidders on 2007-03-20
Hi there,

This is a Linux form. Perhaps you should post your question on a site targeted at Windows users. Additionally, please don't double-post!

---

### Post by hwodin on 2007-03-20
Sorry bout two posts, thiis is all new, didderent posts in different categories made sense...I thought.

---

### Post by Kateikyoushi on 2007-03-20
You can change the drive letters manually if you prefer the way it was.

---

### Post by hwodin on 2007-03-20
Not sure if this wll get to Yooder. Not runing linux or ubuntu, just bios and xp BUT I do consider myself logical or so I thought.

Since I can set the boot sequence and since I have two fully bootable drives (independently installed ) why can't I just select which drive to boot from in the bios when I need to????   

I need to change set up so both drives go to ide connectors on MB.


Am I making any sense???

---

### Post by sigge on 2007-03-20
Yes, you are making sense... Sadly, this is it: You are LOST in cyber-space. This is not, I repeat; NOT a place for windows-problems.:confused: 

You should go here [http://www.microsoft.com]("http://www.microsoft.com"):lolflag:  They might be able to help you. 

This, meaning ubuntuforums.org, is a forum for ubuntu-related information. I do not think you'll find anything usefull for windows.

But, hey... That's just me... If you are willing to try, go to [ubuntu.com]("http://ubuntu.com") and download an iso-image for ubuntu-linux. It might be the best thing that ever happened... On your computer, anyway... ;)

---

### Post by hwodin on 2007-03-20
just so happens another of your elite ilk had the time and necessary info for me, thanks to him and no thanks to you

---

### Post by Efwis on 2007-03-20
connect L and C to the mb, then connect H to the pci card, this should give you the opportunity to boot from L and C

The thing I don't understand is why you want 2 WinXP drives. Take the smaller one and turn it into Ubuntu or some other Linux distro, set the storage drive I presume this is Drive H, and make it a Fat32 partition, so you can share the files between the two OS's more easily. Having two of the same OS is kind of redundant unless you are doing some work that will "break" the OS.

This is also presuming that you are looking at dual booting with a Linux distro using the two hard drives. One thing you do need to remember though is this is a forum dedicated to a specific version of Linux. So be prepared to get a lot of crap thrown at you about using windows without Linux and asking for help on these forums.

If you would feel more comfortable in a forum setting that isn't strictly Linux feel free to visit my site, url is in my profile, I have some top notch windows experts there.

---

### Post by Yoooder on 2007-03-20
> Yes, you are making sense... Sadly, this is it: You are LOST in cyber-space. This is not, I repeat; NOT a place for windows-problems.

You should go here [http://www.microsoft.com](http://www.microsoft.com) They might be able to help you.

This, meaning ubuntuforums.org, is a forum for ubuntu-related information. I do not think you'll find anything usefull for windows.

But, hey... That's just me... If you are willing to try, go to ubuntu.com and download an iso-image for ubuntu-linux. It might be the best thing that ever happened... On your computer, anyway...
__________________
best regards
-Sigvard Lyth- 

**You are NOT helping the Ubuntu or Linux community by driving others from the Ubuntu forums!**  Why not offer assistance to him in the manner you can, since his question was more BIOS related than anything his OS of choice is of diminished concern.  Not to mention I'm sure you were a Windows user at one point or another...

---

### Post by sigge on 2007-03-22
Never meant to be harsh, and if I was I am sorry. :(

Still, I feel it prudent to point out that **I never mouthed off in any way...** **No namecalling**, or other **profanities**, **or trolling** for that matter. I did, however, point in the "right" direction for actual professional advice.

Apart from that, my message contained an invitation to use ubuntu. I still stand by that statement.

I'll shut up, now... :)

---

