---
title: "Visual Effects do not work on my ibook g4"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by Dimi123 on 2009-05-14
Visual Effects do not work on my ibook g4 
my os is ubuntu 9.04 all works good but the effect doesnt
or games like nexus oder warsow why????

pls help

---

### Post by mkvnmtr on 2009-05-14
Most of compiz worked on my Ibook in distros past. I didn't like it's resource usage or feel that it was needed so I think since 8.04 I have removed all the programs related to it. Thus I don't know how it does in 9.04. You have enabled it under desktop effects? As I remember I could never get them all but got quite a few.

---

### Post by Dimi123 on 2009-05-14
i cant enable desktop effects i think my radeon drive didnt work :/ 
i start my ibook an the first i see is (  2.0000) radeonfd *** rom content 
or somethink like that

---

### Post by arsnic265 on 2009-05-14
Just a thought but i would make sure you are using the nvida, if that's what you have, drivers. After installing 9.04 on my macbook pro i was not able to use visual effects until i used nvida's driver.

---

### Post by Dimi123 on 2009-05-14
where can I see if I have nvidia od ati?

---

### Post by lethrj on 2009-05-14
> **Dimi123 said:**
> where can I see if I have nvidia od ati?

lspci | grep VGA

[]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/354677")

---

### Post by Dimi123 on 2009-05-15
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)

---

### Post by lethrj on 2009-05-15
I am having similar problems on my PowerBook G4.

I'm going to investigate this route, when I find a minute:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


> 
 All these cards and derivatives have full 3D acceleration support 
7000 / rv100 based cards
7200 / R100 based cards
7500 / rv200 based cards
8X00 / R200 based cards
9000 / rv250 based cards
9100 / R200 based cards
9200 / rv280 based cards

---

### Post by Shazz.ng on 2009-05-19
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by utgodmode on 2009-07-12
nvidia driver didnt help either

---

### Post by rjcalifornia on 2009-07-14
I can't see visual effects on my ibook G3 either :(

Also it is unable to detect my video card... weird

---

### Post by gabrielgj on 2011-04-01
:confused:I'm having the same problems. I can't get any visual effect to work and when I open an application the window loads very slow. 
"gubuntu@ubuntugubuntu:~$ lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)"

What should I do?

---

