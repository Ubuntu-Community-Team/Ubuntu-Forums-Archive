---
title: "Live CD effectively unusable"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by s66 on 2007-03-04
I bought the book "The Ubuntu Book" and tried the included DVD (Version 6.06 LTS). I tried to preview Ubuntu with the "Live CD" but was unable to open any programs. When the pointer moved at all, which it did only sporadically, it would jerk across the screen. I waited at least 5 minutes just for Firefox to open, which it never did. The laptop in question has only 192 MB of RAM, which I have since learned is below the requirement for Ubuntu, but I didn't expect that the disc would be useless for the purpose of a preview. Is there anything I can do to use the Live CD?

---

### Post by aysiu on 2007-03-04
> **s66 said:**
> The laptop in question has only 192 MB of RAM > Is there anything I can do to use the Live CD? Buy more RAM.

The live CD creates a session using the DVD itself and your computer's RAM. It does not affect your hard drive. Since it is running the session in your RAM, how much RAM you have directly affects the live session experience. Even 256 MB is slow, but at least still usable. 192 and 128 MB or RAM is too little to really preview with a live CD or DVD.

---

### Post by Bachstelze on 2007-03-04
Yes, get more RAM :)

Keep in mind, though, that 256 MiB of RAM is the minimum for the Live CD, not for Ubuntu. You still can install Ubuntu with the text-based Alternate CD.

---

### Post by taurus on 2007-03-04
The LiveCD requires at least 256MB of RAM to run it so try using Xubuntu or even Fluxbuntu since they both require less system resources.

