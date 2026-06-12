---
title: "Using Synaptic Once for Multiboot (X)(K)Ubuntu and varients?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-03-16
Hi,

Right now I am multi booting Ubuntu, Mepis 6.0 (with a Debian-Ubuntu base?), 2 other Linuxes and Windows. Instead, of trying out the two other Linuxes, couldn't I try Kubuntu and Xubuntu at the same time and download the major file updates and add-on software programs to a to a shared folder and configure Synaptic to check the folder and just download the necessary dependencies for the K-X-Ubuntu, Mepis variants.  I got dial-up and things and downloading can be slow.

Paul in New Hampshire

---

### Post by diskotek on 2007-03-16
i can not get the whole question but you can download it as xfce and kde things with your actual ubuntu. you can choose sessions at the log on screen. it would be the fastest way to use ,
 i believe

---

### Post by pmueller on 2007-03-16
Yes, I can download extra KDE dependencies and run extra KDE based programs on Ubuntu, but I understand this would slow down Ubuntu.

I want to try Gnome, KDE, and others in separate distributions. Also, I like extremely fast distributions like Puppy. My computer is not very fast or slow. It has an AMD 1600+ XP processor with 512 RAM.

Downloading on my dial-up is slow at 40k. When I upgraded a few programs using Synaptic. I had to download Firefox, Open Office, Gimp, various media player updates. I have downloaded the same updates several times for my different systems. If I like using these same updates on other distributions, would it not be possible to download the core files into a single folder and configure Synaptic just to get the files needed for Mepis, K-X-Ubuntu that are different?

I hope I am making sense. I figure that each distribution has libraries that are different that are used to get the major software programs to work on their system.

Thanks,

Paul

---

### Post by pmueller on 2007-03-16
Hello Again,

I checked to see if I could switch over to KDE or XFCE and I do not have these pre-installed. Both KDE and XFCE are big downloads. Are they not? I got my original Ubuntu from a CD disk and not from the internet because it would take 24 hours to download with dial-up modem costing me $5/month. I would acquire Xubuntu and Kubuntu the same way, via CD, not through the slow internet download.

Please does anyone have an answer? Can I download synaptic files into the same folder and tell synaptic to only download the additional files that I would need to get multiple and different distributions to work.

How do I do this in Kubuntu, Xubuntu, and possibly Mepis?

Help!
Paul in NH

---

### Post by bench on 2007-03-17
I think what you're saying is technically feasible.  You could copy the .debs downloaded in Ubuntu to the apt package cache on the Kubuntu or Xubuntu partition.  Have a look in /var/cache/apt/archives.  Don't think this would solve the problem with the other distro you mentioned.

---

### Post by pmueller on 2007-03-18
Thanks you Bench for telling me where the archives were. I am still a little lost in the Linux world. 

I just checked the menus in Synaptic and I could not figure out if there was a way to tell it to check the archives. I would like to copy these archives and place them in different distributions that may also use Synaptic.  

It seemed that there was a way to get Synaptic to always check a CD for any updates, but I forgot how to do this. Likewise, there may be a way to get Synaptic to always check the location of the archives. Perhaps it always does this.  I would like to experiment with Mepis 6, which has both Synaptic and Automatix support and see what happens.

Hope there will be something to report.

Paul

---

