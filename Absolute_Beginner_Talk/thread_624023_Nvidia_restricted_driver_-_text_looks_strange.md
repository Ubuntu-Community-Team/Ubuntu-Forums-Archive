---
title: "Nvidia restricted driver - text looks strange"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by davexnet on 2007-11-26
Hello all ,
I'm new to Linux having installed my first system a couple of weeks ago.

I successfully enabled the Nvidia restricted driver (using envy) and had my monitor,
with correct resolution and refresh rate recognized.

It's a dual boot machine, in M$ Windows XP, Text is razor sharp.
In Ubuntu, it's got that slightly odd look you get when you set an LCD
off of it's native resolution.  (I know cause I tried it in XP)

The monitor itself says it's running the correct res so I don't know what's going on.
(By pressing  one of the monitor buttons an overlay comes up giving you all the
relevant info)

I found "Nvidia settings", but I don't see anything obvious.  Under "X server Display config"
I see a button "save to X configuration file"  What does that do?  Does it save a backup,
or is it updating the permanent setings?

Was using envy a mistake?  How do I update the driver in the future?
TIA for any info.
Dave

---

### Post by Hospadar on 2007-11-26
Well using gutsy, generally the restricted driver manager (System->Administration->Restricted...) will work just fine and envy won't be needed, but envy does pretty much the same thing as the driver manager so it shouldn't be the issue.

You might try monkeying with:
Color depth (16/24/32 bit, probably you should be using 32)
Refresh rate, this is monitor dependant, check the refresh rate on your monitor and make sure the output is the same

If you change this stuff, you might want to make a backup copy of your /etc/X11/xorg.conf file before you start in case you have to drop your settings back to something wierd.

Are you using an analog (vga, the blue one) output?  If so, does your monitor have an auto-adjust feature?  If you arn't sure, look in the manual, or poke around in the monitor's menu.  oftentimes on dual boot systems, the frequently changing outputs will cause the monitor to need to be re-adjusted between the OS (especially with vga output)

---

### Post by eldepeche on 2007-11-26
I don't know when this has an effect, but there are font rendering settings under System -> Preferences -> Appearance.

---

### Post by davexnet on 2007-11-26
Regarding the fonts System -> Preferences -> Appearance, I'll check it out.

I am using the VGA analog output and have tried the monitors auto adjustment button.
It shifts the image slightly (Vs. where it is when XP is loaded} but doesn't improve the sharpness.

I'll do as you suggest and take a copy of /etc/X11/xorg.conf - then I can fudge with it for
a while.

Thanks

---

