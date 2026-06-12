---
title: "The Fun of Installation"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Frunkis on 2007-12-17
I built this computer back in April because my old Sony Vaio kicked the bucket thanks to my stupid mistake. I bought some parts to try and fix it and found it couldn't be fixed. I am having some issues installing Ubuntu and wonder if some of this has anything to do with it. Both of my hard drives are IDE as well as my CD-ROM drive. My Asus mb only had one IDE port with 3 devices needing data cables. One of the parts I bought when trying to fix my Vaio was a Promise Technologies IDE PCI card. It plugs into my PCI slot on the mb and allows me to run my slave hard drive which is the one i want to install Ubuntu onto. I'm not the most proficient with computers, but I know enough to be dangerous. I am dual booting with XP Pro and cannot seem to get it to load. Help. Please. Is there another program I need to run? I looked into the virtual basic stuff, but seems a bit over my head. Your help would be greatly appreciated. Thanks.

---

### Post by jken146 on 2007-12-17
> cannot seem to get it to load
What do you mean?

---

### Post by Frunkis on 2007-12-17
When I restart the computer and try and get it to boot from disk, it just loads straight to Windows. I have tried everything I can think of and can't seem to find anything specific on the net that tells anything any different than what I already know. The CD-ROM drive is set to load first and it continues to go straight to Windows. Any suggestions?

---

### Post by diatribe on 2007-12-17
did you install grub?

---

### Post by Frunkis on 2007-12-17
I have a feeling I am going to feel like a complete tool but, I was under the impression that GRUB was included in the software download.

---

### Post by meborc on 2007-12-17
have you changed your BIOS settings to boot the computer from the CD? it sounds like it just boots the HDD not the CD

more info here : [http://www.psychocats.net/ubuntu/installing#booting](http://www.psychocats.net/ubuntu/installing#booting)

EDIT: just read the full thread... sorry for the mis-post :) are you sure you have burned the CD correctly? if the bios is booting from CD as 1st choise, the fault must be in the CD

---

### Post by diatribe on 2007-12-17
maybe I am reading this wrong, can you boot from the cd at all?

---

### Post by Frunkis on 2007-12-17
Yeah, I have checked all of that and still no luck.

---

### Post by meborc on 2007-12-17
did you do md5sum check for the iso and the cd? did you burne the cd at low speed (4x)

read more - [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

EDIT: ok... i'm always a step behind you on this :D ... the cd drive works OK in windows? how about inserting other bootable cd's linux/win to cdrom... what is the result of bootup now?

---

### Post by Frunkis on 2007-12-17
I am re-burning the disk now at the lowest speed my CD-RW will allow, 12X. I did not have any problems installing Windows, and I actually had reformatted Windows at one point, wiping clean a version I had previously installed for a different one. So I know the computer has the ability to read a boot disk. I think one mistake I have been making is allowing Windows to do the writing using its on board Roxio writer instead of Nero. I'll try it like this and go from there.

---

### Post by Frunkis on 2007-12-17
The new disk I burned in Nero does in fact work. When I put it in the drive, it loaded giving me the info about Firefox and Thunderbird and everything so I know the disk is good. Now I just have to make sure that it will load properly to Dual Boot and make sure that it doesn't erase Windows, cuz that would in fact suck. If Grub is not already installed on my Ubuntu disk, where do I get it from?

---

### Post by Frunkis on 2007-12-17
I found some download info on gnu.org, but I'm not sure which to download or how to install it. Sorry to be such a novice at this and needing so much help. Thanks.

---

### Post by Frunkis on 2007-12-17
More help needed. When I put the disk in the drive, it reads fine and shows me all the Live CD info and about Firefox and Thunderbird. But when I reboot and the disk runs, it brings up a DOS prompt saying Caldera DR-DOS 7.03 then at the bottom of the program, after everything has run, it says [DR-DOS] A:\>
What now???

---

### Post by philinux on 2007-12-17
When you load the live cd you should see your dvd/cd drive light flickering. An orange progress bar on the screen and messages about the live cd progress.

if its booting from cdrom

---

### Post by Frunkis on 2007-12-17
So you think that its not booting properly....still. I burned the CD at the slowest speed I possibly can, 12X. Any further suggestions? I don't want to give up on this, I am even more determined to make this work now.

---

### Post by Presto123 on 2007-12-17
This sounds like you burned it as a data disk and not an image. I got that several times before I read that I needed the image file.

Which program did you use to burn it? Nero? If so, it defaults (At least in my case) as burning .iso's as data, search around Nero for a bit and it should allow you to burn an "Image".

**Edit** Yeah, just noticed you DID say Nero, try that above, then. Also, Grub will be auto installed when you install Ubuntu. ;) Just don't use the "Guided, Install to entire disk" option if it is all it shows.

