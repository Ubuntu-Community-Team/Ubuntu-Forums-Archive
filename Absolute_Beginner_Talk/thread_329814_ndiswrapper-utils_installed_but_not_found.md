---
title: "ndiswrapper-utils installed but not found"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Radovitch on 2007-01-02
Hi,

As I want to install a wireless adapter that requires ndiswrapper-utils I installed this module directly from the ubuntu 6.06 installation DvD using the Synaptic Package Manager. However when I attempted to then install the driver (Speedtouch 121g) via the terminal I received the error message that no ndiswrapper versions were found. I tried reinstalling it through the package manager but got the same message. Am I missing something here? 
Thanks

---

### Post by bluefrog on 2007-01-02
using sudo?

what command did you issue?

James

---

### Post by Radovitch on 2007-01-02
Thanks for your fast reply. I first tried to install the driver using the ndisgtk graphic interface. I selected the BT4501G.inf file inside the driver folder and clicked install. But nothing happened. I then used this sudo command via the terminal: 

sudo ndiswrapper -i ~/drivers/BT4501G.inf

and got the reply: Error: no versions of ndiswrapper found.
All the information on this procedure I took from: 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-11fbc64ce97ef2adcee5282e3e36fa7cfbc19586](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-11fbc64ce97ef2adcee5282e3e36fa7cfbc19586)

I know the driver is correct as I downloaded it from the ndiswrapper.sourceforge.net list. I have a dual boot and the downloading had to be done via the Windows half.

---

### Post by bluefrog on 2007-01-02
hopefully you still have dapper install cd.

not sure I understand how you installed ndiswrapper (once you say you installed it thru synaptic, in the next post you installed it from sourceforge...)

So install it from synaptic or from console using the DVD (or internet ubuntu repository).

and then it should run from there without problem.

Silly question:
you haven't installed it on a live session and rebooted afterwards?

James

---

### Post by Radovitch on 2007-01-02
Sorry for the confusion. What I downloaded from the ndiswrapper sourceforge site was the speedtouch driver not ndiswrapper itself. That was installed directly from the Dvd (the DvD that came with the ubuntu book), with the package manager. And it is definitly not a livesession but the full installation.
However, when the reinstallation with the package manager also failed I manually downloaded the ndiswrapper-utils package from: [http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils.en.html](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils.en.html)
and attempted to install it using the terminal command: sudo dpkg -i ndiswrapper-utils_*.deb. This is the output:

$ sudo dpkg -i ndiswrapper-utils_*.deb
(Reading database ... 69552 files and directories currently installed.)
Preparing to replace ndiswrapper-utils 1.8-0ubuntu2 (using ndiswrapper-utils_1.8 -0ubuntu2_i386.deb) ...
Unpacking replacement ndiswrapper-utils ...
Replaced by files in installed package ndiswrapper-common ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

I assumed from this that the installation had succeeded. 
But when I tried the ndiswrapper -i command I got the same error message.

---

### Post by bluefrog on 2007-01-03
paste output of the following commands in a console:

whereis ndiswrapper
dpkg -L ndiswrapper-utils-1.8

and paste as well the command and the output (preferably copy/paste) of the command you are issuing.

James

---

### Post by Radovitch on 2007-01-04
Hi,
Sorry for the delay but here it is:

~$ whereis ndiswrapper 
ndiswrapper: /usr/sbin/ndiswrapper /etc/ndiswrapper /usr/share/man/man8/ndiswrapper.8.gz
~$ dpkg -L ndiswrapper-utils-1.8
Package `ndiswrapper-utils-1.8' is not installed. Use dpkg --info (= dpkg-deb --info) to examine archive files, and dpkg --contents (= dpkg-deb --contents) to list their contents

So, as I guessed, the utils is not installed. But then why, when I check back with the package manager does it indicate that both the utils and the ndiswrapper files are installed? I know this because I clicked on the window in the package manager next to the package list which says 'show only installed' and there it is?

Thanks for your patience

---

### Post by bluefrog on 2007-01-04
don't know what happened.

what you can try is to a complete removal of ndiswrapper-utils using synaptic (if it does allow you todo it) and reinstall.

Hopefully this will work.

Other that that I am afarid I will be of no help.

James

---

### Post by Radovitch on 2007-01-04
That was almost the first thing I tried. However, just out of curiosity, could you tell from this screenshot if it really is installed? Cause then I can try to approach this from another direction.

[IMG]http://www.imagebee.org/images/771Screenshot.png[/IMG]

Thanks anyway for trying and I will let you know when, not if, I get this solve.

Radovitch

---

### Post by bluefrog on 2007-01-04
would be more interesting to see a screenshot of synaptic opened and aligned on the ndiswrapper-utils

James

---

### Post by Radovitch on 2007-01-04
Got it!    

After your last bit of advice I decided to once more deinstall/reinstall the utils module. But this time I also deinstalled the ndiswrapper-commons module and did not reinstall it. I don't know how but this did it. I've now installed the wireless driver with the ndisqtk and what a beautiful sight it all is.

Thanks once again for all your help. Do you know that I originally posted this question on three different linux sites and todate you were the only one who took the time to reply? So if I can ever return the favor...

Radovitch

---

### Post by bluefrog on 2007-01-05
You can :-)

Edit your post and mark it as Resolved :-)

James

---

