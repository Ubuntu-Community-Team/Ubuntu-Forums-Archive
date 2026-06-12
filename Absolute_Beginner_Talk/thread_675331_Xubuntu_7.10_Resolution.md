---
title: "Xubuntu 7.10 Resolution"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by zatlite on 2008-01-22
Hi I installed xubuntu 7.10 to my machine. 
My adapter has a problem with displaying at 1024x768 at 16 bit resolution.
I could change the setting to 15bit when I was using puppy linux and an earlier version of xfce.
I configured the xorg.conf file to set the default depth to 15 and resolution to 1024x768.
When I rebooted, Xubuntu displayed the log on screen correctly at 15 bits for a few seconds and then crashed. It keeps doing that. I'm starting to suspect maybe Xubuntu 7.10's xfce doesn't support 15bit color depth?

---

### Post by A4006 on 2008-01-22
Could be your video card driver.  Is it a integrated card or add on?

---

### Post by zatlite on 2008-01-22
it's a very bad onboard card. that's the reason I'm trying to use 15bits. 
even with window 98 and it's correct driver, it doesn't display properly. But with win98, the problem is at 256 colors depth.

---

### Post by overdrank on 2008-01-22
> **zatlite said:**
> it's a very bad onboard card. that's the reason I'm trying to use 15bits. 
even with window 98 and it's correct driver, it doesn't display properly. But with win98, the problem is at 256 colors depth.

HI and can you reach the terminal with the ctrl, alt, F1 keys at the same time and reconfigure your xorg? ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by A4006 on 2008-01-22
Why don't you just buy a new video card?  Then you could run the advanced desktop effects and have some nice eyecandy.  Here's a nice on that's pretty affordable [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289")

---

### Post by zatlite on 2008-01-22
> **overdrank said:**
>  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I've run sudo dpkg-reconfigure xserver-xorg a few times already but without the -phigh flag. What does that do? I'll try it when I get home.

---

### Post by zatlite on 2008-01-22
> **A4006 said:**
> Why don't you just buy a new video card?  Then you could run the advanced desktop effects and have some nice eyecandy.  Here's a nice on that's pretty affordable [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289")

Simply because my machine is a really old machine that I wont find any graphic cards for. The only slots available are just normal PCI slots. No AGP or PCI-e

---

### Post by A4006 on 2008-01-22
The card I gave you a link to is a PCI card.  GeForce 6200, I think.  A new card would clear up a lot of the graphics issues you have been having (besides supporting 1280x1024 resolution and millions of colors) and would enable you to use desktop effects.

---

### Post by zatlite on 2008-01-27
> **A4006 said:**
> The card I gave you a link to is a PCI card.  GeForce 6200, I think.  A new card would clear up a lot of the graphics issues you have been having (besides supporting 1280x1024 resolution and millions of colors) and would enable you to use desktop effects.

Thanks for the tip. I'd buy it but for now, I'm saving my money for my better machine which has a broken motherboard. :)

---

