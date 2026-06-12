---
title: "New to Linux... anything"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by ffluff on 2007-12-17
I was curious about the new EEE PC using Ubuntu so I wanted to try Ubuntu on an old computer. 

P4   1.6Ghz  512M ram 12 Gig HD CD-RW

All hardware has been tested and working properly. I set bios making the CD as the first boot.

Put in a CD-RW burned using Power iso on my Windows PC. "ubuntu-7.10-desktop-i386.iso"

The black screen with the Ubuntu menu appears I choose the first to install, The CD spins and a popup shows 

Starting...
Loading Linux kernel
|]]]]]]]]]]]]]]]]]___| 71%

It hangs for a while then I get a popup over it saying:

I/O error 
Error reading boot CD
<button>[  Reboot Disk ]

Top left shows a hex number: 204200EF

Then I downloaded another copy from another location same file name and put it on another CR-RW disk "ubuntu-7.10-desktop-i386.iso"

That version, clicking on any of the options only causes the CD to spin faster but nothing happens. 

Is that the end of my Linux Ubuntu Jounrey? 
Unless someone can suggest something for me to try.
If someone can I appreciate it very much.

---

### Post by JillSwift on 2007-12-17
Burn the disk at 4x or slower (if you can and have the patience, 1x). Faster burns are asking for read troubles - especially in older CD-ROM drives.

---

### Post by HermanAB on 2007-12-17
Two things:
1. Burn the CD at the lowest possible speed.  4x seems to work OKish with old CD drives.
2. Test the CD before trying to install with it - calculate the MD5 sum.

If it still won't boot, get a different CD drive.  They are a dime a dozen.

Cheers,

Herman

---

### Post by Frunkis on 2007-12-17
I can't personally get Nero to burn any slower than 12X, any ideas?

---

### Post by alienexplorers on 2007-12-17
There is a free CD burner program that I use under windows called Deep Burner.  I have never had a problem using it and it burns great at 4x or slower.

---

### Post by mdsmedia on 2007-12-17
[http://ubuntuforums.org/showthread.php?t=583007]("http://ubuntuforums.org/showthread.php?t=583007") 

has some great tips.

One suggestion from that thread: (7) Use a CD-R rather than CD-RW to avoid problems caused by using CD-RW disks

---

### Post by Ex-windows on 2007-12-17
> **Frunkis said:**
> I can't personally get Nero to burn any slower than 12X, any ideas?
Try Infra recorder I just used it today to burn a Fiesty Fawn iso
[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)
or
[http://www.download.com/Infra-Recorder/3000-2646_4-10698815.html](http://www.download.com/Infra-Recorder/3000-2646_4-10698815.html)
also you could use this page for help
[http://www.psychocats.net/ubuntu/iso#notes](http://www.psychocats.net/ubuntu/iso#notes) 
Good luck

---

### Post by ffluff on 2007-12-18
Burning on  a CD-R instead of CD-RW did the trick.

Thanks! :)

Learned how to change the refresh rate here:

[http://ubuntuforums.org/showthread.php?t=63486](http://ubuntuforums.org/showthread.php?t=63486)

Good thing I was able to make out enough detail to see what I was doing.

Next thing I wish to learn,
Is there a setting where I can choose to start without a password prompt?

---

### Post by hyper_ch on 2007-12-18
Also make a md5 check after downloading the iso (or use torrent) and you can also, upon the cd boot screen, perform a cd check ;)

---

### Post by SunnyRabbiera on 2007-12-18
> **ffluff said:**
> Burning on  a CD-R instead of CD-RW did the trick.

Thanks! :)

Learned how to change the refresh rate here:

[http://ubuntuforums.org/showthread.php?t=63486](http://ubuntuforums.org/showthread.php?t=63486)

Good thing I was able to make out enough detail to see what I was doing.

Next thing I wish to learn,
Is there a setting where I can choose to start without a password prompt?

well disabling the password is a bad idea, remember the password is there TO PROTECT YOU.
Its one of the reasons why windows is so insecure, it allows just anyone to use your computer...

---

### Post by meindian523 on 2007-12-18
Automatic Login:

System>>Administration>>Login Window

Tab:Security

---

### Post by SunnyRabbiera on 2007-12-18
Yeh but still its not a wise move to make autologins... I dont care if they are used to the windows way or not as the windows way is flawed by default by thinking that its so darned invincible that no password is needed and yet its a malware magnet.

---

### Post by skroops on 2007-12-18
To start without a password prompt there is a menu at administration>users.  Go to the security tab and you should see it there.

---

### Post by meindian523 on 2007-12-18
> **SunnyRabbiera said:**
> Yeh but still its not a wise move to make autologins... I dont care if they are used to the windows way or not as the windows way is flawed by default by thinking that its so darned invincible that no password is needed and yet its a malware magnet.

True,but it's ok if you are the only user at the PC on Linux,like me.....and I +1 SunnyRabbiera,though the facility exists,it's highly "NOT RECOMMENDED FOR USE"

@skroops

Not Administration>>Users,it's Administration>>Login Window

---

### Post by hyper_ch on 2007-12-18
and if you have fully encrypted your system you don't need user login anymore. Without entering passwords first you can't access anything anyway ;)

---

### Post by Ex-windows on 2007-12-18
> **hyper_ch said:**
> and if you have fully encrypted your system you don't need user login anymore. Without entering passwords first you can't access anything anyway ;)

How would one fully encrypt your system????

---

### Post by hyper_ch on 2007-12-18
Most easily? Fresh install from the alternate install cd.

---

### Post by stchman on 2007-12-18
Yes, use inrfarecorder or cdburnerxp.

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/) (works with Vista)

[http://cdburnerxp.se/](http://cdburnerxp.se/) (no Vista support)

---

### Post by ffluff on 2007-12-19
> 
well disabling the password is a bad idea, remember the password is there TO PROTECT YOU.
Its one of the reasons why windows is so insecure, it allows just anyone to use your computer...


I just need protection from virtual intruders. 

Thanks all for your help and support.
:)

---

