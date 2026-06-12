---
title: "How to make compiz and kwin stable with PowerPC radeon UMS."
date: 2013-02-05
forum: Apple Hardware Users
---

### Post by rsavage on 2013-02-05
All, attached is a patched file that should improve the stability of those using opengl window managers in 12.04.  Can people test it please?  

Instructions:

Extract and save file to your home folder.

Open a tty console with Ctrl+Alt+F1

Login

Stop the Xorg server (make sure you've saved any open files you're working on first): sudo stop lightdm

Make a copy of the original: cp /usr/lib/xorg/modules/extensions/libglx.so libglx.so.original

Copy new file into place: sudo cp libglx.so /usr/lib/xorg/modules/extensions/libglx.so 

Start Xorg server: sudo start lightdm

---

### Post by calexand on 2013-02-15
I followed your directions and installed the new file in place, but cannot discern any appreciable difference.
Are there any log files you would like to see or tests you would like done?
I am using a Radeon 9800 Pro 128 4X AGP.
CA

---

### Post by calexand on 2013-02-16
Ok now, finally! I have downgraded the mesa files down to version 7.11-0.3.2, then I added "radeon.modeset=0 video=radeonfb:1024x768-16@60" (no quotations) to the yaboot.conf file, both per the Official FAQ and WIKI. I then installed the above mentioned file in its' proper place.
After battling software rasterizing for months, the combination of all of these things succeeded: glxgears shows over 5000!
Thank you all who provided all the different instructions/fixes.

Mods~Can this please be made "sticky"?

CA
:D

---

### Post by rsavage on 2013-02-17
The patch is only really if you are using compiz or kwin (and possibly other opengl window managers although I haven't been able to run them on my iBook).  If you are using lubuntu or xubuntu then you probably won't see any difference with the patch.

I need to raise a launchpad bug and the reason I wanted people to test was so that they can confirm the bug and solution.  It is much better to seek an official patch because I don't want to keep having to rebuild the xorg core package.

You should try KMS before falling back to UMS.  KMS is hit and miss on PowerPC hence my own interest in UMS.

---

### Post by rsavage on 2013-02-17
If you want to try out compiz and you are using something like lubuntu then the easiest thing is to use lucid's version.  Change your sources temporarily to lucid and install compiz, emerald and compiz config setting manager (ccsm) etc.  For ccsm you'll need the attached deb file.  It is exactly the same as that used in lucid except built against the latest python (I probably should of bumped the package version number, but it was just going to be for my personal use).  To get compiz run:

```

compiz --replace  ccp

```If you've compiled a later version of compiz then you may need:
```
 
LIBGL_ALWAYS_INDIRECT=1 compiz --replace ccp

```Compiz is pretty stable using the cairo window decorator.  It is only when you change to a metacity (or marco) or emerald theme that it goes wrong (and what the patch in post 1 fixes).  To select the metacity theme you want you may have to change a gconf setting (under apps > gwd) .

---

### Post by rsavage on 2013-03-27
I know I'm completely wasting my time here (you've all been brainwashed to use Lubuntu), but I would really appreciate it if you could confirm this bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1160903](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1160903)

Thanks

---

### Post by calexand on 2013-03-28
Actually, I am using Ubuntu with the Lubuntu de over the top. ;) I am not having this particular problem, as far as I can tell, all is now alright. I even run Ubuntu de in 3D occasionally.
CA

> **rsavage said:**
> I know I'm completely wasting my time here (you've all been brainwashed to use Lubuntu), but I would really appreciate it if you could confirm this bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1160903](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1160903)

Thanks

---

### Post by rsavage on 2013-03-29
Your graphics card if better/newer than mine.  If you can run the latest compiz/unity okay then could you think about maybe testing the latest 13.04 builds [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) .  Without people testing them (and marking them as passed on the iso tracker) they can't be released (which is what happened to 12.10).

---

### Post by calexand on 2013-03-29
Downloading now...
CA

> **rsavage said:**
> Your graphics card if better/newer than mine.  If you can run the latest compiz/unity okay then could you think about maybe testing the latest 13.04 builds [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) .  Without people testing them (and marking them as passed on the iso tracker) they can't be released (which is what happened to 12.10).

---

### Post by calexand on 2013-03-29
I could not get 13.04 to run, it always froze at the white screen upon finding the display. I thought that it didn't like my "burn" even though I burned it at 4X, so I burned another at 1X speed, still a no go.
I then thought that it didn't like my current video card, so I replaced it with my Radeon 8500 Mac: froze. I reset the CUDA and zapped the PRAM: froze.
I tried every option that I could think of including "linux video=ofonly": same.
I give up, apparently I cannot help... Sorry.
CA

> **calexand said:**
> Downloading now...
CA

---

### Post by rsavage on 2013-03-30
That's a shame.  Thanks for having a go anyway!

---

