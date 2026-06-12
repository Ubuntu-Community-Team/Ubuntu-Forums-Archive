---
title: "Ubuntu 8.04 + VMWare Fusion + MacBook = Dual Monitor?"
date: 2008-04-30
forum: Apple Hardware Users
---

### Post by bronkeydain on 2008-04-30
Hello people,

I would LOVE to be able to use dual monitors on my Ubuntu. I was told Dual Monitors would be supported on Ubuntu v8.04. 

The thing is that I use it on my MacBook running VMWare fusion. Does any one know if this is going to be possible at all?

---

### Post by mkgkg on 2008-05-01
yes...you have to added this subsection on your /etc/X11/xorg.conf in the section screen:
[PHP]sudo gedit /etc/X11/xorg.conf[/PHP]

add this subsection:
SubSection "Display"
		Depth 24	
		Virtual 2304 1600
	EndSubSection

my virtual is 2304 1600 because one of my monitor is 1280x800 and the external is 1024x800.

then close the file and reboot and type this in console
[PHP]sudo update-initramfs -u[/PHP]
and then reboot again,connect cable  and type in console:
[PHP]
xrandr --output VGA --auto --right-of LVDS[/PHP]

to disconnect:
[PHP]
xrandr --output VGA --off[/PHP]


on my mac works well. if you wanna you can get the grandr from synaptic. is a gui application that you can use after changed xorg.conf file.:)

---

### Post by bronkeydain on 2008-05-01
Hi mkgkg, thanks for your reply.

As soon as I add the subsection my graphics go back to 800 x 600.
Do you have this working with VMWare fusion?

---

### Post by bronkeydain on 2008-05-01
By the way this is what I added, I have a 1280 x 1024 monitor plus the MacBook on 1280 x 800

SubSection "Display"
Depth 24	
Virtual 2560 1824
EndSubSection

---

### Post by cyberdork33 on 2008-05-01
> **bronkeydain said:**
> Hi mkgkg, thanks for your reply.

As soon as I add the subsection my graphics go back to 800 x 600.
Do you have this working with VMWare fusion?
he was showing how to literally make a second monitor on your linux system. This should not be required on a VM (if it is even possible).

---

