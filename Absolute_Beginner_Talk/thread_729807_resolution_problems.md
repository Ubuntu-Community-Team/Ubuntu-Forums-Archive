---
title: "resolution problems"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by architeuthis99 on 2008-03-20
i have tryed to fix an old laptop (fujutsu lifebook). I downloaded GOS burnt on a cd.

When i got to the install menu, i had to pick the "install from safe graph mode" . Because the program could not find any resolution or something...  In the safe graph mode i was able to install the program, but everything was in a very small resolution. Like, the program was not using the whole screen. I googled it and found this guide"[  http://sysdigg.blogspot.com/2008/02/howto-change-screen-resolution-in-gos.html ](  http://sysdigg.blogspot.com/2008/02/howto-change-screen-resolution-in-gos.html ) "

but the problem is that the "Resolution" box is empty... i cant pick or change anything..
I have downloaded the right drivers i think  "Intel graph card 82815"  but i dont know how to install them.. or even if that is the problem.. 


 does this make any sense to any of you guys who are familiar with linux and/or GOS ?

---

### Post by penguinpi.com on 2008-03-20
what does your xorg.conf file look like?

---

### Post by architeuthis99 on 2008-03-20
i dont know how to access it ! :( whats the command for that?!   im very very new to this :p

---

### Post by unutbu on 2008-03-20
I'm not sure if I can help you, but if anyone here can, it will be helpful to them
if you run the following commands and post the output:

```

cat /etc/X11/xorg.conf
lspci | grep VGA
sudo lshw -C display

```

Also it might be helpful to provide a link, if available, to the driver you downloaded.

---

### Post by architeuthis99 on 2008-03-20
links to the drivers:  [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)  but they are not installed.

I enterd the commands and got a lot of data.  but how do i copy paste in linux?! =P  (IM SO NOOOB :P)

---

### Post by unutbu on 2008-03-20
Can you select the text with the mouse?
Pasting is down with the so-called second mouse button, which, is the middle button on a 3-button mouse, and is achieved by clicking both the right and left mouse buttons on a 2-button mouse.

---

