---
title: "Boot Up Screen Changed"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by andril on 2006-10-20
Hello all I need help restoring the original Ubuntu (orange) boot screen. I recently installed the Kubuntu and Xubuntu desktops. Now the Xubuntu bot up screen shows - can you help me? ](*,)

[IMG]http://shots.osdir.com/slideshows/slideshow.php?release=738&slide=4&title=ubuntu+6.10+knot+3+screenshots[/IMG]

---

### Post by jordanmthomas on 2006-10-20
If you look in synaptic for usplash-theme-xxx
you will find the splash packages.
Uninstall the ones you don't want and reinstall the ubuntu one.

(However, this will make you uninstall kubuntu-desktop and xubuntu-desktop, so if you plan on doing major upgrades, you will need to reinstall them and then repeat this procedure)

---

### Post by skymt on 2006-10-20
Or, run this:```
sudo update-alternatives --config usplash-artwork.so
<pick one>
sudo dpkg-reconfigure usplash
```

---

### Post by jordanmthomas on 2006-10-20
skymt's solution is much better and much more elegant.  I'd go with it.  ;)

---

### Post by andril on 2006-10-23
Thanks All I will give it a try! :D

---

### Post by andril on 2006-10-23
:(  usplash restored - but I noticed my original GDM & originals SPLASH has changed](*,)

---

### Post by bulldog on 2006-10-23
Try this one,

[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

---

### Post by andril on 2006-10-23
I also noticed that the original Human GDM & original Splash Screen has gone to an actual GNOME 2.4 spalsh instead of the Ubuntu branded one. All I did is install Xubuntu & Kubuntu ](*,) 

Thanks "skymt" worked after all

---

### Post by andril on 2006-10-23
> **bulldog said:**
> Try this one,

[http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper](http://doc.gwos.org/index.php/Serengeti_Usplash_for_Dapper)

Thanks!!!!! Looking better

---

