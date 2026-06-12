---
title: "3rd time out - Wubi time?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Belgatom on 2007-12-27
Up to now, I've managed to install Dapper Drake on my old desktop. Feisty Fawn ended up on my little Vaio with a little bit of help from my friends. But up 'till now, my main pc has stayed in MS country. 

It's time to flip that last switch. So, I'm planning on going the Gutsy Gibbon way on my current pc. So now for my question. The thing that scares me most is off course the drivers. Dapper Drake did everything out of the box (except Nvidia support for 3d), Feisty Fawn in combination was a bit of problem that only a friend was able to solve. [COLOR="Green"]My question, if I install Wubi in combination with Gutsy, will I be confronted with the same driver problems as a full install of Gutsy?[/COLOR] If so, I could easily testrun Gutsy the Wubi way and get myself prepared for when I go for that final switch. I tried the live CD and had to start in safe mode because the other mode just hung and after booting into the safe mode, no sound. Once I have sound, 3d support and network, I will make the switch. The rest is easier. Oh, btw, my current soundcard is an Audigy (no idea which one actually). 

[COLOR="Green"]Would Gutsy have less trouble with a Soundblaster Live! card? [/COLOR]

---

### Post by cjm5229 on 2007-12-27
What Wubi does is creates a large folder in Windows that has an EXT3 file format. Then it downloads and installs Ubuntu into it. so Ubuntu would have to use all the hardware on your computer, just as it would in a full install. It should be a great way to try it out.

---

### Post by cjm5229 on 2007-12-27
For your sound problem try this [http://ubuntuforums.org/showthread.php?t=649983&highlight=audigy](http://ubuntuforums.org/showthread.php?t=649983&highlight=audigy)

Good Luck.

---

### Post by Belgatom on 2007-12-27
> **cjm5229 said:**
> For your sound problem try this [http://ubuntuforums.org/showthread.php?t=649983&highlight=audigy](http://ubuntuforums.org/showthread.php?t=649983&highlight=audigy)

Good Luck.

Looks good. Will try and return any gathered info. Audio does seem to be a handfull. ON my Vaio, I have to adjust the volume for the headphone jack seperately to the main volume. Thanx for the Wubi info. Will be trying that pretty soon.

---

### Post by Belgatom on 2007-12-27
OK, just been thinkin' (I do that sometimes). Howsabout this then?

If I can install Wubi and Ubuntu on my current Windows PC, I've already gathered that I will need to get the hardware to work, so installing all the drivers and stuff. This seems pretty no risk situation. But correct me if I'm wrong, isn't there a way to create an install Ubuntu CD from the existing configuration. Does this mean that I could create this customized Ubuntu CD from within the Wubi Ubuntu environment and then use it on a fresh hard disk to install Ubuntu without having to go through all the adjustments and driver problems that I encountered in my Wubi environment?

Extra credit question: I just took Wubi for a testdrive using the automatic install way (no predownloaded iso) and I noticed it started downloading 7.04. Cancelled and uninstalled. Is there a Wubi 7.10?

---

### Post by cjm5229 on 2007-12-30
I think there is a way to make a bootable CD with your system backed up on it, but I can't remember the name of the app, I think I saw something about it in Wubi's forum or FAQ I don't remember which. I don't believe that Wubi is working with 7.10 yet.  I don't have Windows on my computer so I haven't been able to try Wubi out to much. I did install WinVista, a few weeks ago to a small Partition and tried Wubi, it did only install Feisty, but after about three days of Windows I had enough and took it back out. The Partition was too small to do much more than install Wubi before I ran out of HDD space so I couldn't try Upgrading it to 7.10. With the restricted drivers manger in Gutsy it should be pretty easy to solve most problems. Just write down the steps you use to solve a problem and you should be able to get a full install up and running in a matter of min. I have noticed that laptops seem to give Ubuntu fits, but most desktops pretty much will run "out of the box" ATI graphics sometimes cause problems but Intel and Nvidia seem to work quite well, most sound problems are a matter of getting the right switches turned on. Use it as a tutorial then you will be ready when you go for the real thing:) Good Luck.

---

### Post by Belgatom on 2007-12-30
Another very good and unambiguous answer. Thanks again.

---

### Post by tylerspaska on 2007-12-30
> **Belgatom said:**
> Extra credit question: I just took Wubi for a testdrive using the automatic install way (no predownloaded iso) and I noticed it started downloading 7.04. Cancelled and uninstalled. Is there a Wubi 7.10?

i have installled wubi 7.04 on a few windows computers and it always works really well. i hear there is an alpha version of 7.10, but it has a lot of bugs and probably isn't worth the headache. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

i have tried to upgrade within my wubu ubuntu to 7.10 using the conventional download and upgrade, but it always causes problems usually with HAL and internet connectivity. i think the general idea is use wubi 7.04 for now and wait until 7.10 is ready.

---

