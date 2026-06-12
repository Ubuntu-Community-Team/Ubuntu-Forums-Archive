---
title: "Ubuntu boots as far as 'Uncompressing Linux... Ok, booting the kernel' and then stops"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by alarichall on 2006-09-27
Hey ho!

I'm completely new to Linux. I haven't found an answer to my problem yet, but my apologies if I've just missed it somewhere obvious.

I installed Ubuntu a few days ago onto my laptop. The machine is a Thinkpad T series; it has 256 mb of RAM; I think it's a T21 (but I'm not sure because the motherboard is not the one which the computer originally came with--might be T20, 21, 22 or 23). Since I can't get the computer to boot up at the moment, I don't know how to check its other specifications.

Sometimes it starts up fine, at which point I've been very happy with it. But usually it gets through the 'IBM Thinkpad' BIOS screen, through the 'grub loading' screen, and then onto another screen, at which point it stops.

This is what it says on the screen when it stops:

[INDENT]  Booting 'Ubuntu, kernel 2.6.15-27-386'

root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
   [Linux-bzImage, setup=0x1c00, size=0x157856]
initird  /boot/initrd.img-2.6.15-27-386
   [Linux-initrd @ 0xf969000, 0x676660 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
_
[/INDENT]

At the end of this (where I've put the underscore) is what looks like a cursor, which flashes, but I can't type anything and no keys seem to do anything. The computer will sit like this, as far as I can tell, ad infinitum.

I'm completely stuck with this--I can shut the computer down by pressing the off button for 20 seconds. If I try starting it again straight away, it has the same problem.If left for a night the computer usually starts up okay, and seems to shut down okay too. I haven't been able to observe any other pattern in its failure to boot up.

Hope to be able to get this working again soon, so any help much appreciated.

Alaric

---

### Post by kaplis on 2006-09-27
hey

some week ago i had similar problem (and text message) with my RAMdisk, but in your mesagge i dont see any clue about that.

try this one- at the startup enter GRUB menu( system offer such thing- there will be a time coutdown to do that). then load RECOVERY mode. and when you are logged in- update your system (in case you have network connection).

this was the way how i fix it. i hope it will help you;)

---

### Post by alarichall on 2006-09-27
Thanks for that advice, Kaplis. Unfortunately it hasn't fixed the problem, but hopefully the results might give someone else some clues?

I've now tried both recovery modes offered ('Ubuntu, kernel 2.6.15-27-386 (recovery mode)' and 'Ubuntu, kernel 2.6.15-23-386 (recovery mode)'). 

In each case, it seems to go through the text which I quoted at the beginning of this thread. I then get a list of text.

With Ubuntu, kernel 2.6.15-27-386 (recovery mode), each entry begins '[17179572.XXXXXX]' (where X stands for various digits). The final entry to appear is

[INDENT][17179572.888000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11[/INDENT]

After that the cursor flashes at the bottom of the screen, but again no keys have any effect.

With Ubuntu, kernel 2.6.15-23-386 (recovery mode), each entry begins '[4294670.XXXXXX]'. The last entry to appear is much the same as with the other recovery mode:
[INDENT]
[4294670.749000] ACPI: PCI Interrupt 0000:00:03.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11[/INDENT]

I installed all available updates over the internet when I first installed Ubuntu a few days ago, so I'd hope that the system is up to date.

All further suggestions gratefully received.

---

### Post by kaplis on 2006-09-27
wow:-k 

this time i cant help:-# 

try with info to get some help in linuxquestions.org or search the web;)

---

### Post by Kateikyoushi on 2006-09-27
Did you try to change the ACPI settings in the BIOS.

---

### Post by kaplis on 2006-09-27
P.s. search the topic of your problem in forums- there are many similar!

---

### Post by alarichall on 2006-09-27
> **Kateikyoushi said:**
> Did you try to change the ACPI settings in the BIOS.

No--have had a little look around my BIOS setup utility and don't see 'ACPI' anywhere--can you suggest where I might look and/or what I might do with it? Or is BIOS too hardware-specific for you to be able to advise?

---

### Post by ignorance on 2006-09-27
I looked up a part of the error code you posted about the recovery mode
and i came up with this [http://www.karbosguide.com/hardware/module5a3.htm](http://www.karbosguide.com/hardware/module5a3.htm).

I started reading somewhat and i saw that that piece of error is handeld by the bios(perhaps the reason why it stops booting). 
Haven't found the reason yet.

---

### Post by Bachstelze on 2006-09-27
Try this

in GRUB, select the kernel you want to boot but instead of pressing enter, press "e", then go to the line ending with "ro quiet splash", add "noapic nolapic" at the end and then try booting. If it still doesn't work, try "acpi=off".

---

### Post by xpod on 2006-09-27
I suppose you have already tried just leaving it for a minute ...see if it eventually carries on??

Sometimes when booting both my ubu and kub pc`s can get stuck at that stage or a bit further.....sometimes i even end up at a prompt.

Even when initially loading the live cd`s on this pc now i get a long hesitation at that stage or there abouts.....sometimes with....

"Dev hdd timeout waiting for device"...or "buffer I/O errors..

It always still went on to load up and the actual install`s still load up if and when they ever do have their strange moments.

---

### Post by alarichall on 2006-09-27
Thanks for these further replies.

HymnToLife suggested

> in GRUB, select the kernel you want to boot but instead of pressing enter, press "e", then go to the line ending with "ro quiet splash", add "noapic nolapic" at the end and then try booting. If it still doesn't work, try "acpi=off".

This doesn't seem to have helped, but I'm not sure that I understood rightly where to type "acpi=off". I've got my usual frozen-up screen, which now includes the line:

[INDENT]kernel  /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash acpi=off[/INDENT]

Is that what you had in mind? Certainly isn't doing anything else...

Kaplis suggested at looking at other forums. A couple of people seem to be reporting the same problem:
[INDENT][http://www.ubuntuforums.org/showthread.php?t=262952&highlight=Uncompressing+Linux+booting+kernel](http://www.ubuntuforums.org/showthread.php?t=262952&highlight=Uncompressing+Linux+booting+kernel)
[http://www.ubuntuforums.org/showthread.php?t=261697&highlight=Uncompressing+Linux+booting+kernel](http://www.ubuntuforums.org/showthread.php?t=261697&highlight=Uncompressing+Linux+booting+kernel)
(I hope those links work--I haven't worked out how to get a proper URL for each thread yet)[/INDENT]
but not to have received a fix for it.

Yeah, as Xpod suggested, I've tried brute patience!

---

### Post by xpod on 2006-09-27
> Yeah, as Xpod suggested, I've tried brute patience!

Sorry mate...i think you type the "noacpi" thing in at the end of the line you get when you choose "more options"....
It was something like that if i recall correctly.

Good luck.

EDIT:That was just at the loading the cd stage though

---

### Post by alarichall on 2006-09-27
> **xpod said:**
> Sorry mate...i think you type the "noacpi" thing in at the end of the line you get when you choose "more options"....
It was something like that if i recall correctly.

Good luck.

EDIT:That was just at the loading the cd stage though

Yeah, the problem is not at the stage of loading the CD. I haven't found anything saying 'more options' so far while working with my laptop. Thanks for the idea though.

---

### Post by technasma on 2006-09-28
hey alarichall, I'm having exactly the same problem... I've setup a dual boot system with XP and Dapper on a Thinkpad T42... I can boot into XP from Grub and Dapper installation went fine but when I try to boot the kernel I get stuck at "Uncompressing Linux... Ok, booting the kernel."
*flashing cursor*
and nothing. I've tried editing the kernel line in Grub to no avail!! Arrrgghhh.

---

### Post by alarichall on 2006-09-28
Sorry you're also having trouble, Technasma. There are some other relevant-looking posts here:

[http://www.ubuntuforums.org/showthread.php?t=187318&highlight=booting+kernel](http://www.ubuntuforums.org/showthread.php?t=187318&highlight=booting+kernel)

I'm not trying anything involving dual booting--quite a lot of posts with symptoms like mine involve that.

What I *have* found with my problem is that if I leave the machine without power for an hour or so (taking out the battery and unplugging it) then it starts fine. But if I shut down and then try to restart shortly after, I get the problem. Maybe this is specific to Thinkpad T22s? They also have trouble with hibernation it turns out--don't know if it could be related.

Still, at least for most practical purposes, my machine is working...

---

### Post by timjohn on 2006-11-06
This is not just a problem with the T22 I have it with the T21 as well, I am glad to see that yo can fix it with unhooking the battery and power overnight though, I never thought of taking out the battery!!!!!! I will try this in my next install to see if it works for me. Thanks;) , Tim

---

### Post by teknofyl on 2006-11-22
With 6.06 (LiveCD), so I thought I would try 6.10 and it would not boot, but the problem was different - it would not get the kernel completely (that is, it failed sooner in the boot process).

So I reburned it, and I noticed that my burner program was giving me an error.  Then I checked, turns out I have 650 MB discs... 

I'll get some other discs and retry, but - if you are getting his problem, maybe you should go back and make sure that the .iso is actually getting burned right.  When I burned it, the error message was so inconspicuous that I thought it had burned correctly.

---

### Post by alarichall on 2006-11-23
Thanks for that suggestion! I don't think it can have been the problem, as I wasn't using a self-burned CD, but good of you to suggest it. In the end my problems were overtaken by the failure of the processor on that machine, so I had to get a new one anyway. Am using a Thinkpad T40, and apart from the usual hassle with trying to get DVDs of all regions to do their thing, it's all going fine :-)

---

### Post by teknofyl on 2006-11-24
So this symptom is not of a specific problem, I guess.

---

### Post by Scott64 on 2006-12-15
> **HymnToLife said:**
> Try this

in GRUB, select the kernel you want to boot but instead of pressing enter, press "e", then go to the line ending with "ro quiet splash", add "noapic nolapic" at the end and then try booting. If it still doesn't work, try "acpi=off".

Just wanted to give a quick thanks. This bit here helped me out. I've had about 20% success starting my laptop (hp pavillion dv6040ca) with ubuntu and as soon as I put "noapic nolapic" it fired up first try :D

---

### Post by Snookered on 2007-01-06
Found this by accident;
[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4R3UYP](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-4R3UYP)
Symptoms corrected by version 1.09 - IYET46WW

    * (Fix) Fn key features do not work after wakeup from hibernation while a ThinkPad docks to a docking station without CD-ROM drive in Ultrabay 2000.
    * (Fix) Resuming from screen off state needs pressing a key two times. (Windows Me and Windows 2000)
    * (Fix) A hard disk drive (HDD) password is requested after warm docking to a docking station which has a HDD adapter without a HDD in its Ultrabay 2000.
    * (Fix) Hang up occurs when suspend/resume is done on a ThinkPad with HDD adapter without a HDD in Ultrabay 2000.
    [COLOR="Red"]* (Fix) ACPI compatible Linux hangs up at boot timing.[/COLOR]
    * (Fix) System shutdown takes long time under Windows 98 after hot-remove from the docking station with a SuperDisk drive in Ultrabay 2000.
    * (Fix) CD-ROM continuously accesses after wakeup from hibernation.
    * (Fix) Reboot from BIOS-call causes system hang

Now if someone could help with updating the BIOS with Ubuntu already installed,no WinXP.
Yes, I are a n00b!

IBM Thinkpad T20 type 2647-46U

Just noticed I'm listed as a Breezy user. Now have Dapper installed and the same thing happens.

---

