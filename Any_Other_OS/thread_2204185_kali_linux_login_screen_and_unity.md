---
title: "kali linux login screen and unity"
date: 2014-02-07
forum: Any Other OS
---

### Post by techme2 on 2014-02-07
my kai linux works fine but today suddenly my kali looks looks completely different my menus are disappear even my login screen also looks different please see below attach file  see below link  [http://img.photobucket.com/albums/v482/MKRayden/kl_zps69590f40.png](http://img.photobucket.com/albums/v482/MKRayden/kl_zps69590f40.png)

---

### Post by Bucky Ball on 2014-02-07
*Thread moved to **Other OS/Distro Support**.*

---

### Post by techme2 on 2014-02-07
sorry i didn't know this by the way the way someone please help me this isssue

---

### Post by mastablasta on 2014-02-07
try ```
startx
``` command

Kali is Debian based. Debians is slightly different. It seems you only got to terminal console. if all is ok then you should be able to get to menues by starting X.

did you maybe do some virtualbox upgrade or something?

you can also try pressing crtl+atl+F7

---

### Post by techme2 on 2014-02-07
startx commandnot found and yes if upgrade and crtl+atl+F7 not works as well should i reinstall again or still there is some hope

---

### Post by mastablasta on 2014-02-08
if it's not startx then it's either an init command (dont' knwo init which might be worth asking on Kali forums) or start service [service name]. i do not know how Kali does it. if you don't have anything important you could just reinstall.

maybe try:
start service lightdm

also since you are running it in Vm i suggets before doing updates to create a snapshot of the image. that way if things go wrong again you could just backtrack to previous system snapshot.


furthermore if you decide to reinstall upgrade virtualbox to latest version before doing the reinstall. you might also try upgrading vbox to latest version and see if that helps to resolve original issues. perhaps they had a kernel upgrade and it messed up with virtual drivers?!

EDIT: Backbox linux on the other hand is Ubuntu based. and i think they have simialr if not same tools as Kali and also hardened kernel.

---

### Post by techme2 on 2014-02-09
it seems there is no solution for above error except uninstall

---

### Post by Bucky Ball on 2014-02-09
Have you tried the Kali forums?

---

### Post by Stephen_Bunn on 2014-06-04
If you are still wondering how to get the UI to startup from the console in Kali, all you need to do is start up the GDM by entering the following command in the command line: ```
/etc/init.d/gdm3 restart
```

---

