---
title: "ATI TV-out with"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by RonnnL on 2008-01-12
I'd like to switch to Ubuntu permanently but one problem still makes me revert to XP often: TV-out support and dual screen support. I want to tackle the TV-issue first:

I have a ATI x1650 Pro. In 'screens and graphics' it says: Graphics card ATI Radeon fbdev, Driver fglrx. No idea if that's the most appropriate driver at this time, but it works...

Enabling tv-out with the 'xrandr'-method, seen in other posts, results in a BADREQUEST-error. I've got no Linux-experience at all, so am a bit afraid of ruining my driver again... Any ideas how to tackle this one?

---

### Post by RonnnL on 2008-01-12
Ouch... I should have edited the 'subject'-field. If an administrator could change it in something like ' ATI x1650 TV-out issues', i'd be grateful.

---

### Post by Dr Small on 2008-01-12
Have you tried out atitvout yet ?
[http://ubuntuforums.org/showthread.php?t=554095](http://ubuntuforums.org/showthread.php?t=554095)

Dr Small

---

### Post by nikoPSK on 2008-01-12
Have you tried atitvout?

EDIT: ohhh I'm too late... :lolflag:

---

### Post by Dr Small on 2008-01-12
> **nikoPSK said:**
> Have you tried atitvout?

EDIT: ohhh I'm too late... :lolflag:
Slightly... lol :D

---

### Post by nikoPSK on 2008-01-12
> **Dr Small said:**
> Slightly... lol :D

well, I open all my subscriptions in new tabs and some of them have to wait for a bit to actually get posted by me from... :lolflag: that's fine, we all benefit. :)

nikoPSK

---

### Post by RonnnL on 2008-01-12
I tried to install atitvout, but the 'sudo atitvout detect' command doesn't yield any results...  Am I using an appropriate ATI driver at the moment? Or should I switch to another one?

(What does 'sudo' mean by the way? I should look up some basic Ubuntu tutorials; thought that I could manage with a simple LiveCD install and some minor tweaks, but it turns out that Ubuntu is not installable without some basic terminal command knowledge... )

---

### Post by CarpKing on 2008-01-12
"sudo" allows you to act as root (able to modify any files).  Without it you can only modify files in your home directory.  

For both your issues, I think you'll probably want the Catalyst control center.  I never had it back when I was using fglrx, so I don't know if it's automatically included these days or not.  The Xrandr stuff I believe only works with the open-source drivers, which you were using before you installed fglrx.  They are slower, though, and you might not have 3d acceleration if your card is at all new.

And don't get upset if atitvout doesn't work.  It hasn't been modified in years and only guarantees that it will work on a few cards.

---

### Post by RonnnL on 2008-01-12
Thanks. I'll try and find Catalyst Control Center somewhere. I can't find it at the ATI-site though, they only let me download the full driver package which I don't need since my current one is working perfectly. Is the Control Center available through add/remove applications or the synaptic package dialog? Can't find it right away...

---

### Post by RonnnL on 2008-01-12
I cannot find the catalyst control center. However, 'Aticonfig' does do -something- in the terminal window. But when I want to play around with the various settings, the system 'could not find the configuration file'...

I suppose there is an intuitive graphic version of aticonfig available? Not much use in having a nice GUI when everything is configured in terminal windows... Up till now my Ubuntu-experience hasn't all been that pleasant; I'm a bit frustrated about the 'it's easy to switch!' tone on the website. With partitioning errors, keyboard incompatibility, printer problems, tablet incompatibility and graphic driver & tv-out-issues, all needing difficult tweaking in terminal windows, that just isn't fair... 

I still have some patience left though ;)

---

### Post by CarpKing on 2008-01-13
Well, like I said, I've never used the thing myself.  I've just heard reference to it in threads about ATI stuff.  I think their dual-screen function is called bigdesktop, so a forum search for that might help you out.

---

### Post by RonnnL on 2008-01-15
I'm still a bit confused with the ATI drivers. Didn't get TV-out working yet. Another problem is that sometimes, when I start Ubuntu, my secondary VGA-monitor is recognized as my primary one, resulting in working on a low 1024x768-resolution on an old 15"... I temporarily disabled the second monitor, but am still stumbling in the dark about how to configure my displays. The 'screens & graphics'-settings screen doesn't exactly give a lot op options... All the 'enable secondary' options etc. are grayed out.

---

### Post by legend2440 on 2008-01-15
I have a ATI Radeon 9660 and I finally got TV Out to work on Gutsy after a lot of searching for info with Google.

To check if you have the ATI Catalyst Control Center installed type amdcccle in a terminal. If it doesn't pop up you probably have to install latest drivers from ATI

Actually the first thing I did was install the latest ATI drivers using Envy at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then i added this section to Xorg.conf using command below and then reboot

sudo gedit /etc/X11/xorg.conf

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "NTSC-M"
	BusID       "PCI:1:0:0"
EndSection

Also if you type aticonfig in terminal all the options for configuring your card will be shown
Hope that helps

---

### Post by sonofabics on 2008-01-22
Hi,

I have a radeon 9600 @128mb.
Finally i got tv out working quite nicely. (dual head separate screens separate resolutions)
I had been fighting with the ATI driver at the first place, reading these forums and how to-s i was able to get it working with 3d somehow after about a week.
After that came the problem of the TV-out the ati control center did not make it to work. So i came back to the forums and got it working by hacking a lot.

If you still have the problem, i can provide xorg.conf and other bits but i am working now on XP in the office:(  

I consider to sum up my experiences and provide small how to about my configurations.

cheers

---

