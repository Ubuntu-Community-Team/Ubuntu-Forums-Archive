---
title: "Not to sure, but..."
date: 2008-03-27
forum: Apple PPC Users
---

### Post by veganjustice on 2008-03-27
Okay, I have an Apple iBook G3 clamshell 466mhz, that I am going to make solely a Ubuntu machine, I can only get 5.0.4 and 6.06.1 are the latest to actually load the installer, everything goes well during the install, but at the menu that lets me do something, after the install, where I can reboot, shut down, etc. the screen is totally screwed up. My mouse goes from half the bottom, down the screen and shows up at the top of the screen, the graphics are all half the screen side to side, it is weird, any ideas as to why this is? Should I go for an older install? 

Unless someone can recommend a version of Linux that has successfully been used on this type of PPC, I am stuck. I have multiple boots on my other computers, but I want a Linux Machine, and this is the perfect to do it, but I am running out of ideas, I can only find so many old versions of Ubuntu. haha

Thanks

---

### Post by tubasoldier on 2008-03-27
You could give YellowDog Linux a try. It is developed for the PPC processor.

Other than that just a regular Debian install would work well. The Debian default install is much like Ubuntu's. And on top of that you can install Debian from the internet, thus only downloading the packages your installing.

I know Debian Testing can run on a laptop with those specs. I have it running on a 333 mhz gateway laptop.

Good Luck.

---

### Post by stream303 on 2008-03-28
> **veganjustice said:**
> My mouse goes from half the bottom, down the screen and shows up at the top of the screen, the graphics are all half the screen side to side, it is weird, any ideas as to why this is? Should I go for an older install?

Live-cd installs can be troublesome.  I'd recommend the "alternate" text-based installer, especially since you plan on devoting it entirely to Ubuntu.

You can pick up something a bit more recent here for Ubuntu Feisty 7.04:

[http://cdimage.ubuntu.com/ports/releases/7.04/release/](http://cdimage.ubuntu.com/ports/releases/7.04/release/)

Grab the "alternate" image, burn as an iso at a relatively slow speed, and hold down the  "C" key when booting and let us know how it goes!

---

### Post by adelahunty on 2008-03-28
> 
Live-cd installs can be troublesome. I'd recommend the "alternate" text-based installer, especially since you plan on devoting it entirely to Ubuntu.


I agree completely.  And try Xubuntu as well, rather than simply the standard Ubuntu flavour.  It is certainly more forgiving on clamshell iBooks.  Feisty installs with no problems here, and then you can easily upgrade using update-manager.

---

### Post by bwilson on 2008-03-28
This might be a silly question, but did you make sure the screen resolution is set to 800x600 or lower? I recall the default install sets the resolution to 1024x768 which is not supported by the iBook 466.

---

### Post by veganjustice on 2008-03-28
Actually BWilson, I left the screen resolution for the 3 it already had chosen. I'll give that a try before I do anything else...

Also, I can try a later version, but like I said, the installer wouldn't begin with 7.10 and 7.04.

But I'll give the screen resolution a try, then try some other distros. 

Thanks, I'll let you all know how it goes sometime this weekend.

---

### Post by veganjustice on 2008-03-28
I changed the resolution, and gave XUbuntu a try, works great...

What are the main differences between Kubuntu, ubuntu and xubuntu? I have always just used Fedora and Ubuntu. Haven't found an old enough Fedora to install on this iBook, but wasn't sure all the differences between those 3 .

thanks for all the help. Also, what about Yellowdow Linux? How does that compare?

---

### Post by BladeMelbourne on 2008-03-29
Ubuntu comes with Gnome.

Kubuntu comes with KDE.

Xubuntu comes with Xfce - the choice for those with older hardware (less RAM/disk/cpu usage).

Installing one of the above doesn't stop you installing applications from another.

I haven't used YDL, but I believe it is geared to non Intel/Amd systems (PPC typically). It is based off CentOS/Fedora - so if you are more familiar with Fedora/Redhat over Ubuntu/Debian, you may feel more at home.

---

### Post by tubasoldier on 2008-03-29
The Ubuntu naming scheme is a bit misleading. It gets you thinking that some software is available only for that particular distro. But all the afformentioned desktops are available in the repositories and can peacfully co-exist.

---

