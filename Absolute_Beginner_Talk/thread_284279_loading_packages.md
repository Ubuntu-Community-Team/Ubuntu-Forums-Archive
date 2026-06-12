---
title: "loading packages"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by WilliamRead on 2006-10-25
I am new to linux/ubuntu - I am trying to set up things in ubuntu (dappy duck). I have looked for a package that might help me, that is libusb, I have found  a version libusb.tar which I have downloaded to a CDdrive. I am not able to access ubuntu from linux at the moment. I tried to install thiis by using install from CD option from within the install package program, but it will not permit this as it is not ubuntu (unable to find any packages). I have tried to look for this package in ubuntu but not ablr to find it to download onto CD to install it.Can anyone please help. By and by please make it as simple as possible as I find that there are endless program files mentioned which I do not know where they are to go

Regards William

---

### Post by TitusDalwards on 2006-10-25
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libusb&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libusb&searchon=names&subword=1&version=dapper&release=all)

here is some information abaout libusb, if your repos is open, you can download and install by using APT

---

### Post by Ben Sprinkle on 2006-10-25
Well did you read the docs about how to install about "dappy duck"? Rofl, it's dapper.

---

### Post by WilliamRead on 2006-10-25
thank you Titus Dalwards  I have been to that site befor in fact I spent quite a time there. Unfortunately I could not understand what was required. All I want to do is install the program. I am still very lost. Sorry for being so slow.

Regards William

---

### Post by WilliamRead on 2006-10-25
Synectics thanks for boosting my confidents I am a beginer

---

### Post by CatKiller on 2006-10-25
> **WilliamRead said:**
> thank you Titus Dalwards  I have been to that site befor in fact I spent quite a time there. Unfortunately I could not understand what was required. All I want to do is install the program. I am still very lost. Sorry for being so slow.

Regards William

If I understand you correctly, you are currently able to connect to the Internet with your Ubuntu install, and you are trying to install some programs (possibly to enable a connection to the Internet?) that you've downloaded with another computer with Internet access. [This page]("http://monkeyblog.org/ubuntu/installing/") may help you understand the methods you can use to install software in Ubuntu, but the upshot is that if you can get a .deb file for the package you want to install then installation is as simple as double-clicking on a file.

Where it becomes difficult is when you have unmet dependencies. If you have access to a properly-formatted repository, then this is easy - all the dependencies get met automatically. If you don't, then you have to meet the dependencies yourself.

I hope this helps. If you post your specific problem, someone may be able to offer you a different method to solve it, or give you step-by-step instructions. Welcome to the community.

PS: Although you may have taken it as a knock to your confidence, there is no way that synectics meant it to be. And dappy duck **is** really funny. Good luck.

---

### Post by WilliamRead on 2006-10-25
Thank you
catkiller for your response.
I am unable to connect to the internet via linux/ubuntu, therefore I have to use wins at the moment.
I have downloaded libusb to a CD this I cannot load usage the ubuntu package loader. I have looked in ubuntu for this package but unable to find it. I have also tries to find out if it is possable to load thar package I have downloaded. This is a linux programm as well

Regards William

---

### Post by bsussman on 2006-10-25
> **synectics said:**
> Well did you read the docs about how to install about "dappy duck"? Rofl, it's dapper.

Some folks thoght it was _dippy_ :mrgreen:

---

### Post by CatKiller on 2006-10-25
> **WilliamRead said:**
> I have downloaded libusb to a CD this I cannot load usage the ubuntu package loader. I have looked in ubuntu for this package but unable to find it. I have also tries to find out if it is possable to load thar package I have downloaded. This is a linux programm as well

Regards William

If you've downloaded a .deb file, you should be able to either double-click it to install it, or copy the file to your Home folder to install it with ```
sudo dpkg -i libusb-0.1-4_0.1.10a-22ubuntu1_i386.deb
``` from the terminal. You get to the terminal with Applications -> Accessories -> Terminal. You won't be able to install a package you've downloaded with the Synaptic Package Manager - that handles all the downloading itself, if you have an Internet connection.

I am still unclear as to what you are trying to do with libusb.

---

### Post by Ben Sprinkle on 2006-10-26
> **WilliamRead said:**
> Synectics thanks for boosting my confidents I am a beginer

Your welcome.
dappy duck, daffy duck, dapper dilso, dippy demmer. What's the diference. 8)

---

