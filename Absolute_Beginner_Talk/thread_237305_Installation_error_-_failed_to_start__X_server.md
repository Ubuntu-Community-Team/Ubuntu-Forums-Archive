---
title: "Installation error - failed to start  X server"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by usr0815 on 2006-08-15
Just created the Ubuntu 6.06.1 CD after verifying checksums and booted the laptop off the CD. I am using a Dell Inspiron E1705 running XP. This is a 17" display, but I read reports of no problems with the display when installing Ubuntu (at least Badger on a 9300 which is the same as the E1705 I believe).

I get an error message that says "Failed to Start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Prior to this blue screen (yes it is blue!) popping up, the checks seemed to go fine from what I could tell.

I chose to diagnose the problem. Consequently it shows me the X server log that I could scroll through. A lot of informational output, but here is what I gleaned:

A warning message

[COLOR="DarkOrange"](WW) I810(0) Bad V_BIOS checksum.[/COLOR]

(then a ton of informational stuff)

At the end, two error messages:
[COLOR="Red"]
(EE) I810(0) No video BIOS modes for chosen depth
(EE) Screen(s) found, but none have a usable configuration.[/COLOR]

Finally ending in:

[COLOR="Red"]Fatal server error:
no screens found.[/COLOR]

---

### Post by usr0815 on 2006-08-15
Oh sorry for the abrupt ending. Please help! Mucho Gracias.

---

### Post by usr0815 on 2006-08-15
I googled (TM) for a solution and saw this [blurb]("http://www.shahidhussain.com/wordpress/index.php?p=29").

So I tried to follow this line of thought - went into the BIOS settings but the device info showed that the Video Memory was already 8MB. The blurb suggests bumping it up to that value but it is already at that value. Moreover it mentions that none of these fields is changeable.

FYI:
Video Controller Intel 945GM graphics
Video BIOS Version 1264
Video Memory 8 MB
Panel Type 17" wide XGA+
Native Resolution 1440 by 900

---

### Post by DSn0wMan on 2006-08-15
Usually if x server is not starting you need to reconfigure it. Even on fresh installs.

Try this:

at the prompt type
```
sudo dpkg-reconfigure xserver-xorg
```

This will walk you through the configuration. Once you have completed this you need to restart the xserver.

```
startx
```

---

### Post by usr0815 on 2006-08-16
Thanks for the response, DSn0wMan.

I did as suggested, chose 'autodetect' when prompted, and chose the default answer that was shown except for entering the monitor name and the exact version/name of the video controller. Then did a startx and x windows did come up. I am now working through the install using the Ubuntu UI and by choosing the Install icon.

Thanks again for your quick response.

---

### Post by Rebada on 2007-03-25
Hi, I can't even get the live CD to boot. I get errors similar to what was posted by usr0815.
I am using a Dell Inspiron e1705, running Windows XP.

I have never had any luck getting linux to run on any of my machines.  I've been trying for years!  Funny thing is, now that I've retired my old desktop unit and got the laptop, my spouse has been able to get ubuntu on the old desktop.  I feel like I'm jinxed!

let me know if I need to supply morei nformation...I'm looking to actually set up a dual boot system, where I can choose which OS to launch.

Thanks for any help!

---

### Post by Stebbins on 2007-03-25
> **DSn0wMan said:**
> Usually if x server is not starting you need to reconfigure it. Even on fresh installs.

Try this:

at the prompt type
...

This may be an extremely stupid question, but... how do I get to this prompt?

Pressing escape from the main menu gives me a "boot:" prompt, but none of the normal shell commands work in that.  After I exit out of the X server error screen, nothing happens until I press ctl-alt-del and quit ubuntu altogether.  I have no idea how to get a normal prompt.

---

### Post by DSn0wMan on 2007-03-27
After you get the Xserver errors just hit this key combination to get to a prompt.

ctrl+alt+F2

---

