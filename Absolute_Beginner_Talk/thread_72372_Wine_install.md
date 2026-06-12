---
title: "Wine install"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by bmarilena on 2005-10-06
Hi 

I got the wine and followed the steps to install.
After wineinstall as user in terminal I got this message "/tools/wineinstall
WINE Installer v0.75

~/wine-0.0.20050725-winehq ~/wine-0.0.20050725-winehq/tools
Running configure...

./configure: line 996: config.log: Permission denied

Configure failed, aborting install.
"

What should I do next?

I'm very confused.

Please help...

Marilena

---

### Post by matthewv on 2005-10-06
try running as root:

put ```

sudo

``` 
in front of the installer command

---

### Post by bmarilena on 2005-10-06
Hi 

With sudo the answer was:

/wine-0.0.20050725-winehq/tools
You are running wineinstall as root, this is not advisable. Please rerun as a user.
Aborting.


What next?

Marilena

---

### Post by matthewv on 2005-10-06
whereabouts on your system is the wine installer... and what instructions are you following.. (link please)

---

### Post by bmarilena on 2005-10-06
The link is :
[http://winehq.org/site/docs/wine-user/config-helper-programs](http://winehq.org/site/docs/wine-user/config-helper-programs)

The installer is on /home/~//wine-0.0.20050725-winehq/tools$

Marilena

---

### Post by bmarilena on 2005-10-06
Please help with wine instalation.
Any sugestion is valuable for me....
Marilena

---

### Post by bmarilena on 2005-10-06
I don't find anything to work now.... what can I do...
Please help me with this wine....


Marilnea

---

### Post by Qrk on 2005-10-06
Whats wrong with the wine from the repositories? You should be able to get it through synaptic.

---

### Post by bmarilena on 2005-10-06
Well, seems like something's broken there... because it doesn't work... I don't remember why but I tried...
RIght now I just ununstall everithing and I want to try again...
And because I didn't do any step yet.... can you suggest a how to or tutorial or something to follow in order to get it working?
Thanks

Marilena

---

### Post by wishyjr on 2005-10-06
hello again everyone, im gonna hijack this thread a little as it seems to be going a bit deralict. Ive also got a problem installing wine - ive added the  addresses for the extra depositories as per the instructions on [www.winehq.com](www.winehq.com) and ive ran apt-get update in a terminal but if i try and run sudo apt-get install wine i get:

[B]paul@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
paul@ubuntu:~$[/B]

so im assuming wine isnt where it should be - any ideas? Also, the installation package doesnt seem to be in the list when i search for wine in synaptic, instead all i have is documentation,  a version of winetools (2.1.1-1), libwine and libwine-dev. Do i need these? is that all i need? it seems i should be seeing another package -please correct me if im wrong.

thanks again guys!

---

### Post by matthewv on 2005-10-06
[QUOTE=bmarilena]Well, seems like something's broken there... because it doesn't work... I don't remember why but I tried...
RIght now I just ununstall everithing and I want to try again...
And because I didn't do any step yet.... can you suggest a how to or tutorial or something to follow in order to get it working?
Thanks

Marilena[/QUOTE]
Just wondering, have you tried using the instructions found here [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by bmarilena on 2005-10-07
:) well, thhis page was the one I used for installing wine, but when configure.. it doesn't work. 
I don't know what to do next.

I tried to uninstall and follow the steps again, and after tried couple of times... the answer was "is not enougs spce on the disc drive... Probably every time was downloading the same things, so I have part of the package few times and part of it I don't have... How can I clear the space?
In /home/~/.... I deleted everithing after uninstall, where else should I look?
Do I have to reinstall the OS?

Marilena

---

