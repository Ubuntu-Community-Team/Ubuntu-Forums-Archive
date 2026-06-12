---
title: "my last problem nvdia drivers on kubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Vodkayum on 2007-06-24
Kubuntu is turning out to be everything I wanted and more. Only two issues remain. The main one is how do update my nvdia drivers?

Envy will not install on kubuntu

I have a geforce 3 card and I'm using kubuntu 7.04 

Please help me and I will be forever done with Billy Boy and his Crappy windows

---

### Post by ajmorris on 2007-06-24
hmm, it can be tricky, but install all the nvidia packages from the repositories (Start Menu>> Administration >> Synaptic Package Manager) then, go into a terminal (Start Menu >> Accessories >> Terminal) then type ```
sudo gedit /etc/X11/xorg.conf
``` and scroll down to the section that will look something like this :

Section "Device"
	Identifier	"Geforce 3"
	Driver		"nv"
	BusID		"PCI:0:2:0"


Change the    Driver           "nv" part to         Driver         "nvidia"

restart X (ctrl+alt+backspace) and your done :)

---

### Post by Vodkayum on 2007-06-24
actually automatix just did it for me.
My nvdia drivers work now. Beryl is still a bit buggy though but oh well i can live without for now,

---

