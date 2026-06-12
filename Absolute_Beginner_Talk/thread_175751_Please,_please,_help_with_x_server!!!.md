---
title: "Please, please, help with x server!!!"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-13
I'm new to Ubuntu and Linux. My motherboard is a GeneratioNext(Genx) with a VIA/S3G Unichrome Pro IGP driver. I've tried running Ubuntu live with no success I get a msg that the x server failed to start. By default it uses vesa but it doesn't work. I've tried via, s3 and vga with no success either. Please help. I also tried installing Red Hat, it installed uneventfully but it can't boot-talks about killing init!:confused:

---

### Post by louis_nichols on 2006-05-13
After such a failed X session, can you post the contents of the file

/var/log/Xorg.0.log  ?

it should show us where the problem lies.

---

### Post by Koech on 2006-05-14
I don't think I'll be able to get hold of the contents of the file you talked of. Let me try anyway but if you can, please explain how. Thanks alot.

---

### Post by louis_nichols on 2006-05-14
well... the best way would be to boot from a livecd, I guess, although there is no guarantee it will start a gui. another way, if by any chance you also have a win installed on that box, would be to boot win and install either ext2ifs or ext2fsd for win, which will let you read your linux partitions.

---

### Post by uzi09 on 2006-05-14
I had the exact same problem, the issue was with just hardware support. I needed something called 915resolution. Dapper Drake carries this by default, so I went ahead and stuck with Dapper. I've been telling others as well, there are only a few more days until the final release date.

I'd give the live cd for Dapper a try if I were you.

---

### Post by DSn0wMan on 2006-05-14
When I had xsessions failing, I was able to use ctrl + alt + f1 to bring up a command prompt. 

I am not sure how well the different run levels work on a live CD though.

---

### Post by Koech on 2006-05-14
I've managed to get to /var/log but got no Xorg.0.log. I'll therefore post some files from the folder. I think these refer to the Red hat installation.

---

### Post by louis_nichols on 2006-05-14
It's gotta be there. Any start of the x server, or failed attempt to start it, will produce this file (it should happen on the livecd also). Still, it's a pretty big file, so if you don't log in to a GUI so you can paste its contents, or perhaps log in to a command terminal, but save it somewhere so you can attach it, then it's pretty useless... try to read it's contents and reproduce the last few lines, especially if they contain error messages.

---

### Post by Koech on 2006-05-14
i couldn't post the files

---

### Post by lnxlvr on 2006-05-15
I'm having the same problem as koech is having.I'm trying to run unbuntu 5.10 as a live cd on Dell Inspiron E1505 with intel duo core processor (Video Card	Intel® Graphics Media Accelerator 950). I'm getting an x server error. Here are the last few lines of the /var/log/Xorg.0.log

I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100, 

i810e,i815,i830M,845G, 852GM/855GM, 865G, 915G, E7221 (i915), 915GM,945G

Primary Device is: PCI 00:02:0
(WW)I810: No matching evice section for instance (BusID PCI:0:2:1) found
(EE) No devices detected

Fatal server error:
no screens found

Does it mean that ubuntu didn't find any drivers for my video card? How to fix this problem?

Thanks
Lnxlvr

---

### Post by prflfoawhgu on 2006-05-19
sudo nano /etc/X11/xorg.conf
Find "i815" in quotes. Change it to vesa. Save and exit, then type startx.

---

### Post by Koech on 2006-05-21
Have you succeeded yet? If you haven't, just go my way and install Dapper Drake. It had no x server problems like I had with Breezy.

---

