---
title: "How do I update Unichrome Pro Graphic video drivers ABIT VA-20 onboard video KM400A"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-09
I just loaded Ubuntu 6.06.1 two days ago and I am trying to update my video drivers for my ABIT VA-20 motherboard using the Unichrome Pro Graphics onboard video with the KM400A chipset.  I read all the forums on video upgrades and now I don't know what to do next.  I downloaded the VIA driver update package for the KM400 and unzipped it to my desktop.  I also used the Synaptic Package Manager to install all of the default dependency package listed under Ubuntu 6.06.1.  I searched and found everyone that was listed on an VIA installation guide that I printed out.  They are all installed.  Now, I don't know what to do next?  I don't want to crash my video so give me some help.  I'm a noobie. so be gentle.:confused:

---

### Post by optotron on 2007-02-09
Heya! I've got an unichrome card as well on one of my laptops. 

It's with the KM808 chipset but that doesn't matter..

anyways; this is what you'll need to know.
assuming that the drivers are properly installed and that the modules are loaded correctly, you should try editing your /etc/X11/xorg.conf file. In case you are not familiar with xorg.conf its the settings that tells the graphical environment (xinit) what to load, keyboard mouse etc, you can also change screen resolution and; device driver for your graphics card.

You can check if you've got the module loaded by typing
lsmod | grep via
then look at the output and see if you've got a line similar to this one
```
via                    39424  2
```

if you do, the drivers might be loaded, im not sure ;)

if not, try 
sudo modprobe via

If you make changes in the /etc/X11/xorg.conf file that for some reason won't work, and have the GDM daemon running (if you're running Ubuntu you can safely assume that this is the case), then you'll most certainly "crash your video", at least GDM will keep try to start X and you'll probably be left with a blank screen or something like that. But stay calm; you'll probably get this result a few times before its configured properly, and you can CTRL+ALT+F2 (or F3 or F4 ->F6) to get to a tty and log in from there (or boot in single user mode).
Just make sure that you back up your xorg.conf before doing any changes to it.

Heres how to edit the /etc/X11/xorg.conf-file so that it loads the via driver.

first make the backup
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
then use your favourite text editor to edit the file. Most new users prefer nano or pico
sudo pico /etc/X11/xorg.conf
now look for the "Device" section, it should look something like this:
```

Section "Device"
        Identifier  "Card0"
        Driver      "via"
        VendorName  "All"
        BoardName   "All"
EndSection

```
The identifier is not necessary to change, but if Driver says "vesa", then try changing it to "via", and restart X (done by pressing CTRL+ALT+BACKSPACE)

---

### Post by rggavubt on 2007-02-10
Thanks for the great reply.  I dowloaded the VIA driver package and unzipped it to my desktop.  I don't know what to do with it next?  Do I execute/run it or do I put in a driver folder?  I saw one of the posts where the person was told to put it in a driver folder.  I could not find that folder.  I assume they were using a different version of Ubuntu.  I did download and install all of the default dependency package required for the VIA driver package to work.

---

### Post by rggavubt on 2007-02-11
I have been reading the how to's at this location :

[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

It looks like I can install the VIA package using the instructions under package install for source package.....is that correct?

---

### Post by rggavubt on 2007-02-12
I am still stuck :confused: ,  I downloaded the build-essential package and then tried ./configure when I was in the VIA package folder.  It wouldn't work so then I used the "make" command and it didn't work either.  I am stuck.......help

PS...the VIA package I loaded was from here :

[http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2260&SubCatID=102](http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2260&SubCatID=102)

This is for the KM400 chipset but package was not listed under Ubuntu but under Linux XFree 86 (not distribution specific)  Can I use this package for Ubuntu??

---

### Post by rggavubt on 2007-02-12
> **optotron said:**
> Heya! I've got an unichrome card as well on one of my laptops. 

It's with the KM808 chipset but that doesn't matter..

anyways; this is what you'll need to know.
assuming that the drivers are properly installed and that the modules are loaded correctly, you should try editing your /etc/X11/xorg.conf file. In case you are not familiar with xorg.conf its the settings that tells the graphical environment (xinit) what to load, keyboard mouse etc, you can also change screen resolution and; device driver for your graphics card.

You can check if you've got the module loaded by typing
lsmod | grep via
then look at the output and see if you've got a line similar to this one
```
via                    39424  2
```

if you do, the drivers might be loaded, im not sure ;)

if not, try 
sudo modprobe via

If you make changes in the /etc/X11/xorg.conf file that for some reason won't work, and have the GDM daemon running (if you're running Ubuntu you can safely assume that this is the case), then you'll most certainly "crash your video", at least GDM will keep try to start X and you'll probably be left with a blank screen or something like that. But stay calm; you'll probably get this result a few times before its configured properly, and you can CTRL+ALT+F2 (or F3 or F4 ->F6) to get to a tty and log in from there (or boot in single user mode).
Just make sure that you back up your xorg.conf before doing any changes to it.

Heres how to edit the /etc/X11/xorg.conf-file so that it loads the via driver.

first make the backup
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
then use your favourite text editor to edit the file. Most new users prefer nano or pico
sudo pico /etc/X11/xorg.conf
now look for the "Device" section, it should look something like this:
```

Section "Device"
        Identifier  "Card0"
        Driver      "via"
        VendorName  "All"
        BoardName   "All"
EndSection

```
The identifier is not necessary to change, but if Driver says "vesa", then try changing it to "via", and restart X (done by pressing CTRL+ALT+BACKSPACE)

I did lsmod | grip via and got this :

"via 39424 2" plus a bunch of other lines

does this mean my via drivers are loaded already?

---

### Post by Shay Stephens on 2007-02-12
I have a laptop with the unichrome video adapter.  When I first got it I tried a number of things, and nothing really worked.  I am not saying you won't find a way to make it work, but if you get tired of messing with it, the standard vesa driver the ubuntu loads works well enough to get your work done.  No 3d or stuff like that however.

Until I find a slam dunk method of getting the unichrome working, I am sticking to the vesa driver, when my laptop dies, then I am going to replace it with a system 76 laptop, then I won't have to worry about it :-)

---

### Post by fenian on 2007-02-12
Have you tried OpenChrome?

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by rggavubt on 2007-02-12
I am not playing games so I guess I will stay with what I have.  The video is working but not great.

---

### Post by Shay Stephens on 2007-02-12
fenian, thank you for posting the link.  I hope that how-to works for lots of people.  I have done enough of those to not even want to try.  Too long and complex, plus it breaks when the kernel is updated.  The longer and more complicated the how-to, the greater the chance it will break somewhere along the chain of events.

I would rather choke on the vesa driver hehehe.

---

### Post by sso71 on 2007-02-13
> **rggavubt said:**
> I am not playing games so I guess I will stay with what I have.  The video is working but not great.

I am having the same video chipset, but on the ECS motherboard. My only complaint is the choppiness during scrolling a document or firefox and dragging a window. Is that your case?

---

### Post by Shay Stephens on 2007-02-13
> **sso71 said:**
> I am having the same video chipset, but on the ECS motherboard. My only complaint is the choppiness during scrolling a document or firefox and dragging a window. Is that your case?
Yes, like a 1 second refresh rate when scrolling...ugh.

---

