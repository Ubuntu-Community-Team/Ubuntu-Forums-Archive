---
title: "Flash Why Won't You Work"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by LiquidFlame on 2006-04-20
ok so my flash did work now all of a suddon when i go to a site it says i need a plugin but when it trys to install it fails.  I don't get why all of a sudden it won't work.  I looked and I'm pretty everything that needs be is installed and when i try: sudo apt-get install flashplayer-mozilla. it says that: flashplayer-mozilla is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

does anyone have any idea please.

---

### Post by catlett on 2006-04-20
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) Follow this thread. Read the post and install the script that it is about "Automatix".  It will make your life easy.

---

### Post by Mustard on 2006-04-20
[QUOTE=LiquidFlame]ok so my flash did work now all of a suddon when i go to a site it says i need a plugin but when it trys to install it fails.  I don't get why all of a sudden it won't work.  I looked and I'm pretty everything that needs be is installed and when i try: sudo apt-get install flashplayer-mozilla. it says that: flashplayer-mozilla is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

does anyone have any idea please.[/QUOTE]

What firefox version are you currently using?  
Have you recently upgraded that firefox version?

I ask this because I installed firefox 1.5, upgraded to 1.5.0.1 with no problems (that I noticed), then recently upgraded to 1.5.0.2 and now it seems that flash is not working.

---

### Post by LiquidFlame on 2006-04-20
i tried the automatix and that didn't work. i'm using Firefox version 1.5.0.2 and as far  asi know i dind't update it recently.

---

### Post by Mustard on 2006-04-20
[QUOTE=LiquidFlame]i tried the automatix and that didn't work. i'm using Firefox version 1.5.0.2 and as far  asi know i dind't update it recently.[/QUOTE]

Hmm..well its interesting at least that we are both using 1.5.0.2 and both of us have flash problems.  I haven't found the answer yet.  You are the first person that I have seen report a similar problem too.  I am hopeful that should others strike this issue that some solutions might be found.  Until that stage, I'm just waiting and reading up what I can about the Firefox 1.5.0.2 installation. :)

Currently, I'm think that a symbolic link might have been lost or overwritten or is now pointing to the wrong place.  I haven't explored this possibility in depth yet.

I installed Firefox using this guide [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
I'm using that guide as a reference for troubleshooting as well.  Basically I think I need to go through install method and see if anything has changed from what I set it too when I first installed 1.5.

---

### Post by phonglong on 2006-04-21
ok, after about 2 hours of mucking around with everything from EasyUbuntu to scripts and other suggestions, i've found out why flash won't work on my brand spanking new installation of dapper beta...

all of the scripts and apt-get installs the flash plugin in /usr/lib/mozilla/plugins

only the files need to go in /usr/lib/mozilla-firefox/plugins

so here's what i did:

download install_flash_player_7_linux.tar.gz from:

[http://physweb.bgu.ac.il/DOWNLOADS/Mozilla/](http://physweb.bgu.ac.il/DOWNLOADS/Mozilla/)

then unpack the guy with 

tar -xvzf install_flash_player_7_linux.tar.gz

then cd into the new directory:

cd install_flash_player_7_linux

now, last but not least:

sudo cp flashplayer.xpt /usr/lib/mozilla-firefox/plugins/
sudo cp libflashplayer.so /usr/lib/mozilla-firefox/plugins/

and there you go... for the neighsayers, there's screenshot

---

### Post by Mustard on 2006-04-21
I appreciate you sharing your solution, phonglong. :)

I'll give this one a go, at some stage in the future.

---

### Post by Sianis on 2006-04-21
Hi!

What version are you using? If Dapper read this...

I just installed a new Dapper. I found a package with synaptic what is looking good. It's the **flashplugin-nonfree** (multiverse), but you can install instlibflash-mozplugin (multiverse) also. And I recommend you edit your **/etc/apt/sources.list** to get the latest fresh packages.

The question is up, what version of Ubuntu?

---

### Post by Mustard on 2006-04-21
Well, I'm on breezy myself. :)

---

