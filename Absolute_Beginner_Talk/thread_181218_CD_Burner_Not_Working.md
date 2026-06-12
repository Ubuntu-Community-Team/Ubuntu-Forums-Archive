---
title: "CD Burner Not Working"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-05-23
Hello all,

I've recently been experience some very strange behavior from my CD burner. I believe it all started when I attempted to use NeroLinux (based on fairly good experience with my Windows version of Nero.) I tried to burn a .nrg image to a CD and then do a write check. During the write check, it found several read-errors, and this caused my system to all but freeze completely. I attempt to cancel the check, and I'm not even sure anymore whether I actually got in cancelled or if it just finished.

After that, I attempt to burn the .nrg image again, but this time at the slowest speed I could, hoping to avoid the errors on the disc. I left my computer for about 30 minutes or so, and when I came back, the write was stuck at 4 or 5%, and going no where--it wasn't reporting any errors, either. So, again, I attemptted to cancel the burn, and I believe I suceeded. Just after this, my real problems start.

I thought I'd give Nero one last try, this time burning a bin/cue image that K3b hadn't burned successfully. I put another blank disc in the my CD drive, and this time, Nero wouldn't recognize there was a disc in the drive at all. Finally fed up, I gave up on Nero, and decided to look for another burning program.

I read around a bit, and decided to get Gnomebaker. I downloaded it, and tried to get it to burn something, but it wouldn't recognize the blank disc either. Thinking maybe it was a problem with the disc, I switched to another one, then a third, finally realizing that, in fact, it wasn't just the programs that weren't recognizing the blank discs, but my computer wasn't seeing them at all.

I got a little worried at this point, but thinking maybe it was something with GNOME, I restarted the GUI, but still the problem persisted. I restarted my computer, but there was no change. I test several other discs, and even borrowed a completely different kind of CD-R from a friend to try, but nothing worked. Finally, I tried a blank DVD, which was recognized. However, when I tried to burn about 3.8 GB worth of stuff on to the 4.7 GB disc, I was told to insert a disc with at least 3.8 GB free.

All this had me a little worried. Then, I tried putting in a burned CD I had been able to read earlier. Nothing--it didn't even register. Non-burned CDs worked fine. Then, I tried a burned DVD of mine. It recongized it, but it told me it was a blank DVD-R. Considering all this stuff had just worked the day before, I was really getting worried my CD-R/DVD-R drive was ruined.

However, I decided, I'd try to reinstall Ubuntu--with Dapper coming out soon, I thought I'd give it a try. Unfortunately, being unable to burn discs meant I'd have to just reinstall from my Breezy disc, then do a distro-upgrade to Dapper. I figured out how to get my /home directory onto a seperate partition, then I reinstalled Breezy. After, I tried to distro-upgrade to Dapper, and ran in to trouble, which I've posted about before, but isn't really imporant here--basically, I just had to install Breezy yet again.

Now, there I was on a new install of Breezy, hoping that my drive is working--a hope that was soon dashed. The first CD-R I put in was recognized right away, but when I tried to burn an iso to it (the Dapper installation iso, by the way), I was told to insert a disc that had enough free space for the image. Hoping that maybe this time it WAS just a problem with the dics, I tried another one--that one and all subsequent CD-Rs I've tried haven't been recognized, just like before my reinstallation.

I tried my DVD-R next. Recognized immediately, I moved about a GB worth of stuff on it to be burned, and it burned successfully. That was some good news--at least until I reinserted the disc, and it recognized it as a blank DVD-R again.

So, that's were I'm at right now. I don't understand why the problem carried over from one installation of the OS to the next--unless there's something in my /home that's causing the problem, but I have no idea what it is--there's not even a .nero folder or anything there. And, I don't understand how a program can actually permanently ruin a hardware device on your computer, which is what appears to have happened.

I'm sorry for the extremely long post, but this is worrying me a lot, and I hoped by going into detail it would help others see what I did wrong. Hopefully with your help I'll be ablt to resolve this problem soon.

Thanks,
Steggy

---

### Post by rahelvey on 2006-05-23
try gnomebaker

---

### Post by Steggy on 2006-05-23
[QUOTE=rahelvey]try gnomebaker[/QUOTE]
I don't mean to be rude, but I clearly said in my post that I tried using Gnomebaker--and something else I didn't mention was that I also attempted to use K3b after the problems started, but to no avail. The problem really seems to be that my drive altogether doesn't recognize burnable media correctly (or at all.)

---

