---
title: ":[ Ubuntu Wireless :["
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by turntabletux on 2006-07-27
Hey guys,

I've been on Suse for a while now. I pretty much know it inside and out. I never used Ubuntu before so I wanna give it a shot. The most important thing to me to even start troubleshooting problems is ofcourse the internet. I always had problems with my wireless, until I started using ndiswrapper. I can get my internet up within 2min with ndiswrapper. 

I finally got ndiswrapper to install, by actually plugging my laptop in to a cord. The only problem is this weird error:

Installing bcmwl5
Unable to create directory /etc/ndiswrapper/bcmwl5.Make sure you are running as root


Every time I type the "SU" command and enter my password I get this:

turntabletux@tux-laptop:~$ su
Password:
su: Authentication failure
Sorry.


I have no clue what is going on. I know obviusly there is something to do with my password. Possibly if I get passed that I can just keep on going. Any help would be greatly appreciated! Thanks guys.
-ant

---

### Post by jimmygoon on 2006-07-27
> **turntabletux said:**
> Hey guys,

I've been on Suse for a while now. I pretty much know it inside and out. I never used Ubuntu before so I wanna give it a shot. The most important thing to me to even start troubleshooting problems is ofcourse the internet. I always had problems with my wireless, until I started using ndiswrapper. I can get my internet up within 2min with ndiswrapper. 

I finally got ndiswrapper to install, by actually plugging my laptop in to a cord. The only problem is this weird error:

Installing bcmwl5
Unable to create directory /etc/ndiswrapper/bcmwl5.Make sure you are running as root


Every time I type the "SU" command and enter my password I get this:

turntabletux@tux-laptop:~$ su
Password:
su: Authentication failure
Sorry.


I have no clue what is going on. I know obviusly there is something to do with my password. Possibly if I get passed that I can just keep on going. Any help would be greatly appreciated! Thanks guys.
-ant
not to be a nazi but use the search, someone can explain this much better than myself

for security purposes there is no root account in ubuntu, rather it uses sudo... for "superuser do" so try you command:

sudo super_user_must_do_this/command.py

or whatever and type your password and see if it works for you ;)

---

### Post by mdecler2 on 2006-07-27
Hey, su doesn't work in Ubuntu because the root account is disabled.
Use 'sudo' before a command, like synaptic package manager 'apt-get'.

For instance, if you are installing bcmwl5 (I don't know what that is) from source, you would use [code]sudo make install[code] after the appropriate configure, and make commands. The configure and make commands themselves should not require sudo.

I suggest you look at the forum by searching for 'sudo vs. su' or a similar query.

---

### Post by trivialpackets on 2006-07-27
Or, 'sudo -s' without the quotes should give you the approximate ezivalent of su.

---

### Post by trivialpackets on 2006-07-27
Also, I would recommend checking out either of the bcm43xx how to's.  I have the card the ends with rev 03 and the how-to at
[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom)
did the job for me.  There are other How-To's if you have other broadcom chipsets if you do a search I'm sure they will come up.  If you want ndiswrapper.  Take a look at this, as the built in broadcom module will give you issues with ndiswrapper.
[http://www.ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom)

Good luck!

---

