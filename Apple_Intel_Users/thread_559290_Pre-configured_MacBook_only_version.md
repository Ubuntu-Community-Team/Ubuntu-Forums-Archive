---
title: "Pre-configured MacBook only version??"
date: 2007-09-25
forum: Apple Intel Users
---

### Post by peestandingup on 2007-09-25
Hey guys. First time poster.

After 8 years of OS X, I believe its time to switch to Ubuntu. I already have it installed via a partition on my MacBook, but am still having a lot of problems getting things working with my hardware. Im pretty proficient with the OS X gooey, but Ubuntu & all the terminal commands are kinda kicking my butt.

Anyways, does anyone out there have or know of a version of Ubuntu thats pre-configured for MacBooks? Would any kind chap be willing to make an iso for me of his/her own OS??

Thanks!

---

### Post by cyberdork33 on 2007-09-25
> **peestandingup said:**
> After 8 years of OS X, I believe its time to switch to Ubuntu. I already have it installed via a partition on my MacBook, but am still having a lot of problems getting things working with my hardware. Im pretty proficient with the OS X gooey, but Ubuntu & all the terminal commands are kinda kicking my butt.

Anyways, does anyone out there have or know of a version of Ubuntu thats pre-configured for MacBooks? Would any kind chap be willing to make an iso for me of his/her own OS??
What are you having issues with? There is a lot of info out there for your hardware.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Note: BTW, it is GUI not gooey (**G**raphical **U**ser **I**nterface)

---

### Post by peestandingup on 2007-09-25
> **cyberdork33 said:**
> What are you having issues with? There is a lot of info out there for your hardware.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Note: BTW, it is GUI not gooey (**G**raphical **U**ser **I**nterface)
I know about those & honestly, they're not the best instructions in the world & the lingo is set up like its talking to a long time Linux user, which I am not. And honestly, I dont have hours & hours to devote to just getting things like WiFI, screen res, trackpad, etc going because I've already wrestled for hours with those instructions. And like I said, its almost all terminal commands, which are hit or miss for me. I just want to start using Ubuntu & have everything work. This is supposed to be the "Linux for the people", no?

And yes, I know what a GUI is & what it stands for. :) I should have written it as "gooey". When writing on message boards its hard to articulate whats being thought. So, I was saying in my mind "gooey", so therefor I wrote gooey. I wasnt saying "gee you I", which some people see it as such.

---

### Post by cyberdork33 on 2007-09-25
> **peestandingup said:**
> I know about those & honestly, they're not the best instructions in the world & the lingo is set up like its talking to a long time Linux user, which I am not. And honestly, I dont have hours & hours to devote to just getting things like WiFI, screen res, trackpad, etc going because I've already wrestled for hours with those instructions. And like I said, its almost all terminal commands, which are hit or miss for me. I just want to start using Ubuntu & have everything work. This is supposed to be the "Linux for the people", no?

And yes, I know what a GUI is & what it stands for. :) I should have written it as "gooey". When writing on message boards its hard to articulate whats being thought. So, I was saying in my mind "gooey", so therefor I wrote gooey. I wasnt saying "gee you I", which some people see it as such.I wasn't putting you down....

The trackpad works fine out of the box. The issue is that you want it to be different than the default. For this to take place, you have to edit the configuration for which there are a lot of options.

The screen resolution required a sort of hack to get working in feisty. After the Intel driver was updated, the hack is not needed anymore. To get it working you are required to edit one word in one file and restart.

wifi is not a pretty situation because 1 Apple uses new hardware that has no working linux drivers (initially) and 2 wifi has been a bit difficult in linux anyway (although it is getting much better)

Lastly, using and configuring linux (especially on hardware does not support linux) is going to require using the command line, and probably quite a bit. There is no GUI for some configuration, and thus, config files have to manually editted.

