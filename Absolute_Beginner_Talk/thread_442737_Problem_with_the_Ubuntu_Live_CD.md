---
title: "Problem with the Ubuntu Live CD"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by ComeGetSome on 2007-05-13
Well I recently downloaded the ISO for Ubuntu from the site and burned it onto a disc. I checked the ISO with the md5 hash checker and everything came out ok. My problem is that I can get to the Ubuntu menu which lists start or install Ubuntu and everything else, But as soon as I click start it proceeds to give me an error. I have tried to click the check CD integrity one ( I don't remember the exact words) it proceeds to the same error.

The error is:
```
/Bin/sh:can't acces tty;job control turned off
(initramfs) [115.862422] ata1:port failed to respond (30secs,status 0xd0)
```

Can someone please help me, I have not real knowledge of Linux but Im good with computers and im in the process of getting my A+ certification.

Thank You in advance for anyone who decides to help me.:)

---

### Post by starcraft.man on 2007-05-13
Right, your having a derivative of the problem[ here.]("http://ubuntuforums.org/showthread.php?t=415009&highlight=control+tty")

Has to do with the new kernel and how it handles drives I think... unfortunately its still not fixed, maybe soon >.>.

Your situation is different from the one I had (when I ran into the problem, I unplugged my second CD drive and then it booted fine). In a few other situations after people unplugged their multiple devices (leaving only one CD/DVD drive and one HDD) they were able to boot. I dunno if that will fix you, can't hurt to try. >.>

If that fails, read over the topic maybe someone has had your specific problem or maybe someone will pop up right after me and have the easy fix. :p

---

### Post by ComeGetSome on 2007-05-13
Oh, Thank you I will try your suggestions. I might try to boot the CD on a different machine maybe a low end one I can build with spare parts. I also forgot to mention that due to my hardware configurations my boot up might be why Ubuntu is not working. My hard Drive spins so slow that my motherboard cannot find it till I press Ctrl+Alt+Delete after it gives me an error. It was the only workaround I could apply to make the PC bootable.
Might that be what is giving the problem? Thats the only thing I can think of thats not normal in my system.

---

### Post by starcraft.man on 2007-05-13
> **ComeGetSome said:**
> Oh, Thank you I will try your suggestions. I might try to boot the CD on a different machine maybe a low end one I can build with spare parts. I also forgot to mention that due to my hardware configurations my boot up might be why Ubuntu is not working. My hard Drive spins so slow that my motherboard cannot find it till I press Ctrl+Alt+Delete after it gives me an error. It was the only workaround I could apply to make the PC bootable.
Might that be what is giving the problem? Thats the only thing I can think of thats not normal in my system.

That would certainly explain why it says "failed to respond" with that info I guess it timed out after 30 seconds... can i ask why your drive spins so slow? I mean can it be slower than 7200 RPM? I thought only labtops had slower drives >.>. The easy fix if you ask me, is to run to the store and buy a regular 7200 RPM drive for 60 bucks, they've gotten to be dirt cheap now. I don't think its a good idea to have a drive that fails to register normally on your mobo...

---

### Post by jerrylamos on 2007-05-13
My interpretation, Ubuntu tries to speedup boot by doing things in parallel plus simulate IDE and SATA as SCSI devices and then gets in trouble when one function tries to start when another function isn't ready yet.  You could check the following post for my workaround, and also a fix by a developer (if you can follow his directions please let me know how you did it)

