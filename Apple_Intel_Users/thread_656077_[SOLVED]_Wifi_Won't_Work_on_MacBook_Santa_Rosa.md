---
title: "[SOLVED] Wifi Won't Work on MacBook Santa Rosa"
date: 2008-01-02
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2008-01-02
Hi all.

I recently purchased a black Santa Rosa MacBook, Intel Core 2 Duo. Is it just me, or does nothing work???

I have tried for weeks now to get Ubuntu working with the new hardware, but I just can't do it. I followed this tutorial:

[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

and accomplished _absolutely nothing._

The things I would like to get working are:
1) Wireless
2) Sound
3) Compiz (only as an aside)

If you have any information that could help, or have experienced this yourself, please, *_please,_* post. At this point, anything you have would be an improvement.

Thanks in advance.

---

### Post by cyberdork33 on 2008-01-02
If you are following the wiki page, then it looks like there are fixes for each of the items you are having issues with. I understand that you are saying you have tried these things, but we will need a little info (error messages, etc) to help further.

Did you use ndiswrapper? did you get the driver installed? What part of the process is having an issue?

Also, according to the last post in the Santa Rosa Macbook thread, there may be an issue with the ppa kernel:
[http://ubuntuforums.org/showthread.php?t=610375&page=13](http://ubuntuforums.org/showthread.php?t=610375&page=13)

---

### Post by RelativelyQuantum on 2008-01-02
I'll post again when I discover more, but I know that "bcmw15" seemed not to install correctly. It gave me an error message originally, but when I tried to reinstall it the computer told me it was already there.

As I said, I'll post again when I discover more, as I am currently using another machine. The actual error message will be up shortly.

Thanks.

~RQ

---

### Post by cyberdork33 on 2008-01-02
if you get an error with ndiswrapper when trying to install a driver, then that is likely not going to work. You have to remove that driver before attempting again.

```
sudo ndiswrapper -r bcmwl5
```

You can list installed drivers with:
```
 ndiswrapper -l
``` (that's a lowercase letter L)

---

### Post by george.talusan on 2008-01-02
I have a problem with my wifi using ndiswrapper as well.  The driver loads fine and I'm able to bring the interface up.  Unfortunately after a few hours of use, the wifi connection disappears and only a reboot will bring it back.

ifdown/up on the interface doesn't seem to do anything when it gets into this state.

---

### Post by RelativelyQuantum on 2008-01-06
```
ndiswrapper -l
```

When I do this nothing happens. Is that a problem?

**Edit:

When I cd to driver/DRIVER/ everything works well. I can't beleive I let this slip by - in the tutorial, "l" looks very similar to "1," so I was actually trying to install "bcmw15.inf" instead of "bcmwl5.inf" I ran "ndiswrapper -l" and got the response that "bcmw15" was not valid, so I removed it, installed "bcmwl5," and everything seems to be fine. I still can't launch the graphical interface though. I'll try rebooting, as ndiswrapper is now listed as in my /etc/modules file.

Thanks again for the support; it was a big help. I'll post again after I've rebooted.

---

### Post by RelativelyQuantum on 2008-01-06
Well, I finally got everything worked out. I'm signed in over my wifi connection, and wifi radar works excellently,

Thanks again for all the help!

---

### Post by cyberdork33 on 2008-01-07
please mark as solved.

---

