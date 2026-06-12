---
title: "No internet for me! :cry:"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by sunosun on 2006-02-28
Greetings,

I have a Sagem Fast 800 dsl usb modem with greek ISP (OTE). I ve seen some threads regardin my issue, but not clear to me how should I fix my connection.

Right.. I justed finished my Ubuntu 5.10 for PC installation. Nothin more nothing less - from the software point of view - on my machine. No other configuration happend, except the one that Ubuntu made for me.\\:D/ 

The thread I found ([http://ubuntuforums.org/showthread.php?t=45974](http://ubuntuforums.org/showthread.php?t=45974)) doesnt help so much, while there is no explanation enough. Some links for a french speaking site (Nice language, specially when I hear it from nice chicas) that has a file (eagle-usb-2.3.2.tar) in it that could be the driver - could not - but I am not risking my freshly installed system to destroy it.

I also went to my modem manufacture' site and found an other file (Fast8x0_3-0-6).

Which one should I use? After all, the threads, the readmes and everyones advices on the subject, gives different or the same commands a little bit different.

I just need the <== right path ==> to follow. 

As an x (microsoft) windows user I have in mind about the linux driver I have to find for my modem in order to work in Ubuntu (My beloving Ubuntu team, why don't u make the things easier for as who love open source and want to leave Bill Gates back and possibly one day to contribute on that?)

Please help!!:rolleyes: 

p.s. Except where to find the latest file, can you explain me if you know, how should I make it work n have it run whenever I boot my machine, without havin every time to enable it from the console?

Thnx for listenin me.
Sun ohh Sun!!

---

### Post by Pragmatist on 2006-03-01
The directions in the thread seem pretty clear to me. First you download the driver file:** Fast8x0_3-0-6.tgz**  This is a compressed file (like a ZIP file).  You decompress the file with: ```
tar xvzf  Fast8x0_3-0-6.tgz
``` This will create a directory called Fast8x0 or something similar.  Change to this new directory and read the instructions.  Probably you will then:```
/.configure
``` the ```
make
``` then ```
make install
``` the **make install** you do as root.

There are more instructions after that.  But first download the file, uncompress with ```
tar xvzf  Fast8x0_3-0-6.tgz
``` change to the new directory and read the README and INSTALL files for instructions.  Come back after that if you need more help.

---

### Post by Brunellus on 2006-03-01
don't cry emokid.  

The post above is a pretty good summary of what's going on.  instead fo make install, though, you do 

sudo make install

My advice:  get a real modem, which speaks proper ethernet, rather than something that uses USB.  Spend a few Euros, save yourself the headaches.

---

### Post by tadashi on 2006-03-01
If you just did the plain coffee no sugar install of Ubuntu you may want to open the package manager under the system tools and install the build-essentials package so you can compile. :)  Also a nice graphical editor might be nice too unless you like vim or nano.

---

