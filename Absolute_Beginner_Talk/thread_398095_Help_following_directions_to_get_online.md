---
title: "Help following directions to get online"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by dnguyen527 on 2007-03-31
Hey,

A bunch of guys helped me install Alien all morning so I could follow these directions to install Belkin f5d6050 USB network card. 

[http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html](http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html)

Download the driver. Extract to a new directory using unzip. Extract the CAB files (DATA1.CAB, DATA1.HDR, DATA2.CAB) using "unshield x" . cd Drivers/WINXP . edit bkusb.in_ and uncomment the CopyFile.XP.Sys section. Run ndiswrapper -i bkusb.in_ as root followed by ndiswrapper -m . modprobe ndiswrapper. ifdown wlan0. ifup wlan0 and you are there.

So I had to get Alien to install Unshield X - I extracted the CAB files by going to the Terminal and typing - Unshield X "drag the CAB file in" then pressed enter and it extracted - No idea where but it did. 

So then I typed:

cd Drivers/WINXP .edit bkusb.in_ 

Now I dont know what to do. 

I also setup ndiswrappers last night - took me hours!!! 


Maybe I am doing everything wrong but PLEASE help me. I cant get online, I've been downloading files on my laptop and using my flash drive to transfer files - I think I am about to  break it : /

I'd love to get online but if I cant - I am going to have to go back to XP : (

---

### Post by annda on 2007-03-31
those are all separate commands. you need to run them one by one.

btw, you can easily edit the file: click on HOME on your desktop, navigate to the the drivers and xp directories and double-click the bkusb.in_ file.

uncomment means remove the hash (#) at the beginning of the line. save the file.

---

### Post by dnguyen527 on 2007-03-31
Ill try that. Sounds to easy! 

AH - i posted this 2 times because I didnt see it the first time. Sorry!

---

### Post by dnguyen527 on 2007-03-31
This is not working... I am so lost.

---

### Post by annda on 2007-03-31
what exactly did you try to do? what isn't working?

have you found the Drivers/WINXP directory? is the file in it?

---

