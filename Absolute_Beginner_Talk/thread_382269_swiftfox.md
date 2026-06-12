---
title: "swiftfox"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by pesach on 2007-03-11
I was using 6.06, but then I had to do a clean boot.  I decided tha I might as well update to 6.10.  On 6.06, firefox had barely any plug-ins supported, so I dwonloaded swiftfox from automatix, and it worked perfectly.  Now, I cannot even get automatix on my computer (website down) so I decided to install swiftfox manually.  I went to their website, and downloaded swiftfox for AMD64 (my processor) now I have a folder on my desktop called swiftfox-2.0.0.2-athlan64.tar.bz2 I opened it, clicked on swiftfox, and a whole jumble of folders jumped out at me.  What do I click on, is there some other way to get automatix, or swiftfox?

---

### Post by shirilover on 2007-03-11
Have you tried using the repository as shown [on this page]("http://www.getswiftfox.com/debian.htm")

---

### Post by Bachstelze on 2007-03-11
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

---

### Post by pesach on 2007-03-11
what does this mean?
   1.  Add the repository to your sources.list file:
      deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
   2. Install from a terminal window as root using the correct package name:
      apt-get update && apt-get install swiftfox-athlon-xp

---

### Post by Bachstelze on 2007-03-12
```
sudo nano /etc/apt/sources.list
```

At the end of the file, add this line :

```
deb http://getswiftfox.com/builds/debian unstable non-free
```

Then save the file (Ctrl+O, Enter to confirm), exit nano (Ctrl+X) and do :

```
sudo apt-get update
sudo apt-get install swiftfox-pentium-m
```

(Replace pentium-m with the arch you want, of course)

---

### Post by pesach on 2007-03-12
> **HymnToLife said:**
> 

(Replace pentium-m with the arch you want, of course)
 Im sorry, im kind of a noob.. what is an arch, do you mean cpu?, like mine is  amd64, so do I put that in?

---

