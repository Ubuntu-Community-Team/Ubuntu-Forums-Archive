---
title: "Toshiba Satellite a215 s4747"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by krazy1912 on 2007-09-03
I just recently installed Ubuntu 7.04 i836 to dual boot with Vista.

This is my exact model [http://www.bestbuy.com/site/olspage.jsp?skuId=8397745&st=a205+s4747&type=product&id=1179877029693](http://www.bestbuy.com/site/olspage.jsp?skuId=8397745&st=a205+s4747&type=product&id=1179877029693)

When I boot into Ubuntu I get the opening Ubuntu logo and the progress bar, but when Ubuntu is finished loading my screen goes completely black and my caps lock button blinks.

However, every once in a while I can boot into Ubuntu and I'm not sure why.  90% of  the time I get the balck screen though.

I want to use Ubuntu!

---

### Post by krazy1912 on 2007-09-03
I haven't done anything, but now when I boot into Ubuntu instead of a black screen I have text, the screen flickers 3 times, and then the x-server fails.

---

### Post by krazy1912 on 2007-09-03
Also, does anyone know where I can get ATI RADEON x1200 drivers for x86 linux?

---

### Post by krazy1912 on 2007-09-03
bump

---

### Post by overdrank on 2007-09-03
> **krazy1912 said:**
> bump

Hi you can boot into recovery mode which is command prompt and follow this guide
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
Hope this helps and good luck!

---

### Post by viceyo on 2007-09-06
Hi there,

I also have that laptop and I just put Ubuntu 7.04 for 64 bits on it. You can find directions on what I did on 
[http://es.geocities.com/vice_yo/Ubuntu_on_A215-S4747.html](http://es.geocities.com/vice_yo/Ubuntu_on_A215-S4747.html)

If you prefer to install the 32 bits version, you and look at this place:

[http://my-geek-side.blogspot.com/2007_08_01_archive.html](http://my-geek-side.blogspot.com/2007_08_01_archive.html)

I hope this was useful to you.

---

### Post by krazy1912 on 2007-09-06
Thank you, but i'm still unsuccessful =[

---

### Post by silvio.viana on 2007-09-09
> **viceyo said:**
> Hi there,

I also have that laptop and I just put Ubuntu 7.04 for 64 bits on it. You can find directions on what I did on 
[http://es.geocities.com/vice_yo/Ubuntu_on_A215-S4747.html](http://es.geocities.com/vice_yo/Ubuntu_on_A215-S4747.html)

If you prefer to install the 32 bits version, you and look at this place:

[http://my-geek-side.blogspot.com/2007_08_01_archive.html](http://my-geek-side.blogspot.com/2007_08_01_archive.html)

I hope this was useful to you.

Hi there,

I have the Toshiba Satellite A215 4747 too, but when I tried to install Ubuntu 6.06 for 64bits my hard drive wasn't detected. 

I really want to use Ubuntu on my computer, but I'm allmost hopeless...

Somebody have any idea why I'm having this problem?!

---

### Post by krazy1912 on 2007-09-09
Download the 6.1 alternate cd

Just load from it and follow the directions.

The only thing that won't work is the wireless.

This is my other post on that [http://ubuntuforums.org/showthread.php?t=547258](http://ubuntuforums.org/showthread.php?t=547258)

---

### Post by krazy1912 on 2007-09-09
If you want to stay with 6.06, than I have absolutely no idea how to help you.

---

### Post by LiquidSmoke on 2007-10-22
I have the same make-model and both i386 and amdx64 versions of 7.10 work just fine except the display driver but it still fires up with no problems at all. but if you hear anything about how to get the graphics card working (properly) please post it.

---

### Post by dawithers on 2007-10-22
In 7.10 all you have to do is
```

apt-get install xorg-drivers-fglrx
```

then go to the restricted drivers manager in your Administration menu and enable the ATI driver.

see [http://drewwithers.com/2007/12/ubuntu-linux-710-gutsy-on-toshiba.html]("http://drewwithers.com/2007/12/ubuntu-linux-710-gutsy-on-toshiba.html")

---

### Post by Ruiz on 2007-10-23
Has anyone figured out how to adjust the brightness?

---

### Post by Ruiz on 2007-10-23
Hey guys, I found out how to adjust the brightness.

```

echo ## > /proc/acpi/video/VGA/LCD/brightness

```

## = 0 - 70 in increments of 10

0 being the lowest and 70 the highest.

---

### Post by krazy1912 on 2007-10-24
Awesome!

---

### Post by krazy1912 on 2007-11-18
Hello,

I'm trying to write to my windows partition.

I am able to mount it.

When I try to copy something to it, it says that I don't have permission.

---

### Post by krazy1912 on 2007-11-24
Does anyone know how to hibernate in 7.10?

When I hibernate my screen goes black and I can't the comp to wake up.

---

### Post by AndrewTheArt on 2007-12-02
Yes, please, someone figure out how to hibernate.

---

### Post by exjinn on 2007-12-22
Unfortunately this doesnt work for me and my Toshiba Satellite A65.

-bash: /proc/acpi/video/VGA/LCD/brightness: No such file or directory

---

### Post by enbuyukfener on 2007-12-31
> **exjinn said:**
> Unfortunately this doesnt work for me and my Toshiba Satellite A65.

-bash: /proc/acpi/video/VGA/LCD/brightness: No such file or directory
Same issue on a Dell Vostro.

I have the following 2 files:
/proc/acpi/video/VID/LCD/brightness
/proc/acpi/video/VID1/LCD/brightness

But they are both on:
current: 0
(it should be 100)

Changing the value doesn't work.

Interestingly, Fn+Brightness keys used to work and then they suddenly stopped.

---

### Post by dawithers on 2008-03-26
> **krazy1912 said:**
> Hello,

I'm trying to write to my windows partition.

I am able to mount it.

When I try to copy something to it, it says that I don't have permission.
In order to write to your windows partition (assuming it is ntfs) you will have to mount it with ntfs-3g 
Something like this:
ntfs-3g /dev/sda1 /media/sda1
Where /dev/sda1 is the partition you are mounting and /media/sda1 is your mount point.
There are more options you can play around with to make it give the permissions you want but that is the jist of it.
You will likely have to be root to issue that command.

---

