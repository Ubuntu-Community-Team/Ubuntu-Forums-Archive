---
title: "[SOLVED] Help please - Gutsy upgrade failure"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by beansdad on 2007-11-04
Upgraded Fiesty to Gutsy on Acer laptop and this went without hitch. Looked good s thought I'd do likewise on desktop. Upgrade seemed to go OK until reboot. Grub loads OK and then goes to brown screen and box saying:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

View details gives:

"(process 5490): Gtk-WARNING **. This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see:
[http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)
Refusing to initialise GTK+"

It then repeats this above except with "(process 5494)" at the beginning and then goes on:

/etc/gdm/Xsession: Beginning session setup.
x-session manager: error while loading shared libraries: libgnomecanvas-2.so.0: cannot open shared object file: No such file or directory"

If I click "OK" it goes to a black screen with the timer circle thingy and nothing else happens until I switch off and switch back on when it all happens again.

If I choose recovery mode from grub I end up at a command line and seem to be able to do some things. I've tried (from other posts) to repeat the update, upgrade, reinstall sequence; reconfigure; configure - all to no avail!

I would prefer to clear this rather than do a complete fresh install of a download and burn to CD as I want to avoid having to reinstall all sorts of other stuff.

Any suggestions?

As an aside - these forums have been enormously helpful in the past and this experience has not sent me running back to the blue screen OS that I tried to use for the last 20 years. Thank heavens for Ubuntu!

---

### Post by bw44 on 2007-11-05
I am very surprised you have not had any follow-up posts to your request.

Given that it is a very specific and fairly detailed description of a problem you are having, maybe it should be posted in the "Installation and Upgrades"  forum. 

I'm not sure if you can move your post there yourself, or have to ask the forum moderator to do it; I have seen a couple of requests by other posters that their post be moved and the moderators did it.

I'm sorry I can't offer a technical solution to the problem.  Good luck.

Cheers.

---

### Post by llamakc on 2007-11-05
Create a new user and try logging in as that user. Does that work?

---

### Post by beansdad on 2007-11-06
bw44 - thanks for support. I did think I should have put it in that section and did so about an hour after I posted the thread. No suggestions there either!

llamakc - thanks for suggestion, I'll have to try and work out how to do that as the prog will only run from Recovery Mode leading to a terminal.

Ho hum - looks like I'm heading for a complete re-install of all.

---

### Post by philinux on 2007-11-06
I upgraded and found little things started to annoy me like mplayer and totem reversing roles as the best player and cdrom mounting problems etc etc.

My home is on its own partition so I thought nothing to loose, do a clean install.

So far much better, no font problems either, only thing so far bugging is divx embedded movies have a very bad video lag. 

all in all clean install.

---

### Post by llamakc on 2007-11-06
> **beansdad said:**
> bw44 - thanks for support. I did think I should have put it in that section and did so about an hour after I posted the thread. No suggestions there either!

llamakc - thanks for suggestion, I'll have to try and work out how to do that as the prog will only run from Recovery Mode leading to a terminal.

Ho hum - looks like I'm heading for a complete re-install of all.

When you are in the recovery mode and at the BASH prompt (at the command line) type this:

```

sudo adduser NEWUSERNAME

```

But before you do that, when you're in recovery mode, run this to check the disk space.

```

df -h

```

Cut/paste the results back here.

---

### Post by beansdad on 2007-11-06
philinux - thanks for that. You're probably right. I did give up on upgrades with the blue screen stuff as it never seemed to work right.

llamakc - many thanks, new user doesn't help, disk space shows 11% used on root partition of about 43Gb.

Will need to copy & retype full results but can't do that until tomorrow am.

As I can still work on laptop am not in a panic to use desktop, so would like to resolve this, even if only out of curiosity and post result should anyone else have same prob, but as am overloaded with work at present i can't spend too much time on it.

---

### Post by beansdad on 2007-11-07
OK back again. Output of df -h is:

Filesystem     Size   Used   Avail   Use%   Mounted on
/dev/sda3      42G  4.3G     35G     11%    /
varrun         502M    16K    502M     1%    /var/run
varlock        502M       0     502M     0%    /var/lock
udev           502M     76K   502M      1%   /dev
devshm       502M       0     502M      0%   /dev/shm
lre                502M    34M   468M      7%   /lib/modules/2.6.22-14-generic/volatile
/dev/sda4     77G      13G     65G     16% /media/sda4
/dev/sda1     35G     5.8G     29G     17% /media/sda1

Seems to be plenty of filespace.
I've burnt an ISO CD and this does load OK but in Safe Graphics (don't think this is relevant) and have accessed the disks which show the "libgnomecanvas" files exist and are in the same location as on the laptop.

---

### Post by beansdad on 2007-11-09
Solved by default - did a clean install from CD. Thanks to all who looked and tried.

---

