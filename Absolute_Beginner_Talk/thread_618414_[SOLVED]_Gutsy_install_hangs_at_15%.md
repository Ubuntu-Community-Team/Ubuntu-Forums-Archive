---
title: "[SOLVED] Gutsy install hangs at 15%"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Milind on 2007-11-20
I've been trying to install Ubuntu 7.10 using the Live CD. After I finish answering the questions, decide on 'Manual partition', make my selections etc., it says "Installing system" --> "Detecting file systems", the progress bar reaches 15% and then nothing further happens. The system hangs, cursor freezes, keyboard doesn't work. I have to shut the computer down by turning off the main switch! I have tried 7-8 times with exactly the same result - hangs at 15%. Any suggestions ?

---

### Post by Nikitas350 on 2007-11-20
Try using the alternate text-based installer (you can download it from [www.ubuntu.com/download](www.ubuntu.com/download))...

---

### Post by Inxsible on 2007-11-20
What speed did you burn the CD @ ? Recommended speed is 4x or less. 

Also, did you check the CD for errors and the MD5 ?

---

### Post by Milind on 2007-11-20
> **Inxsible said:**
> What speed did you burn the CD @ ? Recommended speed is 4x or less. 

Also, did you check the CD for errors and the MD5 ?

I didn't burn the CD. I ordered it from Shipit (Ubuntu site). I have two of them and have tried both after checking for errors.

---

### Post by doowgof on 2007-11-20
Your situation was quite like mine!
I ordered Debian (3xDVDs) from bluesquarelinux and tried to install it to my laptop. The booting was fine (I boot from DVD), I did the partition and started to install. However my computer said couldn't mount DVD! I then switched off my computer manually and tried several time but it didn't work. Therefore I did some research and quote here: "**Sometimes, especially with older CD-ROM drives, the installer may fail to boot from a CD-ROM. The installer may also &#8212; even after booting successfully from CD-ROM &#8212; fail to recognize the CD-ROM or return errors while reading from it during the installation**. " and "**Some older CD-ROM drives do not support reading from discs that were burned at high speeds using a modern CD writer**." and more here "**If your system boots correctly from the CD-ROM, it does not necessarily mean that Linux also supports the CD-ROM (or, more correctly, the controller that your CD-ROM drive is connected to).**"
I then tried to boot using a windows XP DVD and it wouldn't boot. I changed to a CD and it did the booting! And I used my friend's computer burnt a Ubuntu CD it worked well and Ubuntu was installed.
I learnt from above that some old (although my lapton is only about 2 years old) CD-ROM did not work well with DVDs. I suggest that you to burn a CD by yourself using a low speed and do not use DVDs!

---

### Post by kiwikat on 2007-11-20
I am having the same problem right now, just that my system isn't frozen.  Is normal that it takes a long time at 15%?  Sigh... I knew SOMETHING would go wrong lol...

---

### Post by blithen on 2007-11-20
It could be a RAM stick failure. Run memtest86+. I had the same problem. Now I'm back down to 512mb instead of 1.5gb

---

### Post by TalioGladius on 2007-11-20
Last time I had this it was a cd problem.  Burned it at like 1.5x, which took like an hour but it worked.

---

### Post by Milind on 2007-11-26
> **TalioGladius said:**
> Last time I had this it was a cd problem.  Burned it at like 1.5x, which took like an hour but it worked.

I burned a CD at 2x and tried installing with it - same result - hangs at 15%. MAybe I'll just have to wait for the next version :(

---

### Post by Kitsun on 2007-11-26
Does it freeze up or does it just sit there?

I had trouble installing it onto one pc, I let it install overnight and it finished.

---

### Post by Steeperton on 2007-11-26
I had the same problem with the AMD64 version. Installing from the alternative CD (text only) worked fine.

---

### Post by Milind on 2007-11-26
> **Kitsun said:**
> Does it freeze up or does it just sit there?

I had trouble installing it onto one pc, I let it install overnight and it finished.

It freezes.It says "Installing system" --> "Detecting file systems", the progress bar reaches 15% and then nothing further happens. The system hangs, cursor freezes, keyboard doesn't work. I have to shut the computer down by turning off the main switch. I haven't actually left it overnight yet but have waited up to 3 hours. When you let it install overnight were your mouse and keyboard being responded to ?

---

### Post by schruthensis on 2007-11-30
I have the same exact problem (haning at 15% while the cdrom drive spins away and drive access noises eliminate) I get the feeling that it is a video card issue because even though my mouse freezes too, the install appears to be happening anyway... and in fact i can even hit enter on the keyboard to get the harddrive/cdrom to start making (installation related?) noise again.  

I suppose the solution in this (my) case is to use the text based installer (I'm really doubting its a CD burn speed related issue)

---

### Post by Milind on 2008-01-13
> **schruthensis said:**
> I have the same exact problem (haning at 15% while the cdrom drive spins away and drive access noises eliminate) I get the feeling that it is a video card issue because even though my mouse freezes too, the install appears to be happening anyway... and in fact i can even hit enter on the keyboard to get the harddrive/cdrom to start making (installation related?) noise again.  

I suppose the solution in this (my) case is to use the text based installer (I'm really doubting its a CD burn speed related issue)

It worked! It took me a loooooooooooong time to download the iso ( I had to first learn about and install a Torrent client, get used to it and then download the Alternate CD. I finally finished that last night and burnt the CD at 8* and then ran the install today morning. Went like a breeze. Thanks.

---

### Post by Hyppo2007 on 2008-01-16
I have experienced the exact same problem where the installation stops when the progress bar is at 15%. I also thought that it had something to do with reading of the CD. I burned with different speeds on different computers using different CD:s but it didn't help.I also cleaned the laser optics but it didn't help. I started to think that it was some strange instruction not supported by my hardware.
It was the same with version 7.04 and 6.10. 

I finally managed to install 6.06. So now I'm doing the online updating from version to version. Not a good solution but it works!

Has someone reported this as a bug? It seems to be happening on so many different hardwares.

---

### Post by trgz on 2008-01-30
Having exactly the same prob s other even as I type (keyboard and mouse work just fine) - downloaded the 'full' iso this evening - Ubuntu 7.10 "Gutsy Gibbon" Release i386. 
It's beginning to remind me of my attempts at getting Ubuntu (FF and earlier) onto my 64MB 266Mhz laptop...

Bored now

---

### Post by trgz on 2008-01-30
Back in XP now.
Ubuntu had started to affect changes to my 'D' drive, ie it had reduced it's size as I intended (it did corrupt it partially but I've fixed that) but it appears not to have started to format the free space into any particular file system. Will try again.

Sorry to reply to my own post - some people get up tight about that. :)

---

### Post by trgz on 2008-01-30
Me again - talking to myself!

After getting into XP and tidying things up I started the installation again (with a block of freespace now prepared by my earlier attempt) and it worked fine.
I'm a happy bunny - now updating it and bracing myself for ht e8800GTS driver installation...

(p.s. I'm posting these comments for future newbies etc)

---

### Post by Chubuntip on 2008-02-08
> **TalioGladius said:**
> Last time I had this it was a cd problem.  Burned it at like 1.5x, which took like an hour but it worked.

I was wondering what burning/imaging software you used to do this because the one recommended by the install guide (infrarecorder) only goes to 4x.

---

