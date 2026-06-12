---
title: "Extracting JPEG information?"
date: 2007-06-08
forum: Art &amp; Design
---

### Post by Garyu on 2007-06-08
I have a really complicated problem right now. I was shooting lots of pictures from a graduation party that really needs to be saved 'cause I was the only photographer. But... The compact flash card collapsed on me.

What happened was that I used Windows XP to cut the files from the memory card and paste them on the hard drive, 'cause the card was full and I needed to shoot more pictures. So I went away and continued to shoot pictures, thus overwriting the data on the memory card. When I went back to the computer to look at the photos it turned out that only about 10% was viewable.

I tried installing photorec ([http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)) which seems to be a great piece of software in many respects (I made the .rpm into a .deb using alien and then installed with dpkg -i which worked great). However, Photorec can't find my JPEGs.

So I installed GHex (sudo aptitude install ghex) and looked at the hexadecimal code of the files. It turns out that some files has the beginning blanked out (FF FF FF FF....) instead of the JPEG header. It is however easy to see that it is valid data for after a while comes the camera identifier and date of the picture and so on, so the picture is there, just without a header. Other files I looked at started with what seemed the end of another JPEG and then got on to having the JPEG header way down in the file. So the information is correct to the most part, but it has been jumbled.

I tried copying the JPEG headers from one file to another, but the only program that comes close to opening such a file is the Gimp, and it says "too many errors to display" and then exits.

As you may understand, what I want is something to de-jumble this mess. Does anyone know of a piece of software that will extract JPEG image data if you tell it where and how to look? Or something similar to photorec but functional even when the JPEG header is missing or if the header is in the middle of a file rather than at the beginning...? Any tips and hints would be really helpful, 'cause as I said, I really need these photos...

---

