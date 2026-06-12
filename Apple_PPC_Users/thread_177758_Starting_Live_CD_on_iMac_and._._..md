---
title: "Starting Live CD on iMac and. . ."
date: 2006-05-16
forum: Apple PPC Users
---

### Post by RavenOfOdin on 2006-05-16
gotten past the OpenFirmware prompts correctly.

But, the system is taking upward of three minutes to progress past so much as one step of loading. I heard the Ubuntu startup music about 30 seconds ago and my screen is still black.

My video resolution was set to 640X480 in the Live preparations.

The CD drive on the iMac is acting like its trying to read constantly, with little whirring noises from inside the case which stop and start up every so often. . .could this be related?

---

### Post by linear on 2006-05-16
Is this an iMac G3? If so, read on...

You may need to fix some settings in xorg.conf.

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/kdm restart (return) to restart KDE

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart KDE and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by user1397 on 2006-05-16
or are you using an imac G5? if you are, why switch to ubuntu?
(mac os x is awesome!!!!) :)
jk, ubuntu is awesomer, just don't erase mac os x, you paid good money for it!:D
if you had windows, then i would say:"go ahead, destroy it!"

---

### Post by RavenOfOdin on 2006-05-16
@linear: I'll try that, thanks.
@erik: No, its a G3.

(EDIT: OK, tried it and after gaps of what seemed like 10 minutes - waiting for so much as the sudo pico command to finish - I restarted the server. When it finally came up there was nothing but a brown screen and Ubuntu box in the middle. It remained that way all through dinner. 

So I'll try commenting out DRI, and hope that works in both modes.
If not. . .there's always FreeBSD/ppc.)

---

### Post by RavenOfOdin on 2006-05-18
Nope. Live CD is still crapping out on me.

If this is how it runs on a G3, I'll pass.

---

### Post by 3rdalbum on 2006-05-19
Those instructions given should work. I had the Breezy CD running on my iMac 333 with those instructions (admittedly, not Kubuntu). I've also got Breezy running on that same computer, and the installer correctly set up my video card too.

On my PC, I've found that after making edits to the xorg.conf file the X server freezes. This may be similar to your problem.

---

### Post by RavenOfOdin on 2006-05-23
After a couple of days I decided to try it again. . .I'll check that out.

It works faster now, but GDM doesn't give me anything more than a brown screen without splash, until stop of service or reboot.

DRI is disabled in xorg.conf and my monitor resolution settings are up to par.

---

### Post by linear on 2006-05-24
Now it's sounding like the [Ubuntu Date Bug]("https://wiki.ubuntu.com/UbuntuDateBug").

---

### Post by RavenOfOdin on 2006-05-24
Yup!

The date command gives me:

```

Sat Sep 1 00:37:33 CDT 1956

```

As for the PRAM issue, I think I had to reset it once on OS9. =/

Works fine now. Thanks for the help. :)

---

