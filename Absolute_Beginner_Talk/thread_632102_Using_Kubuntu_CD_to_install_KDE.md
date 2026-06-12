---
title: "Using Kubuntu CD to install KDE?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by shafin on 2007-12-05
Hi,
Can I use the Kubuntu CD to install KDE-desktop on top of an existing ubuntu installation?

---

### Post by GSF1200S on 2007-12-05
> **shafin said:**
> Hi,
Can I use the Kubuntu CD to install KDE-desktop on top of an existing ubuntu installation?

Im not sure.. First off, is this because you dont have internet access with said computer, or are you on a slow connection?

You could open up your /etc/apt/sources.list and comment out all the http sources, and then un-comment the cdrom source. I dont think it will let you use another buntu variant cd, but I think the KDE libraries themselves may very well be on the Ubuntu CD or maybe on the alternate. In fact, Im going to start a thread so I know once and for all what packages are located on what CD...

Good Luck ;)

---

### Post by ukripper on 2007-12-05
Enable CD repos in synaptic and then from terminal :

type:
```
sudo apt-get update
```

```
sudo apt-get install kubuntu-desktop kde-core
```

---

### Post by shafin on 2007-12-05
Thanks.

---

### Post by GSF1200S on 2007-12-05
> **ukripper said:**
> Enable CD repos in synaptic and then from terminal :

type:
```
sudo apt-get update
```

```
sudo apt-get install kubuntu-desktop kde-core
```

Let me use this as an opportunity to ask you...

All of the programs available in the main repos (not the multiverse, universe) are on the liveCD, including KDE XFCE, etc? And if this is so then either synaptic or the terminal can fetch and install these, regaurdless of the current package version on the computer vs. the CD? Are there multiverse/universe CD's available for download/purchase, and can I annotate the sources.list to utilize them (still utilizing apt directly)? Could I make my own CD of .debs to make installing programs on offline Ubuntu computers easier? Anything else I need to know?

This has been an issue lately, and I dont exactly know how to help the people resolve their problems because I dont quite know myself... Itd be awesome if you know the answers here...

---

### Post by ukripper on 2007-12-05
> **GSF1200S said:**
> Let me use this as an opportunity to ask you...

All of the programs available in the main repos (not the multiverse, universe) are on the liveCD, including KDE XFCE, etc? And if this is so then either synaptic or the terminal can fetch and install these, regaurdless of the current package version on the computer vs. the CD? Are there multiverse/universe CD's available for download/purchase, and can I annotate the sources.list to utilize them (still utilizing apt directly)? Could I make my own CD of .debs to make installing programs on offline Ubuntu computers easier? Anything else I need to know?

This has been an issue lately, and I dont exactly know how to help the people resolve their problems because I dont quite know myself... Itd be awesome if you know the answers here...

i know what you looking for.

Follow this link [http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

---