[http://www.xubuntu.org](http://www.xubuntu.org)
[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

---

### Post by s66 on 2007-03-04
> **taurus said:**
> The LiveCD requires at least 256MB of RAM to run it so try using Xubuntu or even Fluxbuntu since they both require less system resources.

[http://www.xubuntu.org](http://www.xubuntu.org)
[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

Sounds good- thanks for that. I'm downloading Xubuntu now. However, of the two, which requires fewer resources?

---

### Post by taurus on 2007-03-04
That would be Fluxbuntu.  However, for you, I think you should stick with Xubuntu for now.

---

### Post by s66 on 2007-03-08
I'd just like to post an update, because I'd really like to switch to Linux of some kind but continue running into obstacles: I ran the Xubuntu Live CD (which I had burned onto a CD-RW after a full erase) on my Gateway (192 MB) and Dell (256 MB). In both cases the computer froze after opening the Xubuntu desktop. I was never able to even move the pointer, nor could I eject the disk without manually turning the computer off by holding down the power button. This was equally true in Safe Graphics Mode. I ran a Memory test, which resulted in a pass, and a check of the disc, which reported 1 checksum failed. This is especially puzzling because both computers have more RAM than the 128 recommended for the Xubuntu Live CD. I'd definitely appreciate any input on how to get it to work (at least so that I can verify that I can get wireless internet access like with Windows)!

---

### Post by Bachstelze on 2007-03-08
If I were you, I'd try to install Ubuntu with an Alternate CD. The installer is text-based so it's a bit less pretty but also far less buggy and less likely to fail on you.

---

### Post by towsonu2003 on 2007-03-08
> **s66 said:**
> a check of the disc, which reported 1 checksum failed
if that wasn't a typo, that means your CD image is defective, you should 
1. check the md5sum of the downloaded ISO image
2. burn ISO to CD at slow speed
3. make it check the disk...


see [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

good luck :)

PS. if the disc passes all checks but it still is getting stuck, it might be a graphics card driver issue. although not very helpful, have a look here: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by s66 on 2007-03-09
OK, thanks for the links. I followed the instructions regarding WinMD5Sum and the result was "MD5 Check Sums are the same." Then I again did a full erase on the CD-RW and burned the .iso at 
This time I used an external drive (Memorex DVD16+/-DL4RWID2) and selected the slowest speed listed by Nero Express, which was 4x. Burning was successful. I put the Xubuntu CD in the internal drive of my Gateway, rebooted, and checked the CD. Again the result was "1 checksums failed." Still, I started the Live CD. First, four or five error messages displayed, all but one beginning with “firmware helper.” Next, the screen split in two, with several Xubuntu logos on the top half and several Windows XP logos on the bottom half, with the screen as a whole taking on a “streaked” appearance. Then the desktop appeared and the streaking disappeared. Unlike in my previous attempt, I was able to move the pointer. Also unlike before, a wizard appeared and offered to check installation (no installation had been done). I clicked “next…next…” but the wizard didn’t appear to check anything, but instantly displayed something about success and a Close button, which I clicked. Then I opened first, the Mandela video, and then, the Aesop file. Both played but with neither could I hear audio. 

My questions are:

1. what are the likely effects of installing with a disc that has failed its checksum (since most functions appeared to work despite this)?
	1A. If they are likely negative, what can I do to get a Live CD that does not fail its checksum?

2. What is the significance of the error messages from the “firmware helper?”
	2A. What, if any, is the significance of the split screen with both logos?

3. How can I ensure that audio will play in Xubuntu?

I should mention that the file I used is entitled “xubuntu-6.10-desktop-i386.iso” and was downloaded with Free Download Manager from the UK link on the official Xubuntu site.

---

### Post by towsonu2003 on 2007-03-09
> **s66 said:**
> 
1. what are the likely effects of installing with a disc that has failed its checksum (since most functions appeared to work despite this)?

uhm, think of it like this: would you like to install Windows from an installation CD that you knew was faulty? I wouldn't take the chance -whenever you encounter an error, you'll keep thinking "was this because of the failed checksum?"...
> **s66 said:**
> 
	1A. If they are likely negative, what can I do to get a Live CD that does not fail its checksum?

I'd try a CD-R... Or you could order Ubuntu from shipit.ubuntu.com and do a server install, then install xubuntu-desktop on top. Or you could order a CD from amazon.com I believe... 
> **s66 said:**
> 
2. What is the significance of the error messages from the “firmware helper?”

I don't know. Do you have wireless? it might be complaining that it couldn't find the firmware for the wireless card if your card is Broadcom (which is normal, because Ubuntu can't distribute Broadcom firmware). 
> **s66 said:**
> 
	2A. What, if any, is the significance of the split screen with both logos?

no idea... something to do with something called "framebuffer"?? I'm very confused about that stuff :) google for "<your video card> linux" to see if ppl are having difficulties with it. 
> **s66 said:**
> 
3. How can I ensure that audio will play in Xubuntu?

if audio plays in LiveCD, it should play when it's installed. you could also google (like I mentioned bf) for "<your audio card> linux" to see if ppl are having problems. also have a look at this nice guide: [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
> **s66 said:**
> 
I should mention that the file I used is entitled “xubuntu-6.10-desktop-i386.iso” and was downloaded with Free Download Manager from the UK link on the official Xubuntu site.
that should be fine. you say the ISO file's md5sum is fine on your hard disk but the md5sum check fails when you're booting from the CD, which tells me that the CD-writing process didn't go well :)

---

### Post by s66 on 2007-03-10
Thanks for the input, towsonu. I found out that I do have a Broadcom 802.11g Network Adapter; I don't quite understand what you said about Broadcom firmware- is it possible to get wireless access with Xubuntu and a Broadcom adapter? If not, I'm not interested in it, so if that is the case, are there any other Linux distributions that would work?

---

### Post by towsonu2003 on 2007-03-10
> **s66 said:**
> Thanks for the input, towsonu. I found out that I do have a Broadcom 802.11g Network Adapter; I don't quite understand what you said about Broadcom firmware- is it possible to get wireless access with Xubuntu and a Broadcom adapter? If not, I'm not interested in it, so if that is the case, are there any other Linux distributions that would work?

most broadcom wifis work with linux. but, because broadcom (the corp) isn't a linux-friendly manufacturer, you will have to fiddle a little. see: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