---

### Post by philinux on 2007-12-17
Yep - so you got the .iso file downloaded. 

It must be burned as an image.

---

### Post by Frunkis on 2007-12-17
I did in fact burn it as a boot data disk. I am reburning it now as an image disk. I appreciate the help. Thanks.

---

### Post by Presto123 on 2007-12-17
No problem. If you still have issues, people are here to help. ;)

---

### Post by philinux on 2007-12-17
> **Frunkis said:**
> I did in fact burn it as a boot data disk. I am reburning it now as an image disk. I appreciate the help. Thanks.


Ok when you got it burned, first thing. when it boots its gives you a menu.

Select check disk. this makes sure its ok. It takes a while to run but let it go make a coffee etc.

When you know you got a good burn then you can proceed,


also the menu says install/run - this option just runs the live cd first it does not installl !

It just gives you a live cd desktop with the option to install - an icon.

---

### Post by Presto123 on 2007-12-17
> **philinux said:**
> Ok when you got it burned, first thing. when it boots its gives you a menu.

Select check disk. this makes sure its ok. It takes a while to run but let it go make a coffee etc.

When you know you got a good burn then you can proceed,


also the menu says install/run - this option just runs the live cd first it does not installl !

It just gives you a live cd desktop with the option to install - an icon.

Yeah, I'm really beginning to think that this is always a good idea, but I usually skip it. Not recommended to skip the option. :)

---

### Post by Frunkis on 2007-12-17
I am in Ubuntu hell. I reburned the disk....again, for the forth time now. I spoke to a guy from work who has Ubuntu and i realized that one of my problems what that I was extracting everything in WinRar. Therefore, I burned the disk again with the ISO. file and guess what....it did the same damn thing. I think I am going to just have him bring me his copy of Ubuntu and go from there. Does anybody have any other suggestions as to something to save me from going insane?

---

### Post by Presto123 on 2007-12-17
Yipes...yeah, don't extract .iso's for this kind of thing. Leave them as is. 

Just to recap on Nero, on the "Start Smart" program, you select the icon for "Copy and Backup" then after that, "Burn Image to Disk". Select the file when it prompts for it, and on the brown screen that pops up next that says "Image recording" "Write a premastered image" you can see that there is a drop-down menu below the "Destination Drive" marked "Writing Speed:". In here I have a copious amount of speeds that you can select.

If it does not show it as a possible burning speed, it may be that the CD writer does not support it that low...

---

### Post by Frunkis on 2007-12-17
Thank you so much. I followed your instructions precisely with exception to being able to run the burn at 4X. I ran it at 12X and burned it and went to run it expecting it to screw up again. When the computer rebooted, it brought up the Ubuntu screen and I let out a big sigh of relief. I let it check the integrity of the disk and everything checked out fine. Thanks to everybody that helped. I will continue to visit the forum to help out any way I can. I work in a networking environment and troubleshoot people's internet connections all day long, so hopefully I can provide some assistance to anyone having problems with this. Thanks again.

---

### Post by Presto123 on 2007-12-18
Hey...cool. Glad you got it running. Sometimes, the "biggest" problems are just simple things that slip by. 

Certainly hope you like Ubuntu. I have a feeling you will need some other stuff when you install, like mp3 playing capabilities, etc. If so, just msg me (Will be going to bed soon) and I will help as much as possible.

---

