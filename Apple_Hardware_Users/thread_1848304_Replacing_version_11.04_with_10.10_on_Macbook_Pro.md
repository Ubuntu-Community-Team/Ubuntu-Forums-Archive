---
title: "Replacing version 11.04 with 10.10 on Macbook Pro"
date: 2011-09-22
forum: Apple Hardware Users
---

### Post by Kalimoor on 2011-09-22
Hi, I have recently burned ubuntu version 11.04 using a PC and installed it on my Macbook Pro (partitions, so I have MAC OS and ubuntu), and that generated many problems. 

First problem is no wireless connection problem, I know it is the driver problem and I don't wanna fix it.

Second problem is a weird problem. If I "resstart" mac (in ubuntu OS), the mac freezes (it freezes when you see the ubuntu icon and under the icon, you see 5 dots that can turn from white colour to red colour, the mac freezes at the seocnd dot, leaving 2 red dots and 3 white dots). However, if I shutdown the mac, it shuts down the laptop and no problem occurs.

Third problem is that my Macbook Pro is brand new and its battery can lasts 6 to 7 hours with MAC OS. But when I switch to Ubuntu OS, it can lasts no more than 2 hours...

So I'm thinking of replacing 11.04 with 10.10. I know I have to de-allocated the partition memory of version 11.04 and re-install 10.10.

Note: When I wanted to download 11.04, I had to go to MAC OS and created a partition (in Window) and allocate 20GB. Then I inserted the disk with ubuntu 11.04 and installed it.

Does anyone have done it using a macbook? Any help is appreciated, thank you.

---

### Post by Lisiano on 2011-09-22
Redo everything you did to install 11.04 but with a 10.10 disk. No need to do anything with partitions.
Also I don't know what WiFi adapters Macs use but maybe try taking a look at System -> Administration -> Available Drivers?

The battery thing is probably because you don't have the the proprietary video drivers, I'm taking a guess but I think the GPU doesn't underclock itself when it's not used. Look at System -> Administration -> Available Drivers for the drivers too.

Also to see what is using power, install a program called powertop
```
sudo apt-get install powertop
```
And just run it with this
```
sudo powertop
```

---

### Post by philipballew on 2011-09-23
What version of the mac book are you running. when did you get it? can you paste the output of ```
lspci -vvv
```

---

