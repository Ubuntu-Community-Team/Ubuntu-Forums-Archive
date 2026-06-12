---
title: "Downloading packages with Synaptic"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by aikidave on 2007-12-03
Hi,
I am new to Linux and am running gOS, which I understand runs on top of Ubuntu. I bought one of the Walmart Everex GPCs.  I have used the Synaptic Package manager to successfully download several programs (Gqview, Konsole, Squeak and Didiwiki). Gqview and Konsole show up under my applications menu, but I can't find Didiwiki. 
My question is where does Synaptic put the files when it installs a package?  Where do I go to find and run Didiwiki? I know I  need to learn more about the Linux file structure! 
Thank you,
Dave Raftery

---

### Post by vikram on 2007-12-03
> **aikidave said:**
> Hi,
I am new to Linux and am running gOS, which I understand runs on top of Ubuntu. I bought one of the Walmart Everex GPCs.  I have used the Synaptic Package manager to successfully download several programs (Gqview, Konsole, Squeak and Didiwiki). Gqview and Konsole show up under my applications menu, but I can't find Didiwiki. 
My question is where does Synaptic put the files when it installs a package?  Where do I go to find and run Didiwiki? I know I  need to learn more about the Linux file structure! 
Thank you,
Dave Raftery

Binaries, doc files etc. are installed at different locations. 
/bin  Common commands 
/sbin  used by root
/usr   most user apps
/opt   optional third party apps 

to quickly find a file try:

locate filename
quickly searches based on files indexed everyday (usually)

or uptodate but lengthy search try the find command

more details at man find

to locate commands

whereis command


another easy way is to look for the package in synaptic and look at the details, it will list the files and locations.

---

### Post by forestpixie on 2007-12-03
you should be able to find it with whereis in terminal - application >accessories

```
whereis *packagename*
```

---

### Post by Paqman on 2007-12-03
> **aikidave said:**
> 
My question is where does Synaptic put the files when it installs a package?  Where do I go to find and run Didiwiki?

On Linux you don't necessarily need to know where the package has been installed to in order to run it. All you generally need is the name, the OS is clever enough to know how to launch it.

If it hasn't installed a launcher in the menu you can either open a terminal window and run it from there, or you can make a new launcher and put it wherever you want.

---

### Post by Sims2789 on 2007-12-03
> **forestpixie said:**
> you should be able to find it with whereis in terminal - application >accessories

```
whereis *packagename*
```

Or you could use the Deskbar Applet (the magnifying glass next to your name in the top panel).

---

