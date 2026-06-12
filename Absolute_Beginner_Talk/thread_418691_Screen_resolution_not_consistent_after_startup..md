---
title: "Screen resolution not consistent after startup."
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by firstwave on 2007-04-22
Hi, 

I used Envy to install my nvidia graphics card. I did that by shutting down X server and loaded Envy, uninstalled pre-existing drivers, and installed a fresh new driver.

Everything was working well.. In the System Tools tab in Applications, there's a new Nvidia Setting. I used it to change my screen resolution from 1024 x 768 to 1280 x 1024. However, when I restart, the resolution goes back to 1024 x 768. 

Can someone explain/help me?

Thanks

---

### Post by bobplano on 2007-04-22
try going system>prefrences>screen resolution and changing the resolution there instead of whatever nvidia thing you are going to

---

### Post by firstwave on 2007-04-22
That won't work because 1024 x 768 is the highest resolution displayed there.

---

### Post by bobplano on 2007-04-22
add what ever resolution you need to your xorg

sudo gedit /etc/X11/xorg.conf

---

### Post by firstwave on 2007-04-22
Can you please show me how? I am new:(

THanks

---

### Post by bobplano on 2007-04-22
find the section that looks like this:
SubSection "Display"
		Depth		**24** #my own comment. make sure that the depth is whatever bit your screen is
		Modes		 "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

then change the modes to something like this 
Modes		**"1680x1050"**  "1280x1024" "1152x864" "1024x768" "800x600" "640x480"

this is my own example just replace 1680x1050 with whatever resolution you want

---

