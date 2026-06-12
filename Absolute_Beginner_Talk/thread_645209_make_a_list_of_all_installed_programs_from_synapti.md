---
title: "make a list of all installed programs from synaptic"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by 99bluefoxx on 2007-12-19
so i am about to backup all data to a new hard disk and install winblows for some device compatability and i miss the faster wow framerate, and i was wondering how to obtain a .txt file with a list of all the packages i have installed in synaptic, so i can track them down easily when i put ubuntu back in[my account is going funny saying i dont have write permissions to it, strange as i can but anyways] to my computer
i allso wish to know how well SATA is working in linux so far, i tried to install onto a SATA 250GB seagate with 6.10 back in september and failed badly, if anyone can give me more info that would be great thanks

---

### Post by frank002 on 2007-12-19
You might know this already but if you go to Synaptic>File>History it will tell you all the installs you have done. You would have to copy and paste that info into gedit or another text editor. If there is a better way, I'm sure someone else here will post it.

---

### Post by 99bluefoxx on 2007-12-19
thanks, i just got back and installed the SATA its an 80 gig, but isnt detecting in the bios properly, it thinks its a 270GB?it wont show up in gparted, or at all
so does 7.04 support SATA?or is my drive just faulty?

---

### Post by frank002 on 2007-12-20
I could not tell you since all my drives are EIDE, not SATA.  So far, Ubuntu has detected everything I have thrown at it, even my 2 year old IPOD Nano.

---

### Post by frank002 on 2007-12-20
Found this reading the forum
Can you post the following information, please:

1 A list of all hard drives you have fitted, what types they are and to which channels they are attached. Ditto for any optical drives and any internal USB drives (such as an internal card reader). We need the latter because they are named the same way as for hard drives.

2 The motherboard chipset.

3 Boot up the live CD and open a terminal (Applications > Accessories > Terminal). Post the output of:

Code:

ls -l /dev/hd*

and:

Code:

ls -l /dev/sd*

This way we'll see (hopefully) exactly what the live CD is detecting and what names it is assigning. One thing you need to know is that with a fairly recent development in pata/sata kernel drivers, both PATA (ide) and SATA drives now appear as though they are SATA. (Or at least most of the time - on the machine I'm posting from atm, Ubuntu Gutsy reports my HD as hda, whereas Gentoo reports it as sda - it all depends on how and what has been compiled into the kernel). So I'm wondering if the live CD has in fact detected your PATA drive but has given it a sd* name.

Forget about the Linux drivers on the disc for now. Hopefully, the kernel will have all the drivers you need, but there are some problematic chipsets, which is why I asked for this information.


Edit: Forgot to mention - the output from ls -l can be quite verbose. You don't want to be typing that out. If you can get a working internet connection from the live CD, you can copy and paste from the terminal into the forum reply field.
Hope this helps
__________________

---

### Post by aeiah on 2007-12-20
for future reference (it seems like you may have deleted your existing ubuntu partition already), there is a nice program called APT on CD. its in the repos (aptoncd), or on this site: [http://aptoncd.sourceforge.net](http://aptoncd.sourceforge.net)

might be worth looking at.

---

### Post by bodhi.zazen on 2007-12-20
The command line is very helpful for this.

To list all packages installed :

```
sudo dpkg -l
```

That is a small L

To save the list :

```
sudo dpkg -l > installed_apps
```

You can also do this nifty trick :


=================


```
dpkg –-get-selections | grep -v deinstall > ubuntu-packages
```

This also makes a list of all installed packages.

Now, re-install Ubuntu.

```
sudo apt-get update
sudo apt-get upgrade
```

This brings the fresh install up -to -date.

Now :

```
dpkg –-set-selections < ubuntu-packages
```

This tells your system the packages to install, now lets install 'em :

```
sduo dselect
```

This opens a dselect session. Type ‘I‘ and allow dselect to install of the the packages listed in ubuntu-packages document. When it’s finished, type ‘Q‘ and hit the ENTER key to exit dselect.

Viola

---

### Post by yabbadabbadont on 2007-12-20
Nice one.  :D

---

