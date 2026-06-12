---
title: "messed my cpu up can anyone help"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by trauma1914 on 2008-04-15
I have a dell Lattitude D610 not sure what type of video card I have. If someone could tell me how to do that as well it would be nice....Everything was running fine til I installed compiz I wasn't ablt to get the cube effect.....I started looking into things and downloaded a progrm called Envy it woouldn't install the drivers automatically so I installed them manually...At this point I can't remember if I did ATI or Nvidia drivers...Now I boot to a screen that says "Failed to start the Xserver (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output" when I say yes it show me lots of info I'm not sure of the meaning of ....Then it says "The Xserver is now disabled. Restart GDM when it is configured correctly"..them I'm back to cammand line....Can anyone please help me

---

### Post by spiderbatdad on 2008-04-15
run the command: ```
sudo dpkg-reconfigure xserver-xorg
``` carefully read the dialogues and answer questions to the best of your ability. Use arrow keys to scroll or choose 'ok' and enter to enter your choices.

---

### Post by trauma1914 on 2008-04-15
can you tell me what my x server driver is would it be vga?

---

### Post by spiderbatdad on 2008-04-15
vesa is generally a safe choice

---

### Post by joshrobinson on 2008-04-15
> **spiderbatdad said:**
> vesa is generally a safe choice

yeah i would use vesa, but if you ever want to get compiz and the cube working, your really going to have to find out what kind of video card you have.. actually i just noticed you posted your pc's model number, i looked it up, and this is the video card you have

ATI Mobility Radeon X300 w/ 64MB dedicated RAM

when you get back into the gui, your going to want to install the ati/fglrx driver

---

### Post by spiderbatdad on 2008-04-15
```
sudo lshw -C video
```

or

```
lspci | grep VGA
```

will display your video card.

---

