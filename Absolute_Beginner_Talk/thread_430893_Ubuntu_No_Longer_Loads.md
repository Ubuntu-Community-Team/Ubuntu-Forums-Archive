---
title: "Ubuntu No Longer Loads"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by jackmorelli on 2007-05-02
Hi Everyone,  I am a beginner attempting to learn me some linux, i have a 250 gb computer partitioned between windows vista and ubuntu.

I had Ubuntu working, with KDE, but was having some problems loading my nVidia drivers.  Got that figured out.  Installed Beryl.  Got that figured out.  Everything was great.  

I then attempted to load vnc server using a couple of commands, and before that installed ssh protocol.  i have no idea what ssh does, or whatever.  well, when i tried to log in remotely from my other windows machine, it only showed a gray screen with an X mouse cursor that moved, but nothing happened on my ubuntu machine.  i figured i would restart my ubuntu machine and see what that did.

well, when i rebooted my X server, my computer flashed my nVidia screen, then a black screen with the "thinking" cursor, it paused, flashed my nVidia screen AGAIN (never happened before), then a black screen with the "thinking" cursor, and now it just sits there waiting for ever.

I deleted a couple of random lines at the bottom of my sources.list file relating to beryl, and also replaced my xorg.conf file with 3 different backup files (in turn) that i knew i had working before, all to no avail.

Can anyone help me?  much love, and thanks for letting us windows users explore cooler, and free-er os's.

---

### Post by viciouslime on 2007-05-02
Try deleting the xorg.conf file completely. Ubuntu is supposed to be able to generate a new one when it's missing.... i think.

---

### Post by viciouslime on 2007-05-02
Failing that try running:


sudo dpkg-reconfigure -phigh xserver-xorg

:)

---

### Post by octoberdan on 2007-05-02
> **viciouslime said:**
> Try deleting the xorg.conf file completely. Ubuntu is supposed to be able to generate a new one when it's missing.... i think.

Deleting configuration files is almost never a good thing. Instead, rename it
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.config.bk_bad

```

---

### Post by viciouslime on 2007-05-02
> **octoberdan said:**
> Deleting configuration files is almost never a good thing. Instead, rename it
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.config.bk_bad

```

Yeh good point, always a good idea to have a back-up!

---

### Post by jackmorelli on 2007-05-03
moving xorg.conf worked perfectly.  thanks a ton!

---

