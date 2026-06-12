---
title: "nVidia  Geforce Fx 5200 problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by devthedude on 2007-11-02
My pc wouldn't boot with with nVidia  Geforce Fx 5200 
i had to pull out the card to install ubuntu 7.10 amd64
and now when i insert the card back in
ubuntu wont boot:(
so how do i install the drivers

i'm a complete newbie so please give simple instructions 
i don't even know where u type shell commands

---

### Post by Pumalite on 2007-11-02
Go to the Nvidia site and check your card against the drivers. Then download appropriate driver and follow instructions.
(you might need 'Legacy'. I don't know)

---

### Post by overdrank on 2007-11-02
> **devthedude said:**
> My pc wouldn't boot with with nVidia  Geforce Fx 5200 
i had to pull out the card to install ubuntu 7.10 amd64
and now when i insert the card back in
ubuntu wont boot:(
so how do i install the drivers

i'm a complete newbie so please give simple instructions 
i don't even know where u type shell commands

Hi you boot into recovery mode this will give you the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure xserver-xorg
``` choose vesa as the driver and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by mdpalow on 2007-11-02
I have the exact same card and my Ubuntu 7.10 32-bit works almost perfectly (99.9%). Just one minor, minor display problem on the title bar of my window.

Card not seated properly in the slot, bad card, something going on in your BIOS maybe? 

Wait.....

When you say it won't boot, do you mean your computer hangs up somewhere and you're sure of this OR do you mean you hear the Ubuntu music comes on, but you have a black screen and see nothing?

If it's the later, your computer did boot, but the card sucks for install using the first option when you put in the Live CD disk. You have to select the 2nd option and then it boots up all the way.

Once in, you can install the OS and then the Restricted Drivers window will come up and tell you to enable the nVidia driver.

Also, like I tell everyone - make sure you have a CAT5 Ethernet cable plugged into your computer during install. After reboot, you can take out and use wireless if you want.

Let us know what's going on....

---

