---
title: "A Newb question about Graphics Cards"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-07-29
Hey,
I don't know a lot about graphics cards. Right now I have a ATI Radeon 9600. I don't have the restricted drivers installed since if I do then I can't enable Desktop Effects. This means that when I want to play a video in full screen then it becomes laggy and isn't pleasant. I also tried out the Gutsy Gibbon Tribe 3 Live CD and couldn't enable desktop effects at all.

So I think it must be time to upgrade graphics cards. I hear that all NVIDIA cards will work with Ubuntu, is this true?

I am also wondering about installing the graphics card. Is it basically Plug and Play or do you suggest I take it to a service place? I have installed other parts like new RAM and a new hard drive without much trouble before. 

Thanks and appreciate any help provided.

---

### Post by RudolfMDLT on 2007-07-29
I also had a 9600! UPGRADE! you have no idea the hassle you will save yourself if you upgrade to an Nvidia card.

What is you current PC spec? I think your still using AGP?

Oh - and yeah - if you plan on Installing an Nvidia card it is just plug and play! You basically plug in the new card, do a display reconfig, reboot and your up!

rudolf

---

### Post by overdrank on 2007-07-29
> **tprzepiorka said:**
> Hey,
I don't know a lot about graphics cards. Right now I have a ATI Radeon 9600. I don't have the restricted drivers installed since if I do then I can't enable Desktop Effects. This means that when I want to play a video in full screen then it becomes laggy and isn't pleasant. I also tried out the Gutsy Gibbon Tribe 3 Live CD and couldn't enable desktop effects at all.

So I think it must be time to upgrade graphics cards. I hear that all NVIDIA cards will work with Ubuntu, is this true?

I am also wondering about installing the graphics card. Is it basically Plug and Play or do you suggest I take it to a service place? I have installed other parts like new RAM and a new hard drive without much trouble before. 

Thanks and appreciate any help provided.


