---
title: "Annoying graphics problem..."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by gabemorr on 2007-08-26
Hi
I have a nVidia 6100 integrated chipset which has worked fine in Linux distros until Feisty... But when I try to use it I cannot change out of an 800 X 600 resolution (I want my full 1280 X 1024). But when I upgrade from 6.10 to Feisty (via the Terminal) I can put my resolution from 640 X 480 to 1280 X 1024.
Also, when I couldn't figure out why the graphics cards I decided to try out some other Linux distros (Mint, Debian, etc) and with Debian I couldn't leave 640 X 480, with Linux Mint I got an error saying "Could not start GDM, cannot find /etc/init.d/kdm) or something like that.

Any help you could give me would be very much appreciate

Sorry if I posted a double topic or whatnot, I couldn't find any topics that could help me (but I don't know much about linux)

---

### Post by airbornemist6 on 2007-08-26
you should be able to fix your problem by first enabling the restricted driver, and then opening up a terminal and typing
```
sudo nvidia-settings
```

i think thats the right command... if it's not... sorry, i used to have an nvidia, but i switched to an ati because my nvidia fried and i was short on monies xD

---

