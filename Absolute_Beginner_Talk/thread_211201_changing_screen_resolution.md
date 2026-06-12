---
title: "changing screen resolution"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by PsychicPsycho3 on 2006-07-07
Greetings,


I'm on a Dell Inspiron 8200 and Ubuntu is defaulting my monitor 1600x1200 resolution. Easy enough to change, I thought, except when I put it to the desired 1024x768, it shrinks my screen size as well. That is to say, there's a larger black square behind a tiny square that is the display. If it were a CRT I could (I think) just use the menu to resize it, but I'm on a laptop, so that's not an option. I think I might need to install a monitor driver, but I'm not sure where I would get or install that.

TIA for any help!

---

### Post by KrisDwyer on 2006-07-08
I had the same problem mate, So i know how u feel. It seems to be an Ubuntu problem.

---

### Post by raldz on 2006-07-08
Have you tried reconfiguring your xsrever-xorg to properly identify your hardware? Try this command on the terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

before you do that you may want to back up your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

if xserver won't load after reconfigure, just restore your backup file:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

hope this helps..

---

### Post by indijay on 2006-07-08
Read [http://www.tazforum.thetazzone.com/viewtopic.php?t=2189](http://www.tazforum.thetazzone.com/viewtopic.php?t=2189) carefully.

Solved issue of my HP machine with ATI card

---

### Post by Burritos on 2006-07-08
that sounds like an 'issue' with the laptop, not the OS.

I think you need to press the function key (fn) and then press F5.  If fn-F5 doesn't do it, try fn-F7...it might even be a different FKey but I'm pretty sure on the Dells, it's either F5 or F7.

---

