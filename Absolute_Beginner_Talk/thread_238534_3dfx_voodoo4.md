---
title: "3dfx voodoo4"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2006-08-17
Hello all,

I have a 3dfx voodoo4 / voodoo5 video card in an old computer, and I can't set my resolution to 1024x768.  No matter what I change in the xorg.conf file, its always end up with 800x600.  I'm wondering if I need to install any special driver for this card.

thanks all
Kpham.p

---

### Post by djsroknrol on 2006-08-17
I had a Voodoo in my AMD 400 K-6 and all I could muster was 640 x 480...I don't think you'll get any more than 800 x 600 from a 64MB video card...I might be wrong however...chime in anyone...

---

### Post by kpham.p on 2006-08-17
WooHoo Got it to works.....
I found this thread: [http://ubuntuforums.org/showthread.php?t=56556](http://ubuntuforums.org/showthread.php?t=56556).  

adding the HorizonSync and VertiRefresh for my monitor and it works.

Section "Monitor"
        Identifier      "Daewoo CMC-1707B"
        HorizSync       30-70
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Thanks,
Kpham.p

---

### Post by djsroknrol on 2006-08-17
Great...I'll admit when I'm wrong...glad you got it working...

---

### Post by kpham.p on 2006-08-17
Thanks for repling to my thread though ;-).  I just so surprise that 2 line would make it works.  I'm just so happy now :D.  aight, now is time to learn how to setup an OpenVPN server on this old box.

thanks
kpham.p

---

### Post by h2gofast on 2006-08-17
It's definitely doable, my son's pc is running an old voodoo 5.

---

