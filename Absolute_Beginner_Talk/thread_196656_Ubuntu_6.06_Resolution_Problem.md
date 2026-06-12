---
title: "Ubuntu 6.06 Resolution Problem?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by bparkin on 2006-06-14
Hello, sorry if this has been discussed already.

This happened on the live cd, and when I installed to hdd.

I go to system tools, screen resolution, and theres only one available resolution, like 480 x 640 and there's no drop down, and the refresh rate is like some negative number in the thousands (-1386 or sumthing like that).

what is the deal? I have Ati AIW  (x800 series)

Any help would be appreciated.

---

### Post by bruce89 on 2006-06-14
```
sudo dpkg-reconfigure xserver-xorg
``` might work.

---

### Post by bparkin on 2006-06-14
Wow, amazing forum quick response. Thanks


I'll reboot and give it a try. I must admit I'm extremely new to this and first time asking for help.

---

### Post by renis on 2006-06-14
have you tried installing you video card drivers?

---

### Post by bparkin on 2006-06-14
I was under the assumption that dapper would do that for me?

and even if it doesn't I would think there would more than one resolution option with the default driver.

In anycase, how do I install the drivers, and where are they located? Thanks

---

### Post by bruce89 on 2006-06-14
[QUOTE=bparkin]
In anycase, how do I install the drivers, and where are they located? [/QUOTE]
```
sudo apt-get install xorg-driver-fglrx
```
```
sudo dpkg-reconfigure xserver-xorg
```, and select the fglrx driver.

---

### Post by bparkin on 2006-06-14
should I still do the > sudo dpkg-reconfigure xserver-xorg?

thanks for your continued help Bruce and Renis

---

### Post by johnthejack on 2006-06-14
I tried to follow these instructions and now I can't see anything on my monitor. It's just a dark screen. Could someone help please?

---

### Post by bruce89 on 2006-06-14
bparkin, just do these :
```
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
```
and then select the fglrx driver.  Then press Shift+Backspace.

johnthejack, do this
```
sudo dpkg-reconfigure xserver-xorg
```
then press Shift+Backspace.

---

### Post by johnthejack on 2006-06-14
Thanks but how? I literally can't see a thing. Is there some keyboard shortcut I could try to bring up the terminal?

---

### Post by bruce89 on 2006-06-14
[QUOTE=johnthejack]Thanks but how? I literally can't see a thing. Is there some keyboard shortcut I could try to bring up the terminal?[/QUOTE]
Is there is any white text anywhere?

---

### Post by bparkin on 2006-06-15
Thank you so much Bruce, your help made my experience 10x better.

A couple things:
1. How do they expect new users to install unbuntu if they can't see the 'next' button on the live install cd setup (because of resolution) without doing the alt-f8 thing?

2. Bruce: Why does your help work, but when I tried [https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25") , it didn't work for me at all? Was there something wrong that I did, or should your advice be put there for users to see?

Thanks again Bruce.

---

### Post by johnthejack on 2006-06-15
Last night there wasn't anything other than a blacked out screen. Now, I have a screen but it's all massive, as if I were in safe mode in Windows. Screen resolution is 640 x 480 and refresh rate is -21213 Hz. Neither is offering possible variations.

---

### Post by johnthejack on 2006-06-15
OK well now I've set the horixontal and vertical myself, but I'm back where I was when I first booted. There is a one inch black border to the right hand side, a half inch along the bottom and the actual working screen seems to go off to the top and left.

---

### Post by neoflight on 2006-06-15
[QUOTE=johnthejack]OK well now I've set the horixontal and vertical myself, but I'm back where I was when I first booted. There is a one inch black border to the right hand side, a half inch along the bottom and the actual working screen seems to go off to the top and left.[/QUOTE]


interesting! did u try to install again? 
whats your system config? what display card are you using?

does it (the live/install CD) give any error while ditecting your hardware?

---

### Post by johnthejack on 2006-06-15
Yes, well feeling rather foolish now. I simply adjusted the monitor buttons and filled the screen. Oops. I just installed for the first time, so now everything new and/or wrong is because of the install. It wasn't.

---

### Post by bparkin on 2006-06-17
bump for my two questions

sorry if bumps arn't alowed i'll only do it once.

---

