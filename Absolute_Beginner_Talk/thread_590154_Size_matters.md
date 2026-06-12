---
title: "Size matters"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Splat! on 2007-10-24
I've seen some of the problems others are having with
7-10 and decided to take the plung anyway. I've just
pulled together a machine from old part (600MHx
CPU, 512 RAM, 16G & 20G HDDs). If 7-10 doesn't
work for me I've got 6-06 on CD that I can go back to.

Anyway, I'm wondering about partitioning sizes (my
gPartEd CD is active right now). I'm figuring to set
up the 16G as SDA1 with 1G /swap, 6G root & the
rest as /tmp. The entire 20G HDD (SDB1) would be
/home.

Sound workable?

Splat!!

---

### Post by Inxsible on 2007-10-24
Seems reasonable. Although I am not sure you need a separate tmp drive. I dont have one. Maybe you have other reasons to mandate a separate tmp partition.

Whatever works for you ! :)

---

### Post by kebes on 2007-10-24
If I'm reading your plan correctly, you intend to allocate 9 Gb for the "/tmp/" directory? Is there a specific reason you are doing that? On my system, the /tmp/ directory doesn't accumulates less than 1 Mb of miscellaneous data.

Unless you have a specific need for a very large /tmp/, I think it makes more sense to allocate that space for the root partition or for a secondary storage area. (Or perhaps set it as /var/ if you're running websites that will be stored in /var/www/ ...)

---

### Post by Splat! on 2007-10-24
Thnx for the info. I got things a bit backwards. the 20G is the
master drive, 16Gthe slave.

I'm setting up a 6G root as HDA1, 1G /swap as HDA2, and
will use HDA3, 12G, as /var as I think setting up a website
in Linux will be an educational experience for me.

 HDB1 will be 8G home and HDB2, 7.8G, will be /downloads.

---

### Post by kebes on 2007-10-24
> **Splat! said:**
> Thnx for the info. I got things a bit backwards. the 20G is the
master drive, 16Gthe slave.

I'm setting up a 6G root as HDA1, 1G /swap as HDA2, and
will use HDA3, 12G, as /var as I think setting up a website
in Linux will be an educational experience for me.

 HDB1 will be 8G home and HDB2, 7.8G, will be /downloads.

Yeah, that sounds like a good allocation to me. Have fun!

---

### Post by Splat! on 2007-10-24
So now I have 2 questions ---

How do I set HDA1 as the "active" partition in gPartEd?

and

Is it proper to set (MS-DOS) partition labels using
gPartEd (i.e., designate /, /swap, /var, /home and
and /downloads) ?

Splat!

---

### Post by kebes on 2007-10-24
> **Splat! said:**
> How do I set HDA1 as the "active" partition in gPartEd?

First off, is there any reason you are using gPartEd? I mean, if you're planning on formatting the entire disk anyway, you can just run the Ubuntu installer, and when you get to the partitioning phase, you select "manual" and select the partition sizes (and associate them with directories like root or /home/ or whatever). It will automatically do all the formatting, set the partition active, and install the boot loader.

It's been awhile since I've used gPartEd, but I think there is an option in the menu for changing the "flags" for a partition. Then check the "boot" flag.

> Is it proper to set (MS-DOS) partition labels using gPartEd (i.e., designate /, /swap, /var, /home and and /downloads) ?

Those labels won't hurt, but I don't think they have any effect. During the installation of Ubuntu, you will tell it what to assign for each partition. It then stores the information about the root partition into the boot-loader, and stores information in your Linux install about how to mount the other partitions (as /var/, /home/, and so on).


So, in short, you just have to make sure that you pick the things you want during the partitioning phase of the installation (by selecting 'manual partitioning').

---

### Post by Splat! on 2007-10-24
I'm using gPartEd because it's all I have that will
format "non-M$". Being a Linux nooby, I wasn't
sure what to expect during install so was just
prepping things as much as possible.

In gPartEd I did manage to identity the root
dir using "manage flags" on HDA1 & setting
the "boot" flag. Apparently it worked as 7-10
knew where I wanted the root when I started
the install.

Problem I DID have, tho, was during the 7-10
partitioning phase. I chose manual in order to
keep the config & sizes I wanted but it wouldn't
recognize the swap partn named as either 
/swp or /swap.

Maybe that's why the install is taking so long -
it thinks there's no swap partn. It's been stuck
on "configuring system" for quite some time now.

Splat!

PS - I'm truly impressed with the rapid responses
provided in these forums. Thanks to all the admins
for excellent work.

---

### Post by kebes on 2007-10-24
> **Splat! said:**
> Problem I DID have, tho, was during the 7-10 partitioning phase. I chose manual in order to keep the config & sizes I wanted but it wouldn't recognize the swap partn named as either /swp or /swap.

During the partitioning phase, you should not assign the swap partition as "swap" ... rather, you should select the option for "partition type" and set that to "Linux swap" (instead of ext3 or whatever), and let the installer format that as a swap partition.

The swap is special, and doesn't have a directory location.


> Maybe that's why the install is taking so long - it thinks there's no swap partn. It's been stuck on "configuring system" for quite some time now.
In principle, Linux should be able to run without the swap, but unless your system has a lot of RAM, then you're going to want to go back and make sure you create a real swap partition. You can cancel the install and go back through it.

---

### Post by Splat! on 2007-10-24
Thnx again, kebes.

The install stalled at 81% while doing the "target system configure".
I tried running it again and get to the desktop but can't go anyplace
from there so I suspect it is "shifting" to what has been installed on
the HDD.

Guess it's time to format the root partn and go from there. I'll give
the straight install one more try, tho, before I go that route.

Splat!

---

### Post by kebes on 2007-10-25
> **Splat! said:**
> The install stalled at 81% while doing the "target system configure".

If a fresh install also stops during the configuration phase, you could try using the "Alternate" install CD. It's a text-based installer for Ubuntu (available from the Ubuntu site). I vaguely recall someone telling me that their installation was stalling at a certain point, but that the alternate CD worked fine.

---

### Post by Splat! on 2007-10-25
kebes, your insight and knowledge have made things much
easier for me. The install went smoothly, especially after I
found how to designate the swap area. Got my PPPOE up
and running in jig time. All devices properly recognized and
working.

Next up, security (firewall, AV, etc) and tying in to my
local network. Then I can start thinking about adding
apps and putting this thing to work.

One thing that has had me buffaloed so far, tho, is
that blankety-blank Synaptic package manager. Tried
to upgrade FireFox while on v6-06 and got no place.
Updates manager didn't help much, either.

There's a lot I have to learn about Linux and Ubuntu.
It's gonna be fun. Think I might try using KDE with
Ubuntu and see how it feels. Adventurous cuss,
aren't I?

:biggrin:

Life's a hoot.

Splat!

---

### Post by kebes on 2007-10-25
> **Splat! said:**
> kebes, your insight and knowledge have made things much easier for me. The install went smoothly... All devices properly recognized and working.
Excellent! Glad you got it working... now the real fun starts!

> Next up, security (firewall, AV, etc)
Linux doesn't usually need any Anti-Virus software. (There are basically no know Linux viruses in the wild.) You can still install an anti-virus package if you want (such as ClamAV), but that's mostly for detecting Windows viruses (useful if you're running a file server that Windows users might access).

As for firewall, Linux has a built-in system called "iptables" that acts as a firewall. Ubuntu is quite secure by default (very few applications are 'listening'), so there's usually nothing more to do. If you want to be more secure, you can install an application called "Firestarter" which gives you a GUI interface for controlling the Linux firewall (and by default activates a more secure "default deny" policy).


> One thing that has had me buffaloed so far, tho, is that blankety-blank Synaptic package manager. Tried to upgrade FireFox while on v6-06 and got no place.
Using a package manager may seem strange at first, but once I got used to it, I loved it! Instead of worrying about updating all your various applications, one command can do it all!

Sometimes relying on the repositories can mean that you're not getting the latest features (though you will always be getting the latest security patches). So, yeah, on Ubuntu 6.06, the repositories don't have the latest Firefox or Thunderbird. But if you wan the latest apps then you should use the latest Ubuntu instead of the LTS release (which is designed to be super-stable).


> There's a lot I have to learn about Linux and Ubuntu. It's gonna be fun. Think I might try using KDE with Ubuntu and see how it feels. Adventurous cuss, aren't I?
Being adventurous is a good thing! And it's what Linux is all about... you have the freedom to change anything you want. So enjoy it.

Oh, and by the way, I prefer KDE over Gnome, so it's worth giving both a try until you decide which one is best for you. (You can install KDE by looking for "kubuntu-desktop" in the package manager, and then you'll have the option of which desktop environment you want to use each time you login.)

---

### Post by Splat! on 2007-10-25
I sorry I wied. 

:cry:

I said all devices were properly recognized. How in the 
heck do I get Ubuntu to recognize my simple 3-button 
rollerball Logitech mouse so I can config the buttons?  
I miss the double-click on the center button.

All it says in the device manager is "PS2 Mouse".
Mouse preferences has nothing about buttons 
except left-handed mouse.

Splat!

---

### Post by kebes on 2007-10-25
> How in the heck do I get Ubuntu to recognize my simple 3-button rollerball Logitech mouse so I can config the buttons? 

This might help:
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by Splat! on 2007-10-25
Sorry, kebes. Doesn't look like anything there applies to my case.
It all calls for the use of imwheel which appears to be for use with
"rollerball" mice. Mine is just a simple 3-button, PS2, ball-activated
(versus optical) mouse.

BTW, I tried modifying the mouse config files in /etc/X11 but when
I tried to save the changes I got a message saying I don't have
permissions to make such changes. I went to the users & groups
area and set all permissions for my user name. No difference.

(Could not save file /etc/X11/imwheel/startup.conf
You do not have the permissions necessary to save the file
Please check that yoyu type the location correctly and try again)

Logitech doesn't recognize either the model number or the
part number (I have 3 such meeses) and Google is no help
either.

Hard to break old habits but I might have to use a different moose
if I can't figure this one out.

Splat!

---

### Post by kebes on 2007-10-25
> **Splat! said:**
> Mine is just a simple 3-button, PS2, ball-activated (versus optical) mouse.
In Linux/UNIX, the middle mouse button by default has certain actions associated with it (like if you select text and middle-click it pastes it). I know you can change the behavior of that button for various actions (like clicking it on the desktop)... but I gather you want it to have a system-wide shortcut (specifically, double-clicking)?


> BTW, I tried modifying the mouse config files in /etc/X11 but when I tried to save the changes I got a message saying I don't have permissions to make such changes.
The files in /etc/ are important system files, so to modify them you need administrator access. There is a terminal command called "sudo" that lets you do this, and the graphical version of it is "gksudo." So if you want to use a program (say gedit) in admin mode, then open up a terminal or the run dialog (Alt+F2) and type:
gksudo gedit

It will ask you for your admin password. Be careful using sudo! Normally you are protected from breaking your system, but when you use sudo/gksudo, you can modify important system files! (It's usually a good idea to make a backup of a file before changing it, just in case the change doesn't work.)

---

### Post by lpevey on 2007-10-25
This doesn't relate to the mouse question, but you can apply labels to your partitions using, if I remember correctly, e2fsprogs (for ext3 partitions) and ntfsprogs (for windows partitions).  Once you install those packages, type 'man e2label' and man 'ntfslabel' for options.

---

### Post by arpanaut on 2007-10-25
Here's a couple of links that will help you out, the first has some very useful information I use ALL the time. 
the second gives some explanation of how the whole sudo thing works.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Splat! on 2007-10-28
> **arpanaut said:**
> Here's a couple of links that will help you out, the first has some very useful information I use ALL the time. 
the second gives some explanation of how the whole sudo thing works.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Excellent sources. I've bookmarked them for future use.

*Danke* and *domo arigato*.

Splat!

---

