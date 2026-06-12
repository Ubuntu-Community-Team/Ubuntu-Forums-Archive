---
title: "Unable to start Xubuntu on my iMac G3"
date: 2008-07-25
forum: Apple Hardware Users
---

### Post by sebz2005 on 2008-07-25
I just installed Xubuntu (8.04) on my iMac that my friend gave me and it won't start.
I've been able to narrow it down to the fact that the screen resolution is out of what it can display. I attached an external LCD screen to get that info.

What can I do to run it properly?

---

### Post by stream303 on 2008-07-25
You got it right!  The xorg.conf needs to be manually modified.  For Hardy, instead of changing the values listed, you'll need to add them to the sections of the file listed here:

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

Normally this means booting into the rescue-mode or single user mode (at the second stage of the yaboot boot: prompt, hit -tab- to stop the countdown, and issue rescue-powerpc or Linux single, or whatever the option listed is.  You'll eventually end up being asked what partition to drop into a root shell is, and for most that have just previously installed with "use the whole disk", it is usually /dev/hda3 or /dev/sda3.  From there, you can use vi or nano to edit the /etc/X11/xorg.conf file.  I've never seen nano work though from a rescue shell - anyone?

If you can just get to a virtual terminal with CTRL-ALT-F1, it can make life a lot easier than having to go through the rescue shell.

Note that you may also hit the date-bug if you have an older motherboard battery, and can't get past the gdm login:
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

---

### Post by sebz2005 on 2008-07-25
Ha!
I knew I thought that I knew more about linux than I thought I did.
I'll do it.
Thanks.

Edit:
I've had my iMac on since I first originally posted and I've been pressing Ctrl+Option(alt)+F1 and nothing's happened... :S

---

### Post by stream303 on 2008-07-25
It's a pain to have to resort to 90's technology to do this, but it is a fault of the ppc hardware not feeding back the right info to the usual Linux probing routines.

The graybeards that told me that vi was going to be very useful in the old days were right! :)

Good luck, and let us know how it goes!

---

### Post by sebz2005 on 2008-07-25
It's actually a 2001 model. :P
No, I just tried the Live CD and the whole system powers down (or what it seems like). :(

---

### Post by stream303 on 2008-07-25
Ah, yes - try the "alternate" image instead of the live-cd, which kills the video with the wrong values.  Nice catch-22 huh?  :)

The "alternate" iso image relies on text / ncurses to get the system initially installed, (full gnome gui afterwards) and after installation you can make your edits.  At least it won't shut down the machine just getting it installed.  This is also recommended for very low-memory machines (128-256mb) too.

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by sebz2005 on 2008-07-25
Yeah, tried that with the alternative CD too... :(

Edit:
Ok. Doing the Rescue with the alternative install CD.

Edit 2:
Also this is Xubuntu... No Ubuntu...
XFCE is faster than Gnome with the iMac G3

---

### Post by sebz2005 on 2008-07-25
1. The keyboard is all screwed up and can't access that much anymore
2. I can't find where it talks about the Horizontal Sync and Vertical Refresh... :(

---

### Post by stream303 on 2008-07-25
Is that an Apple keyboard?  Also, I have heard of some users having a better time initially allowing the system to install with a US keyboard mapping, and after installation, changing it to their locale.

Yep, Xubuntu is faster on the desktop, but I'm worried that the latest Xubuntu I've seen for Hardy was a late-beta and not an official release.  It may not be an issue if there are updates coming down after this, but I haven't had any Xubuntu users confirm this.

You may want to initially start out with an Ubuntu install for reference, and then after getting it up and running, installing XFCE4 from the repos, and switching to it at the next session login.

As for Hardy's xorg, it is pretty bare as it is with all distros these days using the new xorg.  Makes it a bit tougher for those new to it.  However, here's a go for the G3's xorg.conf:

Since you have an ATI rage 128 card, put it in the device section:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver      "r128"
        Option      "AGPMode" "2"
EndSection
```

There are other tweaks as seen here:
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

In the monitor section of /etc/X11/xorg.conf, edit it like so:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        "HorizSync"   58-62
        "VertRefresh"  75-117
EndSection
```

At the end of the file, add this to disable glx and dri:

```
Section "Module"
   Disable "glx"
   Disable "dri"
EndSection
```

Let's see if this helps...

---

