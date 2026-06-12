---
title: "X.org Foundation Display screen resolutions"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-06-23
Hi,
I'm a 6 day newee to Ubuntu,
Dual boot from xp and Ubuntu,
When I installed Ubuntu Feisty the installation was defaulted to using the x.org display as i beleive the ATI 9250 card wasn't recognised, it doesn't appear on the hardware list. Anyway i have an intel core 2 duo and Gigabyte motherboard. At install the monitor was running thru the ATI Readon 9250 which is why I beleive I ended up with default settings all round?
I cannot find a config file as I beleive this edition of Ubuntu doesn't require one to install.
Any ways the default resolution is  "Monitor0 1280x1024".
I have a 22 inch viewsonic wide screen and the 1280x1024 doesn't do it justice.

1) How can I get a wide screen resolution set up?


2) The motherboard has an Intel 82945G chipset, how can i connect a monitor to this now and get it to work?

3) I've looked at the other posts around this topic but still cannot find an answer I can use.

4) How do I set up a config file if I need one etc.

5) should I reinstall and connect the mointor to the onboard chipset to get it to recognise it and get widescreen resolution?

Thanks for anyone that can assist me much appreciated.

Best Regards
Bill

---

### Post by ICUR2Ys on 2007-06-23
I am pretty new so you might want to wait until someone with a lot more experience gives you the info.  I had a ATI Radeon and it was suggested that I down load ENVY and use that to install the correct driver.  I did and it worked well for me.

---

### Post by phr0ze on 2007-06-23
> **wapfu said:**
> Hi,
I'm a 6 day newee to Ubuntu,
Dual boot from xp and Ubuntu,
When I installed Ubuntu Feisty the installation was defaulted to using the x.org display as i beleive the ATI 9250 card wasn't recognised, it doesn't appear on the hardware list. Anyway i have an intel core 2 duo and Gigabyte motherboard. At install the monitor was running thru the ATI Readon 9250 which is why I beleive I ended up with default settings all round?
I cannot find a config file as I beleive this edition of Ubuntu doesn't require one to install.
Any ways the default resolution is  "Monitor0 1280x1024".
I have a 22 inch viewsonic wide screen and the 1280x1024 doesn't do it justice.

1) How can I get a wide screen resolution set up?


2) The motherboard has an Intel 82945G chipset, how can i connect a monitor to this now and get it to work?

3) I've looked at the other posts around this topic but still cannot find an answer I can use.

4) How do I set up a config file if I need one etc.

5) should I reinstall and connect the mointor to the onboard chipset to get it to recognise it and get widescreen resolution?

Thanks for anyone that can assist me much appreciated.

Best Regards
Bill
Most resolution problems are because you have incorrect data in /etc/X11/xorg.conf
Open this file by going to a command prompt and type gksudo gedit /etc/X11/xorg.conf

Then go down near the bottom and add your resolutions something like this...

```
	SubSection "Display"
		Depth		24
		Modes		"1792x1344" "1600x1200" "1280x1024" "1280x960" "1152x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
```

The first one listed will be tried first. Usually only need to add to the 24 depth.

Then, here is the part everyone skips. Look up the horizontal and vertical sync specs for your monitor and set them in the monitor section. If you dont set these right you wont get your max resolutions.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-92    <----- CHANGE THESE
	Vertrefresh	50-85    <----- CHANGE THESE
EndSection
```

---

### Post by wapfu on 2007-06-24
Thanks,
Regards
Bill

---

### Post by wapfu on 2007-06-24
Hi,
Tried the "gksudo gedit /etc/X11/xorg.conf" it first asked for a password - gave it and nothing happened.

Explorered to the X11 file  and found the xorg.conf and opened it up.
Wasn't allowed to change anything "Do not have permissions"

There were alot of 'Displays" of various Depths and found the 24th.
Screen resolutions there seemed to point to a possibility that I should be able to have at least a "1280x960"
Can't get past first base.

The section on monitor seemed to have OK refresh rates

The section on "Device"
Idenifier    "Genric Video card"
Driver      "vesa"
dvsid        " PCI:3:1:0

What to do now to edit the xorg.conf?

Regards
Bill

---

### Post by Dscottmc7 on 2007-06-24
Newb here, exasperated!  tried everything....xorg.conf file -one line change at a time NO FIX still can only get to 1280x1024!  Have correct h/v refresh, "Dell2407WFP" and ideas from Dell forum, Ubuntu, you name it.  Can anyone help?  Dunno!  frustrated..:(

---

### Post by Dscottmc7 on 2007-06-24
Bill, sorry, did not answer ? .. in command line (or in terminal) type in sudo nano /etc/X11/xorg.conf and <enter> and you will be in the configuration file.  (assume that location) do ctrl W search "Monitor" (for the monitor section).  No the cursor should be blinking on the word "monitor." you can execute from that line.  Should backup file (ctrl O, rename, Entr) first. 

The "sudo" command will request your password to get you to "root."  The "nano" gets you to command line prompt (works either in graphic mode or in command [i.e. text] mode).

Now, what do do after that??? BGelieve me, I've tried virtually everything related to every line from monitor, screen, device, layout, and on that is on Ubunu, forums, Dell, 3 published books and STILL get 1280x1024.  I've crashed the xserver, lost the GRUB, you name it.  I can now restore everything from scratch...still know NOTHING, and still can't get the !@$@ resolution.  Help!!  anyone??

---

### Post by wapfu on 2007-06-25
Thanks
Regards
Bill

---

