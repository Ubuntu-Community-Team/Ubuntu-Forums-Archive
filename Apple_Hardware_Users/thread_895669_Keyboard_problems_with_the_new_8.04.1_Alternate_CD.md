---
title: "Keyboard problems with the new 8.04.1 Alternate CD"
date: 2008-08-20
forum: Apple Hardware Users
---

### Post by MaddMatt on 2008-08-20
Hello, 

I've previously had 8.04 on my MacBook Pro 4.1 (penryn), and it was running great, but for various reasons I've decided to do a clean install so that I can run a dm-crypt encrypted disc. Upon inserting the alternate CD, the keyboard runs just fine - but once inside the installer, right from the 'select language' prompt, no keyboard commands are working! This is a problem because I do not have access to a USB keyboard where I am, only PS/2, so no installation for moi!

Any ideas on some remedies?

Cheers, 
M

---

### Post by cyberdork33 on 2008-08-20
> **MaddMatt said:**
> Hello, 

I've previously had 8.04 on my MacBook Pro 4.1 (penryn), and it was running great, but for various reasons I've decided to do a clean install so that I can run a dm-crypt encrypted disc. Upon inserting the alternate CD, the keyboard runs just fine - but once inside the installer, right from the 'select language' prompt, no keyboard commands are working! This is a problem because I do not have access to a USB keyboard where I am, only PS/2, so no installation for moi!

Any ideas on some remedies?

Cheers, 
M
You cannot use a bluetooth wireless keyboard is that is what you are using... If you have a wired Apple keyboard, try connecting it to different ports and unplugging other devices.

---

### Post by MaddMatt on 2008-08-20
> You cannot use a bluetooth wireless keyboard is that is what you are using... If you have a wired Apple keyboard, try connecting it to different ports and unplugging other devices. 

I'm not using a bluetooth keyboard - using the keyboard on the laptop. I also don't have access to a USB keyboard since I'm overseas right now, and I don't think any laptops made today have PS/2 ports... 

So fixing this through software is the only option I can see. Does anyone know if it's possible to specify the keyboard configuration through the command line of the main page on the CD?

---

### Post by hajk on 2008-08-24
You still following this thread? 

There is a simple solution to the unresponsive keyboard problem in the alternate installer: after choosing your language for the first time (a black-on-white box), you end up in a coloured page with several choices, the first one being to install Ubuntu. Before you do that, however, hit the F6 button (you may also have to depress the fn button while doing so) and select the EDD=ON boot option, then hit Enter, Enter again, and now proceed with the installation. You'll find the keyboard responsive when selecting your language, etc.

Good luck!

---

