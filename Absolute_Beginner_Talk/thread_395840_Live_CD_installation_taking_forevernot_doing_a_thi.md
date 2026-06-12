---
title: "Live CD installation taking forever/not doing a thing"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Ankher on 2007-03-28
Okay, I'm running on an AMD 64x2, dunno anything else about it, except that its' perfectly capable of running Ubuntu.

Since the thing says 64 in the processor name, I naturally assume that it must be one of AMD's 64 bit processors, and I download (perhaps with uTorrent (I think that's supposed to be a 'mu' thing, but I don't know how to put that in)), burn and run a CD with the amd64 thing. it starts without a hitch, and I select 'run or install Ubuntu' or similar. It shows the normal Ubuntu loading screen, except the logo isn't filled in.

I assume that this means that my machine should run the normal form of Ubuntu, so I download a normal iso. I burn it and try installing. This CD is 1-4x rw. The installer runs, also without a hitch (though I think it's kind of weird that the sight has a Minneapolis mirror, but does not list Minneapolis in its time zone selection thing, so I went with North Dakota) until it gets to Step 5 of 6. I try the Resize option, select what I want, and click _F_orward. It grays out, and in about 30 seconds, it re-colors. I click it again, the cursor turns 'busy' and the button grays out and does not re-color. After a few experiences with this, I check the CD for defects, it says 4.

I try downloading another copy. For this one I use uTorrent, because my computer/router randomly has problems downloading stuff. After I overwrite my CD rw, the first thing I do is check for defects, since it says 0, I reburn my iso to a 1-16x CD-r. That's what is currently running. I have three tabs open in Firefox, and also am running the Installer. It is on step 5 of 6 and is grayed out. It has been this way for around half an hour (probably less). Is this normal? My computer really isn't making any sort of noise, but it's really quiet. Sometimes a fan will come on, and then go off.

So, sorry about writing so much, but any ideas? :confused:

---

### Post by dbbolton on 2007-03-28
64 bit processors can run both i363 and 64-bit versions of ubuntu.

did you check the md5 sum on the iso's before burning them?

---

### Post by Ankher on 2007-03-28
Oh, well mine apparently can't run 64 bit ones. w/e.

How do I do that?

---

### Post by Bartender on 2007-03-28
Go back to the download page you used the first time, but download the i-386 version.  Check the MD5, then burn to CD at a slow speed, somewhere between 2X and 8X maximum.

---

### Post by Ankher on 2007-03-28
Okay, that sounds like it would do something... but I don't know what! :)

If it would help Ubuntu install, I'd like to know how to check the MD5.

But my real question is this: why is it taking so long to install? It's been running for about two hours now, with no signs of progress. I've been running Firefox, and went in and out of Terminal. Won't somebody help? Or at least tell me how long it's supposed to take (someone told me it should take forever, but they've never used Ubuntu, they're just speaking out of experiences with Live CDs)

---

### Post by dbbolton on 2007-03-28
to check md5 sums, enter this in the terminal:
```
md5fum ~/file.iso
```where ~/file.iso is the path to the ISO that you want to burn. after a few moments, the command will return a string of numbers. you must then compare those numbers to the .md5 file that should be found where you got the iso.

if they match, you're ready to burn the iso. if they don't, you'll have to download the iso file again- probably from a different source.

---

### Post by Ankher on 2007-03-28
Ummm... okay. Does this work in Windows? 'cause I still haven't installed Ubuntu, and I haven't mounted my hard disk, (that's what I was doing, didn't really work)

---

### Post by kittyhawk63 on 2007-03-28
What speed did you burn the ISO to the CD?

I recommend that you burn the ISO at 4x or slower. 1X is the best you can do, if you have the time. That is what I did, and I have had good installs except for the situation given below.

Today when I installed, it hung at 82% installed and stopped. I turned on my broadband modem and off it went and finished the install. It showed it was downloading some files. Dunno? But I have had to do this on the last two installs.

kh

---

### Post by Ankher on 2007-03-28
I don't know.

Umm... okay, but that's not the problem I have: When I'm at the partitioning stage I press the Forward button when I'm ready and it becomes disabled. Then in thirty seconds it's enabled again. So I press it. Then the button disables, the cursor goes busy and nothing further happens. Nothing hangs, just nothing happens. So: what's going on?

---

### Post by kittyhawk63 on 2007-03-28
> **Ankher said:**
> I don't know.
Umm... okay, but that's not the problem I have: When I'm at the partitioning stage I press the Forward button when I'm ready and it becomes disabled. Then in thirty seconds it's enabled again. So I press it. Then the button disables, the cursor goes busy and nothing further happens. Nothing hangs, just nothing happens. So: what's going on?

Not sure. But you have not answered this question. What speed did you burn the ISO? Anything faster than 4x can and often does give people problem.

---

### Post by Ankher on 2007-03-28
I'm not sure: I have one that has a max of 4x, so that one is at 4x. The other one can go up to 16x, so I'm not sure. So should I try again with the 4x cd? or reburn the cd at 1x?

---

### Post by kittyhawk63 on 2007-03-28
If you have the time, I highly recommendthe 1x. I> **Ankher said:**
> I'm not sure: I have one that has a max of 4x, so that one is at 4x. The other one can go up to 16x, so I'm not sure. So should I try again with the 4x cd? or reburn the cd at 1x?

If you are not in a hurry, I would recommend the 1X. You will have the very best quality you can get.
kh

---

### Post by Ankher on 2007-03-28
I'll try that! Thanks!

---

### Post by kittyhawk63 on 2007-03-28
> **Ankher said:**
> I'll try that! Thanks!


You're wlecome. I hope that will fix your problem. Come back if it does not.
kh

---

### Post by Ankher on 2007-03-28
Sorry, that doesn't work: My burning software is really weird (when you close it it gives you a bunch of errors) but I don't want to/can't get anything different right now. I tried to set it to 1x, but the only two things I could set it to (for CDs) are Max and 4x, so I chose the 4x, and also checked a box that said something about improving quality. (The software is Sonic). And now I'm running this new Live CD, and here's what's happened: The first time I tried the installer I didn't get past the first part, because the system hung. So I tried again and this time it gives me the same result as always. Any other suggestions?

---

### Post by dbbolton on 2007-03-29
are you using a CD-RW ? if so, use a good quality CD-R.

---

### Post by Ankher on 2007-04-06
> **dbbolton said:**
> are you using a CD-RW ? if so, use a good quality CD-R.

I am, and will try again w/ the CD-R. Thanks!

---

### Post by Ankher on 2007-04-06
Okay, I'm using a CD-R now, the only problem is, my stupid burning software only lets me go down to 16x for the CD-R, so that's what I burned it at, the defect checker says that there aren't any problems with it, but the same thing still happens: once I get to the partitioning screen, I get ready and everything and hit forward. The button disables, and in a few seconds, the button is clickable again. I click it and now it's not clickable, and the cursor is busy when it's over the install window, but nothing's happening. Help!

P.S. I looked [here]("http://www.psychocats.net/ubuntu/installing") for kicks and giggles, to see if they could help, and while looking at the installing page, I noticed that there are message type things in orange at the bottom of the Ubuntu startup screen for the Live CD. None of the 4 or 5 I've burned have had that message, but only one (the 64x one) didn't start up at all. Does this matter?

P.P.S. Okay, instead of choosing to resize sda1 I chose to manually resize the partition table. Anyway, I get all ready and click forward and it starts running and everything seems to be going fine until BAM! I get an error saying that I can't resize sda1. Is there a reason for this? (sda1 is my windows partition btw)

---

### Post by Ankher on 2007-04-06
"I must shout my excitement from the top of something very high!" (Luigi from Cars) :)

It turns out that the problem was that my Windows's partition's file system (NTFS) had a problem w/ it or something, so I did what the details said (run chkdsk /f and reboot twice) and now it's installing! :)  Thanks for all your suggestions! :KS

---

