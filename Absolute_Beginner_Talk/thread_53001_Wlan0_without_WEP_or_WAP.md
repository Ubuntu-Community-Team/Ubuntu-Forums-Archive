---
title: "Wlan0 without WEP or WAP"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by msauro on 2005-07-29
Oh my God!!
It seem soooo easy... I mean, connect ta a wlan without EVEN using a WEP or WAP.
Too easy to be true.

I have a Acer TM2300, I finally went through all the ndiswrapper stuff and got my Wcard working. I did all that at the office where we do use a WEP key.
All was working great, came back home (where I have a neighboor who use a Linksys router and didn't even protect it!! Why I know it's a Linksys... the connection's name is Linksys  ;-) ) but can't connect.

I did: *[With comments]*
sudo iwconfig wlan0 essid linksys *[Worked great]*
*[Tryed]* iwconfig wlan0 enc <> *[Didn't work]*
sudo dhclient wlan0 *[Didn't received nothing... 100% error]*

I even tryed to go System > Administration > Networking and tryed to enter nothing in the WEP field but didn't work!!

Help me opensource brothers  [-o< 

Marc the Noob

---

### Post by adwait on 2005-07-29
Maybe this can help: 
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by msauro on 2005-07-30
[QUOTE=adwait]Maybe this can help: 
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)[/QUOTE]
 Hey adwait,

Thanks bro. I did used this thread to get my wlan working... no problem with that.
It works awesome with WEP. WHat I want now is, a little bit like XP, my Network Identification to be Open [don't know if such thing exist in the so-cool world of Linux] and my Data Encryption to be disabled. As I was saying, I pretty much connect to somebody's wireless router.
The above settings are what I'm using in XP...

It's pretty much a wideopen router!!

Thanks again bro ;-) ,

Marc

---

