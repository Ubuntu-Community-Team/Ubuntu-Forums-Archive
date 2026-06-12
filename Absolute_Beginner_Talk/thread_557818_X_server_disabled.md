---
title: "X server disabled"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-09-23
Hey.

I've been trying to get a game called Dwarf Fortress to work under Linux.  According to the game's wiki, it's very simple to run with Wine, but I've been having terrible problems with it.  Among other things, every time I quit the game I would be “logged out” of Ubuntu and forced to log in again, which is very unusual behavior.

Over at the Dwarf Fortress forum I've gotten quite a lot of good advice, but we still haven't quite solved the problem yet.  One of the posters there suspected that my problems with Wine stemmed from Wine issuing a command line whenever I exited, causing Xserver to crash.  He suggested I do the following:
> sudo apt-get remove xserver-xorg
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get install xserver-xorg 
I followed his instructions, but upon rebooting, Ubuntu couldn't quite restart correctly.  After loading, the screen went black, and then I received the following error message: 
> Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to review the X server output to diagnose the problem?

Yes		No

I select yes.  A short list of information about the OS pops up, followed by:
> (==) log file: “/var/log/xorg.0.log,” date and time
(==) using config file “/etc/X11/xorg.conf”
Data incomplete in “/etc/X11/xorg.conf”
At least one device section is required
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal Server Error: no screens found

OK
I read this as meaning that for some reason the download xorg.conf file didn't contain a device section in the text.

I select okay, and Ubuntu asks:
> Would you like to view the detailed X server output as well?
I must say, it's a very polite operating system, at least.

If I select yes, I get a second report similar to the one above, accept that it also includes three warnings (WW): KDSETMODE, VT_GETMODE, and VT_GETSTATE all have bad file descriptors.  Finally, I get the following message:
> The X server is now disabled.  Restart GDM when it is figured correctly.

OK
After the final okay, I find myself looking at text screen with a blinking cursor.  There's a list of programs that have started up, and also a warning that probably isn't related to this issue at all, but just for the sake of completeness: 

WARNING: Dazuko module is not loaded, please insmod dazuko module.

This is all white text on black background.

So my question is: now what do I do?

---

### Post by PmDematagoda on 2007-09-23
What VGA card do you use?

---

### Post by Mr. Svinlesha on 2007-09-23
Uhhh.... VGA card?

If by that you mean graphics card, then it's an nVidia FX 5200.

---

### Post by PmDematagoda on 2007-09-24
Regonfigure X by-

```
sudo dpkg-reconfigure xserver-xorg
```

After that try starting X using:-

```
startx
```

---

