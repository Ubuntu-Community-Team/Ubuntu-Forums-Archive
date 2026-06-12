---
title: "Brightness Buttons not working, ppc/pbook 12&quot;"
date: 2007-08-19
forum: Apple PPC Users
---

### Post by xefyr on 2007-08-19
I have installed Ubuntu 7.04 ppc on my Apple 12" powerbook (1.33GHz).  I have pbbuttonsd (running), gtkpbbuttons, powerprefs, all installed and all seem to be otherwise working.  My sound and eject hot-keys all work; the brightness controls, however, do not.

Reading man pbbuttonsd tells me I need to make sure CONF_PMU_BACKLIGHT and CONF_PMU_BACKLIGHT_LEGACY are enabled in my kernel, and that they'll be found in (>= 2.6.18 kernels) menuconfig as:
> Device Drivers -> Macintosh Device Drivers:
[*] Backlight control for LCD screens
          
[*] Provide legacy ioctl’s on /dev/pmu for the backlightWhen I grep in /boot/config-`uname -r`, neither of those config variables are found.  When I grab the kernel sources, copy in said config to .config, and run make menuconfig, the above sections are enabled.

Why are my brightness buttons not working?  Is there some way I can verify what key codes these buttons are providing?  Can I verify that the events are being passed to the pmu module in the kernel?  Can I manually send these events in order to verify that the module is working?

Thanks in advance!

---

### Post by mbrennwa on 2007-08-20
I had the same problem until I realized that I needed to configure pbbuttonsd first. Take a look at the PowerPrefs program available at [http://pbbuttons.berlios.de](http://pbbuttons.berlios.de) .

Cheers
Matthias

---

### Post by xefyr on 2007-08-20
Could you perhaps be a bit more specific?  I've used both used powerprefs and tweaked /etc/pbbuttonsd.conf by hand, neither of which are doing me any good.

PowerPrefs recognizes fn+f1 (brightness down) as keycode 224 while xev reports it as 101.  Likewise, brightness up come through as 225 and 212 respectively.  The 'light-bulb' pane in PowerPrefs alternates between saying it has no information about the current brightness level or that the current level is at 0%.


Matthias, did you do anything specific to get thing working?  Thanks!

---

### Post by xevix on 2007-11-04
Same thing on the same laptop, do we just have to compile our own kernels or something?

---

### Post by xevix on 2008-02-01
bump

---

### Post by stream303 on 2008-02-02
I got my brightness controls back by editing out "splash" in my /etc/yaboot.conf file and reapplying the change with sudo ybin -v.

I was trying to get my virtual terminals back, and found that this cured my brightness control problem on my G4 iBook with Gutsy.

Admittedly we're not using the same hardware so this could be a longshot...

---

### Post by xevix on 2008-02-02
The splash thing might work too, but here's how I solved it: [Solution]("http://ubuntuforums.org/showthread.php?p=4257269#post4257269")

edit:

The splash thing does _not_ fix brightness on powerbook G4 w/ nVidia card.

---

### Post by stream303 on 2008-02-04
Strangely enough, this might be an alternative worth looking into if you don't want to compile your own kernel.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/21478)

The last response by Eric Work is what worked for me since I have an nvidia card.

While it addresses the Ubuntu usplash issue, it has the secondary benefit of fixing brightness controls for some powerbooks.  It fixed my usplash issue to being back to normal color, but it doesn't enable a brightness fix for iMacs.  Definitely worth a look for powerbook owners.

---

### Post by xevix on 2008-02-09
stream303's solution works too, but I don't get the splash screen working (not that I care, since removing splash lets me see what's loading which is what I want anyway).

---

