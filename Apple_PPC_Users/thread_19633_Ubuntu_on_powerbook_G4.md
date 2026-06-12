---
title: "Ubuntu on powerbook G4"
date: 2005-03-12
forum: Apple PPC Users
---

### Post by gtjacket7483 on 2005-03-12
I have installed the current update of Ubuntu linux on my 17" powerbook G4. It appeared to install properly. To install i ran install video=ofonly -power4.

It installed fine, i got the updates off the net, through the CD install. It told me to remove the CD and finish install through the option in yaboot. It seemed to go fine and it proceeded to the GUI OS. When I go there the screen was a mix of colors with nothing discernable. I had to hold the power button to restart. Any ideas?

---

### Post by Viro on 2005-03-13
I'm surprised it actually installed. You're not supposed to use the Power4 or Power3 options, since you actually have a PowerPC. This may be the source of the problems.

It could be a problem with your Xfree86 configuration. Once the funny coloured screen loads up, do CTRL+ALT+F1 to load up a text console. Log in, and if possible, post the contents of your /etc/X11/XF86config-4 or /etc/X11/xorg.conf, whichever exists at the time.

---

### Post by ssam on 2005-03-13
if i remember correctly the G4 is based on the Power3 and the G5 is based on the Power4. but i don't know if they are similar enough to run the Power optimised kernels.

I think we need to wait until after GCC 4 before we get good optimisation for altivec.

[http://ubuntuforums.org/showthread.php?t=16691&highlight=altivec](http://ubuntuforums.org/showthread.php?t=16691&highlight=altivec)

---

### Post by Entity on 2005-03-13
FYI, I have installed Ubuntu PPC hoary on my powerbook G4 17" 1,5GHz two days ago using the default install option.

it's now using the powerpc version. I still have issues but I'm progressing ;)

---

### Post by gtjacket7483 on 2005-03-13
alright, i reinstalled and did not select video=ofonly -power4.  i just did the default install without selecting anything.  i have an error im guessing in my horizontal sync rate, im getting strange horizontal lines that appear to be uneven.  i have tried multiple sync rate ranging from 28-49, to my current of 30-107.  these are just guesses based on others laptops. here is the display portion of my XF86Config file.
Section "Monitor"
	Identifier	"Color LCD"
	HorizSync	30-107
	VertRefresh	50-185
	Option		"DPMS"

---

### Post by Entity on 2005-03-13
I think I had the same problem with Debian and XFree86, are you using hoary or warty?

I use hoary (Xorg) and did not have that problem. To me it seems stable after two days of use ;)

---

### Post by gtjacket7483 on 2005-03-13
im using warty, how do i switch(im new to this whole linux thing)

---

### Post by Entity on 2005-03-13
Download this: [http://releases.ubuntu.com/hoary/hoary-preview-install-powerpc.iso](http://releases.ubuntu.com/hoary/hoary-preview-install-powerpc.iso), burn it and use it in order to create a clean new install.

Or I guess you could upgrade your system using apt-get, but I would personaly go for the first option.

---

### Post by gtjacket7483 on 2005-03-13
would i install with the default, or should i do video=ofonly or video=ofonly -power3 or -power4

---

### Post by ssam on 2005-03-13
try the default first

---

### Post by Viro on 2005-03-13
[QUOTE=ssam]if i remember correctly the G4 is based on the Power3 and the G5 is based on the Power4. but i don't know if they are similar enough to run the Power optimised kernels.

I think we need to wait until after GCC 4 before we get good optimisation for altivec.

[http://ubuntuforums.org/showthread.php?t=16691&highlight=altivec](http://ubuntuforums.org/showthread.php?t=16691&highlight=altivec)[/QUOTE]
 Power and PowerPC are different architectures. They may share some similarities, but there are enough differences that can bite you in the behind.

Choose the PowerPC option. The kernels on the PowerPC build are optimized for G3 and G4 processors.

---

### Post by Viro on 2005-03-13
[QUOTE=gtjacket7483]alright, i reinstalled and did not select video=ofonly -power4.  i just did the default install without selecting anything.  i have an error im guessing in my horizontal sync rate, im getting strange horizontal lines that appear to be uneven.  i have tried multiple sync rate ranging from 28-49, to my current of 30-107.  these are just guesses based on others laptops. here is the display portion of my XF86Config file.
Section "Monitor"
	Identifier	"Color LCD"
	HorizSync	30-107
	VertRefresh	50-185
	Option		"DPMS"[/QUOTE]
 My monitor is configured with
HorizSync 25-60
VertRefresh 30-90

It works fine. You might want to try those values and see. I think anything above 100 is dangerous and can damage your LCD as LCDs *never* have a refresh rate that high.

---

### Post by Entity on 2005-03-15
Note that my monitor was autoconfigured properly.

Powerbook G4 17" 1.5GHz

---

