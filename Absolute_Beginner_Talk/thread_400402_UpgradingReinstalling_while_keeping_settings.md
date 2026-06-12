---
title: "Upgrading/Reinstalling while keeping settings"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by rcorlett on 2007-04-03
Okay so I have been having real trouble getting either driver for my ATI mobility radeon card installed. I had it working...then it lost it. So I am looking to reinstall Ubuntu and then try again, as that seems to help a lot of people. I may upgrade to Feisty instead of reinstalling Edgy.

What is the best way to go about retaining my settings when doing this (eg. desktop settings, user data....)? Will I need to install programs/codecs etc again?

Cheers!

---

### Post by Patrick K on 2007-04-03
The best way to keep your settings is to create a separate /home partition. This is where your personal settings and files are saved. I don't have a link on how to do this but I'm someone will be along soon with one.

---

### Post by rcorlett on 2007-04-03
Aha, that sounds good.

 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

- seems to be a good guide. 

So my personal settings will be saved, but will it reset my graphics card settings? That is what I am after, as I think from multiple installations/de-installations of various drivers I have messed with it too much.

---

### Post by Patrick K on 2007-04-03
More than likely you will need to reinstall video drivers. They seem pretty touchy. ATI drivers, so I hear, are somewhat difficult to configure properly. 

The Envy script [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) works pretty well. At least for nvidia drivers. It supports ATI but I have a nvidia card so haven't tried it.

I haven't reinstall so I don't know if you will have to reinstall all your programs even with a /home partition. I suspect some will need to be reinstalled.

---

