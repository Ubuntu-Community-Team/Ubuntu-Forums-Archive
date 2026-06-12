---
title: "Errors with vmplayer"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-24
I have been trying to install various programs using vmware player. I keep getting errors and nothing gets installed.
Any help would be appreciated.
I have attached a screenshot of the error message.

---

### Post by Phoobarnvaz on 2006-09-24
> **HareBall said:**
> I have been trying to install various programs using vmware player. I keep getting errors and nothing gets installed.
Any help would be appreciated.
I have attached a screenshot of the error message.

I was having problems as well getting the player installed with the newest version of the kernal (-27-686).  The reason is that the kernal modules with this are outdated with the -23 modules.  

Here's the steps I did after doing some research:

1.  su in a terminal window
2.  apt-get install vmware-player to install the program itself.  Let it error out & finish!!!
3.  Goto [http://packages.ubuntu.com/dapper/misc/](http://packages.ubuntu.com/dapper/misc/) & look for Package: vmware-player-kernel-modules-2.6.15-27 (2.6.15.10-10)
4.  Download it or do an apt-get.
5.  Install this if you download it or let apt-get do it for you.
6.  Goto a terminal window again (if you downloaded it) & run:  dpkg --configure -a .
7.  Complete the prompts.
8.  Reboot to put the icon in the correct place.
9.  Enjoy it!!!

---

### Post by PriceChild on 2006-09-24
Btw... in the future you can use alt+printscreen to s/c  only the active window.

Just thought its a very cool feature that can save you time uploading/cropping :)

---

### Post by HareBall on 2006-09-24
> **Phoobarnvaz said:**
> I was having problems as well getting the player installed with the newest version of the kernal (-27-686).  The reason is that the kernal modules with this are outdated with the -23 modules.  

Here's the steps I did after doing some research:

1.  su in a terminal window
2.  apt-get install vmware-player to install the program itself.  Let it error out & finish!!!
3.  Goto [http://packages.ubuntu.com/dapper/misc/](http://packages.ubuntu.com/dapper/misc/) & look for Package: vmware-player-kernel-modules-2.6.15-27 (2.6.15.10-10)
4.  Download it or do an apt-get.
5.  Install this if you download it or let apt-get do it for you.
6.  Goto a terminal window again (if you downloaded it) & run:  dpkg --configure -a .
7.  Complete the prompts.
8.  Reboot to put the icon in the correct place.
9.  Enjoy it!!!


I tried some of this, but I don't know a lot about using a terminal yet. I am slowly getting to be able to do some things. I have learned how to move files(sort of anyway) and how to open some other things(alsamixer). I don't know much about apt-get. I know it is used to get stuff, but how to just tell it to, I don't know. I have a long way to go, but hopefully a long time to get there.[-o< 
Larry

---

### Post by HareBall on 2006-09-24
> **PriceChild said:**
> Btw... in the future you can use alt+printscreen to s/c  only the active window.

Just thought its a very cool feature that can save you time uploading/cropping :)

Thanx for the tip. I didn't know about that. Works better and makes things easier to see.
Larry:D

---

### Post by KeighleHawk on 2006-09-28
Don't know if you finally got this all working.  Browsing through the various messages on this subject finally lead me to upgrading the linux kernel.  It seems the VMware stuff and the linux kernel are pretty tightly bound.  So the only way to install the latest VMware is to first have the latest kernel (and possibly kernel-headers).

Robert

---

### Post by HareBall on 2006-09-28
> **KeighleHawk said:**
> Don't know if you finally got this all working.  Browsing through the various messages on this subject finally lead me to upgrading the linux kernel.  It seems the VMware stuff and the linux kernel are pretty tightly bound.  So the only way to install the latest VMware is to first have the latest kernel (and possibly kernel-headers).

Robert

Well I have had other problems and ended up reinstalling Ubuntu. When I ran Automatix I saw some of the same errors pop up. I haven't tried anything else to see if maybe there has been a change in this.
It shows the errors, but things seem to install anyway.

---

### Post by HareBall on 2006-09-30
> **HareBall said:**
> Well I have had other problems and ended up reinstalling Ubuntu. When I ran Automatix I saw some of the same errors pop up. I haven't tried anything else to see if maybe there has been a change in this.
It shows the errors, but things seem to install anyway.
I re-installed Ubuntu again this morning. Now when I load software I don't get the error messages I was getting.

---

