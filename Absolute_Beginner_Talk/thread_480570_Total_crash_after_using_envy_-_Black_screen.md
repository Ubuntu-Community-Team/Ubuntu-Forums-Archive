---
title: "Total crash after using envy - Black screen"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2007-06-21
Just did a clean reinstall so that i can use my Sapphire ATI X1950PRO 512mb. Then the first thing i did was to run Envy and made that do the job by itself. Then it told me to do a restart. Now i see the loading screen with the logo of ubuntu but the screen goes black when it comes to the log in :(

What should i do to fix this? And get my card to work?

---

### Post by overdrank on 2007-06-21
> **U5tabil said:**
> Just did a clean reinstall so that i can use my Sapphire ATI X1950PRO 512mb. Then the first thing i did was to run Envy and made that do the job by itself. Then it told me to do a restart. Now i see the loading screen with the logo of ubuntu but the screen goes black when it comes to the log in :(

What should i do to fix this? And get my card to work?

Hi right when the grub loads  hit these keys all at the same time ctrl,alt,F1 this will enter the terminal and then you can use the command  after login   
sudo dpkg-reconfigure -phigh xserver-xorg  and this should get you going,

---

### Post by U5tabil on 2007-06-21
> **overdrank said:**
> Hi right when the grub loads  hit these keys all at the same time ctrl,alt,F1 this will enter the terminal and then you can use the command  after login   
sudo dpkg-reconfigure -phigh xserver-xorg  and this should get you going,

Ok i got it and running again with the vesa driver. 
But now what? How can i install my ATI card? Is there something else i can try? With the Envy or other stuff?

---

### Post by U5tabil on 2007-06-21
Ok i give this **** up! Now i am running Vesa drivers and i can't change the resolution so everything looks like crap...

---

### Post by overdrank on 2007-06-21
> **U5tabil said:**
> Ok i give this **** up! Now i am running Vesa drivers and i can't change the resolution so everything looks like crap...

I wished I could help more but I am not familiar with that new of a card have you tried the sticky post in the beginners forum on the ati cards with feisty :(
_**Second thought have you tried to enable the restricted drivers   its under system, administration, restricted driver manager**_

---

### Post by U5tabil on 2007-06-21
i only get "your hardware does not need...."

Isnt there any other driver that i can use? I pnly use the pc for surfin, chatting, mail and watching movies...

---

