---
title: "Resolution problem - I messed it up"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by shavedchimp on 2008-02-13
Hi - in an attempt to make things a bit smaller on the screen of my laptop I changed the resolution. For example, I couldn't view the whole of a web page on the screen.

So it seemed ok until I rebooted, and now I can't use it at all. The screen is fuzzy, and I can't disitinguish any of the icons or menus clearly - in fact they seem to be duplicated.

How can I undo this?

Peter

---

### Post by drtre on 2008-02-13
ohh, seems youre in a big trouble. well i had this problem once but the way i solved it was completely by chance. well hereis how i did it:
bring up the terminal and try to type in your graphic cards' configuration panel. for example if you have nvidia type: nvidia-settings. this will bring up the panel. there you should change your settings.

---

### Post by kpkeerthi on 2008-02-13
You can reset the resolution with these commands typed in a terminal window

1. Stop GDM
```

sudo /etc/init.d/gdm stop

```

2. Reset resolution
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
*Choose the resolution(s) you need and reboot

```

sudo shutdown -r now

```

---

### Post by Crooksey on 2008-02-13
If you are having problems with X, please can you post your xorg.conf.

---

### Post by staticvoid on 2008-02-13
> **kpkeerthi said:**
> You can reset the resolution with these commands typed in a terminal window

1. Stop GDM
```

sudo /etc/init.d/gdm stop

```

2. Reset resolution
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
*Choose the resolution(s) you need and reboot:

```

sudo shutdown -r now

```

This is exactly what you need to do.  :)

When its all fuzzy and messed up hold down Ctrl + Alt + F2 and you can use a terminal (I think F1-F6 are all tty's and F7 is display:0 where X is presented, which is screwy)

good luck! this should be an easy fix :)

---

### Post by shavedchimp on 2008-02-14
Thanks everybody with your help so far

The problem I have now is that I'm not sure of the details of my laptop so I can't choose which video driver from the list - I've tried a few and also a few different resolutions and I get the same result as before - an unusable screen.

How can I find out the specifications of my laptop? - it's not clear from looking at the case or on the bottom what they are.

shavedchimp

---

### Post by kesman on 2008-02-14
Well what kind of laptop do you have? Any identification in it?

---

### Post by kpkeerthi on 2008-02-14
Type **lspci **in a terminal

---

### Post by kpkeerthi on 2008-02-14
Other commands:** lshw, hwinfo** [may need to use along with sudo for detailed outputs]

---

### Post by bigken on 2008-02-14
you could just go with the vesa driver for now this will at least get you to desktop

---

### Post by shavedchimp on 2008-02-17
I'm not getting anywhere yet.

I keep ending up at the same point with the screen unusable.

Relavant information from the bottom of my laptop:

E-System    G322 series
Via C7
EM-G320L1

I tried to choose the Via monitor and a resolution of 600, and 800 and 1280 but no joy.

At one point it said 'can't detect driver' so I tried to configure it myself but couldn't find Via in that list.

Using Vesa generic didn't improve things.

Does anybody know a method of reverting to a previous setting - to a time when everything was ok?

shavedchimp

---

### Post by shavedchimp on 2008-02-18
bump

please?

---

