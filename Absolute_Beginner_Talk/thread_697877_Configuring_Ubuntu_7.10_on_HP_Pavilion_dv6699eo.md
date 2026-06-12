---
title: "Configuring Ubuntu 7.10 on HP Pavilion dv6699eo"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by miir on 2008-02-15
**[SIZE="4"]Configuring Ubuntu 7.10 on HP Pavilion dv6699eo - Beginners guide[/SIZE]**
This guide can be used or partially used for other dv6000 and dv6500 series laptops with similar specs.

**_[COLOR="Red"]- This is a work-in-progress - Updated 2008-02-16 -[/COLOR]_**
[B]
System specs of my dv6699eo[/B]
1,5Gzh Centrino Duo
2Gb Ram
160 Gb HD
Nvidia GeForce 8400M GS
Intel PRO/Wireless 3945ABG


If you are stuck with the AMD64 X2 CPU you'll have to add the following to boot options when booting from the live-cd:
**noapic nolapic**
For more help check out [[COLOR="Red"]this[/COLOR]]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)") great guide.

Hello, 
first of I want to thank everyone out there giving their time and help to beginners like me, I'd never be using linux without you guys. _This guide is in no way my own creation_, but rather a place where I have gathered information from many other guides so that users with similar laptops and little experience (like my self) can get started right away.

Installation
This step went as smooth as it can with this laptop, therefor I'm not going to go any deeper with this then explaining how I partitioned my HD. (Note: One time something must have gone wrong with the installation and resulted in like a trillion bugs resolved by re-installing, if you have lot's of bugs it can therefor be worth trying a re-installation before spending hours looking for fixes.)

[B]2Gb was used for SWAP
10Gb was used for a ext3 partition mounted on &#8220;/&#8221;
148Gb (the rest) was used for a ext3 partition mounted on &#8220;/home&#8221;[/B]


[SIZE="4"]**Things to do after the installation**[/SIZE]

1.You're wireless should work somewhat ok out-of-the-box so go ahead and connect to your network (or plug-in cable if you are not using wireless) and update your system by clicking that little &#8220;sun&#8221; next to the clock and follow instructions. After you are finnished updating you may aswell enable your graphic restricted drivers by clicking the green-ish card icon (also by the clock) and then clicking the little box for Nvidia Accelerated Graphics Driver. Then go ahead and reboot.

2.There are a few **terminal commands** you should know from the start, for example how to install and remove applications.
**sudo apt-get install [program name]**
So let's say you want to install the ever so popular vlc mediaplayer that I'm sure you've heard of before as it's THE best mediaplayer in any OS in my opinion.
**sudo apt-get install vlc**
Yep it's as easy as that.

So how hard is it to remove a program then? Yep you've guessed it.
**sudo apt-get remove [program name]**
Easy as a pie,

**Don't be afraid of using the terminal**, it's really preferable in many situations, however there is an **Add/Remove application located right in you're ubuntu menu**.

**Go [[COLOR="Red"]here[/COLOR]]("http://www.danielandrade.net/2007/11/10/10-things-to-do-just-after-installing-ubuntu-710/") and follow the guide to install the basics, it's really a great help.**

3. Now it's time for you to expand your knowledge - remember **search is your friend**. A few recommendations that **I use**:
**Conky** is a kool feature worth googling for.
**x-chat** is a nice IRC client.
**Frozen-Buble**, fun game.
**Avant Window Navigator ( Curves )**, google/youtube this you can thank me later.
**K3B** is great for burning. ( I know it's for KDE but it works great in Ubuntu. )
**Deluge**, like uTorrent for linux - great!
**Wine**, if you need to use a windows application or game - google, there's LOT'S of info on this.

Click [[COLOR="Red"]here[/COLOR]]("http://www.gnome-look.org/") and bookmark, it's a great resource to make your linux look it's best.
_And don't forget to follow the **"10-things-to-do"** guide in step 2!_


[SIZE="4"]**Fixes**[/SIZE]
[COLOR="Red"][B]
Fix wireless connection drop:[/B][/COLOR]
1. Open a terminal and create a text file called blacklist-ipw3945 by writing:
**gedit blacklist-ipw3945**
and add 
**blacklist ipw3945**
Save and exit

2. Copy blacklist-ipw3945 to /etc/modprobe.d/
**sudo cp blacklist-ipw3945 /etc/modprobe.d/**

3. Add iwl3945 to /etc/modules
**sudo gedit /etc/module**s
and add 
**iwl3945**
Save and exit.

4. Restart and once connected to your wireless network right-click the network-manager applet and choose "Connection Information". Verify the driver is iwl3945.

Thanks **specker** for this information, read more about this in [[COLOR="Red"]his guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=595060").

[COLOR="Red"]**Sound and Quickplay bar, mute button always red, fix:**[/COLOR]
Open a terminal and type:
**sudo apt-get install linux-backports-modules**
Now all you have to do is reboot.

For more information check out [[COLOR="Red"]this[/COLOR]]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)") guide.



More to come as I learn more, please write comments and suggestions to make this guide as good as possible.


// miir

---

### Post by Discov3ry on 2008-02-15
Subscribed, I'll be installing 7.10 on HP dv9500z (AMD). So far from what I've gathered it's quite a challenge so I may be able to chip in.

---

### Post by miir on 2008-02-16
I've found a great guide covering alot for HP Pavilion users that have the intel cpu.[URL="http://aldeby.org/blog/?page_id=87"]
Check this out![/URL]

I'm working on an even deeper guide that I'll post in theese forum covering most of HP's laptops (the goal is to cover them all) with information gathered from here and there, Please post tips and solutions here if you want to be sure I've learnt about it.

//miir

---

