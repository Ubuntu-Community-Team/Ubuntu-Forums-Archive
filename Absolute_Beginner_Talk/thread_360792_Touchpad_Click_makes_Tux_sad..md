---
title: "Touchpad Click makes Tux sad."
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-02-13
I swear, I hate this stupid touchpad click. I'm trying to do something and I accidentally click on something I don't want to click on and then I get angry and start screaming and rolling around on the floor and punching the ground.

Simply, how do I get rid of this crap?

---

### Post by Bachstelze on 2007-02-13
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

This will let you configure your touchpad correctly, and install a program to control it more precisely (which includes disabling the "tapping").

---

### Post by Baelfael on 2007-02-13
Theres a problem already.

When I put in gksudo gedit /etc/X11/xorg.conf, It returns the message:

```
(gedit:23847): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by annda on 2007-02-13
try sudo instead of gksudo - i know it's not correct, because you SHOULD be gksudo'ing for gnome applications, but gedit is strange sometimes with that.

anyway, i would recommend making sure that you have "synaptics" as you driver in xorg.conf first. then add the  SHMConfig option (try "true" instead of "on").

then install gsynaptics and configure your touchpad easily using gui.

---

### Post by Baelfael on 2007-02-24
Alright. It seems I just can't edit xorg.conf. It just won't let me. I went into the file system using the GUI, and it looks like it's a read-only file. How do I do this? The link provided says to edit it using the gksudo command and whatever. Not working.

---

### Post by mgmiller on 2007-02-24
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by MrKlean on 2007-02-24
I have no trouble editing mine with..........   sudo gedit <filename>

---

### Post by Baelfael on 2007-02-24
> **mgmiller said:**
> ```
sudo gedit /etc/X11/xorg.conf
```
When I do that the command line just sits there, unresponsive.

---

### Post by Dracar on 2007-02-24
um i use synapts touchpad or watever, i havent noticed nething yet, then i am currently running ubuntu on a vm, do you think i will have troubles with it?

---

### Post by Baelfael on 2007-02-24
> **Dracar said:**
> um i use synapts touchpad or watever, i havent noticed nething yet, then i am currently running ubuntu on a vm, do you think i will have troubles with it?
I don't know. That's what I'm trying to get working.

---

### Post by linux_kid on 2007-02-24
So the sudo gedit /../../xorg.conf isn't working?

Try logging in as root [-( and then typing the command.

---

### Post by irish_flu on 2007-02-24
> **Baelfael said:**
> When I do that the command line just sits there, unresponsive.

Does it die before it asks for your password, or after you've entered it?

---

### Post by mgmiller on 2007-02-24
are you sure you're entering the command correctly?  Just do a copy paste from the forum thread into a terminal.

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Baelfael on 2007-02-24
> **irish_flu said:**
> Does it die before it asks for your password, or after you've entered it?
After I enter the password.

And mgmiller, I copy and pasted and still the same thing.

---

