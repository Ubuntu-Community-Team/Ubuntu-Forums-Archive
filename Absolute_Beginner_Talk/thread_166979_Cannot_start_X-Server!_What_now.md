---
title: "Cannot start X-Server! What now?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by D@niel on 2006-04-27
Hi,

I updated the drivers of my nvidia-card and now the graphical interface doesn't come up. Kubuntu is actually installed and it only shows the logo of it, but nothing happens till I press "CTRL+ALT+F1", and then it only opens the terminal.

What can I do now to get a functional graphic-driver? Internet is available on the linux-machine...

Thanks! :)

---

### Post by Binny45 on 2006-04-27
I had the same thing happen to me with my Sapphire ATI X800 GTO Fireblade.

I had to reload the video drivers as a VESA adapter and it worked like a charm.  

I'll take a look for the post that I got the help on and post the command here for you.

---

### Post by Binny45 on 2006-04-27
Ok, once you get back to the command line, type this out:

sudo dpkg-reconfigure xserver-xorg

I dunno what it does exactly, but it'll let you re-select a video card.  Chose VESA and it should get you up and running.

I'm still running the VESA driver for now, at least until I can figure out how to get a set of working drivers for my ATI card.

I had a thread going in the support forums, but since had a lot of stuff happen and I've lost my spot LOL.

I hope this happens.  It'd be great if it did.  The guys in this community rock for thier support.  Just trying to pass the little I've learned/gotten on. :)

---

### Post by D@niel on 2006-04-27
Thanks Binny45! I will try this... ;)

---

