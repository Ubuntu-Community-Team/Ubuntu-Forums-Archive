---
title: "/etc/init.d/cupsys"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by BobSongs on 2005-12-03
Greetings!

Question. If the file /etc/init.d/cupsys is copied to /etc/init.d/cups, would this pose any security problems?

I'm putting together a 'how-to' for installing a printer driver. However it only seems to work if the file 'cupsys' is called 'cups'. Otherwise it returns a number of errors.

Thanks!

Bob

---

### Post by gord on 2005-12-03
i wouldn't of thought so, allthough it might be better to make a symbolic link, that way anything that requires cups gets the right thing and anything that wants cupsys gets it too.

---

### Post by BobSongs on 2005-12-03
[QUOTE=gord]i wouldn't of thought so, allthough it might be better to make a symbolic link, that way anything that requires cups gets the right thing and anything that wants cupsys gets it too.[/QUOTE]

Thanks!

Uhm. I come from Win/DOS and symbolic links are a complete mystery to me. What code would be used to create a symbolic link? The current code in the instructions is:
```
sudo cp /etc/init.d/cupsys /etc/init.d/cups
```

I'll need my hand held for this one.

Thanks, Bob

---

### Post by gruepig on 2005-12-03
What do you mean by "It only works if the file is called cups"?  This doesn't make any sense to me.  What are the errors you are getting?

There are no security implications to renaming, copying, or linking.  However, any changes you get could get overwritten when the cupsys package gets upgraded.  

To create a symlink, run 'ln -s <real file> <symlink>'.  So to link cups to cupsys, 'ln -s cups cupsys'.

(Also, if you do rename the file, you'll need to make sure it gets started at boottime.  'ls -l /etc/rc*.d/*cups*' should show a bunch of symlinks to the init script.  If it doesn't, run 'update-rc.d <filename> defaults'.)

---

### Post by BobSongs on 2005-12-03
[QUOTE=gruepig]What do you mean by "It only works if the file is called cups"?  This doesn't make any sense to me.  What are the errors you are getting?[/QUOTE]

Well, let's see. If I run the cupswrapper package without the change, I get this error message:
```
**$ sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb**
(Reading database ... 149922 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using cupswrappermfc210c_1.0.0- 1_i386.deb) ...
[COLOR="Red"]lpadmin: delete-printer failed: client-error-not-found[/COLOR]
[COLOR="Red"]/etc/init.d/cups: Command not found.[/COLOR]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
[COLOR="Red"]/etc/init.d/cups: Command not found.[/COLOR]


```
However if I copy cupsys to cups this is the result:
```
**$ sudo cp /etc/init.d/cupsys /etc/init.d/cups**
**$ sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb**
(Reading database ... 149922 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using cupswrappermfc210c_1.0.0-1_i386.deb) ...
[COLOR="Green"] * Restarting Common Unix Printing System: cupsd  [ ok ][/COLOR]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
[COLOR="Green"] * Restarting Common Unix Printing System: cupsd  [ ok ][/COLOR]


```

I believe the problem lies in the way Brother tries to access a non-existent **/etc/init.d/cups** file. Copying **cupsys** to **cups** solved the problem. So my question was whether it was a security issue to rename this system file.

Perhaps it's a minor thing that **cups** isn't there to stop and then restart. But I figured if I'm going to submit a 'how-to' on installing these drivers new users might not understand the errors.

Bob

---

### Post by gruepig on 2005-12-04
Yes, your assessment of the situation and workaround is correct, and writing a howto is great.

It sounds like this should also be reported as a bug to Brother (or whoever maintains cupswrappermfc210c_1.0.0-1_i386.deb).  cupswrappermfc210c expects the file /etc/init.d/cups, but the actual file in Ubuntu/Debian/etc is /etc/init.d/cupsys.

---

### Post by BobSongs on 2005-12-05
[QUOTE=gruepig](Also, if you do rename the file, you'll need to make sure it gets started at boottime. 'ls -l /etc/rc*.d/*cups*' should show a bunch of symlinks to the init script. If it doesn't, run 'update-rc.d <filename> defaults'.)[/QUOTE]

Well, I haven't done this to date. So far the MFC prints properly on reboot. So I'm going to leave well enough alone. However, I will paste this into the 'how-to' in case someone should run into any difficulties.

[QUOTE=gruepig]Yes, your assessment of the situation and workaround is correct, and writing a howto is great.[/QUOTE]

Thanks for the thumb-up, GP. I'm working on it right away. As soon as it's done it'll be posted.

[QUOTE=gruepig]It sounds like this should also be reported as a bug to Brother (or whoever maintains cupswrappermfc210c_1.0.0-1_i386.deb).  cupswrappermfc210c expects the file /etc/init.d/cups, but the actual file in Ubuntu/Debian/etc is /etc/init.d/cupsys.[/QUOTE]

I certainly could notify Brother. The instructions at their site do say this is for Debian. But I'd hate to tell Brother to modify their setup to work with **cupsys** only to find out it's an Ubuntu-specific difference.

Bob
______________
[Here's the How-to]("http://www.ubuntuforums.org/showthread.php?t=99169")

---

