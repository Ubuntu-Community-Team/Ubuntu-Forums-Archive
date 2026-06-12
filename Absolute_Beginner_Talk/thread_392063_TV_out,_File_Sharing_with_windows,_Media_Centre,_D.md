---
title: "TV out, File Sharing with windows, Media Centre, Drivers, HDD Partitioning"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by chingy1788 on 2007-03-24
Hi
I want to use the TV out feature of my video card with Ubuntu

I want the PC to serve as a media centre
Specs as follows
AMD Athlon XP 2000+
512MB RAM
Geforce4 MX440
160GB HDD
DVD Rom

I am planning to install LinuxMCE
[www.linuxmce.com](www.linuxmce.com)

The PC will, of course be plugged into a Standard Definition CRT TV

Right now it is on a 17" monitor so I can configure it to run on the TV

I would like to put video clips, movies, music and photos on this machine
It is likely I would get a larger 320GB HDD for the Machine in the near future

Do I need to install the nVidia drivers? or can I just use Ubuntu's Default drivers?
I downloaded the drivers for Linux IA32

How do I go about splitting up my Hard Drive into 3 parts, One for Ubuntu system files, One for Ubuntu Swap and one for Storing Vids, Photos, Music etc?

As mentioned in the Title, I am using Ubuntu 6.10

I also have kubuntu which im a bit more familiar with since its based on KDE, which I use at Uni  a bit, just for programming and web browsing

---

### Post by lamalex on 2007-03-24
installing nvidia drivers probably won't be necessary for 2d applications like dvd playback, but it may smooth it out a bit. as for partitioning, install gparted and partition your drive that way or boot into live cd and do it through gparted.

---

### Post by chingy1788 on 2007-03-24
Thanks
I'll repartition the drive now

Still, how do I use TV out in Ubuntu?
I'm using a Leadtek Geforce 4 MX 440
It has TV out and it worked in Windows

If I ever do want to play 3d games, how do I go about installing the nVidia drivers?

Also I cant do anything in the root or home folders, How do I get to this Administrator account? (this is for the nvidia drivers I downloaded... It needs to be in the root directory...)

---

### Post by chingy1788 on 2007-03-24
bump

---

### Post by shingalated on 2007-03-24
The easiest way to install video drivers is with this little utility called "Envy"
The .deb is available on the homepage here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

