---
title: "Beryl Questions"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by maxlinux on 2007-04-21
Hi

Does anyone know how to run simple beryl setting without strating up Beryl in Fiesty. I have the whitescreen issue and would like to change the rendering etc. (From forums I read) but it gives no explanation of how to run simple without starting Beryl. Beryl used to work, but  in my infinite wisdom messed it up and are battling to fix it.(Messed about with screen resolutions)

Or can I edit the config files directly? If so where would I find the correct files and how would I need to edit it?

Tried searching for answers but to no avail.

Thanks:)

---

### Post by ffxr on 2007-04-21
you could try removing beryl completely from your system:

```
sudo apt-get --purge remove beryl* emerald* libberyl* libemerald*
sudo apt-get --purge autoremove
sudo apt-get autoclean

rm -r ~/.beryl
rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```

then reisntallling it..

[just a thought]

---

