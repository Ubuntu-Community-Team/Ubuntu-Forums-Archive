---
title: "Cannot boot"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Promy on 2006-08-28
Dear All,

I am a new user to linux and ubuntu. I have downloaded the Ubuntu and created a CD. But when I try to use the CD to boot it from CD, it shows a message window "error reading boot CD". I am not an expert in understanding highly technical things. Please advice with
simplest of advice, so that I can understand.:p 
Thank You
Promy

---

### Post by MrHorus on 2006-08-28
> **Promy said:**
> But when I try to use the CD to boot it from CD, it shows a message window "error reading boot CD". 

Then it's shafted.

Run the md5 sum of the DVD and compare it to the reference hash or if you don't know how to do that, just download the ISO and burn it again as it's likely corrupt.

---

### Post by Promy on 2006-08-28
Thank you for the answer.I am from india and as i couldnt find an indian version i downloaded the UK version. is it enough to download it again ?
Promy

---

### Post by otherMark on 2006-08-28
> **Promy said:**
> Thank you for the answer.I am from india and as i couldnt find an indian version i downloaded the UK version. is it enough to download it again ?
Promy
Your CD is broken (hopefully not the CDrom drive). Before you download it again check wether the file you have already downloaded is broken or not by using the md5sum program (download this error checking program because it gets used a lot. Ask if you can't figure how to use it).
If it's fine just burn another CD. Again check this with md5 sum when burnt.

---

### Post by MrHorus on 2006-08-28
> **Promy said:**
> Thank you for the answer.I am from india and as i couldnt find an indian version i downloaded the UK version. is it enough to download it again ?
Promy

Yes - hopefully it should work.

Download md5 sum and use that to verify the download.

What it does it run a hash on the file and will display a hashcode at the end.

This should match up with the published md5 hash for the file and if it does, then you know you have a perfect download that should be burnable and bootable.

---

### Post by Promy on 2006-08-28
Thank you,

but how can I do the comparison after the downloads ?
Promy

---

### Post by otherMark on 2006-08-28
> **Promy said:**
> Thank you,

but how can I do the comparison after the downloads ?
Promy
You do it with the md5 sum programme that you install in windows. The place where you downloaded Ubuntu from should have a place where it tells you the "md5 sums" or "checksums". You compare THEIR  number with the one YOUR own md5sum programme gives after you used  it to test YOUR downloaded file and/or your CD.

---

### Post by confused57 on 2006-08-28
Maybe this tutorial can help:
[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

---

