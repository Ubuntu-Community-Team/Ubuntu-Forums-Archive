---
title: "Urgent : Offline installation problem"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by cadcrazy on 2007-12-04
I have install Ubuntu 7.10 on my friends system. There is some problem with his network card so can't connect to net. I have all the packages in my pen drive. I copied all of them in /var/cache/apt/archives folder but these are not available to install either through apt or synaptic even refresh/ update.

Plz guys help me its very urgent

---

### Post by skymera on 2007-12-04
if they are .deb just double click them.

but they may need other packages for dependencies.

---

### Post by GSF1200S on 2007-12-04
> **cadcrazy said:**
> I have install Ubuntu 7.10 on my friends system. There is some problem with his network card so can't connect to net. I have all the packages in my pen drive. I copied all of them in /var/cache/apt/archives folder but these are not available to install either through apt or synaptic even refresh/ update.

Plz guys help me its very urgent

You could always use the live cd, assuming the packages you need are located in apt. You dont boot off the live cd- you just stick it in his cdrom drive. Then open his /etc/apt/sources.list and comment out all online sources, and then un-comment out the cd-rom lines. Apt will then search the cdrom for the packages... which repos are the packages located in? If its main your good...

---

### Post by cadcrazy on 2007-12-04
i have all the packages with all dependencies backed up on pen drive. How to add pen drive in apt sources.list ?

---

### Post by cadcrazy on 2007-12-04
bump

---

### Post by skymera on 2007-12-04
5minutes and your already bumping?

as i said before are they .deb files?

---

### Post by cadcrazy on 2007-12-04
yes .deb files. But many of them like vlc,mplayer,gxine,gstreamer etc etc

---

### Post by cadcrazy on 2007-12-04
installing manually is not good option. can i add pen drive to apt source list

---

### Post by deanjm1963 on 2007-12-04
if they are on your pen drive and don't need any dependencies... at a command prompt logged in as root install them ... e.g.

dpkg -i /media/usbdisk/*.deb

that is only an example... you need to know the exact path of your pen drive

I have quite a few programs that I install manually that way... never failed me yet.

---

### Post by hyper_ch on 2007-12-04
if those are .debs from the official repos then it's not a big issue installing them through the command line.

---

### Post by Toet on 2007-12-04
Have a look at this:

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror]("http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror")

---

### Post by cadcrazy on 2007-12-04
I'll install it through command line but my friend is not very much comfortable with command line. He'll prefer synaptic. Plz plz tell me any possible way get synaptic working for offline packages without net connection

---

### Post by cadcrazy on 2007-12-04
> **Toet said:**
> Have a look at this:

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror]("http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror")

Its a very long method and will take some time to get used to it. I think synaptic will be the easiest method to work with if possible.

---

