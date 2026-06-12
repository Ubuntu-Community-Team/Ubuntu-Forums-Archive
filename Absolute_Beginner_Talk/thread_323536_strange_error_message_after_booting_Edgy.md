---
title: "strange error message after booting Edgy"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by atarileaf on 2006-12-22
I just finished installing 6.10 and rebooted for the first time. I get this message (as I have before with the 64 bit edition):

/bin/sh; can't access tty; job control turned off

But thats not the error message I'm referring to but if anyone knows what this is PLEASE let me know.

No, the error message that I got this time was this:

kill: could not kill pid '1855': No such process

I had to reboot since it locked up or froze at that point and it boot normally (well, except for that blasted tty error! ](*,)  )

Anyone know what this kill pid thing is?

---

### Post by atarileaf on 2006-12-22
Nobody knows the trouble I've seen?

I guess I have the most unique problems a Ubuntu user has ever had the misfortune of experiencing. ](*,) ](*,) ](*,) 

These two error messages are driving me nuts. Especially this stupid Kill Pid thing. What the heck does that mean? How can I fix or get rid of it?

I'm using the regular 6.10 Ubuntu and here are my system specs:

Asus K8V-X motherboard
Athlon 64 2800+ (1.8Ghz)
Ati AIW 9800 Pro
80 gig WD HD (IDE)
512MB ram

When I first started using LiveCD I got the blank screen that I've read many people have had which prevents them from getting into the livecd or the installer so I used the following commands I found on these forums to load a vesa driver temporarily

chroot /root nano /etc/X11/xorg.conf

Then I switch "ATI" to "vesa" and I can get into and install Ubuntu.

I get these error messages after the first boot after install and the tty one after EVERY boot. I can type "exit" and it will boot normally. After this particular install, I randomly get:

kill: could not kill pid '1855' :No such process.

The number 1855 is always the same and on this error, the system locks up and I have to do a hard restart. Sometimes it works, sometimes not but its getting to the point now that Ubuntu is becoming useless to me unless I can get some help on diagnosing and fixing this problem

PLEASE HELP!!!!! ](*,) ](*,) ](*,)

---

### Post by Russty of Oz on 2006-12-23
> **atarileaf said:**
> 

/bin/sh; can't access tty; job control turned off



I am trying to install Ubuntu on my computer and I too get this message after it says it is loading.  I don't get to the install process at all.

Is there any way around this?

Russty

---

### Post by LameBMX on 2006-12-23
okay ... it will help a lot of people looking at this (not me im a n00b too)
when the bootloader comes up ... hit F6 for options .. and delete the last two options
quiet splash -- 
^ i believe thats it ... if it freezes then take a digital picture
if it dont freeze and is happening at the same spot .. hit the pause break key just before it happens
if you play with pause break and print scrn you can actually make the boot process step until you are just before.
where its at when it errors out will be a big help to those that know what they are doing

and just a thought ... let the timer go for it to auto select ... back when i played with gentoo the system needed that time .. if i picked gentoo real fast it would always die .... but if i let it go on its own it normally worked

---

### Post by Russty of Oz on 2006-12-24
HEY IT WORKED! :D 

Neat trick ;) 

MERRY CHRISTMAS EVERYONE!

---

