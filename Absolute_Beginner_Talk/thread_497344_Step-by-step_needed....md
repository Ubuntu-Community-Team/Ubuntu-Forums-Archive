---
title: "Step-by-step needed..."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Loddy on 2007-07-10
Hi folks,

I've got a copy of Kubuntu from PC Utilities Magazine and as they suggested, I burnt the kubuntu files to a bootable CD and rebooted my PC.

What happens next is your typcial boot sequence when booting from a CD (i.e. CD drivers, minimal driver checks etc...) and then a DOS prompt...

Nothing automatic happens from this prompt onwards and the only program I can run manually run is wwbmu.exe which is a partitioning program which loads in the fine (but incomprehensible) language of the Dutch people.

So... What blindingly obvious step have I missed here? What's going on?

EDIT: I have tried this both on SATA hard drives, and IDE drives I had spare, no joy...

---

### Post by bigken on 2007-07-10
you may have burnt it to fast the iso should be burnt as slow as possible

---

### Post by atria on 2007-07-10
You are not supposed to boot kubuntu that way (ending up in a dos prompt).

Try downloading the .iso file from [www.kubuntu.org](www.kubuntu.org) and burn it. After that boot the disc. Make sure that your boot sequence is set to cdrom, then hard disk.

Also since you said you receive a copy of kubuntu from them, was the disc itself bootable? If it is just boot the disc you were given.
If they gave you the iso instead, burn the iso as a image instead of extracting the files.

---

### Post by Loddy on 2007-07-10
Thanks for the response guys,

Right so Atria, I think I see the problem lol, what an idiot I am... I was forgetting the file on the Mag CD would be an iso not a zip, so yeah I extrated the files...

NOOB... I can see this is gonna great fun lol.

Ok so burn the ISO slowly, now... should I burn it purely as a data CD in NERO? Because I guess if I burn it as a Bootable disc it'll load that wwbmu again? 
Or should I burn it as a bootable?

---

### Post by bigken on 2007-07-10
no you burn it as an iso

---

### Post by bigken on 2007-07-10
look at[ this ]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Loddy on 2007-07-10
Hi guys, 

Right your advice paid off and Kubuntu loaded and ran through the installation.

BUT... When I rebooted its as if I had no hard drives, I just get an error saying ***"remove media or other disks, press any key to restart"***

This is now the third time this has happened and I can't figure out what I'm doing wrong.

---

### Post by bigken on 2007-07-10
take the cd out of the drive

go into the bios and change the boot order to hdd 1st

---

### Post by Skidpad on 2007-07-10
So, to be perfectly clear, you actually *installed* it?  You haven't just booted into the LiveCd environment?

---

### Post by Loddy on 2007-07-10
Yeah I installed it definately, I know I sound like a complete noob but I am certain it went that far hehe.
It told me to reboot and take out the CD after 30mins of copying system files etc...

I'll try the BIOS settings again and let you know...

**EDIT: **Okay at the moment it seems to be working, thanks for your help guys. Just turned out to be me not thinking straight about any of it.

---

### Post by Loddy on 2007-07-11
OK so I have it working without the CD now, and I have one other question:

Q> Will I be able to set up Belkin Wireless USB adapter on Kubuntu, and naturally, how do I do that?

I have been scouring the net for answers on this one but can't find many that help...

I have TH following model, so far I can't find drivers for it for linux and the network panel does seem to recognise its connected but calls it "Belkin USB 'something' Specific Device"
[B]Wireless G Plus MIMO USB Network Adapter
Part # F5D9050 [/B]

---

### Post by macogw on 2007-07-11
Which Belkin USB adapter is it?  Can you find it on this list? [http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin)

---

### Post by Loddy on 2007-07-11
Hey thanks for the link, my model is: Wireless G Plus MIMO USB Network Adapter >Part # **F5D9050**

Now that link says its supported, so hopefully that ralink driver might help.

One other setup question I guess is, how much of the windows settings for TCP/IP, gateway and dns etc... will I need to take note of to get it working?

EDIT: I want to thank everyone who'd replied to me so far, I'm really looking forward to using Linux and getting used to it, I'm sure I will need lots more help along the way but as I've had a troll-free experience so far I just want to say thanks.

---

### Post by Loddy on 2007-07-11
Ok, so I installed WINE and it appears that my belkin driver is on and the connection utility is waiting for a configured adapter to start looking for a network...

So, at this stage I realise I need IP addresses and DNS, ESSID etc... BUT after typing in what I have from Windows it is rejecting the gateway address saying it is invalid.

Does anyone have an idea of what I need to do now because setting the wan(0) options to automatic isn't working and manually typing what I have, doesn't seem to work either.

I swear, I am being driven in the belief that the second I get Linux onto to the internet, it will be a wonderful OS for me so... Someone please help me out here... Thanks.

---

