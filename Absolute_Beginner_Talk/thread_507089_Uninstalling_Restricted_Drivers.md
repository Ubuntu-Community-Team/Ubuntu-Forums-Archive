---
title: "Uninstalling Restricted Drivers"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by FLYBOY611 on 2007-07-22
Ill try and make this as brief as possible 

So i'm trying to run the new 7.04 Ubuntu and here are my system specs
Athlon 64 X2 3800+ Socket AM2
eVGA **8800** GTS 640MB
2x 250Gb HD
CORSAIR XMS2 2GB DDR2 800
Rosewill 600w SLI power supply
Creative X-Fi Extreme Music
ViewSonic VX922 19inch monitor

Long story short my Ubuntu installed great and I downloaded all those 97 updates but after I downloaded and installed the automated restricted drivers for my 8800 my Ubuntu bricked and the x server gave me grief.

Now I did find this guide to properly install drivers for the 8800 series here
[http://ubuntuforums.org/showthread.php?t=496103&highlight=8800+gts](http://ubuntuforums.org/showthread.php?t=496103&highlight=8800+gts) 

but before I can do all that I need to uninstall the restricted drivers so I can get back to the standard desktop.

What are the commands for uninstalling those drivers that it put in?
OR
Am I just better off reinstalling my Ubuntu?

---

### Post by kevinlyfellow on 2007-07-22
```
sudo apt-get remove restricted-modules*
```

But, as a warning do not do this unless you don't need any other restricted drivers.

The tutorial is all in command line.  Why don't you just print out the instructions and work from command line?

---

### Post by FLYBOY611 on 2007-07-22
Thanks ill try this and if not ill do some more digging around the forums and tutorial before asking more

---

