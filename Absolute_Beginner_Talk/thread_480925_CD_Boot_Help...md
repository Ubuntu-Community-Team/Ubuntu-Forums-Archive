---
title: "CD Boot Help.."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by The Sk on 2007-06-21
Hi,

I followed all the steps giving to me by the Guide, but once I reach the booting part, I mess up. I put in the disc. I Restart, then when I get to the booting sequence, it boots WinXp.. Then I noticed that my BIOS boot settings were off, so I fixed it. I saved it and then i tried it again. Nothing. It just boots WinXp normally. I tried pressing Tab but nothing comes up. I also checked my Disc but everything seems fine.. Except my disc doesn't have the file named CD ROM UPGRADE like it says on [here](https://help.ubuntu.com/community/BootFromCD?action=AttachFile&do=get&target=correctcd.png), but I figured thats because its Feisty Fawn Not Edgy Eft...  Please help me ! :(

---

### Post by Hobo Joe on 2007-06-21
Explain you're problem more, what is 'the guide'?

Have you fully installed Ubuntu, then restarted the computer when it was done? And GRUB doesn't show up?
Did you properly partition the HDD?

---

### Post by atria on 2007-06-21
Try to do a reinstall after changing your bios settings. The bootloader (grub) was probably not installed on your first hard disk. Also, do you happen to have 2 or more hard disks in your computer?

[edit]
Sorry i misunderstood you. Its probably not booting because
1) Your cdrom drive is not at the top of the boot sequence.
2) Your cd is not being burnt correctly; you need to burn it as an iso. DO NOT extract the files from the iso and burn them separately.
3) The CD you just burnt may have been corrupted in some way or another, try burning another disc.
4) There is a small chance that your cdrom drive is broken. If possible, try booting the disc with another drive if all else fails.
[/edit]

---

### Post by the.phantom on 2007-06-21
ok in XP
double click on "my computer"
and look at the name of the disk in the CD

does it say something like ubuntu-6.1 .iso


(it MUST say iso)
if so you burned it wrong 

you must save the download as a iso for it to boot from the cd

---

### Post by Crafty Kisses on 2007-06-21
> **The Sk said:**
> Hi,

I followed all the steps giving to me by the Guide, but once I reach the booting part, I mess up. I put in the disc. I Restart, then when I get to the booting sequence, it boots WinXp.. Then I noticed that my BIOS boot settings were off, so I fixed it. I saved it and then i tried it again. Nothing. It just boots WinXp normally. I tried pressing Tab but nothing comes up. I also checked my Disc but everything seems fine.. Except my disc doesn't have the file named CD ROM UPGRADE like it says on [here](https://help.ubuntu.com/community/BootFromCD?action=AttachFile&do=get&target=correctcd.png), but I figured thats because its Feisty Fawn Not Edgy Eft...  Please help me ! :(

Did you burn the CD as an iso image file?

---

### Post by wormser on 2007-06-21
It sounds like you might have not burned the iso as an image.  The is a [great guide]("http://www.psychocats.net/ubuntu/iso").

---

### Post by The Sk on 2007-06-21
Sorry for not explaining my self right. I am a new Ubuntu User. I downloaded the Feisty Fawn Desktop download. I Followed your guide. ([This One](http://ubuntuforums.org/showthread.php?t=232059)) I Burned the files into a disc. I restarted my Computer then I waited to see the Ubuntu Setup menu thing. But it didn't show up, it Booted WinXp Normally. So i did some troubleshooting and I noticed my BIOS boot settings were not correct. So I fixed them to "CDROM". I tried it again but it still didn't work. It Booted WinXp Normally. And I'm not Computer smart so I don't know if I have more than one Hard Disk. Please help me :( I really want to use Ubuntu.

---

### Post by The Sk on 2007-06-21
> **wormser said:**
> It sounds like you might have not burned the iso as an image.  The is a [great guide]("http://www.psychocats.net/ubuntu/iso").

Thank you. I think this might work. This guide explains it much better and it talks about some steps I missed. I'll get back on you guys if something goes wrong. Thanks again. :D

---

### Post by atria on 2007-06-22
Sorry i misunderstood you there. Reread my post (#3). I just posted some solutions that you might want to try.

---

### Post by alienexplorers on 2007-06-22
When you burnt the disc did you burn it as a DATA disc or as an .iso image.  If you burnt it as a DATA disc it may just skip the cd and boot windows.

---

### Post by The Sk on 2007-06-22
OK i just followed the guide that Wormser put up.. I DID burn it as an Imagine.. But still won't boot... Is there something that i need to change in BIOS? I changed the Booting thing to CD ROM .. But is there anything else I need to do in BIOS so it boots the Cd? ..

---

### Post by logos34 on 2007-06-22
if you burned the iso as an image, and you checked the md5sum of the downloaded iso, and you burned it slowly at 2-4x, and the bios is set to boot cdrom first, then it's a hardware problem with the cd drive or bad media.  If you're using cd-rw try a cd-r disc.  maybe you've already tried that

---

### Post by The Sk on 2007-06-23
Ok thanks logos.. I was using a Cd-Rw and I switched to Cd-R and it works perfectly!! THANK YOU! I love Ubuntu.. It is waaay better than Windows..

---

### Post by logos34 on 2007-06-23
> **The Sk said:**
> Ok thanks logos.. I was using a Cd-Rw and I switched to Cd-R and it works perfectly!! THANK YOU! I love Ubuntu.. It is waaay better than Windows..

Cool...welcome to the community!  Enjoy.

---

