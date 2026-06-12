---
title: "Montior Refresh Rate Problem"
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by Hamad on 2005-06-05
My Montior is Samsung SyncMaster 150MP. I'm using Ubuntu Linux 5.04 : The Hoary Hedgehog Release.
My screen resolution is 1024x768 px.
I need to set the Refresh Rate of my screen to 60 Hz, but in the screen resolution preformances the Refresh rate has only 85 Hz in the list. So is there anyway i can fix this problem ?

Thanks.

---

### Post by poofyhairguy on 2005-06-05
[QUOTE=Hamad]My Montior is Samsung SyncMaster 150MP. I'm using Ubuntu Linux 5.04 : The Hoary Hedgehog Release.
My screen resolution is 1024x768 px.
I need to set the Refresh Rate of my screen to 60 Hz, but in the screen resolution preformances the Refresh rate has only 85 Hz in the list. So is there anyway i can fix this problem ?

Thanks.[/QUOTE]

It can be fixed....but why would you want to? I mean...85 is better. It defaults to the better. There is a file to edit that will make it not do that....but it a lot of work to make things worse unless it doesn't work.

---

### Post by mark on 2005-06-05
[QUOTE=poofyhairguy]It can be fixed....but why would you want to? I mean...85 is better. It defaults to the better. There is a file to edit that will make it not do that....but it a lot of work to make things worse unless it doesn't work.[/QUOTE]
 I agree with poofyhairguy - I'm currently running 1152x864 at 85Hz - trust me, the higher that last number (that your monitor can support), the better...

---

### Post by alexmoose on 2005-06-05
a 60 hz refresh rate is required to run some emulators, and to loop Nintendos and stuff through a video capture card.
 open a terminal and type in sudo dpkg-reconfigure xserver-xorg. this will allow you to choose many, many modes of different resolutions and refresh rates, just make sure to read everything, and you should be okay.

---

