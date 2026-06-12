---
title: "Question about 7.04....."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Christopher on 2007-05-08
I installed 7.04 via the update manager and when i booted, i booted to a command prompt login. I then tried to install my nvidia drivers(Envy) via the command prompt and it says envy isnt compatible with 7.04. Is their a command i can use to get some drivers installed so i can at least get to my desktop. Thank you in advance.

---

### Post by rai4shu2 on 2007-05-08
You could try "sudo nano /etc/X11/xorg.conf" and change where it says:

Driver          "nvidia"

to say:

Driver          "nv"

---

### Post by bulldog on 2007-05-08
To install nvidia drivers ```
sudo aptitude install nvidia-glx-new
```
You should have installed the restricted modules on fore hand.
[code]sudo aptitude install linux-restricted-modules-'uname -a'[/code

---

### Post by starcraft.man on 2007-05-08
> **Christopher said:**
> I installed 7.04 via the update manager and when i booted, i booted to a command prompt login. I then tried to install my nvidia drivers(Envy) via the command prompt and it says envy isnt compatible with 7.04. Is their a command i can use to get some drivers installed so i can at least get to my desktop. Thank you in advance.

After you do the above, you need the [latest debian]("http://www.albertomilone.com/nvidia_scripts1.html") for envy, I don't know what version the repo is but only 0.9.2 is working with feisty.

I also am not sure what you mean by "I installed 7.04 via the update manager", you have to install from a CD or network install... do you mean upgrade? If you did upgrade and didn't turn off your nvidia drivers before it, there are known problems that can occur...

---

### Post by Christopher on 2007-05-08
Thank you guys i'll give this a try.

---

### Post by Christopher on 2007-05-08
I downloaded the ISO & go to install it and select start or install and it loads then after a few minutes i get a flashing cursor then it goes away to a black screen. I see the activity light working like its doing something but nothing is happening, any ideas ?

---

### Post by Christopher on 2007-05-08
I see on the forums theres issues with monitor possibly going into sleep mode? Is there another way to get 7.04 installed?

---

