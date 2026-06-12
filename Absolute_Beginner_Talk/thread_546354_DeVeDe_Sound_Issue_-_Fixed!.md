---
title: "DeVeDe Sound Issue - Fixed!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by ponchuk on 2007-09-08
Hey Everyone, I got the DeVeDe sound issue in version 2.9 figured out!!

Apparently the problem isn't with DeVeDe itself - it's with mplayer and mencoder version 1.0~rc1-0ubuntu9.1.  These versions have buggy PAL and sound code and the last working version is 0.99+1.0-pre8-0ubuntu8, however this old version didn't show up in synaptic - even using the "version" tab.

I went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and searched for both mplayer and mencoder and the previous version was there.  So I went and downloaded the .deb file for each which let me install it after uninstalling the other ones in synaptic.  This forced me to uninstall DeVeDe since mplayer/mencoder are dependencies, but I was able to reinstall DeVeDe from synaptic afterwards.  The iso copied with gnome baker worked great in the dvd player.  Enjoy your dvds now.  You may want to post this as a sticky since it solves all the problems with devede in ubunto.

**Note:**  The update manager will keep bugging you to update to the buggy versions and you will have to uncheck them to keep from reinstalling them.  Apparently there was a security update to mplayer/mencoder (SECURITY UPDATE: buffer overrun in cddb code (LP: #118855)) which is probably why it was rolled out without enough testing.

---

### Post by kelvin spratt on 2007-09-08
This is very old solution but does work but the patch on the DeVeDe site is much better, You can lock the version that you are using in synaptic click on mencoder then left hand top of page click package then click on lock version.you can do that with any package.

---

### Post by ponchuk on 2007-09-09
thank you kevin spratt.

learned about the lock in the package area. no more request to update.  did not see the information i posted in the forums.  i hoped to now have simplified the method  for the ubuntu devede users.

---

### Post by pizpot on 2007-09-11
I got it solved here. Well not cured, but I have a work around. This works now in 7.10beta5 and you can install everything with sudo apt-get.

1. Use avidemux to convert and fix your file into an mpg suitable for DVD. Take your time with this step, and Preview your results before continuing. You have to make the video 720x480 for ntsc, 29.97 fps and the audio 48000 sample rate. You can also crank the sound gain if it is too quiet. When it is done play the mpg file to make sure it is widescreen not 4:3 otherwise do it over... and over... and over till you get it perfect.  OK, you first Open your avi file. Then you click auto dvd. Then click calculator and set mpg and dvd5 and hit Apply. That pretty much does it. Then go into the video and audio configs and check everything. Also look at the video filters and see they are right.
2. Use devede to convert the mpg file into an iso file
3. Use gnomebaker to write the iso to a dvd

---

### Post by pizpot on 2007-09-11
I forgot to mention that in step 2, using devede, the solution the the scratchy sound problem is to click the check box "This file is already a DVD/xCD-suitable MPEG-PS file".

That is located under Properties of the file you are adding to the DVD, Advanced Options, Misc, Special. Good luck finding it. Once you use that check, and your mpg is already correct, no more scratchy sound. Ahhh. And no installing this version or that. And you with avidemux you can preview galore and just look at the filters! I tried a de-blocking filter for cartoons and it worked great and improved the vid.

---

### Post by ponchuk on 2007-09-13
i think my solution is easier. just change the devede.  Everything is pick and do.

---

### Post by pizpot on 2007-09-13
You should see the filters in avidemux though. There are like 40. It is more complete and you can just wait for the programmers to fix the problem rather than bunking up versions of this and that program.

---

### Post by pizpot on 2007-11-28
New solution:

Uninstall devede:

sudo apt-get remove devedee

Then edit your sources file to include the backports source:

sudo gedit /etc/apt/sources.list

and uncoment this part:

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

by removing the #'s from the start of the lines.

Then reinstall devedee and a newer version without the problem will install:

sudo apt-get install devede

Then put your sources file back how it was. Yay!

---

### Post by curiousnoob on 2007-11-29
> **kelvin spratt said:**
> This is very old solution but does work but the patch on the DeVeDe site is much better, You can lock the version that you are using in synaptic click on mencoder then left hand top of page click package then click on lock version.you can do that with any package.

> **pizpot said:**
> New solution:

Uninstall devede:

sudo apt-get remove devedee

Then edit your sources file to include the backports source:

sudo gedit /etc/apt/sources.list

and uncoment this part:

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

by removing the #'s from the start of the lines.

Then reinstall devedee and a newer version without the problem will install:

sudo apt-get install devede

Then put your sources file back how it was. Yay!
I have tried both of these but I still get no sound when played on a DVD.  Any ideas on what might be the problem?

---

### Post by pizpot on 2008-01-29
The above method that I posted upgrades your mencoder. If you go to devede's site, they have a patch that you can run that will downgrade mencoder to fix the bad sound--same effect. I don't know about No Sound though. 

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

### Post by pizpot on 2008-03-04
Update ( Mar 4 2008 ) The problem has fixed itself. Installing Ubuntu 7.10 and devede now results in a version that does not have the sound problem. :-)

---

### Post by stchman on 2008-03-04
> **ponchuk said:**
> Hey Everyone, I got the DeVeDe sound issue in version 2.9 figured out!!

Apparently the problem isn't with DeVeDe itself - it's with mplayer and mencoder version 1.0~rc1-0ubuntu9.1.  These versions have buggy PAL and sound code and the last working version is 0.99+1.0-pre8-0ubuntu8, however this old version didn't show up in synaptic - even using the "version" tab.

I went to [http://packages.ubuntu.com](http://packages.ubuntu.com) and searched for both mplayer and mencoder and the previous version was there.  So I went and downloaded the .deb file for each which let me install it after uninstalling the other ones in synaptic.  This forced me to uninstall DeVeDe since mplayer/mencoder are dependencies, but I was able to reinstall DeVeDe from synaptic afterwards.  The iso copied with gnome baker worked great in the dvd player.  Enjoy your dvds now.  You may want to post this as a sticky since it solves all the problems with devede in ubunto.

**Note:**  The update manager will keep bugging you to update to the buggy versions and you will have to uncheck them to keep from reinstalling them.  Apparently there was a security update to mplayer/mencoder (SECURITY UPDATE: buffer overrun in cddb code (LP: #118855)) which is probably why it was rolled out without enough testing.

Just enable the backports in Feisty and Gutsy.  The rc2 mencoder package is already there.  Update manager will update it automatically.

---

