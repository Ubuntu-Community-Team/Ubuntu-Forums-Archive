---
title: "Mouse settings for mx510"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by jmasgalas on 2007-05-31
Okay I followed this guide for my mx510 mouse: [http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX510.2C_MX518.2C_MX900](http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Logitech_MX510.2C_MX518.2C_MX900)

Now Xserver will not start. Are the steps in the guide even necessary or accurate? I just had noticed my mouse movements were jumpy and thought that would help. Is there a better way? Can I recover my xserver from booting to recovery mode and copying over the backed up xorg.conf? I am not at home right now and can't give more detailed info but anything would help.

One more thing. My firefox fonts suck! I read through these forums but could not come up with one single guide that works and makes the fonts look better. Can you point to one?

---

### Post by aidanr on 2007-05-31
yes, boot into recovery mode (press escape when grub is loading) and type in:
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

and then type reboot to reboot

if you're mouse is working then i'd leave it as is, and instead try [lomoco]("http://lomoco.linux-gamers.net/lomoco.html")(sudo aptitude install lomoco) to increase the dpi and increase the [mouse polling]("http://ubuntuforums.org/showthread.php?t=392494&highlight=mouse+polling")

---

### Post by jmasgalas on 2007-05-31
thanks for the quick reply. i will try that. can you help me with the firefox fonts?

---

### Post by aidanr on 2007-05-31
```
gedit ~/.fonts.conf
```
copy/paste/save
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```

reboot

that's what i did anyway, everyone has a different opinion on what makes fonts look good, you may want to search for improved subpixel font rendering packages if it's still not good enough for you

---

