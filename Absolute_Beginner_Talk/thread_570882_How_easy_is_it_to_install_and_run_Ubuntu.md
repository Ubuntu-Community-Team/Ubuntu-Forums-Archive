---
title: "How easy is it to install and run Ubuntu?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by goltoof on 2007-10-08
I'm a total newb and have grown more and more frustrated with windoze. I installed Ubuntu feisty, because the reviews say it's the most user friendly. At first it ran beautifully, didn't have any problems and most of the apps i needed were already installed, and things like codecs and browser plugins installed themselves intuitively.  But there were still essential things that required long detailed installations involving the command line to install. It wouldn't even detect wireless networks, no dual monitor support, and usb support for a wacom tablet is about a 2 page tutorial just to get it working.  After trying to set these things up, one problem seemed to lead to another, and another and another until I coulnd't start up the gui anymore without working through like 20 things.

So I'm starting over and this time I'm not even bothering with the "advanced" stuff like setting up a simple wireless network!  But outside of just installing it and not touching anything (besides firefox and basic file management which is all i need it for) is there anything I should do after the initial install to make it so that it will keep working without interrupted use?

---

### Post by Paqman on 2007-10-08
IIRC Gutsy supports dual monitors and has a new wifi manager including WPA support. So if you upgrade/reinstall after the 18th you might find some of your problems have magically vansihed.

Hope so anyway! Butting your head against hardware issues is the absolute most frustrating thing about using Linux.

---

### Post by mivo on 2007-10-08
If you are sure about starting over, do make a 10 GB partition for /, 1-2 GB for swap, and the rest of the disk for /home (provided you are not dual-booting). The advantage is that all your personal files, settings, etc. will be kept in /home, so you can re-install Ubuntu at any time without losing your configuration, settings, personal files. You'd only have to re-install the core system and the programs you use (but not have to configure them again).

---

### Post by om1 on 2007-10-08
i would say you will have wifi and dual monitor support with no problems with gutsy.... i haven't had to do anything except click on restricted drivers to enable all of mine....
but you don't have to do anything to have what you seem to be asking for except install

---

### Post by goltoof on 2007-10-08
> **Paqman said:**
> IIRC Gutsy supports dual monitors and has a new wifi manager including WPA support. So if you upgrade/reinstall after the 18th you might find some of your problems have magically vansihed.

Hope so anyway! Butting your head against hardware issues is the absolute most frustrating thing about using Linux.

That's what I'm hoping for as well.  Supposedly 7.1 is going to bring ubuntu to a lot more desktops with its wide scope of compatibility and ease of use. *knocks on wood*

---

### Post by Jimmyfj on 2007-10-08
Hi and welcome to Ubuntu

If you provide us with some specs on your system, name of Wifi card and the other hardware you're having issues with I'm sure you'll find that a lot of people are willing to help you out. Wifi does run with out any issues on the systems I've helped install, some wireless cards are harder to work than others, but in general most cards can be configured and works fine.

---

### Post by om1 on 2007-10-08
Gutsy provides alot more hardware support

---

### Post by goltoof on 2007-10-08
> **mivo said:**
> If you are sure about starting over, do make a 10 GB partition for /, 1-2 GB for swap, and the rest of the disk for /home (provided you are not dual-booting). The advantage is that all your personal files, settings, etc. will be kept in /home, so you can re-install Ubuntu at any time without losing your configuration, settings, personal files. You'd only have to re-install the core system and the programs you use (but not have to configure them again).

I'm sure that was part of the problem the first install, didn't make any partition for swap. But it's really just to compensate for shortfall of ram right?
That's great advice keeping my personal settings in /home.
So do I need three partitions then?

---

### Post by om1 on 2007-10-08
your swap partition is normally about 2-3 times your ram..... i think you need it..... ive never seen a Linux machine not have it
correct me if im wrong about it

---

