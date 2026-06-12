---
title: "xview error msg"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by captmcnet on 2007-04-26
Recently acquired Ubuntu 5.04.  Installed from Install disc.  On boot up, error msg Re 'can't run xview graphical user interface'.  Right away I am confused; I thought Gnome was the graphical user interface.

Next tried to run from 'Live' CD in DVD/CD drive.  Same error msg about not being able to run xview interface.

On next boot I pressed F1 for Help; was directed to [www.ubuntulinux.org;](www.ubuntulinux.org;) and here I am.

Any assistance will be appreciated.

---

### Post by annda on 2007-04-26
is there a chance you could get a more recent ubuntu version?

edgy
[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)

and feisty (the latest)
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

they have much better out-of-the-box hardware support, which includes newer drivers for video cards (which seems to be your problem).

or you can try running this command to configure X after you log in the console:

```
sudo dpkg-reconfigure xserver-xorg
```

(i hope it works for old versions too)

---

### Post by captmcnet on 2007-04-26
Right away you zeroed in on my typo.  The error msg referred to X Server, not xview.
I will try your suggestion.
Tks

---

### Post by captmcnet on 2007-04-26
OK Annda,. I tried your code "sudo dpkg-reconfigure xserver-xorg".   Went through a long list of questions and now at the bottom of the screen is "xserver-org postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200704261855".  Followed by ubuntu@new-host-5:~$

What Now?

I also downloaded the ubuntu-6.10-desktop-i386.iso and will burn that to disc.     Maybe give that one a shot.

---

### Post by annda on 2007-04-26
> **captmcnet said:**
> "xserver-org postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.200704261855".  Followed by ubuntu@new-host-5:~$

What Now?

this is a standard warning saying that a configuration file is being overwritten and you should be careful. you should type y<ENTER> and reboot.

what happens after reboot?

---