Hi and nvidia is a good card and this link may help you with the installation
[http://www.motherboards.org/articlesd/how-to-guides/1168_1.html](http://www.motherboards.org/articlesd/how-to-guides/1168_1.html)
Good luck! :guitar:

---

### Post by w4ett on 2007-07-29
Firstly, I have a 9200 card and use the xorg-driver-ati and run the desktop effects with no problem at all...What driver is being used?  My DVD playback is also smooth.

Nvidia do have better support for the open source community, with frequent driver updates...whether their cards are any "better" than ati is a matter of personal preferance and/or debate.

If you've installed Ram and a hard drive, a vid card install won't be a problem for you...just ensure that you purchase the correct Bus Type card supported by your Motherboard, and follow one of the various how-tos for install and driver configuration.

---

### Post by Daveth on 2007-07-29
but if you are thinking about a Nvidia purchase, go for the 7000 series rather than the newer 8000, as the support is currently better, though if you wait a bit, things will catch up

---

### Post by tprzepiorka on 2007-07-29
Hey, thanks a lot for all the responses(another reason why I love Ubuntu). I have two quick questions and then I should be ok.

> **RudolfMDLT said:**
>  You basically plug in the new card, do a display reconfig, reboot and your up!

rudolf

How do I do a display reconfig? (Sorry, I have no idea what that even is :()

Lastly, how do I figure out what motherboard I have. I am using a computer that is a few years old and was custom built. I have been into Device Manager, but I don't know what I'm looking for exactly. I'm pretty sure it is a MSI.

Thanks once more :)

---

### Post by w4ett on 2007-07-29
The easiest way to do this is from the terminal type:

Code:

sudo dpkg-reconfigure -phigh xserver-xorg

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selectis options, and <enter> confirms selections.

Select the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and press <enter>

save the selections as prompted, then hit <Ctrl><Alt><Backspace> to reset X.


This SHOULD enable the correct driver and 3d capability

If you do not know the exact M/B, you will have to open it up to check what Bus Type that you have (I'm guessing AGP if the system is a couple of years old)

---

### Post by armandh on 2007-07-29
agp is usually a brown socket a little farther from the back of the case than the white PCI socket.
PCIE only on the newest boards  different than the pci  socket

---

### Post by tprzepiorka on 2007-07-29
I'm pretty sure that I have PCI inputs available. However none of the 7 or 8 NVIDIA series support PCI and all use PCI Express. Any suggestions?

---

### Post by tprzepiorka on 2007-07-30
> Firstly, I have a 9200 card and use the xorg-driver-ati and run the desktop effects with no problem at all...

w4ett

How do I install the xorg-driver-ati pacakge? I only have the xorg-driver-fglrx package available. 

Thanks,
tprzepiorka

---

### Post by w4ett on 2007-07-30
> **tprzepiorka said:**
> How do I install the xorg-driver-ati pacakge? I only have the xorg-driver-fglrx package available. 

Thanks,
tprzepiorka

The driver ati is included by default in Xorg 7.2 (already in Feisty)...but you say you are using the fglrx driver already.  This driver is the proprietary from the ATI and is the correct one to use for your current video card.

You are already using the recommended driver.

BUT if you want to experiment use the instructions in post #7 above.

---

### Post by tprzepiorka on 2007-07-30
No, I don't have the fglrx drivers installed, they cause more harm than good. Slow down my computer, disable desktop effects, and I loose windows borders. I tried getting Envy to install them as well as the restricted drivers manager. It didn't work.
I'll be looking for a new graphics card then, but my computer only has one AGP port and a few regular old PCI ports. The newer NVIDIA cards(Series 7, 8) only support PCI Express though. And from my understanding this means they wont be able to work on regular PCI slots.

---

### Post by w4ett on 2007-07-30
There are NVidia 7600 AGP cards...just have to dig to find them...don't know what the supplier situation is in the EU, but look here:

[http://www.newegg.com/Product/Product.asp?Item=N82E16814121064&ATT=14-121-064&CMP=OTC-pr1c3watch&cm_mmc=OTC-pr1c3watch-_-Video+Cards-_-ASUS-_-14121064](http://www.newegg.com/Product/Product.asp?Item=N82E16814121064&ATT=14-121-064&CMP=OTC-pr1c3watch&cm_mmc=OTC-pr1c3watch-_-Video+Cards-_-ASUS-_-14121064)

---

### Post by tprzepiorka on 2007-07-30
Ok, thanks for all the help  :) I'm pretty much all set now.

---

### Post by tprzepiorka on 2007-07-30
Ahhh...I'm sorry, one more question. I found this card:
[http://www.computerhq.com/ASUS_AGP_GF7600GS_256MB_RAMDAC/N7600GS_SILENT_HTD_256M/hardware/partinfo-id-880499.html](http://www.computerhq.com/ASUS_AGP_GF7600GS_256MB_RAMDAC/N7600GS_SILENT_HTD_256M/hardware/partinfo-id-880499.html)
*I just want to know/make sure that it will work with any AGP socket and with Ubuntu.*
Ok, thats it. My last question.

Thanks again.

---

### Post by w4ett on 2007-07-30
> **tprzepiorka said:**
> Ahhh...I'm sorry, one more question. I found this card:
[http://www.computerhq.com/ASUS_AGP_GF7600GS_256MB_RAMDAC/N7600GS_SILENT_HTD_256M/hardware/partinfo-id-880499.html](http://www.computerhq.com/ASUS_AGP_GF7600GS_256MB_RAMDAC/N7600GS_SILENT_HTD_256M/hardware/partinfo-id-880499.html)
*I just want to know/make sure that it will work with any AGP socket and with Ubuntu.*
Ok, thats it. My last question.

Thanks again.

I Googled it and found it's the same card  (It has the same ASUS Part Number) as in my previous post....This card does not have a cooling fan,  and has a extra large heatsink.   It is AGP 4x/8x compatible, so it should work fine...the only consideration being a good case cooling fan to dissipate the heat.

Note:  The pic is incorrect on the website that you linked...it appears as it is for illustration purposes only.

---

### Post by tprzepiorka on 2007-07-30
Ok, I should be able to order and set it up now. Thanks for all of the help ;)

---

### Post by w4ett on 2007-07-30
Nie ma za co, Powodzenia!!!!

---

