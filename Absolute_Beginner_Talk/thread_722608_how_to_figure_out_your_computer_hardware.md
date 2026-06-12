---
title: "how to figure out your computer hardware"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-12
is there a code i can put in my terminal to figure out all or alot of my computers hardware?
what i need to know most is what is my graphics chip and what my wireless card that is built into my laptop but i'd really like to get the termial cod that will tell me most all of my system hardware.

---

### Post by glennric on 2008-03-12
There are several things you can do.  

To find out about pci cards (agp video included) use
```
lspci
```

For a more comprehensive hardware list use
```
sudo lshw
```

For a list of usb devices use
```
lsusb
```

This is just scratching the surface.

---

### Post by WelshChris on 2008-03-12
There are a few ls... commands to help, but the most pertinent would be 'lshw' as in ls hardware.  Best run as root =)

---

### Post by exodus_ on 2008-03-12
whoops never mind just re-read and he wanted terminal not GUI.

---

### Post by 1875 on 2008-03-12
You can also System -> Preferences-> Hardware Information for a GUI way.

---

### Post by 1875 on 2008-03-12
> **exodus_ said:**
> whoops never mind just re-read and he wanted terminal not GUI.

Beat me to it:lolflag:

---

### Post by drs305 on 2008-03-12
As mentioned, lshw is a good command. You can save the output in a really convenient format by running the following. It will save your configuration as an html file on your desktop:
```
sudo lshw -html > ~/Desktop/hardware.html
```

---

### Post by RadiationHazard on 2008-03-12
thanks for all the replies
the think i need to know the most is my wireless card in my sony vaio laptop
does anyone maybe know a code just to figure that out?
hah

---

### Post by glennric on 2008-03-12
If it is a pcmcia card you can try
```
lspcmcia -v
```

---

