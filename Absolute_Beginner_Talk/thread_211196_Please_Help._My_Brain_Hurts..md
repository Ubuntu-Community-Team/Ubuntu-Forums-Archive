---
title: "Please Help. My Brain Hurts."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by klcm0102 on 2006-07-07
I've successfully installed Ubuntu.  I'm a total NOOB and I have read many, many threads on ndiswrapper and I HONESTLY don't understand a word of it.  When I read, ""Use the cd command to- blah, blah, blah..." I seriously have no idea what that means.  I figured out where TERMINAL is, now I don't understand what to type in there.
I have downloaded many, many things including ndiswrapper and my drivers, I have no idea where they all are or how to make them work.
Poking around I have discovered that I have a BCM4306 802.11 b/g wireless LAN.  Device Manager sees it.  Unfortunately, none of the little green lights sticking out of it (PCMCIA) are on and it obviously isn't liking Linux thus far.
I SOOOOOOO badly want rid of Windows XP, but unless one of you MUCH SMARTER THAN I is willing to help out, I may never get it.
Yeah, right now I'm on my desktop, on WinXP, just wishing I could get back on my laptop(wirelessly) and join you all on the other side!
PLEASE HELP!
Seriously, I need step-by-step instructions here.  I have (wired) internet access on the laptop, so if you can gear instructions for me I do have at least that.
TIA.  I'm losing that 'rush' I felt when I first ran my new Ubuntu OS!  Help me find my way....

---

### Post by benuski on 2006-07-07
Have you tried using the wiki entry about how to set up the broadcom driver?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Hope this helps, and if not, come on back  and we`ll try to help you more

---

### Post by benuski on 2006-07-07
> **benuski said:**
> Have you tried using the wiki entry about how to set up the broadcom driver?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Hope this helps, and if not, come on back  and we`ll try to help you more

And I'm fairly sure that you want to go to the 6.06 dapper page, and ignore the whole part about ndiswrapper for now, and try to use the native driver

---

### Post by klcm0102 on 2006-07-07
OK, I know I've been here before...after a WHILE THEY ALL START TO LOOK THE SAME.
i GOT AS FAR AS "1.2.2.1. Extract it Yourself"
I followed the download link & downloaded.
I entered the first command and got:

user@ubuntu-laptop:~$ sudo apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bcm43xx-fwcutter
user@ubuntu-laptop:~$ zless /usr/share/doc/bcm43xx-fwcutter/README.gz
gzip: /usr/share/doc/bcm43xx-fwcutter/README.gz: No such file or directory
/usr/share/doc/bcm43xx-fwcutter/README.gz: No such file or directory
user@ubuntu-laptop:~$
user@ubuntu-laptop:~$

Might as well be Japanese.  Oh, this is depressing!  I'm not sure if being stubborn enough to keep trying is a good trait or not, but I really do want this!

---

### Post by shanlon on 2006-07-08
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)


Goto that link and just copy and paste what it says to do.
That should do the trick.
After you sudo apt-get update

Try to install the drivers again.

---

### Post by klcm0102 on 2006-07-08
Tired that, my terminal gives me the exact same thing.  Phooey.  I know I'm missing something here.

---

### Post by adwait on 2006-07-08
Can you post the ouput of
```
cat /etc/apt/sources.list
```

---

### Post by klcm0102 on 2006-07-08
sue@ubuntu-laptop:~$ cat /etc/apt/sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe mu ltiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

sue@ubuntu-laptop:~$

---

### Post by PriceChild on 2006-07-08
May be silly... but you have checked it isn't already installed in "System>Administration>Networking"?

---

### Post by klcm0102 on 2006-07-08
Network Settings shows me a Wireless Connection (The interface eth1 is active) and an Ethernet Connection (THe interface eth0 is active) and an inactive modem connection. (I'm not even attempting to takle that yet!)
I have tried double-clicking the little network icon in the upper right tray to 'connect,' it spins for a few minutes yet nothing actually happens. 
_The green POWER and LINK lights on my PCMCIA wireless cards are still not on._

---

### Post by Dr. Nick on 2006-07-08
I dont have a broadcom, but running this command from a terminal

**sudo apt-get install bcm43xx-fwcutter**

proceeds to download, have you run 

**sudo apt-get update** from a terminal before trying?

---

### Post by DarkOx on 2006-07-08
I got my broadcom wireless card working using ndiswrapper. A pretty detailed explaination of what I did can be found in this thread: [http://ubuntuforums.org/showthread.php?t=198521](http://ubuntuforums.org/showthread.php?t=198521). The only thing you'd have to change for your setup is you'd have to type:

> sudo gedit /etc/modprobe.d/blacklist

in a terminal and add "blacklist bcm43xx" to the bottom of the file. Save and exit, and your card should be working.

---

### Post by klcm0102 on 2006-07-08
Ok, something happened- I think its downloaded.  Now I have to figure out how to find the actual driver I suppose?  
I have the original driver cd, it includes autorun.inf, udfrchk.exe, and udfrinst.zl (all of which don't actually do anything if I just double click them.)
Now what?

---

### Post by DarkOx on 2006-07-08
Move the udfrchk.exe file somewhere convenient, such as your desktop. You should be able to just drag and drop. Then, from a terminal, type:

> cd /home/username/Desktop

replacing "username" with whatever yours is.

then type: 

> unzip udfrchk.exe

A whole bunch of files should now appear on your desktop. You're looking for one that ends in .inf and one with the same name that ends in .sys
If they exist, then the rest of the ndiswrapper instructions should work fine.

---

### Post by klcm0102 on 2006-07-08
OK, this is what I got:
Archive:  udfrchk.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of udfrchk.exe or
        udfrchk.exe.zip, and cannot find udfrchk.exe.ZIP, period.

---

### Post by klcm0102 on 2006-07-08
Okay, now what to do woth this:

sudo bcm43xx-fwcutter -w /lib/firmware <downloaded file>

What exactly goes in the <downloaded file> area?  The file name or location?  It's downloaded to the desktop, just waiting for someone with some linux sense to know what to do next!!!

---

### Post by klcm0102 on 2006-07-08
OH MY GOSH I DID IT!!
I have no idea how, to be honest.
I really got lucky & figured out the answer to the last question by MYSELF!
Wow.  Who knew. (Certainly not me!)
Thanks to ALL OF YOU for helping me through my very first linux nightmare.  I'm sure it won't be my last!

---

### Post by matthew on 2006-07-08
> **klcm0102 said:**
> OH MY GOSH I DID IT!!
I have no idea how, to be honest.
I really got lucky & figured out the answer to the last question by MYSELF!
Wow.  Who knew. (Certainly not me!)
Thanks to ALL OF YOU for helping me through my very first linux nightmare.  I'm sure it won't be my last!Congratulations! Isn't that a great feeling?

---

### Post by shanlon on 2006-07-08
> **klcm0102 said:**
> OH MY GOSH I DID IT!!
I have no idea how, to be honest.
I really got lucky & figured out the answer to the last question by MYSELF!
Wow.  Who knew. (Certainly not me!)
Thanks to ALL OF YOU for helping me through my very first linux nightmare.  I'm sure it won't be my last!


:) YAY

Forums and irc are always great help

---

### Post by klcm0102 on 2006-07-08
> **matthew said:**
> Congratulations! Isn't that a great feeling?

YESSSSSSSSSS!!! :)
Now I feel as if I've earned my one little bean! :KS

---

