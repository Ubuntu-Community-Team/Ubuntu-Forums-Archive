---
title: "[SOLVED] New Video Card: No Ubuntu"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by ladybumavere on 2008-01-15
Just got a GeForce FX 5700LE to replace my Voodoo3 3000.  Works perfect with Windows, but when I boot to Ubunutu I get the command line.  Now the quesiton I have is should I just run "sudo dpkg-reconfigure -phigh xserver-xorg" from said command line to reconfigure the xorg.conf for the new video card, or will that not work, or what should I actually do since I really am just pissing out these guesses?

---

### Post by ahaslam on 2008-01-15
I'd try: 
```
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable
```
But I may be wrong ;)

---

### Post by stchman on 2008-01-15
> **ladybumavere said:**
> Just got a GeForce FX 5700LE to replace my Voodoo3 3000.  Works perfect with Windows, but when I boot to Ubunutu I get the command line.  Now the quesiton I have is should I just run "sudo dpkg-reconfigure -phigh xserver-xorg" from said command line to reconfigure the xorg.conf for the new video card, or will that not work, or what should I actually do since I really am just pissing out these guesses?

I have an FX5700 Ultra that works fine under Feisty.  Either install the restricted drivers or use Envy.

Use the following to reconfigure your xorg.conf file.

```
sudo dpkg-reconfigure xserver-xorg
```

After that you should be using the "nv" driver.  That will get you to the Gnome desktop.  Once there enable the restricted driver.

---

### Post by ladybumavere on 2008-01-15
> **stchman said:**
> I have an FX5700 Ultra that works fine under Feisty.  Either install the restricted drivers or use Envy.

Use the following to reconfigure your xorg.conf file.

```
sudo dpkg-reconfigure xserver-xorg
```

After that you should be using the "nv" driver.  That will get you to the Gnome desktop.  Once there enable the restricted driver.



Thanks man, that plan worked perfect.  Got it up and running and loving it all over again.

I really appreciate the help!

---

### Post by stchman on 2008-01-16
> **ladybumavere said:**
> Thanks man, that plan worked perfect.  Got it up and running and loving it all over again.

I really appreciate the help!

I am glad I could be of help.

---

