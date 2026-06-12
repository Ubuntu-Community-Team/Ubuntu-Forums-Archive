---
title: "Monitor resizes itself on every boot"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by hunter_te on 2007-11-26
First of all i am new to linux. I am on the brand new gutsy gibbon. And i must say i am having a really nice time learning it. :)

I have a viewsonic 19" widescreen which shows around 75% screen everytime i boot into it. Then i have to go to administrator>screens config(something like this) and change the hertz rate from 60Hz to 75Hz, only then it shows full screen. Also when i am playing some video and i do it full screen, it again resizes to 75% of the total screen. So i cant see any video in full screen. Then i again have to do that same 75Hz thing. 

Kindly Help.

Thanks in advance..

---

### Post by overdrank on 2007-11-26
> **hunter_te said:**
> First of all i am new to linux. I am on the brand new gutsy gibbon. And i must say i am having a really nice time learning it. :)

I have a viewsonic 19" widescreen which shows around 75% screen everytime i boot into it. Then i have to go to administrator>screens config(something like this) and change the hertz rate from 60Hz to 75Hz, only then it shows full screen. Also when i am playing some video and i do it full screen, it again resizes to 75% of the total screen. So i cant see any video in full screen. Then i again have to do that same 75Hz thing. 

Kindly Help.

Thanks in advance..

Hi could you tell us what the model of graphics card ? If it is a nvidia then you may try using the nvidia settings with this command ```
gksudo nvidia-settings
``` using the alt, F2 keys.

---

### Post by hunter_te on 2007-11-26
Hey hi overdrank. 
I am using onboard intel g33 graphics. My board is [Asus P5K-VM]("http://www.asus.com/products.aspx?l1=3&l2=11&l3=542&l4=0&model=1690&modelmenu=1").

Thanks.

---

### Post by hunter_te on 2007-11-26
Myself solved it.
It was simple, just had to go to screen resolution manager and set the default values to 1440x900 and 75Hz as default. :guitar:

---

### Post by Hatchetfish on 2007-11-29
I'll bet you a dollar it comes back randomly.  I've been around that circle ten or fifteen times.

---

