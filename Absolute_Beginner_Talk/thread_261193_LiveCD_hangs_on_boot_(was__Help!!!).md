---
title: "LiveCD hangs on boot (was:  Help!!!)"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by protohunter on 2006-09-19
Whenever I try to run the live cd it gets to the part where it says "mounting root file system" and then after a long time says something like "coulden't mount root file system drive timed out" or something like that!!

Help what could be causing this?:confused:

---

### Post by slibuntu on 2006-09-19
Your post is very vague, and also your title is woeful, read the sticky at the top of this forum, post as much detail as you can to let people help you

---

### Post by protohunter on 2006-09-19
Well it used to work but one time when I tried to run the live cd I got that error, my current os is windows xp pro and I would like to install Ubuntu on a second hardisk so i could dual boot(xp for games) but I can't seem to run the live cd due to the error

Is there a way to install ubuntu without using the live cd function?

---

### Post by sktx on 2006-09-19
Hey there protohunter, welcome to the Ubuntu forums.  

Sorry to hear that you're having trouble with the LiveCD. I'm assuming it's a copy of the default Ubuntu 6.06 Live/Install CD, am I right?  Did you download it or did you get sent to you from ShipIt?

Have you tried the Test CD Integrity option at the first menu? It's possible, if you downloaded and burned the CD yourself, that the CD or the ISO file are corrupted.  

sktx

---

### Post by sktx on 2006-09-19
> Is there a way to install ubuntu without using the live cd function?

There is, if you download and burn the Ubuntu Alternative CD.

---

### Post by protohunter on 2006-09-19
I got the Cd from ship it and here is the exact error- 

"Timeout waiting for DMA"

