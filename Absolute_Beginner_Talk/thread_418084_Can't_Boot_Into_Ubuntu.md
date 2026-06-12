---
title: "Can't Boot Into Ubuntu"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by mikecomua on 2007-04-22
Angry  error bcm43xx_microcode5.fw
Hi, I have an Ubuntu Ultimate Gamers Edition Live DVD and when I try to boot Ubuntu this shows up Failed to start the X server (your graphical interface)
It is more likely that it is not set up correctly. Would you like to view the X server to diagnose the problem. [17178756.068000]bcm43xx:Error:microcode
"bcm43xx_microcode5.fw" not available or load failed.
<Yes> <No>

When I click yes this shows up
Error:Microcode "bcm43xx_microcode5.fw" not
available or load failed. Version 7.11
Release date: 12 May 2006
Protocol version 11, Revision 0, Release 7.11.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri
Oct 13 18:45:35 UTC 2006 i686
Build date: 07 July 2006
or load failed. reporting problems, check [www.wiki.x.org](www.wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown
(==) Log File:/var/log/Xorg.0.log time: Mon Apr 2 19:24:36 2007
(==) Using config file: "/etc/X11?xorg.conf"
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1)
found
(EE) I810 (0): No video BIOS modes for chosen depth.
(EE) Screen(s) found , but none have a usable configuration.
Fatal server error:
no screens found
This is a blue and white and red screen with lots of weird letters around that.

Then a black screen pops up:
firmware_helper [4970]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
for device '/class/firmware/000:0c:00.0' with driver 'bcm43xx'
[17179669.95200]bcm43xx: Error:Microcode "bcm43xx_microcode5.fw" not available
error load failed.
Do you know what I should do? I tried to disable the Wi-fi in BIOS, but that doesn't work. I have an Inspiron E1405. Will version 6.06 have the same problem?
Last edited by mikecomua : 1 Week Ago at 02:02 PM.
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
mikecomua
View Public Profile
Send a private message to mikecomua
Send email to mikecomua
Find all posts by mikecomua
Add mikecomua to Your Buddy List
  #2   Report Post  
Old 1 Week Ago
rajeev1204's Avatar 	
rajeev1204 rajeev1204 is online now
Way Too Much Ubuntu
	  	
Join Date: Nov 2006
Location: India
Beans: 349
Ubuntu 7.04 Feisty Fawn User
Windows User
Send a message via Yahoo to rajeev1204 Send a message via Skype™ to rajeev1204
Re: error bcm43xx_microcode5.fw
Hi

Is this the first time u r installing or did the xserver recently fail?

Anyways do this

sudo dpkg-reconfigure xserver-xorg

This opens up a text based editor for your grphical (xserver ) setup .

Go through the options and see what happens .


regards
rajeev
Reply With Quote Multi-Quote This Message Quick reply to this message
rajeev1204
View Public Profile
Send a private message to rajeev1204
Send email to rajeev1204
Find all posts by rajeev1204
Add rajeev1204 to Your Buddy List
  #3   Report Post  
Old 1 Week Ago
mikecomua's Avatar 	
mikecomua mikecomua is online now
5 Cups of Ubuntu
	  	
Join Date: Feb 2007
Location: Ukraine
Beans: 37
Send a message via ICQ to mikecomua Send a message via Skype™ to mikecomua
Re: error bcm43xx_microcode5.fw
Where should I type it?
Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message
mikecomua
View Public Profile
Send a private message to mikecomua
Send email to mikecomua
Find all posts by mikecomua
Add mikecomua to Your Buddy List
  #4   Report Post  
Unread 4 Hours Ago
gattung gattung is offline
First Cup of Ubuntu
	  	
Join Date: Apr 2007
Beans: 1
Re: error bcm43xx_microcode5.fw
I also am getting this error message but off of the new 7.04 CD. I am also on a dell 1505 (6400) with an ati x300 video card.

