---
title: "Linux distribution which looks like Windows"
date: 2013-10-04
forum: Any Other OS
---

### Post by Cal2 on 2013-10-04
Hallo

I want to make a bootable usb with a linux distibution, that look like Winodws and offers browser and office tools.

It has to look linke Windows (the more the merrier), and I like to know if I can change to look of ex. the desktop and save it into the bootable usb.

It all has to work from the usb. No harddisk. 

Thanks in advance

---

### Post by ibjsb4 on 2013-10-04
Once you understand you new operating system you can just about change them all to look like windows, but out of the box is [Kubuntu]("https://www.google.com/search?q=kubuntu+pictures&client=ubuntu&hs=g1Q&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=FblOUtZnhuT0BPDGgaAD&ved=0CC4QsAQ&biw=870&bih=830&dpr=1.09").

---

### Post by erasmusp on 2013-10-04
I agree on Kubuntu but I would rather suggest LXLE -  "LXLE is a respin of Lubuntu aiming at a fast and capable desktop for ageing computers. Version 12.04.3 has just been unleashed: "LXLE Paradigm goes final with 12.04.3 update. 'Paradigm' is a tentative attempt to create four different desktop paradigms for users to choose from once they start up their aging computers when using LXLE. LXLE paradigm is not an attempt to completely mimic other desktops features and functions but to provide a desktop scheme that is familiar to all different types of computer users whether you are comfortable with Linux, OS X or Windows operating system. Currently the paradigms available at start-up are, GNOME 2 (G2), Windows (XP), OS X (OSX) and Ubuntu's Unity. Each desktop can be entered and/or used at any time, and you can switch back and forth at will." Have a look at [http://lxle.net/](http://lxle.net/)

---

### Post by Cal2 on 2013-10-04
Thanks.

I´ll try

---

### Post by Beren Camlost on 2013-10-04
If you want it to look like Windows, go with Zorin OS.

---

### Post by orb9220 on 2013-10-04
> **Beren Camlost said:**
> If you want it to look like Windows, go with Zorin OS.
Cool Avatar Beren being an old Commodore Amiga user and Selling Amiga computers for 2 years.
Newtek Video Toaster Ruled! :P


[http://zorin-os.com/](http://zorin-os.com/)

[Zorin OS 7.1 Lite is released]("http://zoringroup.com/blog/2013/09/30/zorin-os-7-1-lite-is-released/")
30 September, 2013 - All, Zorin OS

> The Zorin OS Team have released Zorin OS 7.1 Lite, the latest evolution of the Zorin OS Lite series of operating systems, designed specifically for new Linux users utilizing old or low-powered hardware. This release is based on Lubuntu 13.04 and uses the LXDE desktop environment to provide one of the fastest and most feature-packed interfaces for low-spec machines.

---

### Post by Cal2 on 2013-10-10
Thank for the ideas. 

But it has to be much faster at booting from usb. 

Some one know a fast booting Linux LIVE version - boot from USB.

---

### Post by mastablasta on 2013-10-11
booting form USb depends on how many things get laoded when you start up the OS. and also what kind of USB prot and USB stick is used (how fast).

when you boot live the whole system loads itself into ram, so having neough ram and good PCU is also beneficial to fast boot.

in short you can get fast boot OS but might not have all the things you need to boot form any mashcine, or you can tollerate a lsightly longer boot time while plenty of things get loaded and work out of the box on live boot.

AntiX - should be fast. debian based uses icewm ina windows98 kind of setup, has plenty of things added.

if you want something really small and fast then Slitaz or puppy linux (possibly the version that uses Ubuntu repositories).
Bodhi linux is also very fast and one of the looks/themes it comes with is very similar to windows.

you can also create your own using system imager (formerly known as remastersys).

---

### Post by Cal2 on 2013-11-01
Thanks for yours replyes

My demands for a Linux solution

Fast boot on USB
Light a go on the internet
Easy update for latest java to go to online banking
Must work on so many different PCs as possible
Must like to look like windows 7

---

### Post by neu5eeCh on 2013-11-01
> **Cal2 said:**
> Thanks for yours replyes

My demands for a Linux solution

Fast boot on USB
Light a go on the internet
Easy update for latest java to go to online banking
Must work on so many different PCs as possible
Must like to look like windows 7

Can't have it.

Not unless you build it yourself -- which you *can* do via Debian or OpenSuse (make your own spin), and Fedora, I think. (Which, so I've read, isn't hard to do. It's all automated.) The problem is the window compositing. At present, the only DE that looks like Windows 7 out-of-the-box is NetRunnerOS - Dryland, which uses KWIN. Forget anything based on LXDE, XFCE, Gnome, Unity, Cinnamon, yadda, yadda, yadda. KDE is what you want if you want the glassy effects of Windows 7 -- OR -- a modified DE (like XFCE) that uses COMPIZ instead of XFWM4 (or KWIN for that mater). It's all about the glassy effects. Only KWIN and Compiz/Emerald do it.

The problem is that KDE isn't quick to load on a USB -- not unless you heavily customize it so that you're only loading the drivers pertinent to your system (see Debian); but then that means it won't work on as many different PCs as possible. You can try COMPIZ, but that comes with its own unpredictable drawbacks when mixed with a variety of hardware.

You want incompatible goals.

If you want the eye-candy of Windows7, then you're going to have a slower load time via USB (and potential conflicts with older AMD hardware).

If you want a DE that's fast, and works on just about every system, then you're better off with a DE like LXDE (no compositing), and no pretty Windows7-like eye-candy. Give up on the eye-candy, and you can more or less have what you want with something like ZORIN OS.

---

### Post by PeterRJG on 2013-11-02
One that is designed to look like Windows is Linux Deepin. [http://www.linuxdeepin.com/index.en.html](http://www.linuxdeepin.com/index.en.html)

I'm not that fond of it, it's a bit too cute for my liking and it probably fails in many of the OP's criteria.

---

### Post by leeper69 on 2013-11-02
Hi give puppy precise a try it loads into ram on bootup. it dosent look like windows but it is fast.

---

### Post by monkeybrain20122 on 2013-11-04
Why?? This is perverted. :) I dislike kde because it looks too much like Windows. Customizing kde for me means to make it doesn't look like Windows.

---

### Post by Buntu Bunny on 2013-11-04
Wasn't this what Linspire was supposed to do? Take a look at [Linux Lite]("https://www.linuxliteos.com/").

---

