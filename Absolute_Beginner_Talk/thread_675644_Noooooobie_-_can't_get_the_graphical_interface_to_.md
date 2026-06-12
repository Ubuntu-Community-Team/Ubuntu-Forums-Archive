---
title: "Noooooobie - can't get the graphical interface to load"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by jetjock on 2008-01-22
I have done everything I can read to get Ubuntu loaded om my machine.

It's home built, but with Ok parts.
Abit SA-7 Motherboard with Intel Pentium 4 2.4 GHz and 1 GB RAM
40GB Maxtor Drive
An older Plextor CR-R/RW - PX - W1210TA

Everyhting seems to load OK.  I get the initial Ubuntu screen, and install it to the hard drive.  It finishes and tells me to remove the CD and reboot.  When I do, I end up with a command line prompt to login.  After I do, it leaves me at the command prompt.  I'm too much of a newbie to know what to do at that point.

I've tried cehcking the memory and the CD.  Everything says it is fine.

I read in another post to try "startx", but that just gives me an error, not found.

I would really like to get this machine working.  I've spent two days working on it.

Thanks in advance for any help.

---

### Post by jesusfreak107 on 2008-01-22
whoa, *command prompt to log in* ???!!!  Either you are using a *really* old version of Ubuntu that I have never heard of, or something is *really* not right.  Ubuntu's login manager looks cool and flashy, and very graphical.  try "sudo apt-get install gnome" you might just not have installed the graphical enviroment.  are you using Ubuntu 7.10 Gutsy Gibbon? if not, download and burn it to a CD, and use it to install Ubuntu. and, yeah, it'll ask you to download and install a ton of other stuff. you want that, too.

---

### Post by tojge on 2008-01-22
You've installed using Desktop/Live CD, right?

---

### Post by bswilson on 2008-01-22
> **jetjock said:**
> I read in another post to try "startx", but that just gives me an error, not found.

Can you be a bit more specific about the error message you're seeing when you run **startx**?

---

### Post by crjackson on 2008-01-22
> **jetjock said:**
> I have done everything I can read to get Ubuntu loaded om my machine.

It's home built, but with Ok parts.
Abit SA-7 Motherboard with Intel Pentium 4 2.4 GHz and 1 GB RAM
40GB Maxtor Drive
An older Plextor CR-R/RW - PX - W1210TA

Everyhting seems to load OK.  I get the initial Ubuntu screen, and install it to the hard drive.  It finishes and tells me to remove the CD and reboot.  When I do, I end up with a command line prompt to login.  After I do, it leaves me at the command prompt.  I'm too much of a newbie to know what to do at that point.

I've tried cehcking the memory and the CD.  Everything says it is fine.

I read in another post to try "startx", but that just gives me an error, not found.

I would really like to get this machine working.  I've spent two days working on it.

Thanks in advance for any help.

What version of ubuntu are you using? And is it the server or desktop flavor?

---

### Post by jetjock on 2008-01-23
Thanks for your replies!

I downloaded 7.10 Gutsy Gibbon, checked the MD5Sum, and used InfraRecorder to make the CD as instructed.

I never get the "Live CD" as indicated on the website.  Although I downloaded Ubuntu from the website, my Boot CD doesn't say the same thing as indicated on the website.  Instead of "Start or Install" as the first line, my Boot screen says "Install to the hard disk."  Is there a chance that my mirror site wasn't updated to 7.10?  Maybe this is why I am sooooo confused.

I'm not a computer idiot, but not a genius.  Started in DOS and have been on Gatedows or Mac since.  I really want to make this work.

Thanks for any help.

---

### Post by jetjock on 2008-01-23
Small bright spot--the "sudo apt-get install gnome" has it loading a ton of stuff.  Maybe that will get me started.

Thanks

---

### Post by Ptero-4 on 2008-01-23
Looks like you downloaded the server one (or the alternate one maybe).
Ensure that you download the one that says "desktop" in it.

---

### Post by jetjock on 2008-01-23
Oh--forgot to mention, I started trying to load the Server version, but have backed up to the desktop version now.

During the comments after the apt-get command, it had 7.10 in one of the comment lines.

Fingers crossed.

---

### Post by GavinZac on 2008-01-23
did you happen to install using the Server cd?

edit: It appears you did. The server edition doesn't come with a graphical interface as its designed for "headless" (no monitor, external access) machines

---

### Post by jetjock on 2008-01-23
I have both versions burned to CD.  It is possible that I goofed and burned the server version both times.  Is there a way I can tell looking at the CDs or do I need to reburn the CD to be sure?

Thanks

---

### Post by jetjock on 2008-01-23
I think I fumbled when picking the file to burn to CD.  Re-burning.  Thanks for the help.

I'll see how it goes.
TAB

---

### Post by jetjock on 2008-01-23
Yep, I screwed the pooch--mistakenly burned the server version twice.  All seems to be working now.  Thanks for getting my head straight.

---

### Post by bswilson on 2008-03-13
> **jetjock said:**
> Yep, I screwed the pooch--mistakenly burned the server version twice.  All seems to be working now.  Thanks for getting my head straight.

I'm glad that the community could help!  I think you'll be happier with the Desktop version for general computing purposes.  Enjoy!

---

