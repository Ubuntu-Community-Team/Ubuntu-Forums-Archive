---
title: "Skype Installation"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Dominic31 on 2008-02-26
Hi everybody

I have Ubuntu 7.10, and just tried to install Skype.  Only a 32-bit version is available, so I needed to use force-architecture to install it on my 64-bit system:

sudo dpkg --force-architecture -i skype-debian_1.4.0.118-1_i386.deb

The install seemed to go ok, but when I tried to run Skype from the applications menu, I got a message saying

Failed to execute child process "skype" (No such file or directory)

I also couldn't find any file called skype on my file system, It was as if I didn't install Skype at all, except for the entry in the applications menu.  But then I brought up the list of installed packages using

dpkg --get-selections

and skype was listed.  So then I tried to remove it using 

sudo apt-get remove skype

but it said that the package wasn't found!

I don't know if it's just my lack of experience with Linux that's to blame here.  All I want to do is wipe whatever the failed skype install done, and successfully install skype (on my 64 bit machine).

Any ideas?

---

### Post by PmDematagoda on 2008-02-26
Reinstall the Skype package and then try running Skype again.

---

### Post by Dominic31 on 2008-02-26
Thanks for the reply.

Re-running the installation package didn't change anything, still just a broken link in the applications menu.

---

### Post by PmDematagoda on 2008-02-26
Wait, I just remembered something. Did you follow the instructions specified in this [thread]("http://ubuntuforums.org/showthread.php?t=432295") on how to install and run Skype on Ubuntu 64 bit?

---

### Post by Dominic31 on 2008-02-26
No, I hadn't.  Just tried it and it works fine now.

Thank you very much!

---

### Post by Chappy7777 on 2008-02-27
I just went to skype's download page for 7.04 linux (which is what I am running). It all looked great until I saw 

Software needed:

Qt 4.2.1+
D Bus 1.0.0
libasound2 1.0.12
libsigc++2.02

I looked for this software in synaptic and none of it came up as existing, never mind loaded.
Can someone tell me where and how to find this stuff? I am not new to Ubuntu, but I am pretty much an "unterminal" user. In other words, I install and remove using Synaptic as much as possible. The only thing I have installed that I am sure I needed to use a Terminal for is Real Player. That was easy enough after some kind soul on here told me what to type into terminal.

Skype makes downloading, installing, and using itself sound like a no-brainer. If that's true, I can likely do it. 

Some feedback please.

---

### Post by Nitro Fan on 2008-03-01
Iwant to install Skype but cant find it in Synaptic or the default Ubuntu installer how do I get it?

---

### Post by PmDematagoda on 2008-03-01
You will have to add the Medibuntu repositories by following this [guide]("https://help.ubuntu.com/community/Medibuntu"), after the repositories have been added, execute:-
```
sudo apt-get update
```
and
```
sudo apt-get install skype
```
successively, after they are done Skype should now be installed.

---

### Post by Kaare_K on 2008-03-06
my computer crash, got angry at windows and I switched to Ubuntu about 24 hours ago. I like it, however I just moved to Japan and I talk to friends and family through skype...I followed the directions and added the medibuntu repository and that worked fine, however when I got to install skype with the code from above I get this....


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-core (>= 4.3.2) but it is not installable
         Depends: libqt4-gui (>= 4.3.2) but it is not installable
         Depends: dbus-x11 (>= 1.0.0) but it is not installable
E: Broken packages


Is there something else I have not done, well obviously there is, but I don't know what it is, I am new, very New.

Thanks


Kaare

---

### Post by PmDematagoda on 2008-03-06
Go to Software Sources in System>Administration>Software Sources, enable all the repositories in the Ubuntu Software tab except for the CD-ROM and close it, you will be asked to reload the sources list, do that and then try installing Skype again.

---

### Post by p221072 on 2008-03-06
You can download skype also directly from the skype web site.
There is the ubuntu version, you just need to download it and open it with the suggested program (dpkg).
[LIST]
Here you can find the last stable version [v 1.4]:
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)[/LIST]
[LIST]And here the latest beta [v 2], supporting video call:
[http://www.skype.com/intl/en/download/skype/linux/beta/](http://www.skype.com/intl/en/download/skype/linux/beta/)[/LIST]

---

