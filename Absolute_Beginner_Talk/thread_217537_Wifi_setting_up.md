---
title: "Wifi setting up"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by DMud on 2006-07-17
Hi

I was wondering whether anyone knows how to setup a wifi network. 
My card is a Linksys with an RTL8180 chipset. it shows up in the devices but it does not detect the wifi network. do I need to install something, or set it up somehow?

I would really appreciate any help.

Regards, 

D

---

### Post by inf0c0m on 2006-07-17
i would suggest installing network manager, and seeing if that helps. 
> 
sudo apt-get install network-manager-gnome

network manager allows you to run a windows like interface to wireless networks

---

### Post by DMud on 2006-07-17
Thanks Info.

so do I just type that in the terminal? or do I need to install something else?

Regards,

D

---

### Post by Sonic Alpha on 2006-07-17
That's a terminal command :)

---

### Post by DMud on 2006-07-17
Which means I just need to type it without installing anything else before that? (not the sharpest tool in the shed... I know...) ;)

---

### Post by Sonic Alpha on 2006-07-17
That command installs the network manager, so yes, that's all you need to type.

Though, you may wish to use the aptitude command instead: -

```
sudo aptitude update
sudo aptitude install network-manager-gnome
```

---

