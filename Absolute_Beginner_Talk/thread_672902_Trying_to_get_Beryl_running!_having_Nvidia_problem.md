---
title: "Trying to get Beryl running! having Nvidia problem"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Lash540 on 2008-01-20
Ok , I just got Linux , Im brank new to this , however im not a total novice , heres my problem....

I want to get Beryl working on my linux distrobution , but I have a EVGA NVIDIA 8800GTX so everytime I try to enable the video card and I download the driver config for linux , it downloads , reboots , and then doesnt load the xorg file correctly and I dont know how to back up the one that works before I try to enable the driver , so I always have to start back from scratch....  and fyi its not just Beryl , its trying to run regular desktop effects in the regular release of Ubuntu soo yeah I need help with this problem , Im willing to reinstall Ubuntu if thats what you guys want to be able to explain from scratch and get it going perfect.

any help would be nice,

Thank you,
Lash

---

### Post by Joeb454 on 2008-01-20
Well for a start don't get beryl - it's discontinued now :)

If you reinstall that'd be fine, if not then somebody else will have to help (I don't have an Nvidia card sorry), but I know that if you're running the latest release of Ubuntu (7.10) then you should open a terminal from Applications>Accessories and type ```
sudo apt-get install compizconfig-settings-manager
``` this will allow you to change your fancy effects.

As for the Graphics card, there should be a message that pops up on first boot telling you about restricted drivers.

Hope this helps :)

---

### Post by sailor2001 on 2008-01-20
did you system/admin/restricted driver?

---

### Post by Ub1476 on 2008-01-20
I believe you are from scratch now right? If so, download [Envy]("http://albertomilone.com/nvidia_scripts1.html"), which will install and configure the latest driver from nvidia for you. 

To run Envy, type:

```
envy -g #GUI

envy- t #Terminal
```

Since your card is rather new, I think text mode is the only things which works for you (don't worry, it's very straightforward). I just helped a guy with a 8800GT and this worked perfect for him:)

Remember to allow Envy to configure X for you (it will ask you).

---

### Post by Lash540 on 2008-01-21
wow thanks guy that Envy worked perfect , now a new problem , I have teamspeak on this os , but I cant use my mic , cause I dont know how to set it up , I have a USB logitech mic , that connects through my USB keyboard cause my keyboard has 2 USB connections on the top ( G15 Logitech keyboard ), so yeah could use any help your willing to give on that.

Thank you , 
Lash540

---

