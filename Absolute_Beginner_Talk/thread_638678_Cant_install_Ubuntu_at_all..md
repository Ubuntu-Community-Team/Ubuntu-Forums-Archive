---
title: "Cant install Ubuntu at all."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by siion on 2007-12-12
Whenever I try to install ubuntu it stops at the partitioner stage.

I've tried 2 disks, Live and text based, the text based one stops at 36% and doesnt do anything, the live cd one stops at 46% and doesnt do anything. 

I have enough ram, 2gb, tested that. using amdx2 3.1ghz, 880amd320mb. 

I took out all my HDD's and left 1 in, a 200gb one, still same problem.

Any ideas how I can install? :confused:

---

### Post by 720iD on 2007-12-12
how is your drive partitioned at the moment?

---

### Post by Don1500 on 2007-12-12
at the partitioning window, what selections are available, and what choices did you make?

---

### Post by LowSky on 2007-12-12
> **siion said:**
> 880amd320mb. 


what does this mean?

---

### Post by aysiu on 2007-12-12
Did you do a checksum on the .ISO before you burned it?

More details here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by siion on 2007-12-12
thank you for extremely fast replys.

The torrent is going to take hours to download though. 

The md5 sums both came out the same, one thing i dont get is, i am using i386 desktop one. In brackets it says (intel) i have an AMD64 x2, but when i tried the AMD 64bit one, it said my AMD isnt 64 bit and wouldnt install.

Sorry lowsky ment to write 8800nvidia 320mb (gfx)

It doesnt get to the initial partitioning window, it just says starting partitioning and doesnt load. (its after you pick your keyboard language and layout).

The hard drive in is currently 100gb/100gb, 1 for XP and other for ubuntu.

Any ideas what I could do, cheers.

---

### Post by siion on 2007-12-12
any ideas?

thanks.

---

### Post by flamelab on 2007-12-12
Re-burn the new ISO and check !
It is possible that the iso you had downloaded was incomplete .
And I would propose that you download Ubuntu from [www.ubuntu.com]("www.ubuntu.com")
not torrent because it may be corrupt .

---

### Post by siion on 2007-12-12
I've downloaded 3 from ubuntu.com, not tried a torrent yet.

All 3 do same thing. =(, guess all I can do is keep trying ISO's n give up when i run outta cds lol?

---

### Post by philinux on 2007-12-12
Have you tried the safe graphics option.

also at the start screen press F6 for more boot option and remove 

quiet and splash

you'll see any error messages then. Press enter to boot.

---

### Post by siion on 2007-12-12
I just gave that a shot, but no errors came up. I tried the safe graphics option, that too didn't work.

I found this: [http://ubuntuforums.org/showthread.php?t=615217](http://ubuntuforums.org/showthread.php?t=615217)

He said he downloaded 2 alternative ones, finally one worked, should I try same until i run outta cd's?

thank you.

---

### Post by candtalan on 2007-12-12
If the md5 comes out ok then good.However, an additional self check of the cd in the actual target drive (CD boot menu - check/verify CD) has the benefit that the drive is also checked. 

I would also examine your existing partition arrangement with use of say - parted magic - or similar. It is a small live cd based partitioner. Avoid changing anything at this stage yet, just look. See if anything can be reported here?

---

### Post by philinux on 2007-12-12
> **siion said:**
> I just gave that a shot, but no errors came up. I tried the safe graphics option, that too didn't work.

thank you.

when you say no errors were there any messages on the screen. Should have been loads. what was the last one.

---

### Post by siion on 2007-12-12
What file would I check if I check the cd's md5? 

What do you mean by examine my existing partition arrangement? 

Thank you!

---

### Post by siion on 2007-12-12
I thought you ment like, it would of came up with big message saying errors.

I saw this, but wasnt sure if it was like a failure or something.
[http://www.zantetsukan.com/upload2/files/8938DSC01173.JPG]("http://www.zantetsukan.com/upload2/files/8938DSC01173.JPG")
Took shot on phone cam

They where the only things that had errors in, the rest at the begining was just way to fast to read.

---

### Post by Jense on 2007-12-12
Do you have any 3.5 disk in the drive? 
Any usb sticks connected? I had problems installing while my usb stick was plugged in.

---

### Post by siion on 2007-12-12
oh yeah I do have a USB stick in, but I think I tried one time and it wasnt in, tried so many times now... its like a life time lol.

I'll give it a quick shot, can't be 3.5disk, i dont have a floppy drive.

Thank you, report back in a moment.

---

### Post by philinux on 2007-12-12
> **siion said:**
> I thought you ment like, it would of came up with big message saying errors.

I saw this, but wasnt sure if it was like a failure or something.
[http://www.zantetsukan.com/upload2/files/8938DSC01173.JPG]("http://www.zantetsukan.com/upload2/files/8938DSC01173.JPG")
Took shot on phone cam

They where the only things that had errors in, the rest at the begining was just way to fast to read.

Those are hard disk errors on sector 0, hmmmm someone else may have seen something similar.

---

### Post by siion on 2007-12-12
Well jense i think it worked, managed to get past the partitioner stage when it stopped @ 46%.

So fingers crossed it will continue to install.

I took out my mp3 player, flash memory, so maybe that was causing the errors or something?

Thank you! :)


What does "no root file is defined" mean?

---

### Post by philinux on 2007-12-12
Just leave it running it can take a while. Check the hard disk light for activity.

---

### Post by siion on 2007-12-12
is this setup right?
[http://www.zantetsukan.com/upload2/files/6069Screenshot.png2]("http://www.zantetsukan.com/upload2/files/6069Screenshot.png")

(sorry for being a pain in the a lol)

Thank you!

---

