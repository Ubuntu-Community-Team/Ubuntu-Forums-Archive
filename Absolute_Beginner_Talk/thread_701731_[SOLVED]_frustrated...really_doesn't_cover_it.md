---
title: "[SOLVED] frustrated...really doesn't cover it"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by R13120(1&lt; on 2008-02-19
I'm actually going insane. 
all i want is for Firefox (which is now swiftweasel) to play the videos and music that appear on the sites i visit like my space and you tube.
i have installed xine and vlc and mplayer and followed instuctions from countless threads promising the answer but still my videos look like this [IMG]http://a849.ac-images.myspacecdn.com/images01/69/l_12585e4b6e35d485e4cb433e5e57fac0.png[/IMG]
and like_ just now_ when i had to put this up it says i don't have the latest flash or javascript is disabled so i D.L.ed flash and made sure javascript was in fact enabled but still nothing this is the 5th thread I've started and I've been reading the other posts since January.
please help

---

### Post by 449 on 2008-02-19
Everything is going to be ok! :KS

I had the same problem when I installed Ubuntu.

Follow the instructions given in this thread should fix it.

It did for me. 

Good luck.

[http://ubuntuforums.org/showthread.php?t=699361&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=699361&highlight=flash+player)

---

### Post by fatality_uk on 2008-02-19
> **R13120(1< said:**
> I'm actually going insane. 
all i want is for Firefox (which is now swiftweasel) to play the videos and music that appear on the sites i visit like my space and you tube.
i have installed xine and vlc and mplayer and followed instuctions from countless threads promising the answer but still my videos look like this [IMG]http://a849.ac-images.myspacecdn.com/images01/69/l_12585e4b6e35d485e4cb433e5e57fac0.png[/IMG]
and like_ just now_ when i had to put this up it says i don't have the latest flash or javascript is disabled so i D.L.ed flash and made sure javascript was in fact enabled but still nothing this is the 5th thread I've started and I've been reading the other posts since January.
please help

The BEST solution is not xine, VLC it is Adobe's flash player. If you want to view Flash in the best available way right now, you have to install it.

Search Synaptic Package manager for **flashplugin-nonfree**

---

### Post by bodhi.zazen on 2008-02-19
You could consider Mint Linux, it is based on Ubuntu and comes with the codics pre-installed.

---

### Post by R13120(1&lt; on 2008-02-19
> **fatality_uk said:**
> The BEST solution is not xine, VLC it is Adobe's flash player. If you want to view Flash in the best available way right now, you have to install it.

Search Synaptic Package manager for **flashplugin-nonfree**
it was installed already but i went ahead and reinstalled it. no affect.

---

### Post by R13120(1&lt; on 2008-02-19
> **seventhc said:**
> Go to
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
and download the first file
or just download this
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
It's from their site then[LIST=1]
[*]Unpackage the file. A directory called install_flash_player_9_linux will be created.
[*]In terminal, navigate to this directory and type *./flashplayer-installer*                   to run the installer. Click Enter. The installer will instruct                   you to shut down your browser(s).
[*]Once the installation is complete, the plug-in will be installed in your Mozilla browser.[/LIST]  

so in step 2 they says to "navigate to this directory" in terminal.... i'm not sure what this means. if i open the file it lets me run it in terminal and i shut down my browser and go through the motions and open it up to no affect still....

---

### Post by Sinkingships7 on 2008-02-19
if you extracted the tar.gz onto your desktop, then there's a folder there called "install_flash_player_9_linux". to navigate to this directory (not to say that this is where you put it, but just navigate to wherever it is) you'd type this into the terminal:
```
cd /home/USER/Desktop/"install_flash_player_9_linux"/
```
where USER is your user name.
that'll change the directory of where your terminal is looking. then you can execute:
```
./flashplayer-installer
```
and it will begin the installation.

---

### Post by billgoldberg on 2008-02-19
> **R13120(1< said:**
> so in step 2 they says to "navigate to this directory" in terminal.... i'm not sure what this means. if i open the file it lets me run it in terminal and i shut down my browser and go through the motions and open it up to no affect still....

The guys are making things complicated again.

Download that file from adobes website to the desktop.

Right-click it and choose "extract here".

Then inside that folder double click the installer and choose "run in terminal".

Follow the instructions.

It might be a good idea to remove flash-nonfree first using synaptic  (mark for complete removal and press "apply")

---

### Post by R13120(1&lt; on 2008-02-19
thank you i really do apreciate it.. i have done this (browser closed) 5 times (i was hung up on ther terminology).. still nothing any other ideas?  i'm completely stumped..

---

### Post by Sinkingships7 on 2008-02-19
can you post the entire terminal output you get when you run the flashplayer-installer?

---

### Post by stchman on 2008-02-19
> **R13120(1< said:**
> I'm actually going insane. 
all i want is for Firefox (which is now swiftweasel) to play the videos and music that appear on the sites i visit like my space and you tube.
i have installed xine and vlc and mplayer and followed instuctions from countless threads promising the answer but still my videos look like this [IMG]http://a849.ac-images.myspacecdn.com/images01/69/l_12585e4b6e35d485e4cb433e5e57fac0.png[/IMG]
and like_ just now_ when i had to put this up it says i don't have the latest flash or javascript is disabled so i D.L.ed flash and made sure javascript was in fact enabled but still nothing this is the 5th thread I've started and I've been reading the other posts since January.
please help

YouTube uses Flash for their player.  I play Flash videos like a champ in Feisty.  Do this in a terminal:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by billgoldberg on 2008-02-19
Ok.

Lets try this:

1. Remove all media program and or media related addons for firefox (like totem-mozilla or mediaconnectivity or xine, ...) Make sure to complety remove them in synaptic or from the firefox add-ons.

2. Install this piece of software called quickstart:

[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

Here you can install all the correct media for ubuntu including flash player, java and dvd support.

3. Reinstall wanted programs like vlc.

This should do the trick.

---

### Post by R13120(1&lt; on 2008-02-19
removed it then installed.. nothing...

---

### Post by R13120(1&lt; on 2008-02-19
brock@brock:~$ cd /home/brock/install_flash_player_9_linux/

brock@brock:~/install_flash_player_9_linux$ ./flashplayer-installer

Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as a non-root user.
Adobe Flash Player 9 will be installed in your home directory.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...





----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Mozilla installation directory  = /home/brock/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n):

---

### Post by jrusso2 on 2008-02-19
I noticed in your screenshot adblock is on.  Did you try to disable adblock?  Also if you have no script whitelist that site

---

### Post by anewguy on 2008-02-19
It looks like you need to preface the "./........." with "sudo " - it will ask for your password - just enter your normal password.:)

---

### Post by Sinkingships7 on 2008-02-19
hmm...

could you post the results of 
```
ls /home/brock/.mozilla/
```

---

### Post by Sinkingships7 on 2008-02-19
also the results of ```
ls /home/brock/.mozilla/plugins/
```

---

### Post by R13120(1&lt; on 2008-02-19
YOU ARE....MY NEW BestFriend    
so i was going threw deleting $#!T and i got to the Gstreamer section and noticed that i had 2 bad sets i deleted them and now all is well.....freakin A 
when all else fails delete what you've got
thank you god

---

### Post by R13120(1&lt; on 2008-02-19
Thank you all for your help it finally works....:KS:):KS:)

---

### Post by billgoldberg on 2008-02-19
I'm glad you got it working.

---

