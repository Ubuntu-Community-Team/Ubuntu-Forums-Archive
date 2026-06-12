---
title: "[SOLVED] Space bar  in Maya and Houdini"
date: 2008-02-15
forum: Apple Intel Users
---

### Post by jujoje on 2008-02-15
Hi,

I've been running to a problem with both Maya 2008 and Houdini (apprentice)  on a mac pro and was wondering if anyone could shed some light on it.

Both of the programmes use the space key - for the hotbox in maya and camera in Houdini. However in both Gutsy and Hardy pressing the space key freezes the mouse. When space is depressed everything works as normal.

I have a mac pro 8 core with a nvidia 7300 and I reckon that this problem is related to mac keyboard or usb input, since I don't remember is happening in Gutsy on my old pc. I was wondering if anyone has encountered the same problem on or has any idea of why this should be happening.

Below is a list of things that I have tried so far:

[LIST]
[*]Installing the newest nvidia drivers from the nvidia site
[*]Checking keyboard layout and shortcuts as well as the accessability options incase something was clashing
[*]Removed desktop effects (although i usually have it turned off anyway). Also tried commenting out the related lines in the xorg file. (However unlike the crash with compiz, the computer doesn't freeze, just the mouse)
[/LIST]

Any help or suggestions as to what I could try next would be greatly appreciated,

---

### Post by cyberdork33 on 2008-02-15
i would guess it is mouseemu:
[http://ubuntuforums.org/showthread.php?t=545244](http://ubuntuforums.org/showthread.php?t=545244)

---

### Post by jujoje on 2008-02-16
Thanks that worked perfectly :-)

---

