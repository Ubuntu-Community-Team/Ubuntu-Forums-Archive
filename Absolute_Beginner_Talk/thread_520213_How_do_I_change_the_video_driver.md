---
title: "How do I change the video driver?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-08-07
Much to my amazement (as I am brand new to the world of Linux), I was able to successfully install Xubuntu 7.04 to an ancient Toshiba laptop (a Satellite Pro 490 XCDT) with only 96 Mb of system RAM.  Dual booting works (Win 98 SE shares the 10 Gb HDD).

The only problem is that Xubuntu has chosen the wrong "video card" driver.  The system routinely runs 1024x768/16-bit color.  Under Xubuntu's driver choice, not all of the available screen real estate is used, but Xubuntu acts like it is -- on some larger windows with "OK/Cancel" buttons, the buttons don't show, but no scroll bar appears to let them be reached.

In Windows, I would know how to choose a different driver, but I'm so new to Linux/Ubuntu that I don't yet know how to do something as basic as this.  I'm not afraid to drop to the much-vaunted command line; I just don't know how to do that, nor would I know what to do once I got there.  (I'm assuming the solutions lies somewhere in that direction.)  I have the video driver info (gleaned from Windows 98 data):

[CENTER]S3 ViRGE/MX Rev. 1 86C325[/CENTER]

I don't find this problem daunting -- it's just part of the Linux learning curve.  But so far I haven't found anything on the 'Net that directly (or indirectly) addresses my problem.

Any help on this would be appreciated

---

### Post by cobrn1 on 2007-08-07
It would be better if you could tell us what the graphics card is, as opposed to what the win98 driver is called.

---

### Post by Curbuntu on 2007-08-08
> **cobrn1 said:**
> It would be better if you could tell us what the graphics card is, as opposed to what the win98 driver is called.

Thanks for the quick reply!

So far as I know that **IS** the name of the hardware.  S3, Inc. is the maker of the chip, ViRGE MX is the model.  I have no idea what the Windows driver is named.  I was wrong about the chip type, though -- it's actually ***86C260***, not what I reported in the last post.  

That is on a list of supported chips on [http://linux.die.net/man/4/s3virge]("http://linux.die.net/man/4/s3virge").

---

### Post by Curbuntu on 2007-08-11
Okay, I've discovered the location othe necessary file (xorg.conf) and I've found the applicable section.  Now what do I change?

---

### Post by skymera on 2007-08-11
i think you scroll down to
display

and it says - generic video card etc.

change driver.

be warned if incorrect, your dumped with no GUI.
unless you reconfigure xorg

---

### Post by bwtranch on 2007-08-11
OK < i don't know if this is helpful or not. If it's not, I will just get out of the way. But to see what drivers loaded at boot type in:

dmesg | less

The less option allows for easier paging.

---

### Post by Curbuntu on 2007-08-13
I finally solved it, but in the end I had to go to the command line and fiddle with the xorg.conf file.  Here's the saga:

I gathered that xorg.conf is a little like the Windows Registry -- goof it up and the game is over (at least in terms of the X layer under the Xubuntu KFCE GUI).

**1st Problem: **Did I dare use one of the provided GUI-based text editors?  I couldn't get into terminal mode from the Xubuntu menu.  For some reason, after accepting my password, the go-to-terminal process kept dumping me back to the log-in screen.  (Yes, I was typing the password correctly; and, strangely, by default, Xubuntu [and I think all the *buntu's] disable the administrator account and set the first user up with administrator rights.)

**1st Solution:** Because of another problem I've encountered on a different machine's install, I had read about how Alt-F2 would put me into a terminal window.  Sure enough -- that worked.

**2nd Problem:** Should I bypass a text editor?  That seemed a safer bet until I knew more about the editor options provided.

**2nd Solution:** Again, in my reading I stumbled across a scenario similar to mine, in the 412-page *The Official Ubuntu Book* (which has proven to be quite a helpful introduction).  It pretty clearly gave me the steps from the command line:

```
sudo cp xorg.conf xorg.conf.old  
	#to make a "just in case" backup copy, obviously 
sudo dpkg-reconfigure xserver-xorg

```

The latter command opened up a text-based, step-through "wizard" (forgive me for using Windows-speak, but I don't know the Linux equivalent) that was quite "chatty" and helpful, letting me know what options would be presented next and what my best options were if I didn't know what the heck I was doing (which, largely, I didn't).  However, I recognized when it was time to input the data you had provided.  That seemed to prepare the way for the proper resolutions to be defaulted, and, just to play it safe, I opted for a small "depth" of "8" on color quality. 

Once the wizard was completed -- no change.  Well, why not reboot, since the xorg.conf probably is read at boot time?

**RESULT:** I now have a 1024x768 screen working as it should.  The apps know their place, Xubuntu 7.04 uses all the available real estate.  The pre-school-sized icons and system font have disappeared.  My geriatric Tosh laptop is waiting for me to shove some clutter off of my desk so that I can hook it up to the 8-port switch and get it online for DHCP configuration, browsing, and e-mail testing.  The world became a slightly more Linux-y place this morning...

P.S.: Once the screen-resolution problem was solved, I've had no further problem getting into the terminal and the command prompt from the Applications menu.  Go figure!

---

