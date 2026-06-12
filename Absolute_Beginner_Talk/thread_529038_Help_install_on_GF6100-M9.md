---
title: "Help install on GF6100-M9"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by KMW on 2007-08-18
I have 7.04 installed on 2 other machines but can't get it to run with this motherboard. It is a Biostar GF6100-M9 using all O/B hardware and 1 gig memory. Monitor is an Acer AL1916W wide screen.

I have been able to load and run Mandriva 2007 and Mepis from a harddrive on this setup but not Ubuntu Feisty. It will start to load then gives an error for XSERVER. So I don't know if it is the chipset or the monitor that is causing the problem.

Right now I do not have Feisty installed on a drive but have one I can format and use. It currantly has Mepis on it but would rather use Feisty.

So if anyone would be interested in walking me through this I would appreciate it.
Thanks.

---

### Post by logos34 on 2007-08-18
It's not the board.  See [this]("https://wiki.ubuntu.com/Biostar_Geforce_6100-M9?highlight=%28geforce%29%7C%286100%29").
(I have the Tforce).

So it may be that the graphics driver it is loading ('nv'?) will not work with your widescreen monitor

Try safe graphics mode or use the vesa driver.

---

### Post by logos34 on 2007-08-18
You might want to just try the ubuntu text-mode Alternate install CD.  If after installation the X server still won't load, download and install the nvidia driver from the command line:

sudo apt-get install nvidia-glx-new

sudo nvidia-glx-config enable

---

### Post by KMW on 2007-08-19
> **logos34 said:**
> You might want to just try the ubuntu text-mode Alternate install CD.  If after installation the X server still won't load, download and install the nvidia driver from the command line:

sudo apt-get install nvidia-glx-new

sudo nvidia-glx-config enable

Can these be installed from the command line after I reinstall from the LiveCD?
Still learning command line usage. I will need both of these lines? Can I install them at the same time?
Would using a CRT monitor male a difference to get it loaded and working then change  to the LCD?

Thanks for the leads!

---

