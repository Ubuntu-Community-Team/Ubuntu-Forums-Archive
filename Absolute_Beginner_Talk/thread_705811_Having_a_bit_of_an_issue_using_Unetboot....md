---
title: "Having a bit of an issue using Unetboot..."
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-02-23
I just recently have added to the topic about Unetboot about an issue I'm having. 

[http://ubuntuforums.org/showthread.php?t=427540&highlight=unetboot]("http://ubuntuforums.org/showthread.php?t=427540&highlight=unetboot")

The program is great and I love the idea, but I've apparnetly done something wrong. I'm not sure if I'm aloud to start a new post about it, but I thought it might gain interest faster as its own topic and so that anyone having the same issue I'm having could find the topic easier and apply it for themselves. Of course it helps me find a answer sooner myself ;-)

The following is the post I made:

Hello all,

I downloaded Unetboot and followed all the directions to a 'T'. When it asked which distro I wanted to go with I chose Xubuntu. I know Xubuntu will work on this computer as I've installed it before. I am currently using a patition with a messed up Ubuntu/Xubuntu/ interface but that's another story I won't get into. This computer has a very slow CD-ROM drive so I figured this Unetboot would be an excllent method. I'm already loving it and thinking its an awesome idea, but I'm having an issue with it that I was hoping someone could share some enlightenment with me on. I went to boot it for the first time after it was finished installing. It did all the checks then it asked me to login in text. Odd, I thought, as I've never had to do that before. So, I logged in with my user and pass and then i was given a quick warning about how ubuntu comes with no license and then.... well that's it. Its just all terminal. Its all command prompt...... What did i do wrong?!

[COLOR="Red"]**Edit:**[/COLOR] I see that there are updates that need to be installed now that I'm back on the working partition. If I did half the installation last night, and the other half this morning, when new updates were to take place after it checked for updates or something, would that cause an issue? Just trying to think of things here! thanks!
[COLOR="Red"][B]
Edit #2:[/B][/COLOR] I decided to write down and type everything grub said to see if it would help the situation at all.

Basically, I turn on the computer, lots of stuff is said but the very last screen says the following:

* Mounting local file systems... [ok]
* Activating swapfile swap... [ok]
$Mounting securityfs on /sys/kernel/security: done [ok]
Loading APParmor profiles: done
*Checking minimum space in /tmp... [ok]
*Configuring network interfaces... [ok]
*Setting up console font and keymap... [ok]
*Loading ACPI modules [ok]

*Starting ACPI services [ok]

*Starting system log daemon... [ok]

*Starting kernel log daemon [ok]

Ubuntu 7.10 Shekels tty1

Shekels login *Starting deffered execution scheduler atd [ok]

*Starting Periodic command scheduler crond [ok]

*Running local boot scripts (/etc/rc.local) [ok]

That's where it stops. I've let it sit for a good hour or two and it stays there, but when I press enter it says the following:

Last login: Sat Feb 23 17:25:09 EST 2008 on tty1
Linux Shekels 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/sharedoc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

shekels@Shekels:~$

The last part is a prompt where I can enter terminal commands. I don't know grub that well (if that's what the linux version of DOS is called I'm not sure enlighten me if I'm wrong I'd much rather know what its called then to not know... kind of obsessive like that).

A thought I just had was that when I installed this I chose the username to be shekels just like the other partition. I named it this, because it is the last name of my mother and little brother and it is easy for them to remember. I suppose if the issue is caused by having them both be named shekels I could reinstall it with a different name. Now I could be wrong here, but I thought the SDA1, 2 so forth and so on were each assigned to each partition to seperate them from one another so an issue like having the username on both be the same wouldn't be an issue. Chances are, I'm wicked wrong here, but I like to guess things and have people tell me whether I'm right or not to further my knowledge on such things.

If anyone can help me out thanks a million.

---

### Post by rapiscan on 2008-02-25
Hello there.

I noticed you haven't had any sort of response and thought I would weigh in.  Since you clearly have the OS installed, it may just be that you need to install the window manager. I would first try to find out if xubuntu-desktop is installed.

```
sudo aptitude show xubuntu-desktop
```

If it's not installed, you can install it:
```
sudo aptitude install xubuntu-desktop
```

I'm not familiar with the Xfce desktop environment, but you should be able to start it up after it's installed. A startup script will likely be placed in the /etc/init.d/ folder.  For gnome you would type:
```
 /etc/init.d/gdm start 
```
I assume it would be something similar for Xfce.

---

### Post by rapiscan on 2008-02-25
In fact, if you look at this article, it looks like my guess may have been right.

[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

---

