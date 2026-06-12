---
title: "runit 1.3.1 install 'failure'"
date: 2006-03-05
forum: Bug Reports / Support
---

### Post by mderouss on 2006-03-05
Hi folk, I'm a Ubuntu newbie ( though not a complete Linux newbie... ) just trying to find out why I seem to have borked my Ubuntu ( 5.1, Breezy Badger ) installing this backport.  

By 'borked' I mean that Ubuntu completes runit's stage 1, but hangs at runit's 'stage 2'. I do not get a login prompt. However, runit still responds to CtrlAltDel, shuts down everything it has started, and then powers the system down. Thus it appears that runit stage two may not have been correctly configured.

A little background - I'm only trying to install this in the first place because [Webcleaner]("http://webcleaner.sourceforge.net/install.html") lists it as a dependency ( although I suspect it's really more of a would-be-nice ), and I want to run Webcleaner.

Firstly, I tried to follow the instructions [here]("http://backports.ubuntuforums.org/wiki/index.php/Main_Page") to give me access to backports. Infact, I discovered that /etc/apt/sources.list contained instructions for this purpose too. The URL specified in /etc/apt/sources.list for backports was different to that on the backports page - [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) as opposed to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu). 

However, with either of these URL's, when I fired up Synaptic there were a variety of complaints such as 'could not stat...' etc etc. Eventually I just ignored these, looked at the list of packages, found that runit and a related package were present,  and asked Synaptic to install them.

This did not go entirely smoothly, as the install appeared to stall on a couple of occasions. I'm not sure what I did now to overcome this. Anyway, I was eventually presented with terminal output that told me that the installation was successful and that I should restart my system by entering something like 'initsysv 6', which I did.

The system went down to a login prompt, and seemed to be going no further. I hit CtrlAltDel, and got as far as described above. 

Any clues as to :

1. Whether the system as it stands is recoverable ?
2. Where did I go wrong ?

---

