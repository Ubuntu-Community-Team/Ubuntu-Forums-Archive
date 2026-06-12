---
title: "Envy doesnt work Feisty- How do I install Nvidia drivers now?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-30
For some reason, if I try to install drivers Envy tells me it wont work. When I view the .log file, it tells me my Operative System is not supported (Im guessing Fiesty upgrade). 

I want to be able to run Baryl (sp?) but considering it uses OpenGL accelerated graphics, I know I need my video card setup.. Any ideas?

---

### Post by overdrank on 2007-03-30
> **GSF1200S said:**
> For some reason, if I try to install drivers Envy tells me it wont work. When I view the .log file, it tells me my Operative System is not supported (Im guessing Fiesty upgrade). 

I want to be able to run Baryl (sp?) but considering it uses OpenGL accelerated graphics, I know I need my video card setup.. Any ideas?

Hi have you tried this way to use envy
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
Hope it works for you. Good luck!

---

### Post by TheMono on 2007-03-30
Basically, you answered your own question. Envy does not support Feisty.

Install the drivers from the repository instead, they work fine. 
sudo apt-get install nvidia-glx linux-restricted-modules

---

