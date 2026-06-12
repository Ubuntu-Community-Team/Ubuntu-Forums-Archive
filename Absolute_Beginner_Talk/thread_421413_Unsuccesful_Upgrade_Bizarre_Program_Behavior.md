---
title: "Unsuccesful Upgrade Bizarre Program Behavior"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-04-24
Hello,

Recently, I used the Alternative CD upgrade route to feisty from edgy. and I tried to compete the upgrade by downloading the additional program updates with my dial up modem. The update module said that I needed an additional 287 files to complete the process. During the download my internet provider dropped the connection. I did use a few programs during this very slow over modem upgrade taking more than 12 hours for 200 meg. Perhaps, that was a mistake and corrupted part of my download.

With 87 files to download, I started noticing problems. My sticky notes do not go away when I click on the screen. None of my programs have the "x" to close the programs such as Firefox (which I am using right now) and Open Office.  Firefox only sizes to half the screen. I can not make it larger.

Open Office shows up in miniature and when I try to make it full screen, half of it does not show on the screen. The file save function blinks on and off very fast and I can not save open office files that I am producing. The menu bar (file,edit, view, history etc.) does not show up at all. However I was able to close Open Office by using alt-f and scrolling down the menu to close.

After my updating was complete and I rebooted, I noticed that I still have these problems.

How do I fix all of this? Should I rebuild by reinstalling everything? Hopefully, I will not have to download everything again.

Paul in NH

---

### Post by micfreedom on 2007-04-24
> **pmueller said:**
> Hello,

Recently, I used the Alternative CD upgrade route to feisty from edgy. and I tried to compete the upgrade by downloading the additional program updates with my dial up modem. The update module said that I needed an additional 287 files to complete the process. During the download my internet provider dropped the connection. I did use a few programs during this very slow over modem upgrade taking more than 12 hours for 200 meg. Perhaps, that was a mistake and corrupted part of my download.

 Hopefully, I will not have to download everything again.

Paul in NH


I am also new to Ubuntu, but with a fast connection.
I think it might be best if you went to Amazon and bought a copy of "Ubuntu for Non-Geeks, 2nd Edition: A Pain-Free, Project-Based, Get-Things-Done Guidebook (Paperback)" (This is the next edition with Ubuntu 7.04 Feisty Fawn CD in it, the latest Ubuntu released on June 15 07, the first edition has an earlier CD program) 
I think for dial-modem it might be more interesting to have your hard copy to be able to install it at leisure off line, so the download problem and missing files does not occur. 
I am buying the disk that goes with this book. On top of this you have also the explanations in black and white that you can refer to. Then, if you still have  problems, this forum is always here.
I am also buying a back-up device called an external hard disk drive, so I can put up my work and all the programs from Windows on it to be on the safe side. You may not want to buy an external disk drive, but you should consider how to back up your files/work to have them intact in some place, so you can always copy a program that may have been corrupted in the transfer of files.

Hope this help :KS

---

### Post by pmueller on 2007-04-24
Hello,

I have been using Ubuntu since about a year ago and all of the problems seem very novel, such as a system breakdown when I tried to install vmware about a year ago and lingering video problem where my refresh rate is incorrect for just a few seconds during boot up making my monitor constantly report this back to me during bootup. The community has helped me fix most of my troubles and help me understand a few things that I was mistaken about.

I do have a cd disk for the alternative upgrade install of fiesty. I used the mdsum (sp?) command and it checked out OK. I believe that perhaps I could just try to reinstall from my CD. Would that fix my problems? Would it erase all of the files that I have downloaded?  All of these downloaded files are basically the latest version of programs that are not installed by the default CD.

I wouldn't mind buying a comprehensive book, but it will take a few days at least to get it.
Thanks,
Paul

---

### Post by pmueller on 2007-04-24
Are there any ideas. I've tried sudo "apt-get install ubuntu-desktop" and "sudo aptitude install ubuntu-desktop". One command found only a few obsolete files and libraries and uninstalled them. Both commands later said that everything was up to date and that there were no dependency issues.

I also used my install CD, but it just said that everything was already up to date. How do I uninstall and reinstall without loosing all of those updates?

Paul

---

### Post by pmueller on 2007-04-25
Hello,

From doing a search and reading many different posts  I found the answer to my problems. I had to go up to System, Preferences, and Desktop Effects and check Enable Desktop effects. Oddly this made my problems go away. Since I did not like the window wobble and suspected that adding effects would subtract RAM available, I later decided to disable desktop effects. So far I have had no return of oddly performing programs.

It must be a bug in Feisty or the programs involved with these effects. I am using a Saphire ATI 9600SE Radeon with no special ATI or open source drivers downloaded expressly for my video card.

Since my problems started in the middle of a download I always assumed that it must have been one the updated files. Other people seem to be having trouble with the desktop effects.

Paul

---

