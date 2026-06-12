---
title: "Macbook now unbootable"
date: 2009-03-07
forum: Apple Hardware Users
---

### Post by NoBugs! on 2009-03-07
Long after installing Ubuntu on a macbook (4,1 model), I noticed it will no longer boot bootable cds. I tried holding alt/option while starting up, and selecting cd, but it just won't start. It only shows a black screen with "_". I can still successfully load the Ubuntu or Mac os operating systems on the hard disk, but it seems there is no longer any way to boot from cd.

I know the cd drive and cd I am using both work, because I have successfully started this ubuntu livecd in virtualbox, once the computer is running in mac os. Mac os has the latest updates, too.

It seems that something about the ubuntu installer, and/or refit has messed up something with efi??

---

### Post by inphektion on 2009-03-08
I noticed this too after I installed refit and ubuntu.  to boot from cd I have to boot into the mac os and then go to startup disk and select the CD from there.  then it will reboot direct into cd.  
But yes refit never shows it and holding opt down never does either.  weird.

---

### Post by NoBugs! on 2009-03-08
> **inphektion said:**
> I noticed this too after I installed refit and ubuntu.  to boot from cd I have to boot into the mac os and then go to startup disk and select the CD from there.  then it will reboot direct into cd.  
But yes refit never shows it and holding opt down never does either.  weird.
I used to be able to boot using mac os select-startup-disk, but now it seems that won't work either. refit showed the cd, and I can select to boot it, but it only shows black screen with underscore _.

I remember doing some ram-reset and smc-reset that still wouldn't fix this problem. 
Could it be related to a refit [bug]("http://sourceforge.net/tracker/?group_id=161917&atid=821764")?

---

### Post by cyberdork33 on 2009-03-08
> **NoBugs! said:**
> I remember doing some ram-reset and smc-reset that still wouldn't fix this problem. 
Could it be related to a refit [bug]("http://sourceforge.net/tracker/?group_id=161917&atid=821764")?
If it was a refit bug, then holding alt on startup to select the disc would still work since that would not use refit.

Macs are notorius for having issues with booting CDs. Are these pressed CDs or burned ones? Can you try a pressed CD?

If you can only try burned discs, make sure to burn the disc as slow as possible to increase compatibility.

---

### Post by NoBugs! on 2009-03-09
I also tried a professionally-labelled OpenSolaris livecd, and it had the same exact problem.

---

### Post by cyberdork33 on 2009-03-09
> **NoBugs! said:**
> I also tried a professionally-labelled OpenSolaris livecd, and it had the same exact problem.
that doesn't mean it is pressed...

What about the OSX Install Disc that came with your mac? Does that boot?

---

### Post by NoBugs! on 2009-03-14
I got the livecd to boot!

The steps to fix this problem:
1: With the computer turned off, without the cd in it, press and hold the power button, it will flash the light on the side and then start up. Start up into Mac OS.
2: Put the Linux cd in.
3: Go to Mac system preferences, startup disk.
4: Select the Linux cd, and restart.

This seems to be the only reliable way to boot bootable disks on my mac. I've had this problem for quite awhile, do you think Apple knows about this problem?
This seems related to [this problem]("http://discussions.apple.com/message.jspa?messageID=6606353").

---

### Post by cyberdork33 on 2009-03-15
> **NoBugs! said:**
> I got the livecd to boot!

The steps to fix this problem:
1: With the computer turned off, without the cd in it, press and hold the power button, it will flash the light on the side and then start up. Start up into Mac OS.
2: Put the Linux cd in.
3: Go to Mac system preferences, startup disk.
4: Select the Linux cd, and restart.

This seems to be the only reliable way to boot bootable disks on my mac. I'v had this problem for quite awhile, do you think Apple knows about this problem?
This seems related to [this problem]("http://discussions.apple.com/message.jspa?messageID=6606353").
you actually need to be careful doing that because Ubuntu has no way to set the startup disc back to OSX...

---

### Post by NoBugs! on 2009-03-15
> **cyberdork33 said:**
> you actually need to be careful doing that because Ubuntu has no way to set the startup disc back to OSX...

Yes, but you could just hold alt/option at startup and select Mac. Or, just take the livecd out. It seems to work well so far.

---

### Post by pclark36 on 2009-03-16
Even with the older macbook, shouldn't holding the "C" key down during boot fire up the CD?

---

### Post by NoBugs! on 2009-03-16
> **pclark36 said:**
> Even with the older macbook, shouldn't holding the "C" key down during boot fire up the CD?

Yes, it should, so should alt/option and selecting cd. However, the above instructions were the only way I was able to start from cd recently (I also noticed the alt-option menu always shows the cd as "windows", could this be a bug in the Apple/intel efi?)

---

### Post by cyberdork33 on 2009-03-16
> **NoBugs! said:**
> Yes, but you could just hold alt/option at startup and select Mac. Or, just take the livecd out. It seems to work well so far.
Yes, I am aware, but there are those that have complained in the past about not being able to boot into OS X after booting Ubuntu ("Ubuntu Broke My Mac" and all that).
> **NoBugs! said:**
> Yes, it should, so should alt/option and selecting cd. However, the above instructions were the only way I was able to start from cd recently (I also noticed the alt-option menu always shows the cd as "windows", could this be a bug in the Apple/intel efi?)
I guess you could call it that. I don't think Apple cares though. It is normal. rEFIt will recognize it better.

---

### Post by thairan on 2009-05-14
> **cyberdork33 said:**
> Yes, I am aware, but there are those that have complained in the past about not being able to boot into OS X after booting Ubuntu ("Ubuntu Broke My Mac" and all that).

I guess you could call it that. I don't think Apple cares though. It is normal. rEFIt will recognize it better.
I'm not sure if my problem is quite the same. I installed Jaunty on my macbook 1 as per instructions in these forums, everything went well, but no sound. I thot i'd re-install cuz i read the sound mite work after that. To start rite from scratch again i tried to boot from my pressed mb start-up disk and got a grey screen with what resembles a padlock on it, and a spot to put in my password....no go. I've tried numerous keys held down at start-up...still nothing. Other than the sound..the Linux works fine. What am i missing?

---

### Post by cyberdork33 on 2009-05-16
> **thairan said:**
> I'm not sure if my problem is quite the same. I installed Jaunty on my macbook 1 as per instructions in these forums, everything went well, but no sound. I thot i'd re-install cuz i read the sound mite work after that. To start rite from scratch again i tried to boot from my pressed mb start-up disk and got a grey screen with what resembles a padlock on it, and a spot to put in my password....no go. I've tried numerous keys held down at start-up...still nothing. Other than the sound..the Linux works fine. What am i missing?
it sounds like you have a firmware password on your mac.

---

### Post by thairan on 2009-05-19
> **cyberdork33 said:**
> it sounds like you have a firmware password on your mac.
Brain-dead me.....it wanted the mac password, not the ubuntu....works good now...even the sound.
Thanks a lot for your quick reply.

---

