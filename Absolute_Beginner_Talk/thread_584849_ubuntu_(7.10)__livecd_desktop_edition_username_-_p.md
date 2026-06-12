---
title: "ubuntu (7.10)  livecd desktop edition username - password"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by rednectar on 2007-10-21
It seems many of us are searching for the default username and password for the livecd desktop edition version of Ubuntu 7.10 - SOMEONE MUST KNOW
Please do not post replies like try <enter>/<enter>  ubuntu/ubuntu ubuntuuser/ubuntuuser root/root or anything that you are not sure of - i think i've tried all the common suggestions and none work

To my way of thinking this is unacceptable that a release (beta or otherwise) goes out without a well known way of at least getting to see a desktop at least

I'd really appreciate if anyone can tell me

---

### Post by tenmillionmilesaway on 2007-10-21
The live cd boots up to the desktop by default.  Why do yo need the username and password?

---

### Post by Niniel on 2007-10-21
Because sometimes it doesn't, Mr. Smart.

I had the same problem. I think it was due to me having a [screwed-up] installation of Ubuntu on my hd, and the login manager tried to read that. 
The issue only went away after I deleted the Linux partitions, recreated them and re-installed Ubuntu. 

Rednectar, there seriously aren't any passwords for the Ubuntu live CD, unlike some other distributions. It *is* supposed to boot straight to desktop.

---

### Post by steve.horsley on 2007-10-21
I've never seen it fail to boot to the desktop, but I think the username is ubuntu and the password is blank.

---

### Post by LowSky on 2007-10-21
This is happening alot, I wonder if it has something to do with where they are downloading the Live CD from

---

### Post by abosio on 2007-10-21
I can confirm the the username is "ubuntu" and the password is blank. I had it running as LiveCD off of a USB drive, following the instructions at [pendrivelinux.com]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"). I had turned off auto-login and was actually typing in "ubuntu" and leaving the password blank to login.

It is for this reason that I got myself into other trouble. I wanted to secure my installation so I created another administrative user account for myself and logged in with that user/pass. Then I did **sudo passwd ubuntu** so I could could prevent people from logging in.

After that, I am not able to log into either of the accounts. No idea what happened.

---

### Post by kaishan on 2007-10-21
Hi.  I am encountering the same problem, except I am getting the login screen everytime I try to boot the livecd.  I've tried multiple logins, but for some reason, I can't get past the login screen.  It looks like it is going to load sometimes (I can see the Ubuntu 7.10 desktop) but then it exits back to the login screen.  Not sure why this is happening with the boot cd.

---

### Post by dbvanhorn on 2007-10-21
Using the alternate 64 bit CD here, installing on what used to be a debian system (formatted /) .
I got thru the install to the restarting of the system, but then I get a login screen where nothing works.
Tried all the obvious usernames/passwords I could think of. 
Trying a reinstall..

---

### Post by kellemes on 2007-10-21
I've heard of this before.. it seems to be a bug you may expect in beta's but not in final releases.
There are suggestions to change download-location or have ship-it send it to you since the iso may be corrupt.
Still it sucks and should not happen.

---

### Post by bapoumba on 2007-10-21
> **dbvanhorn said:**
> Using the alternate 64 bit CD here, installing on what used to be a debian system (formatted /) .
I got thru the install to the restarting of the system, but then I get a login screen where nothing works.
Tried all the obvious usernames/passwords I could think of. 
Trying a reinstall..
With the **alternate cd** the first user created during the install is **oem**. You should have been prompted for a password during the install.

Enter **sudo oem-config-prepare** in a terminal (> Accessories > Terminal). Next reboot, the definitive username will be set up (you'll get to choose one) and the oem user deleted.

---

### Post by rednectar on 2007-10-22
Update and thanks - I burned a new CD, and the problem went away - booted right onto the desktop as it was suposed to.   BUT why my first CD didn't work?  Who knows?  Why are others having the same problem? 

So once again, thanks to those who helped, but I'd still like to know if there IS a username and password that would let me get passed the login when it comes up.

---

### Post by Niniel on 2007-10-24
> **abosio said:**
> I can confirm the the username is "ubuntu" and the password is blank. I had it running as LiveCD off of a USB drive, following the instructions at [pendrivelinux.com]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"). I had turned off auto-login and was actually typing in "ubuntu" and leaving the password blank to login.


There, he confirmed it. :) 
However, I don't think that this will help if there's a problem with the CD.

