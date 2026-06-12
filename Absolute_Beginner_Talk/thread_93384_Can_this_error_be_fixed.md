---
title: "Can this error be fixed"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-21
**SOLVED**

The printer saga continues.  I logged in as root (I know this is not a good idea, but I've tried everything else, search for my other posts for the whole story) and followed the instructions to untar and install the Samsung Linux drivers.  I executed the commands correctly, I thought, but I get the following error:

r# ./image/setup.sh
./image/setup.sh: line 143: 11473 Segmentation fault      "$setup" "$@" 2>>$NULLThe setup program seems to have failed on x86/glibc-2.1

Please contact your Customer Support

Any ideas on how to solve?  is glibc-2.1 a missing file or something?  Thanks.

---

### Post by kennethb on 2005-11-21
What kind of printer do you have?

---

### Post by deNoobius on 2005-11-21
It's the Samsung CLP 510N.  It has Linux drivers, but Ubuntu is not one of the supported distros.  The instructions require that one be logged on as root before installing.  I have confirmed that "sudo" does not work; trying that way just results in a string of errors which I have posted in one of my other messages.  Also, CUPS does not work, either with the printer attached via USB cable or Ethernet.  

Having my printer work is absolutely critical to me, and I won't be able to use Ubuntu except as an occassional intellectual exercise unless I can find a solution.

Apparently, the glib file in question IS on my system, so I don't know why I got that error.  Maybe the installation file and the glib file have to be in the same location?  I'll try moving things around and see if that helps.

---

### Post by kennethb on 2005-11-21
I'm not familar with Samsung printers; sorry. Do you have any other printer options? I have Ubuntu woking very well with an OficeJet T45 (a 10 year old prinet). Maybe HP has more "swing" with th Ubuntu dev team than Samsung???? ;-)

---

### Post by deNoobius on 2005-11-22
No other printers, nor would I get another one just so I can run Ubuntu.  This is a new color laser that I bought a few months ago.  

What about the error I'm getting?  Anyone know what it means?

---

### Post by Spikextrem on 2006-02-02
I have the exact same problem on a Samsung ML-1710. 


# ./setup.sh
./setup.sh: line 143:  6736 Erreur de segmentation  "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1


Plz someone, help. Do i need to reinstall glibc or something?
It's written that you solved the problem, how?? :confused:

---

