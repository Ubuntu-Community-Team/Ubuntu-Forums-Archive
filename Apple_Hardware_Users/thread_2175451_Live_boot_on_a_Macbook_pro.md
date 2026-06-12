---
title: "Live boot on a Macbook pro"
date: 2013-09-19
forum: Apple Hardware Users
---

### Post by Theobalt on 2013-09-19
Hi!

My girlfriend's macbook pro no longer boot, so I would like to use a live CD to at least check the state of the hard drive and do a backup before some genius touches it. The macbook was bought in 2008, in case it could help you...

I tried booting with ubuntu 12.04.3 AMD+mac (an iso I found on the website) and an old 10.04-64 bits CD I found in my stuff. The first menu appears when I press spacebar, with options like "try without installing", "install", "...". I choose to try without installing, and then it seems to go nowhere. Still nothing after an hour, except maybe a flashing underscore line in the top left corner.

Anyone has a clue what is going wrong? Maybe another distro would work better? 

Thank you very much!

---

### Post by Theobalt on 2013-09-19
Hi!

 My girlfriend's macbook pro no longer boot, so I would like to use a live CD to at least check the state of the hard drive and do a backup before some genius touches it. The macbook was bought in 2008, in case it could help you...

 I tried booting with ubuntu 12.04.3 AMD+mac (an iso I found on the website) and an old 10.04-64 bits CD I found in my stuff. The first menu appears when I press spacebar, with options like "try without installing", "install", "...". I choose to try without installing, and then it seems to go nowhere. Still nothing after an hour, except maybe a flashing underscore line in the top left corner.

 Anyone has a clue what is going wrong? Maybe another distro would work better? 

 Thank you very much!

---

### Post by Quackers on 2013-09-19
It could be a graphics problem.
When the purple screen appears press F6 and look to the bottom right of the screen. There are about 6 boot options, one of which will be "nomodeset". Try that one first and see if it will boot to the desktop.

---

### Post by Quackers on 2013-09-19
Try the nomodeset boot option by pressing F6.

---

### Post by Theobalt on 2013-09-19
Nice, now it works with the "nomodeset" option! But, ubuntu doesn't seem to view the hard drive. Is there any package that must be installed so a mac partition could be detected, or does it mean it is dead for good...

---

### Post by Quackers on 2013-09-19
That's a start :-)
Not sure about that but I don't think so.
Do you mean Ubuntu can't read the OSX file system or do you mean Ubuntu just doesn't see the drive at all?
If it's the latter I fear the drive could be dead.

EDIT
It might be worth checking that the Mac's hard drive is properly connected.

---

### Post by Theobalt on 2013-09-19
Success!!! 

But, ubuntu doesn't seem to see the hard drive. Does it mean it is dead for good? Or do i need to install some package so the mac partition (hence, all the hard drive) becomes visible to ubuntu?

---

### Post by Theobalt on 2013-09-19
In gparted, for example, it says "No devices detected". The drive doesn't seem to be detected at all. Sounds bad to me...

Maybe I should begin considering some open heart surgery on her computer...

---

### Post by Quackers on 2013-09-19
Hmm, I suspect so. Not being detected at all can't be good.
Might be worth a look inside but don't trash it, it could still be worth money!

---

### Post by cariboo on 2013-09-19
Please do not create multiple threads on the same subject, I have merged your two threads.

---

