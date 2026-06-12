---
title: "Digital Camera Problems"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by geek_overlord on 2006-06-11
I just installed Dapper and I'm having trouble importing pictures from my Casio and Sony camera's. Here's the message I'm getting     **"An error occurred in the io-library ('Could not find the requested device on the USB port'): Could not find USB device (class 0x6, subclass 0xffffffff, protocol 0xffffffff). Make sure this device is connected to the computer." and An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."**  I can see the images on the camera but I cant import anything. Can anyone suggest where I can look to resolve this problem? Thanks in advance.

---

### Post by geek_overlord on 2006-06-12
Anyone? Man this is a fast forum. I posted 10 hours ago and I was on the fourth page when I checked back. I want to solve this problem by myself but it's a cryptic error message and I have no point of reference to start from. Also, I have tried the camera on several usb ports that are working in Windows so I don't think anything's broken. I could just do this in Windows since I dual booted however I really want to learn how to use Linux. Thanks in advance for your help.

---

### Post by jvictor on 2006-06-12
How are accessing the cam ?  Use gtkam to connect your camera .. it does a gr8 job.

---

### Post by geek_overlord on 2006-06-12
Gthumb is the program that is launched automatically when the camera is powered on. I couldn't find gtkam when I looked in synaptic. Where would I look to see if it is installed? Sorry but I'm still having trouble locating some things in the file system. The strange thing is that I can see the pictures but I just cant import them.

---

### Post by jvictor on 2006-06-12
Oh ! my mistake I shouldve told you to enable the 'extra' repositories

u can change the lines in /etc/apt/sources.list

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted 

to 

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse


and then run 
```

sudo apt-get update

sudo apt-get install gtkam
```

Gthumb dint work well for me.

---

### Post by nalmeth on 2006-06-13
If you can see the images, then there must just be a problem with the program you are using, but that wouldn't explain your error message. :-k

F-spot is a really great, professional looking photo-manager. Try to see if it will let you import your pics.

should be just a 
sudo apt-get install f-spot
away (with universe mulitverse restricted enabled)

---

### Post by jvictor on 2006-06-13
>  	If you can see the images, then there must just be a problem with the program you are using, but that wouldn't explain your error message.

F-spot is a really great, professional looking photo-manager. Try to see if it will let you import your pics.

should be just a
sudo apt-get install f-spot

Thanks it looks gr8 !

---

### Post by Franko30 on 2006-06-13
Hi,

do you, by any chance, use any other kernel than the standard linux-386 (like linux-686)?

I had a similar problem described here:

[http://www.ubuntuforums.org/showthread.php?t=195248](http://www.ubuntuforums.org/showthread.php?t=195248)

and found out, I could use my digital camera when starting Ubuntu using the linux-386 kernel.

Cheers

Franko30

---

### Post by geek_overlord on 2006-06-13
Well I tried to do the change in /etc/apt/sources.list but I was told that it was a read only item and I didn't have permissions to change it. It's funny because I was never prompted to enter the root password. Does anyone have any other ideas? I did verify that I have the 386 kernel installed. Thanks to everyone who responded for all your help.

---