[http://ubuntuforums.org/showthread.php?t=424225&highlight=workarounds](http://ubuntuforums.org/showthread.php?t=424225&highlight=workarounds)

The easiest fix is to use Ubuntu Edgy Eft 6.10 the preceding release that doesn't have the fancy code in it.  They are working on a fix for Feisty 7.04, but maybe the fix might be in Gutsy 7.10 next fall.

Cheers, Jerry

---

### Post by ComeGetSome on 2007-05-13
> **starcraft.man said:**
> That would certainly explain why it says "failed to respond" with that info I guess it timed out after 30 seconds... can i ask why your drive spins so slow? I mean can it be slower than 7200 RPM? I thought only labtops had slower drives >.>. The easy fix if you ask me, is to run to the store and buy a regular 7200 RPM drive for 60 bucks, they've gotten to be dirt cheap now. I don't think its a good idea to have a drive that fails to register normally on your mobo...

Well the reason is that I was too broke when I upgraded my processor/mobo/ram to go for a new HDD. Im in the  process of buying a new drive yet after reading that link you gave me It seems as if Ubuntu doesn't like SATA drives, So should I go for a IDE drive or SATA? And my hard drive spins at 5400 if I remember correctly, Its ancient.

---

### Post by trak87 on 2007-05-13
Ubuntu handles SATA fine. The decision  whether to get PATA or SATA is what your motherboard will support. From what I hear they are about the same as far as speed with perhaps a slight advantage to the SATA for burst speed.

---

### Post by ComeGetSome on 2007-05-13
> **jerrylamos said:**
> My interpretation, Ubuntu tries to speedup boot by doing things in parallel plus simulate IDE and SATA as SCSI devices and then gets in trouble when one function tries to start when another function isn't ready yet.  You could check the following post for my workaround, and also a fix by a developer (if you can follow his directions please let me know how you did it)

[http://ubuntuforums.org/showthread.php?t=424225&highlight=workarounds](http://ubuntuforums.org/showthread.php?t=424225&highlight=workarounds)

The easiest fix is to use Ubuntu Edgy Eft 6.10 the preceding release that doesn't have the fancy code in it.  They are working on a fix for Feisty 7.04, but maybe the fix might be in Gutsy 7.10 next fall.

Cheers, Jerry

Hmm, As I mentioned before I am a Linux newbie. I will try the booting with no hdd suggestions from that thread. From what iv read everyone seems to think it deals with the change in the Kernel as Starcraft.man first pointed out.  The hardest part about finding the solution to my problem is that everyone has some slight deviations from my exact problem. Hopefully they fix this soon as I would really love to try Ubuntu out. 

Also you mentioned the Edgy version of Ubuntu, Do you know the link to where I can download that?

---

### Post by ComeGetSome on 2007-05-13
> **trak87 said:**
> Ubuntu handles SATA fine. The decision  whether to get PATA or SATA is what your motherboard will support. From what I hear they are about the same as far as speed with perhaps a slight advantage to the SATA for burst speed.

Alright then thanks. Ill buy a SATA then.

---

### Post by starcraft.man on 2007-05-13
> **ComeGetSome said:**
> Hmm, As I mentioned before I am a Linux newbie. I will try the booting with no hdd suggestions from that thread. From what iv read everyone seems to think it deals with the change in the Kernel as Starcraft.man first pointed out.  The hardest part about finding the solution to my problem is that everyone has some slight deviations from my exact problem. Hopefully they fix this soon as I would really love to try Ubuntu out. 

Also you mentioned the Edgy version of Ubuntu, Do you know the link to where I can download that?

[Here,]("http://releases.ubuntu.com/") easy place to get the old edgy version till you get new drive. Just pick your version :)

EDIT: OIIIII!!!! The Main Ubuntu mirror page is down? Can it be? I can't load the page... >.>.

Well, go here then, the [mirror homepage.]("https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive")

Is there something funny with me or is the first link to releases page dead?

---

### Post by catdriver on 2007-05-13
well that answers my issue... I think.... My question would be why did I get this error after I tried to upgrade from 6.05 Dapper to 6.10 Edgy?  I also get it with a brand new 7.04 disk.  I get that I guess....  I do have an ancient  1 ghz machine with one ATA maxtor 60gb drive and two cd's (a burner and a reader...) I need em both, but I need a viable system first.  So I will attempt unplugging one CD and see......


1 hour later......
well it works with one HD and one CD, 7.04 is up..... Love the migration tool, and the new partition resize tool... I was in fear of having to reformat my entire disk as previous versions required....

---

### Post by ComeGetSome on 2007-05-15
Thank you for the link Starcraft.man, Ill try Edgy out till I get the new disk.

Cat, thats good to hear :), I might try something like that to see if I can get it to work as well. One quick question where that one HD and CD drive on one IDE cable or on separate cables?

---

