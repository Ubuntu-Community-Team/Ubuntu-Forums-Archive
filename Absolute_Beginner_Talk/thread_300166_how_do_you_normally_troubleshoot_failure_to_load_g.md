---
title: "how do you normally troubleshoot failure to load gui?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by at0mic on 2006-11-15
hi,

last night i installed something i shouldnt have [a desktop accelerator] and when i next booted it failed to load the gui xubuntu and dropped me to command line. i thought to myself to remove the accelerator and its dependancies but didnt work. i next tried to reinstall the xubuntu desktop via apt-get install xubuntu-desktop but it said its already installed [ is there a reinstall cmd?] so i then installed ubuntu desktop to overwrite the current, and it failed load BUT told me i should look at the xconf.cfg file... i read it and it said it failed to load the nvidia driver. so i reinstalled the nvidia driver via script envy which worked great.... so i take it reading the xconf is always the first step? how should i have reinstalled the xubuntu desktop this case?

---

### Post by bulldog on 2006-11-15
In most cases when X-server fails the following command is the first thing to use,to reconfigure xorg.conf.
```
sudo dpkg-reconfigure -phigh  xserver-xorg
```

---

### Post by joshsherman on 2006-11-15
About reinstalling

```

apt-get install xubuntu-desktop --reinstall

```

you have to use it in combination with the action.

-j

---

### Post by lazyart on 2006-11-15
I would've first:

sudo dkpg-reconfigure xserver-xorg 

That, followed by startx would get you into the gui.  From there, edit xorg.conf or reinstalling via envy would work.

---

### Post by at0mic on 2006-11-15
thnx for the tips guys. ill know for next time.

---

### Post by bodhi.zazen on 2006-11-15
Usually X will print some error messages to the terminal. I start by reading and correcting those.

If that fails I look at the log files.

---

