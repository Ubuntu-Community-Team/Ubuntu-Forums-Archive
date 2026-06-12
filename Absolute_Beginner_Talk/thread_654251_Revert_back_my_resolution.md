---
title: "Revert back my resolution"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Jeeverz on 2007-12-30
I was messing around with my resolution while attaching another monitor, and now my ubuntu would not go pass the login screen(which is massive due to the low resolution).
Is there a way i can default my resolution back to what i had before ?

---

### Post by MillDaKill on 2007-12-30
> **Jeeverz said:**
> I was messing around with my resolution while attaching another monitor, and now my ubuntu would not go pass the login screen(which is massive due to the low resolution).
Is there a way i can default my resolution back to what i had before ?

if you hit ctrl + alt + f2 you will bring up the virtual console and you can restore the default xorg.conf file in /etc/X11 .  If that does not make sense let me know and I can walk you through the process. Once you make the update you can get back to the gui by hitting ctrl + alt + f7.

---

### Post by drolex on 2007-12-31
Can you walk me through that restore process, please? I'm on a laptop and I misunderstood the second motitor option. I selected a resultion for a second monitor, which I don't have, then it told me it needed to log out, so I logged out which just restarted the computer and it only boots into tty1. When I type gnome-session it says (gnome-session:4749): Gtk-WARNING **: cannot open display. Hopefully resoting the default configuration with this file will solve the problem.

---

### Post by forestpixie on 2007-12-31
first you need to work out what the xorg.conf backup is named

```
ls /etc/X11/xorg*
```

one will ne named xorg.conf - that is the working one. you should have backups - once you know which is the last working one you can replace them

```
sudo mv /etc/X11/nameofbackup /etc/X11/xorg.conf
```

obviously replace nameofbackup with the xorg backup file you've found

if you're still not sure post the output you get from the ls command

---

### Post by drolex on 2007-12-31
Thanks. I solved it before your post, but your post would have been helpful in getting my back to where I was.

Here is what I did:
Run "sudo dpkg-reconfigure xserver-xorg"
I selected auto and left or selected all the preset answers except for the resolution/frequency section. It finished and when I restarted it booted up like normal except now my resolution is the correct 1440x900 instead of 1024x726 or whatever (without better options).

---

### Post by forestpixie on 2007-12-31
it's always nice to be able to get there yourself I think :)

sudo dpkg-reconfigure xserver-xorg - is a nice command to remember

---

### Post by Jeeverz on 2008-01-05
Thanx for the help i got it working !!

---

