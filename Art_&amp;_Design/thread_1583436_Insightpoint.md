---
title: "Insightpoint"
date: 2010-09-27
forum: Art &amp; Design
---

### Post by samigina on 2010-09-27
[http://www.icytec.com/]("http://www.icytec.com/")

Its a vector editor, Im trying to test it, but I cant run it.

Someone else can try it?

---

### Post by 23dornot23d on 2010-09-28
Its an **exe** ..... even the linux version .......

with a 14 day condition in the readme .....


InsightPoint readme file since version 3.2.1 
 
Thank you for using InsightPoint.  
 
Please note that the Software is protected, including without limitation by copyright laws and international copyright treaties, as well as other intellectual property laws and treaties.  
 
**Please also note that after 14 days of installing this software, you have to either stop using it or register the software** if you wish to continue using it. To register, please visit [http://www.icytec.com](http://www.icytec.com).

________________________________________________________________________________

It makes no sense as there is no where to register on that page ..... seems too basic a page ......  how can anybody trust it ?

I have done a search on it [LINK]("http://www.google.com/search?hl=en&q=InsightPoint&aq=f&aqi=g-p1g1g-sx2g1&aql=&oq=&gs_rfai=") I am not sure about it ..... it might be ok but I will stick with Inkscape ...... ty

---

### Post by samigina on 2010-09-28
Mhhh the Linux version includes a .exe file, but if you run this one like a unix .bin you will get some terminal stuff:


./insightpoint
*** glibc detected *** ./insightpoint: munmap_chunk(): invalid pointer: 0x0a333a06 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0xb7783501]
/lib/libc.so.6(+0x6d77e)[0xb778477e]
/home/mendicante/Descargas/icytec/insightpoint-3.2.5/rt/jetrt/libXKRN45086.so(+0x39be9b)[0xb6f92e9b]
/home/mendicante/Descargas/icytec/insightpoint-3.2.5/rt/jetrt/libXKRN45086.so(+0x3c7ffe)[0xb6fbeffe]
/home/mendicante/Descargas/icytec/insightpoint-3.2.5/rt/jetrt/libXKRN45086.so(+0x39b9ae)[0xb6f929ae]
/home/mendicante/Descargas/icytec/insightpoint-3.2.5/rt/jetrt/libXKRN45086.so(+0x39b68b)[0xb6f9268b]
/home/mendicante/Descargas/icytec/insightpoint-3.2.5/rt/jetrt/libXKRN45086.so(+0x3accc1)[0xb6fa3cc1]
/home/mendicante/Descargas/icytec/insightpoint-3.2.5/rt/jetrt/libXKRN45086.so(+0x3db43c)[0xb6fd243c]
./insightpoint[0x804906c]
/lib/libc.so.6(__libc_start_main+0xe7)[0xb772dce7]
./insightpoint[0x8049024]


And yex, Inkscape is the best, but I was trying something different, you know... the linux sindrome :D

---

### Post by 23dornot23d on 2010-09-28
I have run the** exe **to try it and it works ok using wine ..... 

The bin file which you ran .....which directory is it in ?

The library is quite old .... but has a few interesting things in it too ....

[http://img685.imageshack.us/img685/6109/snapshot44.png](http://img685.imageshack.us/img685/6109/snapshot44.png)

> 
And yex, Inkscape is the best, but I was trying something different, you know... the linux sindrome :grin:
Yep me too .... 

I like trying things out ... but am not happy running **exe** files .... without them being in a virtual box
or away from my main system .......



It looks like you ran the file in the rt directory .... and got a crash ..... maybe you need to install

[B]apt-get install build-essential

or run the exe and install wine 1.2
[/B]

---