Why there are so many issues with CD/Rs I don't know. I just learned that one has to be patient and try over and over again until it works. Fortunately, CD/Rs are quite cheap.

---

### Post by RichardIII on 2007-10-24
Just to add to the confusion :)

Tonight I downloaded the live CD from Ubuntu.com, burned it from within Ubuntu 7.04 FF, and... got the same problem (Username/password) and no access. Will try again on a new CD; just hope I do't have to spend the spindle to get a working one :lolflag:

---

### Post by Niniel on 2007-10-25
If you are not doing it yet, always check the the checksum after a download; I also had a few cases where they didn't match even though the download appeared to have completed successfully.

And then there are ISOs that seem particularly resistant to burning. One I could not get to work is Linux Mint; I just wanted to take a look via Live CD, but to no avail. Once I got Ubuntu installed I gave up on Mint since I didn't want to waste any more CD/Rs on something I was most probably not going to use anyway (since I like Gutsy and have invested some time now getting to know it).

---

### Post by RichardIII on 2007-10-25
What I think you should be careful with is the type (read: quality) of the CDR used. My first attempt was on an "el cheapo" CDR, and it failed completely. After reading this thread, I retried on an "A" brand CDR, and it works...perfectly!

Now to get it installed is a whole different chapter, but does not belong in this thread :)

---

### Post by ngageguy on 2007-11-04
I can confirm this bug. I downloaded the latest liveCD from here and everything was fine. I put the CD in one of my two laptops and it booted directly to the ubuntu desktop with an option to install as per normal.
I put the same CD in a different laptop and all I get to is a login screen and cannot get any further. Various attempts at different suggested logins do not work at all. I am now downloading the alternate install cd do try and make that work.

---

### Post by RichardIII on 2007-11-04
What I did notice in the whole process is that dirt, even the smallest particle of dust, can make this happen, so make sure your CD is as clean as it came from the spindle or jewel case. 

If your CD runs on one system perfectly, then the CD is fine as such; the only thing that could have happened is that fingerprints, or dust came on it. Had that happened with my 7.04 CD recently, cleaning it with a soft, non-fluffy, cloth made it work as new again!

---

### Post by Officer Dibble on 2007-11-04
> **RichardIII said:**
> What I did notice in the whole process is that dirt, even the smallest particle of dust, can make this happen, so make sure your CD is as clean as it came from the spindle or jewel case. 

If your CD runs on one system perfectly, then the CD is fine as such; the only thing that could have happened is that fingerprints, or dust came on it. Had that happened with my 7.04 CD recently, cleaning it with a soft, non-fluffy, cloth made it work as new again!

lol when I read information like this I can't help remembering a UK TV program called Tomorrows World spreading jam on a CD to demonstrate its resilience... I would not have wanted to have seen the inside of that drive afterwards... :)

---

### Post by RichardIII on 2007-11-04
> **Officer Dibble said:**
> lol when I read information like this I can't help remembering a UK TV program called Tomorrows World spreading jam on a CD to demonstrate its resilience... I would not have wanted to have seen the inside of that drive afterwards... :)

OMG! Did they show how the drive's looked inside, afterwards? I'm pretty sure they didn't. :)

(Downloading GG alternate CD now, to see if that will solve my upgrade problem, Time to make yet another image of this installation <SIGH>.)

---

### Post by Officer Dibble on 2007-11-07
> **RichardIII said:**
> OMG! Did they show how the drive's looked inside, afterwards? I'm pretty sure they didn't. :)

(Downloading GG alternate CD now, to see if that will solve my upgrade problem, Time to make yet another image of this installation <SIGH>.)

No, they didn't show the inside the drive afterwards, I was just saying that in their keenness to demonstrate this new fandangled technology they must have totaled a player - that's why I would not have wanted to have seen the inside of the drive then - it must have been one very expensive demonstration. :)

---

### Post by RichardIII on 2007-11-07
Well, at least - after the mess they made of it - the least thing they could say is that the system had a "fruity fragrance" :)

But I still would love to see the inner works of that particular drive, after the experiment of course ;)

---

