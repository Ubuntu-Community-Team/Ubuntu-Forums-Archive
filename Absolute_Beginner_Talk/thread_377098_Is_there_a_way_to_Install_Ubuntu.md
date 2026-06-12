---
title: "Is there a way to Install Ubuntu"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Ibuntyou on 2007-03-05
I have tried to install Ubuntu and this is what I get

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Is there any easier way to install ubuntu with the latest nvidia drivers without going through the command line installation?

---

### Post by Ibuntyou on 2007-03-05
Is there a ready made beta version for desktop 64 bit to download .. if not when will it be released?

---

### Post by AndyCooll on 2007-03-05
What's happened here is that the setup process has failed to recognise your graphics card.

At the command line prompt type:
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a sort of wizard. Accept most of the defaults, but at the graphics card bit I suggest you choose "vesa". It's a bog standard graphics card configuration that works with almost everything and should get you going. Once you've got a desktop you can always at a later stage play around and try to get an optimum graphics card configuration.

:cool:

---

### Post by r4ik on 2007-03-05
Here is is something to read :) there is an automated script in the third link you might want to use that.
Please read the two first links to get you're card working.

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Good luck !

---

### Post by AndyCooll on 2007-03-05
> **Ibuntyou said:**
> Is there a ready made beta version for desktop 64 bit to download .. if not when will it be released?

And yes there is a 64-bit version. Never tried it but I've heard it's more difficult to get up and running than the 32-bit version.

:cool:

---

