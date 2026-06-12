---
title: "Ubuntu Live Not Working"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by DaMann on 2008-03-06
I have tried many times, I even created a new live cd and checked it for errors. It still doesn't work. I will explain the whole process. To be honest I barely know anything about Linux I get the idea. I am just pissed at Micro$oft right now.

I get to this screen.
[http://www.dailycupoftech.com/wp-content/uploads/2006/08/ubuntu02.png](http://www.dailycupoftech.com/wp-content/uploads/2006/08/ubuntu02.png)

I press "Start or install Ubuntu"

Then it goes to this and loads.
[http://topi.xdt.hu/images/ubuntu_boot2.jpg](http://topi.xdt.hu/images/ubuntu_boot2.jpg)

Then it has these four bars of text at the top. I cant remember exactly what they say nor find a picture. But one says "Checking battery state". They all end with " [ Start ] ". Then it tells me it could not properly detect my video drivers or screen. So I set my video drivers to the NVidia 8 series. I don't know exactly what model my moniter is but I chose one that was from the same company and same line. A Mag Innovision. 

So then I press OK and it takes me to the screen with the four bars that all end with " [ Start ] ". And it just sits there. If I press ALT+F4 it takes me to a non graphical Linux interface. I really don't know what to do at all. I know my computer can handle it also it has two gigs of RAM. Please help

-DaMann

---

### Post by Crafty Kisses on 2008-03-06
Have you tried the alternate CD installer.

---

### Post by rjmoerland on 2008-03-06
Can you boot Ubuntu if you choose the 'Safe Graphics Mode' ?

---

### Post by DaMann on 2008-03-06
> **rjmoerland said:**
> Can you boot Ubuntu if you choose the 'Safe Graphics Mode' ?

I tried and I just had a beige screen. It made sounds like it was logging in or something but I couldn't see anything.

> **Codename said:**
> Have you tried the alternate CD installer.

If I understand what the alternate CD installer is thats just to install it. I don't want to install it yet I want to see what it is like for a few days before I commit to it.

---

### Post by rjmoerland on 2008-03-06
I had something similar on an Acer Aspire laptop. It actually was (I guess) too underpowered to boot Ubuntu. In my case I suspect a too little amount of RAM. Perhaps the same for you? Trying Xubuntu instead helped for me, though I had to edit the boot line (F6) and remove the 'splash'. After that, Xubuntu (finally) booted successfully.

---

### Post by DaMann on 2008-03-06
> **rjmoerland said:**
> I had something similar on an Acer Aspire laptop. It actually was (I guess) too underpowered to boot Ubuntu. In my case I suspect a too little amount of RAM. Perhaps the same for you? Trying Xubuntu instead helped for me, though I had to edit the boot line (F6) and remove the 'splash'. After that, Xubuntu (finally) booted successfully.

I got two gigs of ram don't think that would be a problem. 700 watt power supply.

---

### Post by Therion on 2008-03-06
Let me guess... You have an nVidia 8800 series?

Boot from the LiveCD and use F6 to remove the words "Quiet" and "Splash" from the bootloader.  

If you want to install to your hard drive, the solution is a little more complicated (easy enough, there's just more steps involved), but this should get you to the desktop using the LiveCD so you can tool around and give Ubuntu a test drive.

---

### Post by DaMann on 2008-03-06
> **Therion said:**
> Let me guess... You have an nVidia 8800 series?

Mhmm just built my computer.

---

### Post by rjmoerland on 2008-03-06
> **DaMann said:**
> I got two gigs of ram don't think that would be a problem. 700 watt power supply.

Should do :D

---

### Post by Therion on 2008-03-06
> **DaMann said:**
> Mhmm just built my computer.
Yep... It's the Black Screen o'Death.  Pretty well documented and dealt me a fit when I first installed Ubuntu.  See my edited message above.

---

### Post by DaMann on 2008-03-06
> **Therion said:**
> Let me guess... You have an nVidia 8800 series?

Boot from the LiveCD and use F6 to remove the words "Quiet" and "Splash" from the bootloader.  

If you want to install to your hard drive, the solution is a little more complicated (easy enough, there's just more steps involved), but this should get you to the desktop using the LiveCD so you can tool around and give Ubuntu a test drive.

Alright I'll try it in a bit then you score major browny points if it works.

---

### Post by DaMann on 2008-03-06
Alright I did that.... instead of the loading screen it showed all the text it was going through. Then it gave me the graphics driver and screen setting thing. I did that then it just went back to the black screen of death.

---

### Post by DaMann on 2008-03-06
Hey! I altered the boot, got rid of quiet and splash and started in safe graphic mode or whatever. Then the screen just turned black. I sat there for a few minutes. Heard some sounds. Still nothing, then I got tired and pressed ctrl+alt and was reaching for delete, then all of the sudden Ubuntu popped up! It's pretty cool. And you know what... Windows XP doesn't compe with chess.....Ok quick question while I'm exploring. I saw a guy on Youtube have  6 different screens and were arranged in a cube. How can I do that or can I not do it on live?

---

