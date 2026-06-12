---
title: "Live Ubuntu CD wont boot"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-03-11
Ok, I copied the 6.10 download after extracting it to a floppy (three floppies, actually).  One floppy must have not copied because, although the disc shows up on my machine as a data disc that is closed, when I explore to it in XP, there are no files shown.

Disc two had the files, and I can cold boot to it.  That takes me to a command line for Caldera DOS (interesting, haven't seen that in a long time).

Disc three will auto start from an open session of XP and I can read about how all I need to do is to cold boot with the disc in my CD drive.

However, when I do that, I can see my bios stating that it is booting from the CD, but, then, the machine proceeds to boot into XP again.

What am I doing wrong?

Thanks.

Caruso

---

### Post by overdrank on 2007-03-11
> **carusoswi said:**
> Ok, I copied the 6.10 download after extracting it to a floppy (three floppies, actually).  One floppy must have not copied because, although the disc shows up on my machine as a data disc that is closed, when I explore to it in XP, there are no files shown.

Disc two had the files, and I can cold boot to it.  That takes me to a command line for Caldera DOS (interesting, haven't seen that in a long time).

Disc three will auto start from an open session of XP and I can read about how all I need to do is to cold boot with the disc in my CD drive.

However, when I do that, I can see my bios stating that it is booting from the CD, but, then, the machine proceeds to boot into XP again.

What am I doing wrong?

Thanks.

Caruso

HI, May I ask why you are using floppies for the install?

---

### Post by dptxp on 2007-03-11
You copied the iso to 3 floppies, and the machine does not boot from CD !!!
You have to burn the iso to a CD (use Infra-Recorder, it is free, not NERO),
put the CD in CD drive, and power up.:guitar:

---

### Post by Kateikyoushi on 2007-03-11
I do not really understand what did you do, why do you need the floppies. Take a look at this guide how to download and burn the ubuntu cds, you can find installation help as well on the site. [LINK]("http://www.psychocats.net/ubuntu/iso")

---

### Post by carusoswi on 2007-03-11
Sorry, my age must be catching up with me or I am gradually losing the ability to hide it!
What i meant to say is that I have made three attempts to create the Live Ubuntu CD.  CD#1 turned out blank.  CD#2 seems to have all the files, but, when I cold boot with that disc in the drive, I end up at the Caldera Dos command line.

CD#3 will auto start and take me to a lovely screen that offers a link to download Firefox and a couple other ubuntu applications.  That screen explains that the CD is a Live Ubuntu CD, and that, all I need do to watch a non-destructive demo is to boot with that CD in the drive.

But, although my system appears to recognize that a bootable cd is in the drive, it continues past the CD and loads XP again.

I have checked my bios - even reset boot priorty to include CD, CD, CD.

So, I must be doing something wrong (besides typing misleading, inaccurate posts . . . sorry for the confusion).

Caruso

---

### Post by carusoswi on 2007-03-11
Trying another CD Burn.  Tried to follow those directions in the link.  I guess I'm confused about the iso image.  I downloaded ubuntu 6.10 and, in previous attempts, had just used winrar to unzip the file, then, copied the contents into the lower pane of the cd burner and instructed the burner to write the disc as a bootable iso level 1.

This time, I had the burner create an image and checked it with the checker (can never remember the name, only that it includes the number "5").

We'll see what happens.

Thanks for your help.

Caruso

---

### Post by Kateikyoushi on 2007-03-11
That was the problem, it could not boot because it wasn't burned as image file but data disc. Going to work this time if your burned not faster than 4X.

---

### Post by carusoswi on 2007-03-11
Didn't work.  Booted me into Caldera dos.
When I burn my ISO image, it shows up with a file association tied to WinRar.  I don't know if that makes a difference or not.  The CD burning ap recognized the file as an ISO.  I wonder what I'm doing wrong.  I am really not computer illiterate at all, but sometimes I am just so "pre-enlightened" that I cannot see the forest because my vision is blocked by a single tree.

When I downloaded the program (version 6.10) that's all I should have to download, right?  In addition, I downloaded the burner ap (although I own Steinberg's Wavelab that I believe would also burn an ISO), and the md5 program as well.

I was hoping to install this OS and play with it some today.  

Any further suggestions would be appreciated.

Caruso

---

### Post by overdrank on 2007-03-11
> **carusoswi said:**
> Didn't work.  Booted me into Caldera dos.
When I burn my ISO image, it shows up with a file association tied to WinRar.  I don't know if that makes a difference or not.  The CD burning ap recognized the file as an ISO.  I wonder what I'm doing wrong.  I am really not computer illiterate at all, but sometimes I am just so "pre-enlightened" that I cannot see the forest because my vision is blocked by a single tree.

When I downloaded the program (version 6.10) that's all I should have to download, right?  In addition, I downloaded the burner ap (although I own Steinberg's Wavelab that I believe would also burn an ISO), and the md5 program as well.

I was hoping to install this OS and play with it some today.  

Any further suggestions would be appreciated.

Caruso

