---
title: "I think ISOs hate me"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2005-12-20
Ok So I ate 10 CDs last week burning Ubuntu.  Finally I burned it on a l;aptop and got it installed.  I LOVE IT.

I Put that same CD in to move the laptop over....bad cd.  Red screen on file copy the base system.

So I burn and ISO in Gnomebake,,,at 1 X.  Nope.

I reformat the laptop with the "proven" good burner, put XP and nero on it and..Burn process failed.  On new media.

So far BURNING Ubuntu has been the hardest thing ever!

Just venting.

Aside from that, Ubuntu ROCKS.  Im going to erase windows on my machine entirely.  It runs everything wonderfully, INCLUDING EverQuest...Im scared!  Gaming in LINUX!


So Anyway...I ordered the Ubuntu CDs ...any ETA on those.....and in the mean time..any sugguestionms on windows software that will burn CDs...nero is rapidly becomming my least fave....I dont have the cash to get a new Burner for my Ubuntu box yet.

---

### Post by phillyboy on 2005-12-20
It is probably not your CD, but something with your motherboard if it works in one and not the other. Do you have any sort of enhanced IDE transfers or bus mastering you can toggle? 

I have a P4P800 SE (still the original BIOS version...9 I believe), and if I did not turn off their "enhanced mode" and put it into "compatible mode" for IDE transfers, then Ubuntu would conk out with a red screen during install. I believe it was when it would either try to automount the CD or copy files. 

So give that a shot, or if you already have Linux/Windows installed there are ways of doing a cd-less installation of Ubuntu (one is very straightforward, one takes a few steps to accomplish). I will check this thread later if you would like a run-down of how to do this (after my last final :razz:)

EDIT: Wait, I think you might not need this then...I am not quite as clear of what you want. Did you have two machines? One where Ubuntu successfully installed and one where it would show a red screen? Or are you just having trouble burning CDs in general?

---

### Post by acascianelli on 2005-12-20
Have you tried running MD5 checks on the images you're downloading?

---

### Post by GQed76 on 2005-12-20
Well, i checked the MD5 on the actual ISOS at one point..didnt burn them, just mounted them..and even THEY didnt check out....so thats not even the burn process.

I think its a combinaton of crappy burning software and a bum drive...its wierd...on the laptop, the CD i used worked on the PC, but errored out in different places on the laptop...and the CD checked its own integrity fine.

There are like NO options in the laptop BIOS to set...wonder if it has a update to that.

---

### Post by Bartender on 2005-12-20
It took about 5 or 6 weeks for the CD's to show up here in Western Washington State.  

I've got a weird one for you guys - I tried four different LiveCD's on my M$ machine (not the one in my sig; that's for Ubuntu only) and not a one of them worked.  
Yes, the BIOS was reset to boot from CD first.  The DVD drive started, then stopped, started/stopped, several times.  The drive light blinked numerous times.  Then the computer gave up and went on to the HDD.  I think it has something to do with the MB.  Maybe the BIOS IDE Modes (I think it is in Enhanced Mode) have something to do with it...

---

### Post by phillyboy on 2005-12-20
[QUOTE=GQed76]Well, i checked the MD5 on the actual ISOS at one point..didnt burn them, just mounted them..and even THEY didnt check out....so thats not even the burn process.
.[/QUOTE]

If the md5sums did not check out, then you will have bum cds when you burn them. :D How did you download them? Certain browsers *cough* netscape,mozilla *cough* used to download files in ASCII, not binary (I dont remember if it was just a default that you could change or not) and would fubar whatever you were downloading that wasn't a text file. 

Anyhow, try not mounting them either and checking out their md5sums, or redownload the ISO images and check again.

---

### Post by GQed76 on 2005-12-20
Downloaded them in Firefox...one in ubuntu one in Xp..both 1.5..I think I just have  bad luck hehe

---

### Post by phillyboy on 2005-12-20
[QUOTE=GQed76]Downloaded them in Firefox...one in ubuntu one in Xp..both 1.5..I think I just have  bad luck hehe[/QUOTE]

Dang, sounds like it :( You could try using wget to download them in Ubuntu

---

