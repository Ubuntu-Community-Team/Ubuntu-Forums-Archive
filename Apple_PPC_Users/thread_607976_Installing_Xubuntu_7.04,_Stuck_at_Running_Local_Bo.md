---
title: "Installing Xubuntu 7.04, Stuck at Running Local Boot Scripts"
date: 2007-11-09
forum: Apple PPC Users
---

### Post by apjent on 2007-11-09
Hello,
I am having difficulties starting Xubuntu 7.04 after installing from the alternate disk. the last line i get is "Running Local Boot Scripts ... ok."

if i hit enter, i get a login prompt where i am able to login ok at the shell prompt.

I have read many of the other threads about people hanging on this line, but most sound like they are having problems getting the tty prompt.

I am not familiar with starting the GUI.. what would i do to finish the installation?
Should it generally open something graphically automatically when booting for the first time?

So far i've installed the xubuntu 7.04 via the alternate cd onto my beige G3 All-in-one with 192 mb ram.

Any help is appreciated.
Much thanks,
Aaron

---

### Post by peege on 2007-11-10
I'm having the same problem; anyone have any solutions?

---

### Post by peege on 2007-11-12
Anyone? Bueller?

---

### Post by pxwpxw on 2007-11-13
If you got a login and command line -

To see if you have X windows
```

startx

```
and note what happens.

And/or run
```

df -h

```
to see the installed system size - less than 1GB is probably no desktop.

To install a desktop
```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```
(or ubuntu kubuntu ... )

---

### Post by doronz on 2007-11-19
Hi,
Thanks for the reply but I dont get any command prompt.
The installation just gets stuck at this point and the only thing I can do is a restart.

any other solutions?

Thanks

---

### Post by nise8181 on 2008-04-21
Hm, I am having the same problem after transfering one hdd with an installed xubuntu 7.10 to another mashine without network connection and cd-rom or usb-boot ability.

has anyone a solution? or just a hint?

---

### Post by stream303 on 2008-04-21
Definitely keep these faqs handy - it may not solve all problems, but is a good guide even if it doesn't pertain to your problem immediately at hand:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

With Hardy-release so close at hand, some of these solutions may no longer be necessary, or possibly be modified.

Transferring a hard drive from one machine to another will usually involve resetting the nvram/pram, and perhaps an smu/pmu reset, (since apples like to be notified of major hardware changes) along with rebooting into a rescue mode, and modifying your /etc/yaboot.conf file among others.  You may also run up against the 8GB partitioning limitation if you are using a very early G3 iMac etc.

I guess it can be done, but I think the best bet is to install onto the disk once it is in the machine proper.

A good place to gather up some hardware info can be found here:
[http://www.everymac.com/](http://www.everymac.com/)

You may also have better luck installing the Ubuntu "alternative" Feisty, and then performing an install for xubuntu-desktop afterwards.

With the repositories changing, and the Hardy-release imminent, hang in there in case things get a little strange.

---

