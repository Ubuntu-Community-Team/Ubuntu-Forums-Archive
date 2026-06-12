---
title: "installing a Webcam"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by elpichi on 2007-09-14
Hello i'm having some trouble finding drivers for my webcam according to 

lsusb
this is my webcam

Bus 001 Device 004: ID 05a9:8519 OmniVision Technologies, Inc. 

I found various websites supplying with different drivers but i wasn't sure of the exact version of my webcam. i tried a few of them, with nothing but errors in the installation process.

my webcam is pretty similar to this one except for the colors: 
[http://images.google.com/imgres?imgurl=http://www.chicony.com.tw/img/dsc_photo/dc-3120.gif&imgrefurl=http://www.suseitalia.org/modules/newbb/viewtopic.php%3Ftopic_id%3D13953%26forum%3D2%26post_id%3D75718&h=230&w=216&sz=15&hl=en&start=23&um=1&tbnid=rXNUEf3rtnGz-M:&tbnh=108&tbnw=101&prev=/images%3Fq%3Dov511%2Bwebcam%26start%3D20%26ndsp%3D20%26svnum%3D10%26um%3D1%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26sa%3DN](http://images.google.com/imgres?imgurl=http://www.chicony.com.tw/img/dsc_photo/dc-3120.gif&imgrefurl=http://www.suseitalia.org/modules/newbb/viewtopic.php%3Ftopic_id%3D13953%26forum%3D2%26post_id%3D75718&h=230&w=216&sz=15&hl=en&start=23&um=1&tbnid=rXNUEf3rtnGz-M:&tbnh=108&tbnw=101&prev=/images%3Fq%3Dov511%2Bwebcam%26start%3D20%26ndsp%3D20%26svnum%3D10%26um%3D1%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26sa%3DN)

so I tried a driver supporting ov511

took me farther than most installations but no complete results,:confused:

any advice for this situation?

---

### Post by HokeyFry on 2007-09-14
what is the part number to your webcam? there should be a sticker with that number on it, probably starting with OV

---

### Post by elpichi on 2007-09-14
wow haha(it was at the end of the usb cable), well according to the sticker is...

DX-WC101

---

### Post by linuxwizard on 2007-09-14
According to this you need the Bridge OV519. Look down page for   Chicony  iCam 330 (model DC-3120)  N/A 	OV519 (05a9:8519) 	OV7648, built-in microphone

[http://alpha.dyndns.org/ov511/cameras.html](http://alpha.dyndns.org/ov511/cameras.html)

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by HokeyFry on 2007-09-14
try this


[http://www.dynexproducts.com/skins/Skin_1/Topics/Drivers/DX-WC100_Drivers.zip](http://www.dynexproducts.com/skins/Skin_1/Topics/Drivers/DX-WC100_Drivers.zip)


many times if you just google the part number it will give you a page with either info about the device and/or a driver for that device

if that doesnt work im not sure what to do then because i have never owned a webcam and this is about as much as my knowledge can probably help you

good luck man

---

### Post by elpichi on 2007-09-14
Thanks alot guys, almost got it working!! =D (funny video quality)

for future reference I downloaded OV51x driver here

[http://alpha.dyndns.org/ov511/download.html#1.xx](http://alpha.dyndns.org/ov511/download.html#1.xx)

 and followed the instructions provided in this page

[http://ovcam.org/ov511/install.html](http://ovcam.org/ov511/install.html)

rebotted and voila!

---

