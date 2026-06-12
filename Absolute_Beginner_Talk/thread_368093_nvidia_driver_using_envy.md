---
title: "nvidia driver using envy"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-02-22
Hi

Having problem with the Envy script which I accidentally installed the beta (6.1) and then purged this to install the latest stable nvidia driver (0.8.2). The beta driver did work but when I installed the stable one I was left with no X driver (just black screen where there should be a login window).

I changed the xorg.conf entry from "nv" to "nvidia" and this toggles whether I get a login window or blank screen respectively. I don't know the difference between these two btw. After I installed the stable driver but didn't auto configure xorg.conf a message appeared to change to nvidia but if I do this I get a blank screen so suppose the driver isn't loaded unless the entry is nvidia?

Any ideas as to what is wrong and how to check which driver is installed?

---

### Post by PartisanEntity on 2007-02-27
Do you have an NVIDIA Settings option under Applications > System/Tools (something like that, im not at my Ubuntu machine right now to check).

If you do have NVIDIA Settings open it and here you can check what version of the nvidia driver you have installed.

Have you tried to run the Envy script? It should clear up any problems you are having.

---

### Post by kelbizzle on 2007-02-27
yea with the envy script I usually remove any drivers I have installed and then use envy.

---

### Post by kelbizzle on 2007-02-27
.

---

### Post by Patrick K on 2007-02-27
Try running the script and uninstall drivers first, then try installing. It usually is a good idea to uninstall drivers before installing new ones. If you recall from windows, the video driver install instructions say to change drivers to the basic VGA drivers before installing the new one. 

Also, and I don't know why, I have better luck with the script if I edit xorg.conf myself rather then letting the script do it.

---

### Post by geezerone on 2007-02-27
I did uninstall the driver first and also ran the script and let it remove the old driver (beta) as well as manually changing driver to "nvidia". I have used the Envy script on another nvidia machine with a Ti4400 gfx card and worked with no problem. Wasn't sure if the problem was the type of card or the fact that I installed a beta driver first (which I suspect is the case)?

I am using the beta driver at present with no problem but would like to install the latest and greatest still.

TIA. :)

---

### Post by Patrick K on 2007-02-27
I suggest going to the Multimedia and video forum. Take a look at the sticky by tseliot, it's the last one. You might try PMing him with your issues. I really don't have any ideas.

---

### Post by ndefontenay on 2007-02-27
I would run envy again, choose option 1 to install.
It will remove it by itself if required.
Then choose all the default options for X configuration and restart of X server.

---

