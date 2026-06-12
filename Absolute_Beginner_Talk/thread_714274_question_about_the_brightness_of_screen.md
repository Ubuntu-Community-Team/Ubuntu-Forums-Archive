---
title: "question about the brightness of screen"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-03
Hi
I have just installed Xubuntu in thinkpad t61. Compare to the vista operating system, the screen in xubuntu is dark. Can any one help me to fix this problem

---

### Post by Pandemic187 on 2008-03-03
To my knowledge this is a known issue, but it is one that has not been fixed. I have the same problem with my laptop, and the only way I can really adjust the brightness is while the boot screen is loaded (I believe), or by dual-booting - booting into Windows, adjusting the brightness, then booting back into Ubuntu, as it will change for Ubuntu as well. Yes, it's very annoying, but it hasn't been fixed as far as I know.

---

### Post by thungmail on 2008-03-03
Hi
I was on Xubuntu, then i restared my computer and i booted into window vista. Into vista,I adjusted the highest brightness and then I switched back into Xubuntu(after restar and boot into Xubuntu).However, the brightness of screen ( in Xubuntu)is s as same as before.I am not sure I followed the step.Just let me know about it.

---

### Post by gigaferz on 2008-03-03
im not expert but some thinkpads have a "Function" button and extra functions on some keys to adjust the lcd brightness,by pressing it you can get things like turning off the lcd,adjust brightness and switch to an extra monitor,look at your keyboard or go to power management to see if there is an option to 
adjust it. 

i have a t20 and i just saw pictures of the model you have so ,it does have the function button. is the "Fn"

---

### Post by gigaferz on 2008-03-03
i see, unfortunately i ve never used xubuntu, but
I have heard a lot of times, if it works in Debian it works in ubuntu.
>  Display

Thinkpad T61 comes in two flavour : a more powerful (and power greedy) Nvidia, or a Built-in Intel (965) chipset.
Display Brightness

Brightness keys doesn't work by default. you can still use Gnome's "Brightness Applet" (FIXED in Lenny)

You can get it to work, if you modify /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi : duplicate T60 section, and replace T60 with T61.

        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.version" string="ThinkPad T61">
		<merge key="laptop_panel.brightness_in_hardware" type="bool">true</merge>
	</match>



I found it here [http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html](http://www.klabs.be/~fpiat/linux/debian/Etch_on_Thinkpad_T61.html)

however ill keep looking around

By the way, anybody outhere we need help some expert advise here

---

### Post by gigaferz on 2008-03-03
i just found on the synaptic package manager "tpb"

program to use the IBM ThinkPad(tm) special keys
This program enables the IBM Thinkpad(tm) special keys. It is possible to bind
a program to the ThinkPad button. It has a on-screen display (OSD) to show
volume, mute and brightness of the LCD.

It should work with xubuntu,

there is also gddccontrol

I searched for "brightness" in synaptic

I always had issues installing *buntu on my t20, however you dont mention any hassle... lucky you...

here is more, [http://ubuntuforums.org/archive/index.php/t-613949.html](http://ubuntuforums.org/archive/index.php/t-613949.html)

i found another page @ wiki ubuntu something it says they fn keys work but in the terminal, however is  very old and does not have any useful information

let us know how things go for you

---

