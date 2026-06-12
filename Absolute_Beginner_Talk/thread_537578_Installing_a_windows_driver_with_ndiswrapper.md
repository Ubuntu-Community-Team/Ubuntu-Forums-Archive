---
title: "Installing a windows driver with ndiswrapper"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by jonkanon on 2007-08-29
Hello, this is a somewhat n00b question but although I've spent hours I'm lost.
I'd really like some help installing my GPLUS driver using Ndiswrapper. My card is DWL-G650+ and this is said to work.

[I]jon@jon-laptop:~$ sudo ndiswrapper -i ~/DWL/gplus.inf
Password:
driver gplus is already installed
jon@jon-laptop:~$ ndiswrapper -l
gplus : invalid driver!
[/I]

I read about deactivating the current linux driver, but how is this done?

Another message I had in terminal:

[I]jon@jon-laptop:~$ sudo ndiswrapper -i GPLUS.inf
installing gplus ...
couldn't open GPLUS.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174.
[/I]
I tried to uninstall ndiswrapper and install again, now I don't know... I'm lost.
It's probably quite simple. Anyone help?

EDIT: I could also add that I tried the interface "Windows Wireless Drivers" but nothing ever appears in the "Currently Installed Windows Driver" box. I get no error message, but installation seems to fail.

---

### Post by chrome307 on 2007-08-29
Is this any help to you?

[http://ubuntuforums.org/showthread.php?t=534617](http://ubuntuforums.org/showthread.php?t=534617)

---

### Post by jw5801 on 2007-08-29
Try this:
```
sudo ndiswrapper -r gplus
sudo ndiswrapper -i ~/DWL/gplus.inf
```
Make sure the check the case (ie. Gplus.inf or GPLUS.inf etc.) of the driver you're installing and that the directory is absolutely correct. If you don't quite give the correct directive to ndiswrapper, it won't tell you it can't find the file it will just create the driver entry anyway and then get cranky and tell you it's invalid.

---

