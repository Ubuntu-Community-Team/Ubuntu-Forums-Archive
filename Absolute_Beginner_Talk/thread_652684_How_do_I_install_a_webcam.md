---
title: "How do I install a webcam?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Bruce2 on 2007-12-29
I know you put your webcam into the USB port....:) but how do i install the disk that came with it?

It says in the instructions to click the my computer prompt which i dont have. It says to find "setup.exe" which i did. I double clicked on it and its said:

"Cannot open /media/Star-eye PWC-130/Setup.exe: No application suitable for automatic installation is available for handling this kind of file."

Can anybody help me with this please?:confused:

---

### Post by Bruce2 on 2007-12-29
BUMP....anyone?

PLEASE HELP! I have an angry mrs who wants to talk to me on my computer in another country...lol

---

### Post by CCNA_student on 2007-12-29
The reason that did not work is that the .exe file is a Windows executable. You would have to use WINE to get that program to work. You can easily download that from the package manager(the Add/Remove thing).  There may also be some Linux program that can control your webcam. I am not exactly sure. You might want to ask this question in the Multimedia/Video area of the forum. I hope that this helps you.

           Sin Cere,

           CCNA

---

### Post by xtrm_redbull on 2007-12-29
Hi, the webcam installer cd will not work in ubuntu, its for ms windows. You can try to plug it in and install camorama webcam viewer its on add/remove programs, after that run camorama and see if its working. BTW what is your webcam?

---

### Post by Can+~ on 2007-12-29
Linux can't run windows applications (.exe) by default. It's a whole other OS, you could:

a) Check for a driver designed for linux:
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

b) Try installing the setup.exe using wine:
sudo apt-get install wine

---

### Post by Bruce2 on 2007-12-29
Thankyou!.....i will give that a shot

---

### Post by Hallvor on 2007-12-29
Webcam support in linux is not that good, and windows drivers will not work.

Just plug the camera to a usb port and install an application called camorama to test if it works.

```
sudo apt-get install camorama
```

---

### Post by Bruce2 on 2007-12-29
> **xtrm_redbull said:**
> Hi, the webcam installer cd will not work in ubuntu, its for ms windows. You can try to plug it in and install camorama webcam viewer its on add/remove programs, after that run camorama and see if its working. BTW what is your webcam?

Its called a Star-eye. Model number: PWC-130S

---

### Post by xtrm_redbull on 2007-12-29
Im not really sure if Star-eye PWC-130S is supported in ubuntu but here are some useful links [HardwareSupport/Components/Multimedia/WebCameras]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras") and [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam) . Hope it helps:)

---

### Post by Bruce2 on 2007-12-29
> **Can+~ said:**
> 

b) Try installing the setup.exe using wine:
sudo apt-get install wine

How do I do this?

I looked for a webcam driver, but couldnt find one and ended up um....back here. It doesnt help when the only driver I know is in my golf bag.

---

### Post by lancest on 2007-12-29
Try this at terminal:  lsusb
 Supposedly hundreds of web camera's work in Linux. My camera worked out of the box in Ubuntu but not in my wife's XP. (She needed a driver). You'd be surprised.

---

### Post by orrie on 2007-12-29
What's your camera called?

And.. what is the output after lsusb?

---

### Post by zhecool on 2007-12-29
> **Hallvor said:**
> Webcam support in linux is not that good, and windows drivers will not work.

Just plug the camera to a usb port and install an application called camorama to test if it works.

```
sudo apt-get install camorama
```

I learn it, thanks
Maybe Bruce2 should have a try

---

### Post by Bruce2 on 2007-12-29
OK...apparantly ive already got camorama installed. But when i go to use my webcam it says:

Cannot display the webcam's image. Make sure your webcam is well plugged and installed. No grabber device available.

---

### Post by Bruce2 on 2007-12-29
BUMP....Please!

---

### Post by sailor2001 on 2007-12-29
what application are you trying to use it in? AMSN works for web camera but not skype.  Download CHEESE from synaptics to see if the cam actually works.

---

### Post by sailor2001 on 2007-12-29
> **sailor2001 said:**
> what application are you trying to use it in? AMSN works for web camera but not skype.  Download CHEESE from synaptics to see if the cam actually works.

sorry, not in synaptics but [http://www.getdeb.net/release.php?id=1435](http://www.getdeb.net/release.php?id=1435)

---

### Post by Bruce2 on 2007-12-29
I down loaded CHEESE and its still not working.

---

### Post by Quash on 2008-01-01
Where are you from?  You may want to try one of those cheap logitech webcams from walmart.  Most all of them work.  My Logitech quick cam orbit MP works just fine.

---

