---
title: "[SOLVED] display problem on my hp"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by saveferris7872 on 2008-04-15
i just finished installing ubuntu on my hp dv6636nr laptop. all was fine on the live cd but when i booted it up for the first time, the display was completely out of whack. it looks like someone took the display and sliced it into a bunch of horizontal stripes and then shifted them to the right so it looks like i have four of the same displays overlapping each other.

ive been following  dark_stangs tutorial on istalling ubuntu and have followed it to the T up to **Post Installation Setup** where the display issue first arose. [http://ubuntuforums.org/showthread.php?t=575750&highlight=dv6636nr]("http://ubuntuforums.org/showthread.php?t=575750&highlight=dv6636nr")

any help would be greatly appreciated as i am eager to try ubuntu. thanks

---

### Post by Inxsible on 2008-04-15
Happens sometimes.

What graphics card do you have? If you are not sure, open up a terminal and type in ```
lspci | grep VGA
``` Post the output here.

---

### Post by saveferris7872 on 2008-04-15
NVIDIA GeForce 7150M / nForce 630M

---

### Post by Inxsible on 2008-04-15
> **saveferris7872 said:**
> NVIDIA GeForce 7150M / nForce 630MOk. Have you enabled the restricted drivers ?

---

### Post by saveferris7872 on 2008-04-15
no. i cant see anything im doing on the display when i boot into ubuntu. im on my vista partition right now

---

### Post by Inxsible on 2008-04-15
> **saveferris7872 said:**
> no. i cant see anything im doing on the display when i boot into ubuntu. im on my vista partition right nowok. Try and boot into the recovery mode and then execute this command```
sudo aptitude install nvidia-glx-new
``` then```
startx
``` if that doesnt work, you might have to reconfigure xorg -- which is pretty straight forward too.

---

### Post by saveferris7872 on 2008-04-15
nope, that didnt do anything

---

### Post by Inxsible on 2008-04-15
> **saveferris7872 said:**
> nope, that didnt do anythingOk. Back in the recovery mode type this command```
sudo dpkg-reconfigure xserver-xorg
```Then select Vesa as your driver and then select the appropriate resolution. Once you can log in to Ubuntu, we can re-enable your restricted drivers.

---

### Post by saveferris7872 on 2008-04-15
thanks a lot. it seems to be working now so im gonna finish up this tutorial and hopefully be enjoying by new OS.

i did get an error though after i logged in saying there was a problem loading OAFIID:GNOME_FastUserSwitchApplet and asked if i wanted to delete it. should i?

---

### Post by Inxsible on 2008-04-15
> **saveferris7872 said:**
> thanks a lot. it seems to be working now so im gonna finish up this tutorial and hopefully be enjoying by new OS.

i did get an error though after i logged in saying there was a problem loading OAFIID:GNOME_FastUserSwitchApplet and asked if i wanted to delete it. should i?
No dont delete it. Honestly I have never seen that error so I cannot comment, but the fast user switcher applet in Ubuntu is far from perfect :(

---

### Post by saveferris7872 on 2008-04-15
ok. thanks again for the help

---

### Post by Inxsible on 2008-04-15
> **saveferris7872 said:**
> ok. thanks again for the helpyou are welcome. You can mark your thread solved by Thread Tools>>Mark thread as solved :)

---

