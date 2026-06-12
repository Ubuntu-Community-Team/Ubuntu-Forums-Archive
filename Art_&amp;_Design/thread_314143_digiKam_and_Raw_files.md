---
title: "digiKam and Raw files?"
date: 2006-12-07
forum: Art &amp; Design
---

### Post by beefcurry on 2006-12-07
I have a problem with the Image Editor in DigiKam, it displays pure black when trying to open a Raw file in DigiKam, to be exact its the image editor in Digikam that is not working as it should be, when i try opening a RAW file with it, it just shows me a black background, The image renders fine as a thumbnail, it only dosnt work in the image editor...

any ideas?

---

### Post by Aldrik on 2006-12-07
0.9.0 will have better support for RAW pictures. RC2 came out just the other day so shouldn't be to much longer to wait (if you dont wanna compile it your self that is).

---

### Post by Oki on 2006-12-08
Or you could try another program that can hadle RAW files, look here; [http://www.freewebs.com/artlinux/](http://www.freewebs.com/artlinux/)

---

### Post by beefcurry on 2006-12-08
Very well detailed site, I would host it (to get it off freewebs) if i still had my hosting plan which i decided i didnt need a while back :P. BlueMarine seems VERY promising, a Java version of Lightroom, im abit worried about speed but i'll definately have to try it. Im surprised no one mentioned BlueMarine before.

---

### Post by Oki on 2006-12-08
I would stay away from BlueMarine until it gets more mature, its still beta. I have tried Lightzone, and I love it for RAW converting. Sorry to tell its commercial, but free for Linux. Or you could look at Rawstudio, F-spot and Ufraw&#8230; well, you can check the list for yourself:-)

---

### Post by beefcurry on 2006-12-09
Ah yes, ive tried everything else But blueMarine. I would say Bluemarine dosnt work with my computer yet :P. The concept is good, i would say a good alternative to lightZone.

Lightzone is good but the functions are too light if not too little, Ufraw is my fav right now and raw studio is just too lacking in features. But thanks :D

---

### Post by ariel on 2006-12-10
I am using digikam rc2 (hot off the press) and it can read Nikon D80 raw files perfectly (edgy digikam package could not). Not only that, but they added *lots* of cool features like direct Gamma adjustment, Color Management and tons of others.

I could build RC2 (after building and manually installing exiv2), and it runs extremely well. Unfortunately, I could not build digikam-imageplugins 0.9.0RC2  under edgy. If anyone succeeded on this,  a small howto would be much appreciated :)

---

### Post by Jetjoint on 2007-08-06
Hi all,

I have exactly the same problem as Beefcurry in his original post. Has anyone come up with a solution? Does anyone else have this problem. I am using Canon Raw (CR2).

Thanks for your help..............

---

### Post by beefcurry on 2007-08-06
> **Jetjoint said:**
> Hi all,

I have exactly the same problem as Beefcurry in his original post. Has anyone come up with a solution? Does anyone else have this problem. I am using Canon Raw (CR2).

Thanks for your help..............

Try Re-installing DigiKam, best if you compile the newest version. :) I've solved mine that way, maybe I did something else but I can't remember now. And don't forget to have dcraw.

---

### Post by Jetjoint on 2007-08-08
Thanks Beef. I am trying to do that (install new version). However after typing ./configure it seems to be installing but I then get the error " Can't find X libraries. Please check your installation and add the correct paths!"

I am a bit of a noob. Any ideas? 

Thanks for your help

---

### Post by smartboyathome on 2007-08-09
install xorg-dev (I think). This will give it your X development libraries.

---

