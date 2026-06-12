---
title: "Arch Installation Problem - CAn't Select Packages"
date: 2008-11-15
forum: Arch and derivatives
---

### Post by WaeV on 2008-11-15
When I go to install Arch it won't let me select packages.  this happens with two versions of unetbootin and one CD I burned.  It happens whether I choose to select packages from the CD or from FTP.

---

### Post by handy on 2008-11-15
Can you please give lots of details?

We can't work with what you have given us so far.

---

### Post by WaeV on 2008-11-15
I get errors such as these when I try to select a mirror.  Occasionally it just tells me it can't connect to the server.  But it doesn't work when I try to load the packages from the CD either.
I have tried running pacman -Sy pacman before attempting to select packages, but it didn't help.
I am using the 64 bit version.

```
[*] Error:    ^
[*] Expected  ^
[*] at        ^
[*] least     ^
[*] 7         ^
[*] tokens    ^
[*] for       ^
```

```
[*] Error: ^
[*] Expected ^
[*] Error: ^
[*] Expected ^
[*] Error: ^
[*] Expected ^
[*] Error: ^
[*] Expected ^
```
Note:  Each [*] is on it's own line, some php formatting error won't let me display it that way.

---

### Post by handy on 2008-11-15
Are you following the [***_Arch Beginners Guide_***]("http://wiki.archlinux.org/index.php/Beginners_Guide")?

It is apparently available on the install CD, though I have never used it that way, I have 2nd PC to reference it with whenever I do an Arch installation.

If you follow the Beginners Guide ***to the letter***, you should have no problems, unless you have an unusually difficult wireless chip set.  If you can't set up for the ftp install then go the other way (I always do), it won't take that much longer if you are on broadband, a pain if you are on dial-up though.

---

### Post by WaeV on 2008-11-16
I'll try again and post the error I get when I try to select packages from the CD.

---

### Post by handy on 2008-11-16
Are you using the Beginners Guide?

You really make it hard for someone to help you as you don't give any details, & details are what is needed.

---

### Post by WaeV on 2008-11-16
Ok, it worked this time.  I was using the beginner's guide, ftp installation failed for some reason. :confused:

Now to transform a simple command line into a full desktop environment! :)

---

### Post by handy on 2008-11-16
> **WaeV said:**
> Ok, it worked this time.  I was using the beginner's guide, ftp installation failed for some reason. :confused:

Now to transform a simple command line into a full desktop environment! :)

Great news =D> have a big pile of fun. :-D

---

### Post by WaeV on 2008-11-16
I have a few questions:

When I try to run "alsamixer" to set my sound settings, it gives me "Symbol `acs_map' has different size in shared object, consider re-linking" and won't run.

Also, the beginner's guide has a specific order ti install and setup xorg, opensource drivers, etc. but doesn't mention proprietary drivers until later.  Should I install proprietary drivers before I configure xorg.conf?

---

### Post by handy on 2008-11-16
Do things as the Beginners Guide instructs, it rarely fails, though occasionally some weird hardware does crop up.  Don't worry about your sound at this stage. 

For the X installation, I have found using hwd works really well for setting up the xorg.conf .

pacman -S hwd

The instructions are in the guide.

---

### Post by mips on 2008-11-17
> **WaeV said:**
> 
Also, the beginner's guide has a specific order ti install and setup xorg, opensource drivers, etc. but doesn't mention proprietary drivers until later.  **Should I install proprietary drivers before I configure xorg.conf?**

Yes. Just jump to the proprietary drivers section and follow that, they have their own xorg config utilities you can run to generate a xorg.conf file

---

### Post by handy on 2008-11-17
Oops, I was a bit off the ball in my previous post.

Too long since I installed I guess... ;-)

---

### Post by WaeV on 2008-11-17
Thanks, mips that seems to have worked.  I got XFCE working anyways.

Though I might switch back to gnome, I'm too used to it.  I'll try KDEmod on the way.

---

