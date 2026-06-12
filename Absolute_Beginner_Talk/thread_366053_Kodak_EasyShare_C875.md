---
title: "Kodak EasyShare C875"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by KB9JTO on 2007-02-20
I have a Kodak C875 and I can not get it to work, Can anyone help me?
Keeps giving me some kind of USB error. 

Thanks
KB9JTO:confused:

---

### Post by n8bounds on 2007-02-21
Did it ever work?  Do you have a bad cable?  Tried every possible usb port?

---

### Post by KB9JTO on 2007-02-22
[SIZE="2"][FONT="Arial Black"]It works fine on my wifes XP machine. I have a Dell Inspiron 2200 Laptop. 
I have 3 USB Ports. They all work. 
I just did not know if there is any special software that I need. I do not like using the Kodak software. [/FONT][/SIZE]

---

### Post by netkid91 on 2007-02-22
Kodak cameras have a bad rep with libgphoto(the camera library behind F-Spot and most other photo programs).  I have had the same problem with a C530, but the fix was very hacky, and required me to install packages from the Feisty repo's (Feisty's libgphoto has better PTP/IP camera support, which is what new Kodak EasyShare camera's use).  I'm at school right now, so I can give you a list of packages to get, etc.  But you have two options right now, use my hackish method or grin and bear it until April when Feisty is released.

---

### Post by charles nicholls on 2007-02-23
This one's had me flummoxed for quite a while, I'm using a Kodak v750 that I finally got to work in digikam by adding it as a usb ptp camera class. :)

---

### Post by netkid91 on 2007-02-23
That's the only way they want to run.  But the issue is some cameras don't work well right now with libgphoto2's PTP support in Edgy, the newest version in Feisty is much bette.

---

### Post by grendel38 on 2007-03-02
I got my Kodak C875 to work by trying this:

[http://www.ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb](http://www.ubuntuforums.org/showthread.php?t=340271&highlight=kodak+camera+usb)

good luck

---

### Post by xavier_r on 2007-04-22
I have a Kodak EasySHare C875 and it workds fine with the main user...
But with other user accounts it shows USB error...

Login in using your main administrative account, and then switch on your camera and plug it in the usb...
Try that out

---

