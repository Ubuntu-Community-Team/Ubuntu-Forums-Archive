---
title: "ATI mobility X1600 driver"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Marbash on 2007-12-05
When I try to install the ATI driver, I get this error message:
This application conflicts with other installed software. To install 'xorg-driver-fglrx' the conflicting software must be removed first. Switch to the 'synaptic' package manager to resolve this conflict.

I've checked around some in the package manager, but I'm afraid to mess around too much, 'cause I'm kinda new to Ubuntu. Does anyone know what can be conflicting with the driver? And how to fix it? :)


Thanks in advance.

---

### Post by Mariano Oliveto on 2007-12-05
> **Marbash said:**
> When I try to install the ATI driver, I get this error message:
This application conflicts with other installed software. To install 'xorg-driver-fglrx' the conflicting software must be removed first. Switch to the 'synaptic' package manager to resolve this conflict.

I've checked around some in the package manager, but I'm afraid to mess around too much, 'cause I'm kinda new to Ubuntu. Does anyone know what can be conflicting with the driver? And how to fix it? :)


Thanks in advance.

Not sure but shouldn't the Synaptic package manager or aptitude tell you exactly which is the installed software that is conflicting with the package you are trying to install?

You could post the exact message you are getting in order to help us help you ;)

Edit: Sorry, I just realized that this post was not too help full. What I was trying to say was that you could open the Synaptic Package Manager (System->Administration->"Synaptic Package Manager") and click on the search button and find the package. Then click on the little box on the left and choose "Mark for installation". A window will pop up and it should say if there are conflicts with any packages and which of them are conflicting. Then post which of them are conflicting and hopefully someone will be able to help you :P

---

### Post by Marbash on 2007-12-05
When I just try to enable the driver by the "Restricted Drivers" menu, I get this message: 'Could not apply changes. Please fix broken packages first.'

And in 'synaptic' I get this message: 
xorg-driver-fglrx:
Depends: libstdc++5 (>=1:3.3.4-1) but it is not installable

---

### Post by Marbash on 2007-12-05
There are two drivers that are listed, and I get the same error message as I stated above. Not really sure how to troubleshoot this. :P

---

### Post by Mariano Oliveto on 2007-12-06
Maybe you could search for libstdc++5 in Synaptic, mark it for installation and see why it is not installing (post your outcome). I installed the ATI propietary driver using the ati driver installer and worked for me in Gusty, but mine isn't a ATI mobility x1600. I do have libstdc++5 1:3.3.6-15ubuntu2 installed.

Did you add the restricted repositories in your /etc/apt/sources.list?

You can do this going to System->Administration->"Software Sources" and selecting the option "Propietary drivers for devices (restricted)"

Not sure if this will help though.

By the way, what version of Ubuntu are you running?

---

