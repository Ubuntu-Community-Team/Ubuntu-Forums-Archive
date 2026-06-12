---
title: "Scared to make new kernel ..."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by baekeland on 2007-04-21
]...as it has taken me AGES to get Ubuntu 7.4 on my system.  Therefore could someone please decode the following and tell me what I need to do.  Maybe after a few run-throughs with Ubuntu I will give it a go, but at the moment I am not up to it. -- Thanks


Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.
:guitar:...as it has taken me AGES to get ununtu 7.4 on my system

---

### Post by annda on 2007-04-21
are you sure you need to do this?

if you are, check out steps 2 and 3 in this HOWTO:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

just out of curiosity, why do you want a new kernel? what is wrong?

---

### Post by Nythain on 2007-04-21
i wouldnt be to worried about making a new kernel... just dont nuke your old one and you've always got a stable back up plan... custome kernel compiling can be a great learning experience, though the rewards arent the most noticable really... possibly a wee bit faster boot time, but i havent noticed boot time to be to terribly slow on modern computers anyways... i guess the only real major benefit would be if you needed to patch in support for something not supported in the current kernel

---

### Post by Alterax on 2007-04-21
It may not be making a full-out kernel; more often the kernel source is used to make custom modules to get devices to work.  So take a deep breath, it's nothing to worry about.

The first part is to find out exactly which of the kernels you are running.

Go to a terminal window and type:
uname -r

On mine it came up with 
2.6.20.15-generic

So, once you've found out which kernel you're running, just get the source as follows:
Drop the dot,fourth number, dash and descriptor from the line (in my case, the .15-generic).
2.6.20

That tells you which kernel source you'll need.

Then you just
sudo apt-get install linux-source-2.6.20

And that's it.


--Alterax

---

### Post by baekeland on 2007-04-22
Hi All,

I thought the "problem" with my kernel went away.  I am trying desperately yo install the Emerald Themes and attempting to install  Virtualbox via Kpackage, I get the following message:

dpkg -i '///home/baekeland/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb' ;echo RESULT=$?
(Reading database ... 159659 files and directories currently installed.)
Preparing to replace virtualbox 1.3.8_Ubuntu_edgy (using .../VirtualBox_1.3.8_Ubuntu_edgy_i386.deb) ...
 * Stopping VirtualBox kernel module vboxdrv
   ...done.
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
virtualbox-puel-1-2 license has already been accepted.
Unpacking replacement virtualbox ...
Setting up virtualbox (1.3.8_Ubuntu_edgy) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Configuring virtualbox
----------------------

Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult 
/var/log/vbox-install.log to find out why the kernel module does not compile. 
Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup


as root.

 * Starting VirtualBox kernel module vboxdrv

 * No suitable module for running kernel found.

RESULT=0
 
Can someone please help me ... this seems to be getting more difficult than IBM's OS/2 Warp  :lolflag: :lolflag: 

Bill

---

### Post by baekeland on 2007-04-22
> **Alterax said:**
> It may not be making a full-out kernel; more often the kernel source is used to make custom modules to get devices to work.  So take a deep breath, it's nothing to worry about.

The first part is to find out exactly which of the kernels you are running.

Go to a terminal window and type:
uname -r

On mine it came up with 
2.6.20.15-generic

So, once you've found out which kernel you're running, just get the source as follows:
Drop the dot,fourth number, dash and descriptor from the line (in my case, the .15-generic).
2.6.20

That tells you which kernel source you'll need.

Then you just
sudo apt-get install linux-source-2.6.20

And that's it.


--Alterax

Alterax,

Thank you.  I built a new kernel and the same numbers as you displayed also displayed on mine making your commands that much more easy to follow.  But that must not be the problem because after it was done , I shut down and came back up trying to install  the Emerald Themes the same as before and again I got the posted error message which I copied and pasted.  Oh God, what a day and I do not mean Linux if that was the only thing on my mind I would have had a pleasant day .... :lolflag: 

Bill

---

