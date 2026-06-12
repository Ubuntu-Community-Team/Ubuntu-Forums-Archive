---
title: "writing iso images?"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-10-25
how to i do it with ubuntu? i want to write an .iso file to a cd for a bootable disk

---

### Post by heimo on 2005-10-25
If your system is working properly, writing iso files should be very easy. Find the file with nautilus (it's the file browser), for example using Places-menu. Right click on the file and select Write to Disc. Select options (write speed etc) and hit Write button. That should do it. :)

---

### Post by stoeptegel on 2005-10-25
The commonly made fault is that people burn an image as data files, where it has to be burned as image file. This applies to 99% of the "i can't boot my cd/dvd" problems.

---

### Post by patrick295767 on 2005-10-26
[QUOTE=jasonpeinko]how to i do it with ubuntu? i want to write an .iso file to a cd for a bootable disk[/QUOTE]

apt-get install k3b
can burn your iso files ... 
  
  
 
to check the integrity of ur iso (from windows):
[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)

See ya'

---

### Post by interse on 2005-11-07
ISO image follow-up question.  I have spent quite some time today seeking information on how to burn an ISO image to DVD.  Not much success.  I have a downloaded ISO image file that I would like to burn to a DVD [too large for a CD].  Is this possible in Hoary and, if so, how do I proceed?

---

### Post by jonzep on 2005-11-07
try gnomebaker, it's very easy to use...

```
sudo apt-get install gnomebaker
```

or open synaptic and search for gnomebaker

---

### Post by interse on 2005-11-07
[QUOTE=jonzep]try gnomebaker, it's very easy to use...

```
sudo apt-get install gnomebaker
```

or open synaptic and search for gnomebaker[/QUOTE]

Tried gnomebaker and it burned an image of the file, but not an iso image.  Gnomebaker seems oriented to ISO images on CDs.  I could not, after indicating that I wished to burn an ISO image, get to the DVD screen to set it up.  Did I miss something?

---

### Post by patrick295767 on 2005-11-08
[QUOTE=interse]Tried gnomebaker and it burned an image of the file, but not an iso image.  Gnomebaker seems oriented to ISO images on CDs.  I could not, after indicating that I wished to burn an ISO image, get to the DVD screen to set it up.  Did I miss something?[/QUOTE]
  
I usually use k3b and it works fine for burnign ISO
 
apt-get install k3b

Greetz'
Pat'

---

### Post by HJThis on 2005-11-08
Hey,All

One other thing i find that always gives my friends problems
with burning iso or anything.

is the speed that they use go with a low speed works
for me all the time. ;) 

Best of luck

---

