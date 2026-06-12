---
title: "Azerus closes a few seconds after I start..."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-06
It used to work just fine. Now, it starts up, the window is displayed for a bout a second, then it just dissapears. Tried reinstalling...no luck.

---

### Post by NeoLithium on 2007-06-06
Open up your home folder, type CTRL+H to see the hidden files.  Then open up your .azureus folder and delete your logs.  Try to load it then. Should be all good :)

Hope this helps.

---

### Post by Ek0nomik on 2007-06-06
If that doesn't work, please run azureus from the terminal and post any errors in the output that you receive.

---

### Post by FleetAdmiral74 on 2007-06-06
Here is what I got in the terminal:

ed@ed-desktop:~$ azureus
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
should load blocklist from: [http://www.bluetack.co.uk/config/spconfig.txt](http://www.bluetack.co.uk/config/spconfig.txt)
Retrieving data from: [http://www.bluetack.co.uk/config/splist.zip](http://www.bluetack.co.uk/config/splist.zip)
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb042f172, pid=6728, tid=3084879552
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid6728.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
ed@ed-desktop:~$

---

### Post by NeoLithium on 2007-06-06
Did you clear all the logs before trying again?  More than once I've just been fed up with it, and deleted the whole .azureus folder (Makes it as if it is the first time you run the program) However I also switched to Deluge, which seems to be a little less problematic...just a personal preference though.

---

### Post by Josey on 2007-06-06
Use ktorrent.
Azureus is nothing but headaches.

---

### Post by FleetAdmiral74 on 2007-06-06
I did delete the logs, think I got em all...

I will certainly try either of those, just curious though. How do they stack up to Az? Well, one thing is are they foss? My other concern is protecting myself. Az had safepeer, and I know thats not 100% protection, but I prefer a layer of security. How do those programs stand up?

---

### Post by thegreenblob on 2007-06-06
I also like ktorrent. It has a IP Blocking Filter built in, all you do is go to the plugins and activate it.

But with the azures problem, reinstalling java may fix the problem.

---

### Post by thehessian on 2007-06-06
You should try changing your Java version to the Sun 1.5 package (not sure of the commands, but search the forums for Azureus Java and see what you come up with).

Hessian

---

### Post by FleetAdmiral74 on 2007-06-06
Well I reinstalled the java-common in synaptic, no luck. Guess I might just give Deluge a try, unless someone has a good analysis of how they stack up.Are they directly in competition or something? (used to be gTorrent...)

and deluge does not seem to in the repo...is that bad? makes it hard to keep track of right? im still new to this, but if I stick to the synaptic thingy things seem to work...

---

### Post by NeoLithium on 2007-06-06
To double check your java, you can type
```

sudo update-alternatives --config java

```
Make sure the option used is the Sun Java option.

Deluge is quite good, though I'm not sure about the security stuff, since I just use it from time to time with distro stuff and the occasional bit of music. However it's quite fast, which is somewhat appreciated, compared to some other torrent programs.

---

### Post by FleetAdmiral74 on 2007-06-06
Switching topics to kTorrent...the blocklist seems to be down..
Connection to host coblitz.codeen.org is broken

Is there another url I can use for p2p lists?

---

### Post by jackmc on 2007-06-06
I deleted the logs, but the problem came back. This is currently working for me:

> I have this same problem on Kubuntu 6.10. I solved the problem by replacing /usr/share/java/Azureus.jar with Azureus2.5.0.0.jar (rename to Azureus.jar) which can be downloaded from [http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.0.jar?download](http://prdownloads.sourceforge.net/azureus/Azureus2.5.0.0.jar?download)

---

### Post by osarusan on 2007-06-14
I've had this problem over and over as well. Deleting all the error logs and the log folder as was suggested just worked for me! :-)

Changing the Java to 1.5 did not help.

If the problem comes back, I will try replacing the .jar file with the one recommended.

---

