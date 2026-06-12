---
title: "Camera Fuji Download photos"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Lancerlan on 2008-04-12
Hello, I have a fujifilm camera S100fd and I am unable to download/import the photos to my harddrive. When I plug the camera to the usb port, after a few seconds I get form dolphin file manager that the camera cannot be locked to the computer. Any idea what's going on?

 The output of lsusb is the following:

:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04cb:01d1 Fuji Photo Film Co., Ltd
Bus 001 Device 003: ID 04b8:0818 Seiko Epson Corp.
Bus 001 Device 002: ID 046d:092c Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
 
I also have an other older fujifilm camera and it works perfect. When I plug it to the usb port it being recognized as usb mass storage and I can access and download the photos.

Thanks
Lancer

---

### Post by mgmiller on 2008-04-12
See if there is a setting in the camera itself that changes how it talks to the computer.  I think it's called PTP mode.  There may also be a setting in the application that you are using to import the pictures with that can give the choice to use PTP mode.

---

### Post by Lancerlan on 2008-04-20
Thanks for the advice. I checked the camera manual, and there is no option to choose from and ... The Finepix8100fd only used PTP and it seems that that mode doest not work so easily with ubuntu. I did some research but I really couldn't find anyway to make it work right. In my desesperation, I deceided that the best option that I had available was to buy a cheap a memory card reader and use it each time when I need to download photos to my computer......at least it worked and I got the problem solved. I really like Kubuntu, but things like this make the whole experience difficult.
Thanks
Lancerlan 
:-|

---

### Post by mgmiller on 2008-04-20
I didn't realize you were using kubuntu.  In ubuntu, the default up through 7.10 has been gthumb to import camera pics.  You could try installing it.  

I don't know where you would make the following settings changes in KDE.  
In gnome, you would go to System > Preferences > Removable Drives and Media and in the cameras tab you would enter the following command:
```
gnome-volume-manager-gthumb %h
```

I don't know what would happen in KDE using a gnome command.

If you simply enter the command:
```
gthumb
```
it would run the program when you plug in the camera, but you would then have to click File > import photos to bring up the import utility.

Not too bad a work around if it works.

---

### Post by wewek on 2008-04-26
Kubuntu 8.04

plug in and turn on your Camera
then just open Digikam -> Camera -> Add Camera... -> Auto Detect 
your Camera should appear.
now you should be able to ex/import your photos

---

### Post by Lancerlan on 2008-05-22
Digikam worked fine, It took several seconds to recognize the camera but now it's ok.
Thanks
Daniel

---

