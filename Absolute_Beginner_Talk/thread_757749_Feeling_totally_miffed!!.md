---
title: "Feeling totally miffed!!"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by 10Digits on 2008-04-17
Hey there ,

After a breezy install of ubuntu Gutsy on my desktop computer , I was really amazed how easy it was for me to install it...

But it seems I am stuck with some kind of problems ...
Like whenever I turn On or off Ubuntu a message comes up about power management and it says that my Monitor is out of frequency...
What does that supposed to mean?
Is it because I have not installed drivers for my nVidia 5200Fx graphics card?
How am I supposed to Install these Drives without having an Internet connection??

I can't install easyubuntu too??
When i double click on the .deb file I downloaded It installs on my computer and comes up on the main menu...
but when I click on the entry on the menu it doesnot work:(
Also I tried using the terminal , after I read its readme file 
  
but an error came up 

sudo apt-get install subversion

E: couldn't find package subversion.

Also I cannot install envy <another package I downloaded off the net>
it says 
error: dependancy is not satisfiable : xserver-xorg.dev

and compiz <downloaded off the net>
says to use $ autogen.sh:confused:

only it doesn't work...


Can you guys help me out .. Using Ubuntu without an internet connection
this tough??
HELP!!!


PS : all downloads are recent and found while navigating thru the forum...  

Thanx in advance

---

### Post by pedro_orange on 2008-04-17
Hi,

You may find it alot easier to install stuff from Synaptic Package Manager. It looks at what dependencies you need etc and downloads/installs it all for you. Magic.

Also, since you're using Gutsy can you not install your graphics card drivers from the Restricted Drivers Management area? 
If not, Envy will do the trick nicely. 

If you try to install stuff and it says "missing dependency: xxxxxx" - you need that file. So, try and apt-get it. 
Although I think the package name for xserver-xorg.dev is actually xserver-xorg-dev. Although I maybe/and probably am wrong. So search for it using:

```
apt-cache search xserver-xorg
```

or something.

I think you're getting "Out of range" because your PC is not sending anything down the graphics cable. One of my old PCs used to that for a second when I first turned it on, and then after the box was off, the monitor would display "out of range".

I wouldn't worry about the out of range error unless it's stopping you boot into GNOME.

Regards

---

### Post by Hospadar on 2008-04-17
Also, you may want to go into System-Adiministration->Software Sources and turn on the extra repositories, "universe" "multiverse" (And I think there is one more?)  Some of the packages you want might be in there.

---

### Post by 10Digits on 2008-04-18
Thanx guys I found out that if I installed some files from the CD I would have much lesser trouble.

Can you guys tell me anything about APTonCD??

Also, even though libpango 1.0-0 is installed , envy finds an error in the dependancies...
and I cannot enable compiz...

It gives some kind of error....

---

### Post by hyper_ch on 2008-04-18
(1) compiz fusion is already installed... you just need to get the Compiz Composer Settings Manager [or something like that] to get access to the advanced desktop effects

(2) installing in general:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

