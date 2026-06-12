---
title: "iMac G3 Not Booting"
date: 2008-01-22
forum: Apple PPC Users
---

### Post by banjobeast2233 on 2008-01-22
I'm a new Ubuntu Forums user but I have used Ubuntu before.  I'm trying to install Ubuntu on an indigo iMac G3.  When I load the CD, I get a message that says I should press tab to get a list of options or just press enter.  When I press enter, the screen says "Loading Kernel.  Please Wait"  it then goes to a white screen then back to black where it says "loading, please wait", the print changes font and then the computer shuts off.  Why is it doing this?  I have enough ram (PLENTY, I've got a gig!) so it can't be that.  When I tried installing 6.06 to see if that would work, The screen said "Please wait, loading kernel. . ." and then froze with the CD drive spinning down.  Later, it says "read failed"  Why is it doing this?  does anybody know?  I would greatly appreciate anyone knowing anything about this issue.

---

### Post by jwalcker on 2008-01-23
It might just be you're CD drive, if it has a problem reading you might want to go to the source, at least thats what i would do, you might consider running a system diagnostic to check and see if the CD drive is functional, just my 2 cents :)

---

### Post by stream303 on 2008-01-23
Have you tried burning the iso at a very slow speed and on high-quality media?

There are some threads here from January I believe that describe symptoms similar to yours regarding taxing the supply.  Maybe the cd drive needs cleaning or is running like crazy trying to read a disk that was burned too fast....  Have you tried 7.04 Live Cd or Alternate?

---

### Post by Midwest-Linux on 2008-01-23
Try the alternate text based installer CD.

---

### Post by stream303 on 2008-01-23
The only time I ever had a machine lock up and turn itself off during install was long ago with NetBSD on a 90mhz pentium.  During the install I switched over to the error console and the system was just getting hammered with so many read errors that finally the kernel panicked.

Burning the install cd at something ridiculous like 1X and trying it on different media finally got it to install without hammering the system with errors.

---

### Post by Keith Hedger on 2008-01-23
just to reiterate what has been said above ive installed ubuntu on an imac,powerbook and clamshell ibook and have never been able to get the live cd to run the alternate install disk works every time

---

### Post by banjobeast2233 on 2008-01-24
Thanks for all your help, but I still am having problems.  I was able to install Ubuntu on the hard drive, but now it won't boot!  I get to the Ubuntu logo with progress bar, the progress bar gets a tiny little sliver, and then it seems to freeze up.  After about 5 minutes, the OS goes into a text-based entry mode that I have no idea what to do with.  If anyone knows what's going on, PLEASE help me!!

---

### Post by stream303 on 2008-01-25
Ok, getting close!

Have you looked through these two faqs?  They have some very important info that will help, especially for the G3:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

and

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Give some of these commands a shot and let us know....

---

### Post by banjobeast2233 on 2008-01-29
Thanks for all your help.  It turns out that my problem was that it was getting stuck at Bootstrap.  I typed in modprobe ide-core, and that fixed it, but then I ran in to the GNOME date bug.  I was able to fix that with a new clock battery, and I have it working fine.  I did not stay Ubuntu though, since the applications weren't working right.  If I could figure out a way to make it work 100%, I would use Ubuntu, but I think I'll stay with OS 10 for now.
Thanks to everyone.

---

### Post by UFRMF3B5 on 2008-05-13
> **banjobeast2233 said:**
> [...] it says "loading, please wait" [...] then the computer shuts off.

Ubuntu 8.04 (alternate) installed on an iMac G3 (Early 2001) refused to boot with the same symptoms. Appending "break=top" at the boot prompt did not help: the boot process would stop in BusyBox but the keyboard would not work.

The fix was to boot the machine using some other linux, mount the root filesystem, edit /<mountpoint>/etc/yaboot.conf, remove all occurrences of append="quiet splash" and invoke ybin -C /<mountpoint>/etc/yaboot.conf. 

With the edited yaboot.conf the machine boots normally but then the screen goes black. To fix that switch to the text console (Ctrl-Alt F1), log in, sudo vi /etc/X11/xorg.conf, add the lines HorizSync 60.015 and VertRefresh 75-110 to the "Monitor" section. Switch to the X display (Ctrl-Alt-F7), kill the server (Ctrl-Alt-Bksp), and you have got a working machine.

I believe only the "splash" part is critical in the append line above; however, I did not bother to check.

Hope this helps.

---

### Post by stream303 on 2008-05-13
> **UFRMF3B5 said:**
> With the edited yaboot.conf the machine boots normally but then the screen goes black. To fix that switch to the text console (Ctrl-Alt F1), log in, sudo vi /etc/X11/xorg.conf, add the lines HorizSync 60.015 and VertRefresh 75-110 to the "Monitor" section.

That brings up a good point - on some machines, it is very sensitive to the HorizSync value, and it is best to give it some leeway such as 58-62, since a strict value of 60 sometimes doesn't work.  Close, but no cigar. :)

The splash screen has been nothing but trouble for me, or just basically useless as a distorted colorful piece of eye-candy. :)  I tend to disable it completely by using *nosplash* (or other no-splash variants) as a kernel parameter so I can see the boot messages roll by instead.

I add it to the append= line in /etc/yaboot.conf:

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        **append="nosplash"**

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        **append="nosplash"**
```

...and then make it permanent with:

```
sudo ybin -v -C /etc/yaboot.conf
```

Glad to hear Hardy is working for you!

---

