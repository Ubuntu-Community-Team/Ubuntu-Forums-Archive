---
title: "Nvidia Geforce 8500GT"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Knuxyl on 2007-11-30
I have the the nvidia geforce 8500gt 512mb graphics card and im trying to install ubuntu on an empty 10gb hard drive. i have the image burned, i boot up with it, and when i click install, my monitor stops recieving signal and goes to a black screen. ive tried with vga options, ive tried with safe graphics mode, nothing. how can i get this to work? ty

---

### Post by kefurd06 on 2007-11-30
sorry, i don't have any advice for troubleshooting thatp roblem, but if you're trying to install from the LiveCD (burned image boots into ubuntu and install icon is on the desktop), then you might try the alternate text installer. it's more reliable and so far ubuntu has worked on every computer that liveCD wouldn't boot on.

---

### Post by Colro on 2007-11-30
This issue seems very common with the 8xxx series. I don't own one (unfortunately..), but I wouldn't be suprised if such new hardware isn't well-supported yet.

---

### Post by Knuxyl on 2007-11-30
well i already had ubuntu installed on the hard drive but it would go to a black screen and i thought maybe it was because i had enabled effects or w/e on it through a different pc so i wiped it and im trying to do it again. i tried the text installer but it had an error and said that Install Base System coulnt install or w/e. im going to burn it again but wut do i do if that doesnt work?

---

### Post by Colro on 2007-11-30
I know that the default driver works for a friend of mine, but the 3d accelerated driver gives the same issue you describe. If you still have your old installation, you can boot into safe mode (press ESC when grub comes up, you won't have much time so hit it as fast as you can).

Then run this command:

```
dpkg --reconfigure xserver-xorg
```

It'll give you a bunch of screens with options. The defaults usually work just fine, so don't change anything unless you know for a fact that it needs changed.

This'll only give you a 2D driver, though, so 3D applications such as games probably won't be able to run at all. I don't have an 8xxx series card myself, so I can't tell you where to get a driver that'll work for them, but I'm sure someone here knows.

---

### Post by overdrank on 2007-11-30
> **Colro said:**
> 
Then run this command:

```
dpkg --reconfigure xserver-xorg
```



```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Knuxyl on 2007-11-30
well i already whiped the hard drive. if the fresh install doesnt work that code will fix it?? btw im a total newb to linux, i have no idea wut a terminal is or anything but im learning. thank you very much :)

---

### Post by Knuxyl on 2007-11-30
ok i just tried again with the new burned text disc and it wouldnt install all of the software packages, it froze at 6% and stayed there forever and then said error. if ubunutu wouldnt lock the drive i could take the disc out and clean it cuz its a **little** scratched. i went ahead and installed the bootloader and finished isntallation but when i boot up its all text. like theres no graphics. i can log in and everything though. is there a code to boot up to the graphics part??  is linux worth all this bs im going through?

---

### Post by Sef on 2007-11-30
So Ubuntu can install, but you have to GUI or graphics?

---