If you are just looking for someone to do all the work for you and wrap a bow around it, then I am pretty sure you are out of luck, Sorry. If you have specific issues that you would like help resolving, I will be glad to try my best to help you, but that is all I can do.

---

### Post by martalli on 2007-09-25
For any hardware in linux, but especially laptops, it is a good idea to investigate compatibility closely before making a purchase.  The components on a laptop rarely can be replaced, so one incompatible bit of hardware can cause many headaches.

You've already got your hardware, but for your next purchase consider the Linux on Laptops site, or just extensive use of google.  Sometimes slightly older hardware may be more compatible with Linux (my year-old Dell m1210 works great except for the webcam, and that has a simple CLI fix).

Even though the Macbooks are not the most compatible hardware, you do have the benefit of a fairly large community of other users struggling through with their hardware...and maybe some more interest from the folks who work relentlessly to reverse engineer drivers for us.

Older hardware may not be sexy, but it certainly can be cheap.  After a while, you may start finding yourself trolling ebay for good deals on old hardware =).

---

### Post by peestandingup on 2007-09-25
Thanks for the tips.

Honestly, I just want to get started using Linux asap & been hearing about Ubuntu a lot, so I just downloaded it. What distro do you guys recommend for me that will work "outta the box"?? Fedora looks nice & seems well supported for MacBooks.

Also, im getting out of the Apple world soon I think, so what quality lappy do you guys recommend running well & thats supported with Ubuntu. I despise Dell, so I was thinking Lenovo??

---

### Post by dmber on 2007-09-25
i used the help wiki about macbooks for mine, and i can't think of one thing i'm missing right now in my dual-boot on my macbook.  i actually have more functionality with my touchpad in ubuntu than os x (adding middle-click).

i have a Core Duo 1.83 Ghz Macbook.  The wireless worked out of the box, i just had to OK using the "unsupported Atheros" driver.  compiz fusion is much prettier (and more functional) than the GUI of OS X.  I've already got Spaces with CF.  and I've already got stacks with AWN.

I'm a big eye-candy guy (probably the main reason i went to OS X with my macbook, and Ubuntu (linux in general) is much prettier than OS X.  i was nervous that all the "cool" stuff (AWN, Compiz-Fusion) wouldn't work on the macbook, but it works with hardly any "terminal tinkering."

if you've got the same hardware as I do, i'd be happy to copy/paste my xorg.conf or whatever else you need -- as long as that's cool with the non-noobs.

-russ

---

### Post by peestandingup on 2007-09-25
> **dmber said:**
> if you've got the same hardware as I do, i'd be happy to copy/paste my xorg.conf or whatever else you need -- as long as that's cool with the non-noobs.
Would you mind? I'd really appreciate that.

I do have the same exact hardware as you. The only thing I've done different is mod my wireless card. I swapped it out to the one that comes with the Core 2 Duo's simply because I wanted wireless N & that wasnt possible with the Core Duo model's card.

It should still work though. Upload away! :)

---

### Post by cyberdork33 on 2007-09-25
> **peestandingup said:**
> Honestly, I just want to get started using Linux asap & been hearing about Ubuntu a lot, so I just downloaded it. What distro do you guys recommend for me that will work "outta the box"?? Fedora looks nice & seems well supported for MacBooks.
We actually have pretty good mac support here... I have not looked too hard at fedora, but it will only cost you a few discs to try. 

> Also, im getting out of the Apple world soon I think, so what quality lappy do you guys recommend running well & thats supported with Ubuntu. I despise Dell, so I was thinking Lenovo?? Intel hardware is well supported: Wifi, Graphics, chipsets. If you want higher end graphics, go with nvidia over ati. Steer clear of broadcom wifi. There are also many linux-ready computer distributors out there are are supported well (and have their own support forum here) like [System76]("http://www.system76.com/")
There are several hardware lists out there:
[http://www.linux.org/hardware/laptop.html](http://www.linux.org/hardware/laptop.html)

---

