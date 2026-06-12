---
title: "Cannot Boot Ubuntu 7.04"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by jessek on 2007-04-26
I cannot boot Ubuntu from a CD I've burned.  I know the CD burned successfully, because I can bring up the autorun - in windows XP and everything looks fine.  When I try to turn off my PC, and boot up Ubuntu - no matter if I go into system setup and put the boot sequence at CD ROM first, or CD ROM ONLY - it will not boot up with the Ubuntu disk.

Is this a 7.04 thing?  Am I doing something wrong?

Thanks in advance
Jesse

---

### Post by Kobalt on 2007-04-26
You may need to boot with noapic nolapic options. 
Start your computer with the Live CD inside your drive. When you get to the first Ubuntu boot screen press F6 to access *Other options* and add at the end of the line (and after a space) : *noapic nolapic*
Finally press Enter to boot.

Hope it helps.

---

### Post by AmyRose on 2007-04-26
If Kobalt's idea doesn't work, try running the defect check on it.

However, this description is pretty vague. Do you mean it's skipping the CD in the boot sequence, or do you mean that you see the Ubuntu logo and it can't boot after that?

---

### Post by Hackza on 2007-04-26
I only 2 days ago prformed a dual boot of feisty with the liveCD. I guess redownload the iso  and burn it checking the md5 checksum and make sure again that it is cd boot first. Sorry I could be of more help

---

### Post by Kobalt on 2007-04-26
If you want to check the MD5SUM, here is how you can do this (from either windows or Linux) : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by jessek on 2007-04-26
I just verified the checksum, and everything is ok.  When I am logged into windows XP - I can double click on the drive with the ubuntu disk in it, and the open source software opening preview window comes up fine.  It says to reboot and Ubuntu will load up.

Problem is, no matter what I choose in the , I cannot get the ubuntu disk to load up.  I've tried just about everything to force the CDrom to boot first.  I cannot get the Ubuntu screen to load up.

grrr.....

---

### Post by Kobalt on 2007-04-26
You should describe a little further your hardware then, there must be a problem there...

---

### Post by jessek on 2007-04-26
fyi, I've tried this on multiple computers now....same result

---

### Post by kjaonline on 2007-04-26
if that's the case there must be something wrong with the cd..

---

### Post by Kobalt on 2007-04-26
At which speed did you burn the ISO file ? I advise never to burn these at more than 4x ...

---

### Post by jessek on 2007-04-26
probably faster than 4x.  Thanks for the advice - I'll try again!

---

### Post by Josey on 2007-04-26
Make sure the machine is set to boot from cd in bios and also burn the disk at 4x.  Sometimes the brand of the cdr can make a big difference too in my experience.

---

### Post by jessek on 2007-04-26
burned at 4x....still no dice....tried multiple machines...grrrr

---

### Post by jessek on 2007-04-26
I guess I'll try to download it again, but that doesnt make sense to me, since I can get the CD to run in windows just fine.  It just won't boot up for me.

---

### Post by Kobalt on 2007-04-26
What is happening ? Do you get an error message ? if so which ?
Does it even get to the first Ubuntu boot screen (where you can select to Install Ubuntu) ?

---

### Post by Drakkor on 2007-04-26
I think there needs to be a sticky in big print,on the front page entitled "Ubuntu Won't Boot" with proper instructions for finding the proper distro for your machine, downloading it, checking the md5sum of the download to make sure it's not corrupted,burning the .iso file,and booing from the CD drive !  It never fails that everyday  about 10 people have the same problem,
over and over and over and over again. Seems to me it could avoid the constant posting and reposting of the same problem :popcorn:

---

### Post by gohanssjn on 2007-04-26
Silly question for the TC, but did you tell the CD to finalize?

---

### Post by Josey on 2007-04-26
My guess here is that if you use a different brand of cdr your problem will be solved.  What program are you using to burn the .iso?

---

### Post by jessek on 2007-04-26
> **Drakkor said:**
> I think there needs to be a sticky in big print,on the front page entitled "Ubuntu Won't Boot" with proper instructions for finding the proper distro for your machine, downloading it, checking the md5sum of the download to make sure it's not corrupted,burning the .iso file,and booing from the CD drive !  It never fails that everyday  about 10 people have the same problem,
over and over and over and over again. Seems to me it could avoid the constant posting and reposting of the same problem :popcorn:

Yeah, I searched for all that, btw with no relevant returns.

I have the proper "distro" 7.04 desktop for normal windows machines, I downloaded it, checked and verified the correct md5sum, burnt the iso file correctly (I can get it to autorun in windows just fine) - and I've even disabled every other boot method except cd rom to try and get it to boot.  I've downloaded it 3 times, burnt it at 4x speed, on 3 different cdroms.  I am using imatation cdroms.

I've tried booting on 3 different machines, all within the hardware requirements with the same exact result.  I have no idea what more to do except download it from a different source, and try again...and again.

---

### Post by banditv1 on 2007-04-26
I had a problem like this with my notebook. Even thought it burnt correctly and checksums where ok, it still would not boot. After a lot of foul words I will not utter here my 9 year old son said why not try a different cdrom. When I did it booted right up. I have no answer as to why I just know it worked for me. 

I used an 16X cdrom that I had as a spare.

Let me know if it works for you too.

I just saw the part of your post that said 3 different PCs.

---

### Post by Josey on 2007-04-26
Yeah as I recommended a few times try a different brand of cdr altogether.  My cd burner cannot make a memorex cdrw bootable for the life of it.  It doesn't matter how many different memorex cd's it claims it burns successfully.

---

### Post by jerrylamos on 2007-04-26
When you say Ubuntu won't load up, does anything ever display on the screen?  If so, what?
What is the last thing on the screen?

Cheers, Jerry

---

### Post by Quickened on 2007-04-26
Or you can try burning the Fiesty Alternate. Thats what i ended up doing after having a very similar problem to yours. Now everything seems good

---

### Post by Drakkor on 2007-04-26
Hmmmmm............ burned mine on a  Memorex CDRW, and it installed just fine !  :) 
I really think the laser diodes,and possible and adjustment of them lead to many possible 
errors ! :popcorn:

---

