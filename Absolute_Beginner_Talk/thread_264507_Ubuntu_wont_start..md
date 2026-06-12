---
title: "Ubuntu wont start."
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Dapilot1 on 2006-09-24
So I'm trying to install Ubuntu on a butchered old HP Pavillion (700MHz Intel Celeron w/ 192MB RAM), but it fails to start.  Using the Live CD it will get to the point were it shows a ubuntu logo, above a progression bar, above a list of stuff with Ok next to them.  After that screen finishes it go to a blank black screen with a small, white horizontal line in the top left of the screen.  It never goes past this screen.  I tried it again on a slightly better HP Pavillion (1GHz Intel Pentium 3 w/ 384MB RAM) and the same thing happens.  I have gone past this screen on a computer I built, and even used it to install Ubuntu on to a hard drive.  But when I move the drive back to the HP, It gets stuck at that sceen again.  I think the problem is the BIOS.  Not the configuration of it, just it itself.  Does anyone know the solution to my delima?

---

### Post by xpod on 2006-09-24
Anther case for an "alternate cd" install or you might even need to try a lighter version like Xubunto.
THe "alternate " cd dont use a gui so uses less resources and is much easier to install on older  hardware...
I could`nt get Ubunto on a pc with similar specs but eventually managed to get the kubunto alternate on it once i boosted it`s memory...

xubunto might be the one for you though...you just need to try till you find one that will work like a lot of us do

---

### Post by jcrnan on 2006-09-24
I had the same problem once with a cd I burned and then Ive used it for two installs after that. Its probably some error in the burning of the disk. Burn a new disk and try again :)

---

### Post by Dapilot1 on 2006-09-30
So, I did a Xubuntu install from the alternate cd. I did the text install fine, but when it restarted it still stopped at the screen with the white line after the logo screen's progression bar finished.  I have no idea what else to do.  What happens during this screen that my computer is too dumb to handle?  Any help would be appreciated.  I don't want to go back...

---

### Post by sbergman27 on 2006-10-01
> **Dapilot1 said:**
> I don't want to go back...

It is probably a problem starting X, the graphical subsystem.

Boot the machine, hit escape after it says grub is loading.  Select recovery mode and hit enter. (It could say "single-user mode".) It should, rather verbosely, boot to a text console with a '#' sign.

You want to configure your X to use a generic driver called 'vesa', which may work better.

To do this, we need to edit a file in a directory called "/etc/X11" which is called xorg.conf.

Do this:

```

cd /etc/X11
cp xorg.conf xorg.conf.sav
nano xorg.conf

```

Look for a line that says:

```
Section Device
```


A line or two below that, you will see a line that says:

```
Driver "Something"
```

Write down what that "Something" is.

Then replace it so that the line looks like:

```
Driver "vesa"
```

Hit ctrl-X.  Press Y to save, when prompted.  If you think you may have messed up, hit N and run nano again.

Once this is done, type "exit", and the machine should continue to boot normally.

Hopefully, you will get a login screen.

If not, come back and we'll try something else.

-Steve

---

### Post by Dapilot1 on 2006-10-03
Thanks for the help Steve.  That didn't fix the problem, but I think I know what it is now.  In xorg.conf at Section "Device", it listed the device as a long name which I believe is the name of the on-board video.  That assumption was further re-enforced by the driver listed as i810 which I believe is the driver for the on-board Intel video.  After removing my video card, NVidia GForce 2 MX200, and plugging the monitor into the on-board, Xubuntu booted fine*.  So I guess I have a new question now.  How do I get my video card to work right?  I can remember my friend complaining about NVidia drivers once or twice.

~Lewis

* Booted on i810 driver instead of vesa.

---

