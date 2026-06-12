---
title: "[SOLVED] problems with flash"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by bscasta on 2008-01-09
I am having problems getting flash installed i keep getting this error.



----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/brian/.mozilla

Proceed with the installation? (y/n/q): y
cp: cannot stat `./libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/brian/.mozilla/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n):

---

### Post by philinux on 2008-01-09
Are you following this.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

It worked a treat for me.

---

### Post by bscasta on 2008-01-09
Yes     thats how i got to this point.

---

### Post by bscasta on 2008-01-09
ok  i fixed one problem    so now I just get      how do i remove xpti.dat

----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/brian/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n):

---

### Post by philinux on 2008-01-09
ok

In the terminal you need to 

cd /Desktop/install_flash_player_9_linux

copy and paste it.

Then run 

./flashplayer-installer

---

### Post by philinux on 2008-01-09
ok you sorted it.

in terminal type

locate xpti.dat

I then used gksudo nautilus 

to remove if from components directory

---

### Post by bscasta on 2008-01-09
Ok   im trying to work this through.   now im getting 
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla):

---

### Post by Kosimo on 2008-01-09
The easiest way to do it is the following:

Open Firefox, disable the ubufox extension.  
Close it
Reopen it again
Then go to some webpage that requires flash. Follow the automatic installation in firefox.

That's it.


Then, if you really want the latest version, go to the flash download site and get the manual file, extract the  flash plugin and replace your current one in  /home/.Mozilla/Plugin

Hope it helps.

---

### Post by bscasta on 2008-01-09
Im a retarded newbie       how do you disable ubufox?

---

### Post by Kosimo on 2008-01-09
> **bscasta said:**
> Im a retarded newbie       how do you disable ubufox?

Go to tools, add-ons  then search for ubufox and disable it

---

### Post by bscasta on 2008-01-09
ok   now that i disabled that I didnt have to download anything.   now all of a sudden all my vids are playing.    must have been a crap @ss plugin

---

### Post by Kosimo on 2008-01-09
Cool ;) 

I still don't like ubufox at all, It still need lot of improvement.

---

