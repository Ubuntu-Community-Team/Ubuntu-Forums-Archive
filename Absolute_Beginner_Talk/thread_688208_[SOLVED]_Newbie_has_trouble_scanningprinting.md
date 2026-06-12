---
title: "[SOLVED] Newbie has trouble scanning/printing"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by silverj on 2008-02-05
Hello All

After my first time install of Ubuntu, I was able to get my Brother HL-1250 scanner working (it is attached to my windows box).
My Canon N670U scanner is apparently 100% compatible with Ubuntu ([https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners)) and was detected upon connection to my Ubuntu machine (Gutsy)

However, making the two work together is somewhat trickier. Using XSane, the scanner works (almost) fine, in that it gives me reasonable quality scans with black lines or other artefacts I've read about on these forums. However, I cannot get it to accurately scan up to the borders of an A4 page (another problem I've read about on these forums). This is in the XSane 'Viewer' mode.

When I use the XSane 'Copy' mode, I get a different version of my page (scan edges slightly different from 'Viewer') making it rather difficult to use.

I've been playing with the XSane Advanced settings and used a test sheet of A4 paper marked in the corners, but I cannot make it work properly. Sometimes I find that XSane doesn't remember the Advanced I've set for it and reverts. I have also manually edited the .drc file in the sane folder, but no joy.
My printer is correctly set for A4 printing.

So, I have two questions:
[LIST]
[*]Can someone help me with the XSane settings for my scanner?
[*]or... How can I return to a completely original scanner/XSane set of settings? (Does simply uninstalling XSane really remove everything? What about uninstalling the scanner completely?)
[/LIST]

I new Linux & Ubuntu had one hell of a learning curve when I started and I've not been disappointed... ;-)

Under Windows, the base point for a scan is the bottom left of the scanning area, hence this is what I have been trying to set the scanner up for. Would the 'base point' in Ubuntu be one of the other corners, for example?

Any help you can give would be very appreciated, thanks.

---

### Post by drs305 on 2008-02-05
In the Preferences, Setup, Copy, the offsets are applied from the bottom left. If you hover your mouse over the numbers the program will bring up a balloon that says this.

I don't use a default paper size setting and have just set the dimensions to the actual dimensions of the paper I use. I have noticed a slight difference between the viewer and printout but with the offsets I have in the setup page my results are fairly consistent (and they don't disappear between sessions).

On the first tab of preferences, there is a "Save device preferences in default file at exit". I keep that checked. If you uncheck it the modified data would probably be wiped clean. My personal settings are retained in my home .sane/xsane/xsane.rc file. Note that if you use inches in the offset settings it is converted into some other value in the .rc file. You could rename this file and xsane would probably create a new / blank rc file the next time you started up the app. Just make a backup first.

---

### Post by silverj on 2008-02-05
Thanks for the reply drs305.

> **drs305 said:**
> In the Preferences, Setup, Copy, the offsets are applied from the bottom left. If you hover your mouse over the numbers the program will bring up a balloon that says this.
first.
Okay, I take the implication that I'm calculating from the bottom left. So now on Preferences->Copy I have 210, 297, 0, 0 for the fields Width, Height, Left O/s and Right O/s respectively. 


> **drs305 said:**
> On the first tab of preferences, there is a "Save device preferences in default file at exit". [...] My personal settings are retained in my home .sane/xsane/xsane.rc file.
I have the similar tick as you and it saves it in xsane.rc as you pointed out.
This is the config file for the XSane software; there is also a config file for the scanner (Canon:Can...N670U...LIDE20.drc in my case). This file contains the options in Window->Show Advanced Options selection.
Now I've set the settings in Preferences->Copy, as I remarked above, I see these reflected in the Advanced Options settings. How do you suggest I change these? Do I change these?
Or at least, what are your settings please? (If I can't get a perfect result, then I can stop if I have something that is as good as it will get!)

Also, in the main XSane window when Copy is selected, how should I set the 'Define image position for printing' option? (I have the little green square at the bottom left at the moment. I've not noticed it really make a difference to the output.)

Thanks once again for your reply!

---

### Post by drs305 on 2008-02-05
> **silverj said:**
> 
Also, in the main XSane window when Copy is selected, how should I set the 'Define image position for printing' option? (I have the little green square at the bottom left ...

I have the green square in the upper left even though the offsets are from the bottom left. I don't recall if I set this or if it was the default. I don't use A4. In the copy setup, I have the physical dimensions of the paper I use. 

On the main Xsane menu the dimensions near the bottom of the screen inside a rectangle are the dimensions to be scanned, as set up in the preview window. I keep these dimensions the same size as the paper I'm using. Because of that or perhaps just because I'm lucky I currently don't need any offsets. I used to have offsets with a different printer but don't recall now what they were.

---

### Post by silverj on 2008-02-06
Hmm... playing with settings (or perhaps equally not touching the initial ones...) seem to be the order of the day! I also noticed one can play with margins for the printer itself, independently of the scanner. At least I was able to revert those to the defaults.

I think I've got mine set up similarly to yours now, so it must be about as good as it gets, or at least as good as *I'm* going to get it. The joys of Ubuntu.

Thanks for your help.

---

