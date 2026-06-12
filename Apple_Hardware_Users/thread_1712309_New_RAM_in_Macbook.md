---
title: "New RAM in Macbook"
date: 2011-03-22
forum: Apple Hardware Users
---

### Post by falsedichotomies on 2011-03-22
Hi. I'm running 32-bit Ubuntu 10.10 on a Macbook 3,1. The other day, I decided to upgrade my RAM from 1GB to 4GB, the maximum amount that I thought that my computer and Ubuntu could handle.

The installation went fine, but my 4GB are currently reading as 3GB in virtual box and when I use the top and free commands. Does anyone know the reason for this and if/how I can fix it?

The website that I bought the RAM from says that "Firmware in MacBook2,1 , MacBookPro2,1 and MacBookPro2,2 models will display 4GB as 3GB even though most operations will access the full RAM," but since I'm not using any of those models or even running OSX, I don't think this is the problem.

Thanks in advance!

---

### Post by desnaike on 2011-03-22
You need the 64 bit version of ubuntu or Pae kernal on 32 bit.

---

### Post by falsedichotomies on 2011-03-22
Ahhh okay.. I will dabble. Thanks.

---

### Post by falsedichotomies on 2011-03-27
So okay, I've got a new complication now. I installed the pae kernel and everything was going smoothly for about a day with my memory showing up as 4GB.

Then all of a sudden, my internet browsers started repeatedly crashing (both firefox and chrome) as well as the virtual system (XP 32-bit) that I was loading using VB. At first I thought it was my firewall settings, but turning it off didn't help, and neither did reinstalling the programs in question, so I concluded that it had to either be the RAM or the new kernel. First I uninstalled the pae kernel, but my browsers were still crashing. Then, I swapped in the old 1GB of RAM and this seemed to solve the problem. Now everything is running smoothly again and I haven't had a crash in a day and a half.

Does this seem like a case of bad RAM, and if so, is there a way to go about confirming this? The reason I ask is because I thought that if I had bad ram my entire OS would crash, not just my browsers and VB.

---

