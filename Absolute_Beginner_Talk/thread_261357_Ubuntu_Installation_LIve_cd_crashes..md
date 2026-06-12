---
title: "Ubuntu Installation LIve cd crashes."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by mcai8rw2 on 2006-09-20
I am converted to linux. All hail open source.

I Ordered the live cds from the ShipIt and they arrived a while ago. I wish to install ubuntu on my really old laptop that only has 128mb ram.

The live CD seems to load fine and dandy [up to a point]...however it always seems to crash when the live CD comes to load the 'Nautilus' thing. Hang. Nothing. The CD stops whirring.

This means that no matter how hard i try i cannot get a desktop environment with which i can click the INSTALL button.

My question is...can i instigate the installation script/process at the boot prompt? I.e. Before the live cd begins to load into ram and my computer has a chance to 'crap' out on me.

Hope you can help.

Thanks

---

### Post by benfindlay on 2006-09-20
I'd download a copy of the alternate disk and install the text based version. you still get the full ubuntu experience, it's jsut that the installer is done in a very basic menu based system (a basic GUI). You jsut select things with "Yes" and "No" basically

The reason I suggest this is that the graphical installer is likely having problems because you don't have enough ram to handle the live cd installer.

Hope this helps

---

### Post by mcai8rw2 on 2006-09-20
Thanks for the tip Ben, I will try it when I can.

Annoyingly though...my computer setup doesn't have a dvd/cd burning option [my 'main' machine melted leaving me in the arms of the worlds oldest laptop until I can afford to buy new stuff.], so should i download the alternate ISO, i would not easily be able to burn it to anything.

As such I would still be interested to know if there is a command to type into the boot prompt to start the installation procedure.

Maybe there isn't such an option though?

---

### Post by benfindlay on 2006-09-20
I'm not sure, but the Shipit discs might actually have the text or server install built into them. If they have the text then you're good to go! If they have the server then you can install that too. Once the server is installed you are put at a command line, from where you can type ```
sudo aptitude install ubuntu-desktop
```
This will download and install the X server, gnome and all the apps you normally get with the standard GUI isntall. However, with such an old laptop I would recommend you install xubuntu-desktop, or even just download the xubuntu cd instead as it is a much "lighter" OS

---