"Drive not ready for command":(

---

### Post by protohunter on 2006-09-19
I got the Cd from ship it and here is the exact error- 

"Timeout waiting for DMA"

"Drive not ready for command"

Anybody know?

Pleasae don't leave me using windows!!!!!:-&

---

### Post by confused57 on 2006-09-19
You may have to enable IDE DMA access(or something similar) in your bios?  Just a guess, may or may not be the problem.

---

### Post by protohunter on 2006-09-19
Ok thanks for the reply, i'll try looking for something like that in the bios and post back after I find out what happens.

---

### Post by protohunter on 2006-09-20
Nope no such option in bios:confused: 

Guess ubuntu just hates my hardrive?:-({|=

---

### Post by Brunellus on 2006-09-20
Thread title was changed to better reflect nature of help request.

When posting requests for help, please try to post under appropriate thread titles.

If, for instance, you need help with a USB device of some sort, a good thread title would be:

"Need help with USB device"

A bad one would be

"HELP!!!!TOTAL NEWBIE"

The first one tells users who know a thing or two about USB problems that they know how to solve your problem. The second, while appealing to the pity and mercy of the community, is not likely to get you much help--especially if it turns out your particular problem is complex, new, or rarely-seen.

---

### Post by sirlancelot on 2006-09-20
It's not your harddrive, DMA is your CD-ROM drive. There's an option in your bios to enable/disable DMA I believe.

If not, then Ubuntu should have an option somewhere before it starts booting...

---

### Post by sktx on 2006-09-20
Hey proto, I did a little bit of searching around and might have found a possible solution...

Start your computer up with the LiveCD in the drive, and when it gets to the first LiveCD menu, make sure the first option is highlighted and then hit **F6** to open the Other Options, which shows some of the commands that are passed to the boot loader. Hit the left-arrow key on your keyboard until the cursor is right before the **--** at the end of the line, and type **nodma** there... 

the end of the line looks like this, the part you'll add is underlined:
```
boot=...root=/dev/ram rw quiet splash _nodma_ --
```


Hope this helps..
..sktx

---

### Post by protohunter on 2006-09-21
Sorry not even adding that command line helps.

---

### Post by sktx on 2006-09-21
Have you tried installing with a copy of the Alternative CD instead of the Desktop LiveCD?

---

### Post by Brunellus on 2006-09-21
I suspect the CD itself was corrupted during the burn.  verify the .iso you used to burn the CD, and burn it at a slower speed.

---

### Post by NordicRX8 on 2006-09-21
It may also be the optical drive itself.

I recently tried an ubuntu install, same error as the OP.  Checked the CD, and it checked out ok.  The alternate install CD and server CD versions worked fine though.  Gave up on ubuntu (for the time being), and tried Fedora 5 and then OpenSuse 10.1.  Both installs had minor issues that acted like a bad optical (long time to access, unusual access noise) drive.  Checked their install disks, none found bad.  Messed around with opensuse for about a week, and during that time installed that distro about 6 times (too much messing around, can cause an install to get fubar'd).  I decided to burn a DVD image of Opensuse instead of relying on the multiple CDs.  Went out and got a $30 16x DVD-DL burner (to replace the 32x24x32x CDRW) for my Linux box.  Re-installed opensuse... wow! It loaded sooo much faster!   Hmmmm.... got me thinkin.  How about we try Dapper again... popped in the Live CD disk that wouldn't fully load... whala!  Unbuntu loaded from the CD, installed the distro to the HD (TWICE!, first install went bad, due to too much tweaking), and I'm a happy camper.  OpenSuse was nice... but seemed a lil sluggish (bloated) on that old PC.  Nothing was changed (no BIOS adjustments) except the Optical drive itself.

How old is your Optical drive?  Those things USED to last forever (admitted plextor junkie), but in the last 10 years or so, I've noticed optical drives don't seem to work as long (they are also a LOT cheaper).

Good Luck

---

### Post by protohunter on 2006-09-21
I have 2 drives, an Hp cd-writer plus 8100 series (made in 1998 i think) and a tobisha Dvd-rom drive and both get the same error.

I'll try downloading the alternative iso again (last night I gave up on it downloading 32kb/sec)

---

### Post by sktx on 2006-09-21
> **protohunter said:**
> I'll try downloading the alternative iso again (last night I gave up on it downloading 32kb/sec)

If the D/L is moving too slow for you, try getting the torrent and using that.  Or vice versa, if you're already using the torrent.

Heh... when I got my copy of the alternative cd, to upgrade from breezy, I was stuck on dialup.  It took me about a week to download, using wget. So think of downloading a whole CD image at 2kb/s to 4.5kb/s and suddenly 32kb/s doesn't seem so bad. :)

..*sktx*

---

### Post by protohunter on 2006-09-21
heh ya, I guess it would suck @ 2kb/s but for my dsl which usually gets 330kb/s, 30kb/s seems like tourture

I had dialup for over a year and man did that suck lol.

---

### Post by podunk on 2006-09-21
Did you just install your second hard drive, or has it been there and working for a while?

If you just installed it - did you set the jumpers? When you first start your computer is the drive listed in the first hardware screen as the right kind of drive?

You say the CD used to work. Has something changed in your system? New hardware, anything like that?

could the cd be scratched maybe? Can you download and burn a new one to see if that is the problem?

---

### Post by protohunter on 2006-09-23
That's just great, after burning the alternative cd windows says "this cd is not in a format recinized[spelt wrong i know] by windows"

---

### Post by gn2 on 2006-09-23
You can ignore that warning, because you won't be running it with Windows...

---

### Post by protohunter on 2006-09-23
And it wont let me boot from cd to install it!!!!!!!!!!!!!!!

---

### Post by xpod on 2006-09-23
> "Timeout waiting for DMA"

"Drive not ready for command"
Reply With Quote 

I get that same error 6 times when running live cd then a I\O buffer error for 8 lines THEN it goes on to run and install fine.

It used to load up right away without a prob but since messing around and tearing 80 wire cables and having to use a 40 wire cables...well i cant think what else caused it to slow down with those errors..

It takes about 5 mins to get past that but goes on fine as i said after that

---

