---
title: "Switching Graphics Cards"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-07-07
Hey there, I'm going to be switching cards in my comp soon. I currently have an ATI X700 Pro 128mb and will be buying a EVGA Geforce 7600GT 256mb. Now, how do i make sure that it recognizes the new card when I put it in and how do I make sure I'm utilizing the new nvidia drivers and not the old ATI ones? Basically I'm kinda looking for a walkthrough on how to swap em out without any cobwebs sticking around or any weird issues. I appreciate any help!! :)

---

### Post by bigken on 2007-07-07
this how I would do it swap the cards boot into safe mode at the prompt type 
sudo dpkg-reconfigure -phigh xserver-xorg select nv as your video reboot in normal mode when your in ubuntu go to admin and select restricted drivers and follow the prompts ;)

---

### Post by Tumpster on 2007-09-04
Ok, anyone else have any other way or anyone thats crossed over from ATI to NVIDIA? How did you switch over properly? I just bought my card so I'll be doing this shortly!!

---

### Post by WheelsOfSteel on 2008-02-17
Heh Tumster,

Did you get the switch done?  I am goingto be doing something similar soon and would appreciate the info...

---

### Post by Tumpster on 2008-02-17
Thanks to Ubuntu's smart programming I had no troubles, although eventually I did just whipe my Fiesty and move up to Gutsy which has COmpiz out of the box and is perfect for a nvidia card. I recommend doing this going in with a new graphics card although it's no trouble if you stay current with you're current install.

---