The funny thing is I can boot the 7.0 beta live cd just fine.
Reply With Quote Multi-Quote This Message Quick reply to this message
gattung
View Public Profile
Send a private message to gattung
Find all posts by gattung
Add gattung to Your Buddy List

---

### Post by ~SkyBlue~ on 2007-04-22
You can try reconfiguring X, select Ubuntu failsafe from bootloader, when shell prompt comes up, type

dpkg-reconfigure xserver-xorg

If driver for your video card doesn't work, try choose Vesa, it has lower performance, but higher chance to work.

---

### Post by mikecomua on 2007-04-22
I typed sudo dpkg-reconfigure xserver-xorg and it took through many menus, but I have no idea what parameters my display has.

---

### Post by leibowitz on 2007-04-22
Try with -phigh, it will avoid to ask you too much questions.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mikecomua on 2007-04-23
I typed ubuntu@ubuntu: ~$ sudo dpkg reconfigure -phigh xserver-xorg
And here's what it gave me:
[17179756.45600] bcm43xx : Error : Microcode "bcm43xx_microcode5.fw"
not available or load failed.
xsever -xorg postist warning: overwriting possibly customized configuration
file; backup in /etc/x11/xorg.conf.20070432184458
ubuntu@ubuntu: ~$ [171179779680000] bcm43xx: Error: Microcode "bcm43xx_microde5.fw
And so on"

---

### Post by leibowitz on 2007-04-23
> [17179756.45600] bcm43xx : Error : Microcode "bcm43xx_microcode5.fw"
not available or load failed.

This message is not related in any way to your X org configuration. Please try startx after you did sudo dpkg-reconfigure -phigh xserver-xorg

And post here what errors you get.

Then, you can paste your /var/log/Xorg.0.log file and even your /etc/X11/xorg.conf file and lspci output.

---

### Post by Ayle on 2007-04-23
It's not related to the wifi because I have the same message but it still boot: I hear kde startup sound but my screen goes from black to green and then white and stays that way....

---

### Post by Annigma on 2007-04-23
Hello :)

I'm new to Linux too. I've got a Ubuntu 5.10 'Breezy Badger' install CD which I managed to trawl through.
I had a problem logging in i.e. I couldn't! but seem to have flopped over this hurdle with a little help from searching for answers. Very strange indeed, but I can log in now, so not overly worried about that atm :o

My problem now is that I seem to have the same screen as Mike and looking at the 'diagnostics' information doesn't help me (<--noob). I've seen a couple of similar replies to yours Sky but when I try it it asks me for a password (which I enter as the username one, since I don't think there is a root one..?). It seems to accept this, at least it doesn't comlain, but it just returns me to the next $ prompt...

My xserver doesn't seem to be loaded, but I did some command which tells you what's loaded and my Radeon 9700 Pro appears in the Vga compat. and display controller fields, so... 

It took me ages to work out all the partition stuff and I really don't want to mess about with that again. I'm surprised and relieved that I got this far without messing up my XP installation, and I don't want to 'rock the boat'...

I've been wanting to try Ubuntu for a while, but I'm finding it quite hard work just to set up.. (tried half-heartedly a couple of times already in the last few months) I want to dabble with the Unix code thing and learn that side of it, but I was hoping to start with a GUI...

Any advice would be appreciated.

Thanks

:)

---

### Post by leibowitz on 2007-04-23
**Annigma**, Ubuntu 5.10 is pretty old now. You can try with a new 7.04 maybe, and see if the Live-cd Session boots in the graphical user interface at least!

Anyway, for your problem you must create another topic in the forum for getting more replies related to your issues. That's the way we handle this right here.

Feel free to post a link from here to your new thread and I will be glad to try to help you.

---

### Post by Annigma on 2007-04-23
I thought as much. Well, thanks for your reply. I've started again here:
[http://ubuntuforums.org/showthread.php?p=2518097#post2518097](http://ubuntuforums.org/showthread.php?p=2518097#post2518097)

:)

---

