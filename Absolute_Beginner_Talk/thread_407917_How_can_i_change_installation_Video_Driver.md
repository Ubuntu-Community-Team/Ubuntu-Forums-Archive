---
title: "How can i change installation Video Driver"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by kchimko on 2007-04-12
Hi Guys,

I am using an Nvidia 7800Gt video card and i am quite certain it is causing me to get grphic curruption issues while attempting to install Ubuntu.

Basically it will show the gui bassed installer with lines going across and whatnot, aswell this freezes the install. I can install no problem in text only mode but alas i cannot boot into the OS without getting the same issue.

If you could please provide for me a way on how to change the Driver which is being loaded up for my Nvidia card so tha ti can install using the GUI. OR better yet give me a way so that i can boot into the text ubuntu mode and please provide commands i could use to change the default driver for a temporary fiix to allow me to boot into the OS and download the lastest Nvidia driver. 

Thank you for your help!

---

### Post by taurus on 2007-04-12
Assuming that you have already installed Ubuntu on your machine, boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Use **vesa** driver for your graphic card for now and once you get it running, then install nVidia driver for it.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by kchimko on 2007-04-12
great!

I am at work now but i will give this a shot when i get home.

I appreciate this!

Thank you!

---

