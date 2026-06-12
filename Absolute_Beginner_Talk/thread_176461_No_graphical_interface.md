---
title: "No graphical interface?"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by ephoenixzh on 2006-05-14
Hi:
i have receive my ubuntu v5.10 cd and happly install it on my HP Compaq nx6310 Notebook PC. with all default option, i can just see a message after installation, which shows **"Fail to start the x server(you graphical interface).it is likely that it is not set up correctly. would you like to view the x server output to diagnose the porblem?".** and i can see only command line. i am quite new to linux, and i am not a programmer, so i do not think i can do some development, all i want now is to use it. how can i simply get my GUI??

---

### Post by Ob1 on 2006-05-14
This might work.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Omnios on 2006-05-14
```
Fail to start the x server(you graphical interface).it is likely that it is not set up correctly. would you like to view the x server output to diagnose the porblem?".
```

 It means that there is a config problem with xorg. I am not shure how it works with that model of lap top of laptops in general but it sounds like you have to config your vid card, monitor manualy or try using the vesa driver till you get this problem sorted out. Anyways what kind of video card do you have and what kind of monitor, is it a wide screen, there have been numerous problems with wide sceeen monitors. 

 ```
sudo dpkg-reconfigure xserver-xorg
``` 
is old turtle like graphical config thing for xorg and will allow you to config varios aspects of xorg.

 Edit:typo correction.

---

### Post by nalmeth on 2006-05-14
By versa he mean vesa
when you run that command, and you're asked to select your video driver, rather than going with the default (which has failed) pick vesa. If you require 3D accel, you can look into that when you have the GUI up and running.

---

### Post by ephoenixzh on 2006-05-15
My video card is ATI MOBILITY RADEON X300. i have tried > sudo dpkg-reconfigure xserver-xorg, and it do show some dialogs to configure xorg. But I just do not know which to choose. I tried more than an hour, and finally I quit. well, at least now I know there do exist an GUI. But still I can not use it.:(

---

### Post by Perfect Storm on 2006-05-15
This might help: [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X300)

---

### Post by ephoenixzh on 2006-05-16
Thank you all guys, I have already logged in Ubuntn Linux with GUI. It is very exciting to see a different user interface other than Windows. It is a complete new world!

---

