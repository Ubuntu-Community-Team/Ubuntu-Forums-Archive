---
title: "24&quot; Cinema display on Ubuntu Intel Mac Mini?"
date: 2006-09-22
forum: Apple PPC Users
---

### Post by peter@neubauer.se on 2006-09-22
Hi,
I'm trying to get a Dell 24" 1920x1200 display to work in full resolution with my Ubuntu installation, but I can only come up to 1200x1024. Is there anyone who has that working, and what steps are necessary (X configuration, 2D graphics drivers etc)?

Thanks for any hints!

/peter

---

### Post by wvmac on 2006-09-22
I am having the same trouble with a 19" widescreen and a ppc mini. It will not display the 1440? X 900, only 1280 x 1024. So any help would be appreciated.

---

### Post by seatea on 2006-09-24
If you have  your original manual for your monitor, you can manually edit your xorg.conf and add the supported resolutions from your manual. It might also be helpful to print out a copy of your xorg.conf for reference and check the values as they are presented by running ```
sudo dpkg-reconfigure xserver-xorg
```. This will ask you to make choices about all of your input devices as well as the monitor. Having the xorg.conf printed out will help in making choices for your setup.

---

### Post by vynsane on 2006-09-25
seatea already helped me out with something like this a couple of days ago... from my experiences it could be a simple measure of running through the motions of the dpkg-reconfigure command... it may actually auto-detect the proper settings. i've installed ubuntu twice now, once on a graphite g4 using the vga input on a samsung 204t (that should've been at 1600x1200) and a dell inspiron 7500 laptop (that should've been at 1440x950 or something odd like that...) and each time only got resolutions up to 1024x768. for some reason, just hitting "enter" through the entire reconfigure each time let it properly auto-detect my monitor's actual settings, and x restarted at the default resolution for each. it seems the initial install isn't able to detect monitor settings very well, as i've read a lot about this problem since my first foray into linux territory.

---

### Post by pan_linux on 2006-09-25
Can one of you explain this to a total newbie? I am running Ubuntu on my MacBook and want to get rid of the damn 1024 res. Something like 1152x720 would be nice...

---

### Post by vynsane on 2006-09-26
just open the terminal and type the line that seatea typed above.

```

sudo dpkg-reconfigure xserver-xorg

```

this will open a configuration utility that will ask you a bunch of questions about your system. answer them and when you get to the part about your monitor, refer to your manual with the proper settings (horizontal/vertical refresh rates, resolution settings, etc...)

however, in my experience, i haven't needed my manual, and just hit "enter" the entire time - somehow the initial install of ubuntu didn't detect the proper settings in either of my installs, but this configuration utility did.

---

### Post by wvmac on 2006-09-29
been away on vacation, couldn't check the forums.
I tried the dpkg-reconfigure tool and when I select the highest resolution 1400x960 I get a screen that is garbled. I'll keep playing with it and try to find a setting that works.  thanks for the help.

---

