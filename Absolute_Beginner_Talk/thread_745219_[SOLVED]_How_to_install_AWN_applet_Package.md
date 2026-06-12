---
title: "[SOLVED] How to install AWN applet Package?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by tstack77 on 2008-04-04
I downloaded the latest version of AWN (2.6) from getdeb but it didn't come with any applets preinstalled. I then went to [https://launchpad.net/awn-extras](https://launchpad.net/awn-extras) to download the awn-extras-applets0.2.6.tar.gz.

My problem arises when I try to install them using the "Install" button (then selecting the AWN Applet Package from above). I get the notification that the install was a success, but I still get no new applets :confused:

How do I fix this?

---

### Post by DK-420 on 2008-04-04
Have you tried restarting your machine? When I installed AWN, I had to restart it for the applets to work correctly.

Oh and do you have Compiz Fusion running?

---

### Post by kaivalagi on 2008-04-04
Apologies if I am explaining stuff you already know. If you want a newer version of awn than this will provide then apologies again. But I find the following to do the job nicely. No compilation required.

Edit you sources.list file to include reacocard's repository, e.g.:

```
gksudo gedit /etc/apt/sources.list
```

Then add the following lines to the bottom of the file, these will allow a apt based install:

```
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
```

Then install it through apt/synaptic. I think the following will get everything in:

```
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr
sudo apt-get install awn-core-applets-bzr
sudo apt-get install awn-manager-bzr
```

[COLOR="Red"]Important:[/COLOR] Make sure you uninstall what you currently have in place though before doing this...

Edit: This provides "Avant Window Navigator 0.3.1" etc

---

### Post by tstack77 on 2008-04-04
I tried a restart first thing without success. Compiz is installed and running. I do have AWN installed and the dock is displayed with Firefox and Terminal (which I added from the panel by a simple drag/drop). With the newer version there is an option button to install new 'AWN Applets Packages'. 

I'm lost and I'm not even sure that the tar.gz package that I downloaded before is of the correct type.

Any other ideas?

---

### Post by kaivalagi on 2008-04-04
The above repo has the install applet functionality

---

### Post by tstack77 on 2008-04-04
kaivalagi, I tried your route but I get the following error:

Couldn't find package avant-window-manager-bzr

EDIT: scratch that, forgot to update sources list

EDIT2: It still can't find avant-window-manager-bzr, then aborts

xxxx@xxxx:~$ sudo apt-get install avant-window-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-manager-bzr
xxxx@xxxx:~$ sudo apt-get install awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nautilus-actions
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr
Recommended packages:
  avant-window-navigator-bzr python-libawn-bzr python-alsaaudio
  python-libgmail python-imaging python-feedparser tsclient
The following packages will be REMOVED:
  libawn0 python-awn
The following NEW packages will be installed:
  awn-core-applets-bzr libawn-bzr
0 upgraded, 2 newly installed, 2 to remove and 2 not upgraded.
Need to get 3337kB of archives.
After unpacking 11.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by kaivalagi on 2008-04-04
my bad, try the following instead :) I'll update my previous post too in a mo

```
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr
sudo apt-get install awn-core-applets-bzr
sudo apt-get install awn-manager-bzr

```

---

### Post by kaivalagi on 2008-04-04
tstack77, You are running Gutsy right?

---

### Post by tstack77 on 2008-04-04
No, Linux mint 4. I thought that it was the same...no?

---

### Post by kaivalagi on 2008-04-04
Yep, mint 4 is 7.10 gutsy so you should be fine

In case you need to install AWN on an alternative version of ubuntu look at the following post (where I found out how to install it):

[URL="http://ubuntuforums.org/showthread.php?t=385981"]http://ubuntuforums.org/showthread.php?t=385981
[/URL]

There are also details on how to get the curved dock :) still buggy though (bad alignment of applets)

---

### Post by tstack77 on 2008-04-04
thanks, I'll try again using your link.

---

### Post by kaivalagi on 2008-04-04
Probably a good idea :)

Happy AWNing

---

### Post by tstack77 on 2008-04-04
success!

---

