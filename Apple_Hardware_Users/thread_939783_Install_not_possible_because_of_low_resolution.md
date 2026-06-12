---
title: "Install not possible because of low resolution"
date: 2008-10-06
forum: Apple Hardware Users
---

### Post by simon486 on 2008-10-06
Hi there

I try to set up my ibook 750mhz G3 with xubuntu 6.06 and get a problem with the install-wizzard. The screenresolution is too low to display the whole wizzard window and that's why i can't see the "continue" button to get throu the whole process. I tried to move the window around or to make it smaller but nothing is working. What can i do? is it possible to install the driver of the screen or is there any possiblitiy to install the os in the console mode?
Thanks for every hint!

Simon

---

### Post by stream303 on 2008-10-06
It's been awhile since I ran across this, but have you tried holding down either the control, alt, or command key (I forgot which one), and left click/hold on the window to move it so you can force it to see the continue button?

On some laptops, I've needed three hands to do this. :)

---

### Post by cyberdork33 on 2008-10-06
clicking anywhere on a window while holding alt should allow you to move that window around on the screen.

---

### Post by joninkrakow on 2008-10-07
> **simon486 said:**
> Hi there

I try to set up my ibook 750mhz G3 with xubuntu 6.06 and get a problem with the install-wizzard. The screenresolution is too low to display the whole wizzard window and that's why i can't see the "continue" button to get throu the whole process. I tried to move the window around or to make it smaller but nothing is working. What can i do? is it possible to install the driver of the screen or is there any possiblitiy to install the os in the console mode?
Thanks for every hint!

Simon

I had this problem with an earlier version of Ubuntu. Back then, in order to fix my screen resolution, I had to type the following into a terminal window:

```

sudo dpkg-reconfigure xserver-xorg

```

It pops up a commandline program. Simply go through the entire process for keyboard, etc. until you get to the display part, and make sure that your native resolution is selected among the options, and go and finish the program. When done, log out, and log back in, and you should have your full resolution. Once there, you can install.

I don't remember, but you may have to do this once again once you install and are running from your hard drive.

One last caveat. It may not work on later versions of Ubuntu.... I can't remember.

-Jon

---

