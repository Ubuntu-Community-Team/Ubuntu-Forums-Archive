---
title: "Screen resolution"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by c500 on 2007-03-05
24 hours into Linux and my experience has crashed to a halt. for some unexplained reason my resolution changed from normal to so big that I cannot use the computer at all (lap top). I have no internet connection yet either so I am using a PC windows to ask for some help. I am not technically sophisticated so would not know how to write Unix code - nor could I likely access any screen to input. Can I reset up from the bios? Reinstall Ubuntu? I read on a more advanced forum about something called 915 but it means nothing to me. 

Any ideas or is 24 hours the end of my attempts to get into Linux.

---

### Post by radioouman on 2007-03-05
You need to get into the boot menu.  Then you can choose Ubuntu (recovery mode).  Once you get to a prompt, type: "dpkg-reconfigure xserver-xorg"
This will allow you to reconfigure the graphics adapter and choose your monitor's maximum resolution.

---

### Post by Bushfire on 2007-03-05
Boot into Ubuntu, and press CTRL + ALT + F1 then enter

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

And answer the setup questions there, then reboot.

---

### Post by radioouman on 2007-03-05
What does the "-phigh" switch do?

---

### Post by Bushfire on 2007-03-05
I'm not sure technically, but it just limits the questions to the display driver and the resolution. If I recall correctly (I could be wrong) without it, you get asked a lot more questions.

---

### Post by c500 on 2007-03-05
I followed as best I could the instructions but now I have a blank screen - and I cannot ctrl alt F1 anymore. I entered the command as suggested. I set the resolution to what I thought it should be - I entered and a message came up with a warning that I was overwriting manual settings. I pressed enter and then I got the command code ending in $ and then I was unable to exit. I had to turn the power off to reboot. Any ideas re the blank screen?

---

### Post by c500 on 2007-03-05
Now the screen is blank and unusable. How might I fix this? I seem to be going from bad to worse on all this

---

