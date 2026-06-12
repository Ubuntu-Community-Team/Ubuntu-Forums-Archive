---
title: "[SOLVED] xfce4-terminal causes log-out"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2008-03-24
Hi Folks,

**Xubuntu 7.10**

When I run *xfce4-terminal* it reacts the same as if I did a *[Ctrl]+[Alt]+[Backspace]*.

Obviously I am now not using it as the default terminal, I have gnome-terminal installed for this.

But this error puzzles me, and I'd like to see it working so I can use it as the Default terminal package as I think it is supposed to be in Xubuntu.

Thanks
Bruce

---

### Post by Bruce M. on 2008-03-24
gladstone in another thread pointed out the answer.

The problem seem to exist for people that have an Intel motherboard using the on-board video (card?).

The answer is in [Bug #91849 in xorg-server (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849"), specifically by Jim Campbell (about half way down)

Quoted here:

>  Jim Campbell  wrote on 2007-06-13:  Re: [Bug 91849] Re: i810 + xorg = xfce crashes when opening terminal  (permalink)

Hi Morgan,

I think that this fix has worked for a few people:

As for X crashing when you open the terminal, I recommend the following:

To do this, you'll need to boot into an xterm session, so when the login
screen comes up, click on the Sessions icon, and select Terminal session or
something similar.
This will bring you into an xterm session - not an xfce4-terminal. It
should work. :)

* use the "cd" command to navigate to your /etc/X11 folder and make a backup
copy of your xorg.conf file. You can do this by entering:
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup

* edit your xorg.conf file, changing the default depth from 24 to 16. You
can
do this by entering:
sudo nano xorg.conf
. . . then scroll down to the Screen section, and find the DefaultDepth
option. Change that number to 16.

*press control-o (letter "O") to save the file, then press control-x to exit
the nano text editor.

Then exit from the xterm session, and it should bring you back to the login
window. Select an Xfce session from the session button, and proceed to login
as usual.

I hope this helps! Sorry it is kind of a non-pretty way to do things, but
it's hard to tell you to enter these changes into a regular terminal when
the
regular terminal crashes your X session! I think that this should work,
though . . .
Let us know if it doesn't work. Thanks!

Jim

Hmmm, Intel Motherboard.

Sorry to have bothered you, but maybe this will help others as well.

Have a great day folks
Bruce

---

### Post by OptikKnight on 2008-03-24
Reiterating Bruce's point:

I saw this same behaviour with my cheap eMachine when I installed Xubuntu 7.04

Quoting Bruce's bug reference: "changing the color depth in xorg.conf from 24 to 16 fixed the problem." ... This worked for me also, but I don't know if it's been fixed yet in the drivers.

Good luck.

---

