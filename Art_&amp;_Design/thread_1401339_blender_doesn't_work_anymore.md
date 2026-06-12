---
title: "blender doesn't work anymore"
date: 2010-02-07
forum: Art &amp; Design
---

### Post by Salvagluque on 2010-02-07
Hi

I have been installing some apps for ubuntu 9.04 64-bits, and also I tried to make dual monitor my desktop, with out success. I reverted the graphics configuration and xorg.conf but since then blender doesn't run, I tried uninstalling and reinstalling blender but nothing. 

this is the link to the tutorial I used to try to change my desktop environment to a dual monitor 
[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

Thanks

---

### Post by durand on 2010-02-08
Open a terminal (Applications > Accessories > Terminal) and type blender, press enter. What error comes up?

---

### Post by Salvagluque on 2010-02-09
Hi,
I did found the error, it was the xorg.conf. What I did to solve it was to go to this folder /etc/X11/. Then I serached for a bbackup file of the xorg.conf open the new one and the backup and just copy paste the old one in the new one.

---

### Post by durand on 2010-02-10
That's great! Do you know what might have caused it?

---

