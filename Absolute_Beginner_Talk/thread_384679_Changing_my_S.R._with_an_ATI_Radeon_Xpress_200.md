---
title: "Changing my S.R. with an ATI Radeon Xpress 200"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by falciron on 2007-03-14
This seems to be one of the hardest graphics cards to find a driver for and to get a good resolution with. Here's my stats, see if you can provide a thorough list of instructions:

-OS: Ubuntu 6.10 Edgy Eft
-Processor: Intel Celeron D Processor 352
-Graphics Card: ATI Radeon Xpress 200 (Integrated) using a PCI-Express slot
-Top Resolution at the moment: 800x600
-Resolution used on Windoze: 1024x768
-Resolutions that it would be nice to have: 1024x768, 1280x1024

Thanks for the help!

---

### Post by Dr. Nick on 2007-03-15
Try manually adding them to xorg.conf?

Here is a link I made on how to do it
[http://www.geocities.com/aebcoat/xorgresproblems.html?20069#Fix_low_resolutions](http://www.geocities.com/aebcoat/xorgresproblems.html?20069#Fix_low_resolutions)

It should be the same for ati, though the link uses nvidia

---

### Post by igknighted on 2007-03-15
Try installing the ATI video drivers if you haven't already.  Search in synaptic for the package "xorg-drivers-fglrx" and install it, then run the command "sudo aticonfig --initial" in the terminal.  Then reboot and you should get your desired res.

---

### Post by falciron on 2007-03-15
Ouch. Didn't notice the reply. Well, now I've got another problem because of my impatience.:( 

I d/led and installed Envy, which I believed would work. It installed fine, but when I restarted, Edgy Eft came up with a black screen after it got done filling up the loading bar. The kettle drums sounded, so I assumed that the login stage was up. When I looked at the troubleshooting on Envy's page, I saw that I needed to do some editing of my xorg.conf file. Unfortunately, I realize that the only way to do this is in recovery mode, which is completely text-based, and I can't imagine that editing the xorg.conf file will be easy in this mode. Here's what I need to change in my "Screen" section:

Depth 16

Modes "1280x1024**_60**" "1024x768**_60**" "832x624" "800x600" "720x400" "640x480"

EndSubSection

And the same for Depth 24. Is it possible to do this, and if so, could I get some instructions?

Again, any help would be greatly appreciated.

---

### Post by lamalex on 2007-03-15
editing xorg in recovery mode is very easy
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Songwind on 2007-03-15
Also, remember that if your X screen comes up garbled or blank because of refresh rate, you can press CTRL-ALT-F1 and get a text-mode terminal, and do your editing there.  No need for recovery mode or live CD.

---

### Post by falciron on 2007-03-15
Igknighted, your instructions were ultimate. It worked perfectly on my dad's computer when we tried it out on his, which luckily I didn't run Envy on. Also, thank you to the rest of you guys for providing all of the answers I need to get my system working.

---

