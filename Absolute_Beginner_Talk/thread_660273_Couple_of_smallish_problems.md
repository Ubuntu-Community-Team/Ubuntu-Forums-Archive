---
title: "Couple of smallish problems"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by eeeandrew on 2008-01-06
hi guys, I've now been using ubuntu 7.10 for just over 3 months. I've got it up and running with some majorly complex help from various parts of these forums but I still have a couple of niggling problems

My soundcard does not work. I spent a few hours on the IRC channel and its still unsolved. we determined that the driver is installed and working properly and its a mystery why I always get squeaking out of the left speaker. sudo lspci for this card gave:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

anyone know where to get and how to install an alternate driver?

Second small niggling problem. I downloaded and use Emesene messenger. I need to run it each time by finding the executable file in a folder and running it. Anyone know how to put it into menus?

Last small concern I would like to make some changes to my desktop and there doesn't seem to be much I can do. Is there a program I can get or some new themes?

Also can anyone recommend any good linux/ubuntu beginners guides/books?

thanks for all your help so far and Happy New Year to you all,
Andrew

---

### Post by philinux on 2008-01-06
For the eye-candy install gnome-art from synaptic, makes it real easy.

Have you seen this.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869)

---

### Post by jonnywombat on 2008-01-06
To save having to navigate to the messenger every time is quite simple. Go to system >> pref >> main menu..

Then hit the new item button..then in the name add the name you want to give it.. then hit the browse button, and make your way to the file you wish to run and if it has an icon somewhere within it's folder you can add that by clicking in the launcher icon on the left...If you want to add a description then feel free but no real need to bother..Hit the OK button

You can then place the new launcher anywhere within your menus by dragging it around..hit close when your done and you should be good to go

Jonny

---

### Post by eeeandrew on 2008-01-06
johnywombat: thanks for the menu help worked first time

phillinux:thanks for the GNome art. at the moment it says downloading over 1000 wallpapers! is that gonna use hard drive space or is it more like a list and I can choose which ones I want?

also looking at the link in phillinux post I see theres a fix listed but I'm not sure how to apply it.anyone know how?

thanks again for all your help

---

### Post by philinux on 2008-01-06
The wallpapers are tiny.

---

### Post by timbounceback on 2008-01-06
they're just a list, don't worry :-)

---

### Post by eeeandrew on 2008-01-06
thanks guys, figured that out while having visions of losing my hard drive to 1000 picture quality images. got a nice sleek looking blue wallpaper now...shame the window borders and stuff are still brown but I'm working on it.

hmmm clicked install for an application type theme and theme manager popped up with the same list as before? do I have to save the downloaded theme somewhere then run with theme manager?

Can now clarify. I'm using the C2 for windows borders but I can't get options to combine it with other theme packs(icons and applications) to finish off the appearence. anyone know how?

Got it. need to click customize theme. thanks for the help

---

### Post by oldos2er on 2008-01-06
There are loads of themes and wallpapers at [www.gnome-look.org](www.gnome-look.org) .

---

### Post by eeeandrew on 2008-01-07
thanks to everyone for their help so far. We've managed 2/3! If someone could explain how to apply the fix listed in the link from phillinux initial post then I would be very grateful. Below is the excerpt from the forum posts which gives a directory and a line of code. I have no idea how to get to that directory or what to do with the code. If someone could explain this I may yet have sound in ubuntu!

> 
I can confirm that this fix:

"/etc/modprobe.d/alsabase file:

options snd-hda-intel position_fix=1 model=3stack"

Works for my laptop in Feisty.

thanks again for all your help,
Andrew

---

### Post by nikef on 2008-01-07
> **philinux said:**
> For the eye-candy install gnome-art from synaptic, makes it real easy.

Have you seen this.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/85869)


thanks for telling us about gnome-art
thats what i love about ubuntu,you learn something new every day :)

---

