---
title: "[SOLVED] is there a .deb package for the restricted audo codecs?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-07-14
my brothers computer is having bios issues and so no wireless, but that is not the issue the issue is he wants to play mp3s so i need to download a .deb package for the audio codecs. i hate tarballs so please no tar.gz files.

---

### Post by DSn0wMan on 2007-07-14
Is he using Ubuntu 7.04?

---

### Post by rickycodie on 2007-07-14
yes but like i said no internet

---

### Post by p_quarles on 2007-07-14
Do you -- or anyone you know -- have access to a machine with Ubuntu and an internet connection? If so, you could make an "apt-on-cd" with those packages on it.

And, no, I have no idea if those codecs have ever been released as .debs. You could check Debian's package pages, though.

---

### Post by jediborger on 2007-07-14
You can download the packages for him by going to packages.ubuntu.com. Here's the links for the two packages he'll need, just goto the bottom and select the package for your machine, usually i386.
[http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly")
[http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly-multiverse]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly-multiverse")
Now I think that the dependencies for these should already be installed on his machine but if they aren't then you'll have to manually download yourself, which can turn into a real pain. Hope this helps.

---

### Post by rickycodie on 2007-07-14
i am running ubuntu how do i make a cd like that?

---

### Post by ev5unleash1 on 2007-07-14
Ok to fix the wireless, If your wireless is a restricted driver this should work.
System > Administraton >Network. Then if you see the wireless device click it and then click propertys. Make sure you know the exact information about the network like the name, type of code and the code to get in. Then once you are in the propertys uncheck enable roaming mode then type in the EXACT network information else it won't work. Then click ok. If the wireless network is unchecked check it but make sure a dialog comes up saying changing network setting and then goes away. If it is check then uncheck it and then check it again and make sure that it says Changing wireless settings. Now close everything and try to fire up a firefox browser. If it did not work then restart and/or fiddle around with the check box because I know it does not act right some times.

If you need a driver for the wireless adapter then try some linux websites with drivers and burn them to a CD and put then on the PC with the internet connection/ try the same with the audio drivers.

And if your audio is not working/you don't hear it. This gets fixed in most cases when you update Ubuntu. (Needs a working internet connection).

I hope this helps.

---

### Post by rickycodie on 2007-07-14
the wireless is bios related. there is a password on the bios and network card is set to off. the password won't let me change it on. please no more help about the wireless. thank you

---

### Post by ev5unleash1 on 2007-07-14
Sorry, there may be a setting depending of the BOIS. But take me up on that burning drivers of your audio.

---

### Post by p_quarles on 2007-07-14
> **rickycodie said:**
> i am running ubuntu how do i make a cd like that?
First, you'll need to install this ```
sudo apt-get install aptoncd
```

Then, you'll find the utility in the System >> Admin menu. You can put whatever packages you're brother would like to have onto a CD, and use that to install.

---

### Post by rickycodie on 2007-07-14
thanks it worked

---

