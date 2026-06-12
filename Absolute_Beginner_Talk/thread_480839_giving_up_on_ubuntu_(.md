---
title: "giving up on ubuntu :("
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by mitch707 on 2007-06-21
ok you may have seen my other posts im just hoping form somebody who can help me with this problem i have reinstalled installed and reconfigured i have followed most of the guides people have given me 
ok installed the nvidia driver for my two 7300 LE cards and i still had a blank screen i reconfigured the xserver stil l blank screen and reinstalled and repeated

---

### Post by skymera on 2007-06-21
hummmm....
when u reconfigured, did u select the correct driver?

this most liekly been mentioned, i havent seen your other posts. sorry .

---

### Post by mitch707 on 2007-06-21
yes i selected the right driver

---

### Post by Crafty Kisses on 2007-06-21
> **mitch707 said:**
> yes i selected the right driver

You selected the "nvidia-glx-new"?

---

### Post by mitch707 on 2007-06-21
yes

---

### Post by Crafty Kisses on 2007-06-21
> **mitch707 said:**
> yes

That's weird, how much RAM do you have?

---

### Post by mitch707 on 2007-06-21
1gb

---

### Post by Crafty Kisses on 2007-06-21
> **mitch707 said:**
> 1gb

What's your processor?

---

### Post by mitch707 on 2007-06-21
i have a AMD 3200  nathlon 64 venice 2.2ghz and 300gb HD and two 7300 LE cards

---

### Post by crispy_420 on 2007-06-21
This should cover all the basics to get up and running:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by mitch707 on 2007-06-21
ive tried lots of things in that guide and nothing seems to work i just keep on getting a blank screen install nvidida kill x restart x stiil blankv reconfigure x still blank and ive even reinstalled ubuntu nothing works

---

### Post by logos34 on 2007-06-21
I'd try the proprietary driver straight from nvidia website.  New version for Geforce 7 series cards just released today:
**[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html")**

Then use Method 2 in this howto:
**[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")**

---

### Post by mitch707 on 2007-06-21
can anybody reccomend another great distro besides fedora i dont have enough discs

---

### Post by mitch707 on 2007-06-21
but the probelm is i have no GUI so i cant download the, fomr the nvidia site 
can i ?

---

### Post by Celegorm on 2007-06-21
You can download from the command line. Try ```
wget <website>
``` replacing <website> with the URL of the download.

---

### Post by logos34 on 2007-06-21
use the live cd...then save it to a usb stick, or mount your root partition and save it to your desktop. Then from the console you'll cd over to the directory and run 'sudo sh NVIDIA-Linux-etcetc.bin' and that starts the interactive installer.

edit: wget would be easier, as celergorm suggested

---

### Post by mitch707 on 2007-06-21
ok so would i mount my windows partition and cna ubuntu se a ntfs partition ?

---

### Post by Crafty Kisses on 2007-06-21
> **logos34 said:**
> use the live cd...then save it to a usb stick, or mount your root partition and save it to your desktop. Then from the console you'll cd over to the directory and run 'sudo sh NVIDIA-Linux-etcetc.bin' and that starts the interactive installer.

edit: wget would be easier, as celergorm suggested

Yep, that should work. If not remember to post back.

---

### Post by jimrz on 2007-06-21
just a thought, maybe the problem is not with the vid card but with the way xorg + nvidia driver has your monitor configured. check your monitor specs at the oem's website and try entering whatever the y list for refresh rates when you do a reconfigure.

---

### Post by mitch707 on 2007-06-21
ok im gonna try this to see if it will work but if doesnt what do you think of pclinuxos ?

---

### Post by swoll1980 on 2007-06-21
> **mitch707 said:**
> can anybody reccomend another great distro besides fedora i dont have enough discs

Pclinux is pretty cool if you and Ubuntu can't work out your differences

---

### Post by logos34 on 2007-06-21
here's the url you'd use with wget:

> wget [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run)

Can't promise it'll work, you might even have to step down a release or two, but if you're not having any luck with nvidia-glx-new, give it a shot.

---

### Post by mitch707 on 2007-06-21
ya no luck im just switching distros

---