Hi agian, Have you tried following the burn instruction,
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
and burn the cd at the slowest possible speed and see if that works. Good luck!

---

### Post by carusoswi on 2007-03-11
Well, I used the CDBurnerXP Pro3 application, but, in reviewing those instructions, didin't see anything that jumped out at me as the source of my problems.  I have deleted the folder containing my extracted ubunta files, have extracted them again and am trying to start over from scratch.  

I have an ample supply of CDs, and my paper shredder handles the duds just fine.  I will prevail here (I think).

Thanks for the reply.

Caruso

---

### Post by carusoswi on 2007-03-11
Ok.  This CD boots into Caldera DOS.  I can explore from the command line.  If I type in the name of the only .exe file available, a screen boots up that appears to be the partitioning utility, but, I do not want to use it because it is in German - don't want to accidentally mess up my system.

Why is this in German?  I downloaded from one of the US sources.

Arg!

Caruso

---

### Post by gorkur on 2007-03-11
Hmm..

This sounds kinda like the problem I had when I was starting out with Knoppix.

Do **not** extract the ISO prior to burning.

I'm not familiar with your burning software so these instructions show how to do this in NERO. You can download a 30 day trial version on their official site.

1. Put empty CD in your burner

2. Start up NERO

3. Instead of selecting the type of CD you want to burn in the left hand selections bar click on the "Open" button in the bottom right corner and select your Ubuntu ISO there.

4. Click "Burn", have a coffee and a smoke if you're into that and wait until NERO has done it's thing. :popcorn: 

5. After burning has finished you might want to check the CD. The ISO should have extracted itself onto it.

6. Boot from CD and enjoy all the sweetness of Ubuntu :guitar:

---

### Post by carusoswi on 2007-03-11
Do I extract the Ubuntu archive after I download it, or are you saying that I should create an ISO disc from the archive, itself?
Caruso

---

### Post by Kateikyoushi on 2007-03-11
Do not do anything to the downloaded file, that is not an archive, burn it as you downloaded, no extraction.

---

### Post by carusoswi on 2007-03-11
That could have been my problem.  I am burning another CD, now.  I don't know if this will be a problem as well, but, I use the CD program to create an ISO image before burning.  We'll see what happens.  If this doesn't work, I will go back to the originally downloaded file and just tell the burner to burn it as an ISO and see if that works.  That is what you are suggesting, right?

Thanks for your help.

Maybe this is a case of me "knowing" too much and imposing assumptions that caused my own problem.

Caruso

---

### Post by carusoswi on 2007-03-11
Giving up on version 6.10.  Nothing I try works.  I don't think I'm doing anything wrong at this point.  The results seem to be the same, whether I extract the file and create an ISO image using all the files or whether I just take the unextracted file and create an ISO image from that . . . well, maybe I should not create an ISO file, just burn as an ISO, I don't know.

Everyone who has responded has tried to be helpful, and I do appreciate that.

I am going to download the "supported" version.  Maybe I'll have better luck with it.

Oh, and one more issue that no one has really addressed - why is it that the partitioning ap keeps coming up in its German form?  I downloaded the 6.10 version twice from different USA locations - still the menus and instructions are in German.

Caruso

---

### Post by Kateikyoushi on 2007-03-11
Do not create an iso file, just burn it as it was downloaded, burn as image select the file.

---

### Post by carusoswi on 2007-03-11
Well, I downloaded the 6.06 version and am presently burning it to disc at a very slow speed.  I went back through the tutorial that explains the step by step procedure.  One thing I did not understand . . . I am supposed to paste the nd5 text into a notepad document, save it with the ISO file name, then, right click and verify.

When I do that, it states that one or more characters contain ascii or something like that - but, basically, I am thinking that if I accomplished a clean download, then, things should work.

. . . and, while I assume that the boot I'm getting from those coasters that will boot at all is not correct, I still have not had anyone address the reason why the partitioning instructions/menus are in German.  Would that offer some clue as to why I am having a problem, or is that something that is unique to the 6.10 version?

I will find out if I get the same problem with the 6.06 version shortly (burn is at 60% now).

Thanks again for your response.

Caruso

---

### Post by carusoswi on 2007-03-11
Well, I managed to install ubuntu, but I lost my C Windows drive.  The ubuntu install crashed half way through, and, when my machine rebooted, there was no operating system.  WinXP would not repair itself, so I decided to reinstall XP from scratch.  That seemed to go around in circles until I got tired of fussing with it, so I installed ubuntu from the now thrice formatted C drive.  Ubuntu installed without a problem this time.  Now, I need to figure out how to get some form of XP running again so that I can work with some of my essential XP only applications.

Ubuntu looks fine on first blush.

Will be interesting to see how much I can do with it.  Some of my Aps, I am certain, will simply not work with it - Steinberg's Wavelab, Sony's Vegas, MS ACCESS to name a few.  If I can find aps that will do instead, I will happily leave XP.

I am certainly never moving to Vista - that is not going to happen.

Thanks for your help, everyone.

Caruso

---

