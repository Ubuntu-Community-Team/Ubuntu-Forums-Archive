---
title: "Ubuntu studio installation issues, please help"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by phylwx on 2008-04-14
Hello, thank you for taking the time to read this post :)

After hating feisty fawn blackscreen and livecd screensaver bug, tried lots of step by step tuts i gave it up and I installed Ubuntu studio ( Gutsy Gibbon ), but not without difficulties, installation wont work if i make a partition for /home so i had to put all together in one partition, desktop and audio drivers couldnt be installed, the installer got stuck and crashed, so i went and installed it without desktop, and installation was finished. I Installed Gnome-core and gksu  as indicated in a tutorial and got Ubuntu working in GUI after typing startx.

After Grub Boot start up runs until :
"*Running local boot scripts (/etc/rc.local)  [OK]"
and then i gotta press enter, "login", "Password" and "startx"

My hardware
Processor Intel Pentium 4 1.8 Ghz 32bits
Video Card ATI Radeon 9550 RU 350
80gb HDD partitioned in 40gb for lamedows, 38.5gb for Ubuntu Studio, 500mb swap
256 RAM (I know, barely made it,  im putting 512 more as soon as i get back from school)
Sound blaster24 ext usb
Some generic crappy dvd/cdr combo
 
This was my first approach at Linux and it was i dont know how much exhausting hours (still i gotta say i learned lots), but night has come and gone and id like to keep trying but i gotta g2 school, so i decided to ask you guys and i would really appreciate if anybody can help me or point me in the right direction to get a Splashscreen instead of having to press enter, login, password and startx. Other than that i love Ubuntu studio so far, runs smooth as silk, Enlightenment kicks ***, and im really getting to digg apt-get command :)

Again, thank you for your time and patience and i apologize for any typo, Enlglish is not my primary laguage.

---

### Post by phidia on 2008-04-14
Maybe you should try the alternate cd in ubuntu? 

To get a gui/graphical login open a terminal or from the commandline type:
> sudo gdmsetup. You should be able to set up a gui user loging from that.

---

