---
title: "kubuntu &amp; iPod"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by fca_neo on 2007-03-04
Hi,

I started using ubuntu two months ago and now I switched to kubuntu. I wanted to get rid of windows so i did a clean install of kubuntu 6.10 and wiped the hda1 partition (it felt good).

When I was using gnome (and when I tried kubuntu by installing the kubuntu package in my gnome ubuntu) my ipod nano mounted automagically without any troubles and showed up on my desktop. I was able to access it with amarok, rythmbox, nautilus, etc..

Now, I plugged it in and it doesn't show up automatically. I can manually mount it, but amarok cannot find it automatically (it can find it manually). Also, i cannot get a nice icon on my desktop.

Btw, I have an external usb dvd writer and it worked perfectly and mounted automatically.

I think kubuntu should mount the ipod automatically but i cannot get it to work. Any help would be very appreciated.

I tried using google and I found this ([https://wiki.ubuntu.com/KubuntuIpod](https://wiki.ubuntu.com/KubuntuIpod)) but I don't really understand it and I'm sure there is an easier way.

Other than that, KDE is nice and very very customizable. I think gnome was a good choice for the main distro.

 Thanks,

Carlos

---

### Post by aysiu on 2007-03-04
I'm not sure why Kubuntu has different mounting behavior from Ubuntu, but I see a couple options here.

1. Use Gnome. Clearly it works better for you.

2. Force the iPod to mount by adding it to your /etc/fstab. More details here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Make sure it's plugged in before you do the *sudo fdisk -l*

---

### Post by fca_neo on 2007-03-06
Thanks Aysiu. Now it is working well, it mounts automatically and everything. I just restarted my KDE session and the problem was solved. I think I'll stick around with KDE though.

---

