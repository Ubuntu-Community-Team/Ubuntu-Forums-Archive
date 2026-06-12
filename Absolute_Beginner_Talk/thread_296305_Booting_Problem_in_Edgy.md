---
title: "Booting Problem in Edgy"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by icelechi on 2006-11-09
Hi everyone,

I just installed Edgy and it looks great. I have one problem though: When, starting up, after it has gone through loading all the different things, it freeezes with a cursor at the upper left corner of the screen.
Is there anything I can do about this?

If it is any help, I use a Thinkpad T22 with 256MB of memory and a 900MHz Pentium 3 processor.

Thanks.

---

### Post by taurus on 2006-11-09
So the GUI login screen never comes up!  If that's the case, then you need to reconfigure your X again.  Boot to recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```

---

### Post by bulldog on 2006-11-09
Just wait for a minute and if nothing happens try to CTRL-ALT-F1 to see if you can open tty1.
If so try startx or sudo /etc/init.d/gdm start

---

### Post by icelechi on 2006-11-09
> **taurus said:**
> So the GUI login screen never comes up!  If that's the case, then you need to reconfigure your X again.  Boot to recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```

Ok. I am yet to try this but just so I know what it going on, will this automatically reconfigure X or do I have to type some more stuff in?

---

### Post by taurus on 2006-11-09
It will ask you a few questions about your video card, your monitor, you keyboard layout, mousse, etc.  If you are not sure about something, just use the default settings, hitting the return key...

---

### Post by icelechi on 2006-11-09
> **taurus said:**
> It will ask you a few questions about your video card, your monitor, you keyboard layout, mousse, etc.  If you are not sure about something, just use the default settings, hitting the return key...

Sorry about the time lag. Had things to tend to. I'll give it a shot.
Thanks for all your help!!!:-D

---

### Post by ishift on 2006-11-09
i had the same problem:

[http://ubuntuforums.org/showthread.php?t=291769](http://ubuntuforums.org/showthread.php?t=291769)

hope that helps!

---

