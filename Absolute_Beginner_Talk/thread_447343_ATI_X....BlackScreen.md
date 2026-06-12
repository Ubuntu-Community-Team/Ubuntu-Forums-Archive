---
title: "ATI X....BlackScreen"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by PartyTaco on 2007-05-17
I have an ATI Radeon X1650.  I have tried the method described in the sticky above, envy, and the graphics accelerator method that comes with Ubuntu. Each of these solutions only results in my Ubuntu desktop loading to a black screen after I restart my computer. if anyone could help me fix this it would be much appreciated. As I have reinstalled ubuntu about 10 times now. :]

Cheers.

---

### Post by krisfrajer on 2007-05-17
no need to reinstall ubuntu. You just have to recover your xorg.conf file.  Do it following the following steps.
When you get to the option of loading ubuntu... shose ubuntu command line and then type the following commands


cd /etc/X11/


sudo dpkg-reconfigure -phigh xserver-xorg


THis line willa sk you for your root password and then he will ask you simple questions about the video card that you have (in your case an ATI) and then when you restart ubuntu again it will be in your grpahics mode again. These steps only recover your old video card configuration but it does not solve the problem of how to install the video card correctly. I am just hoping you do not have to go through the installation process everytime you get a black screen after messing/trying to configure your drivers of your video card.  Setting up the video card is another story... and no sorry I do not have experience setting up those cards.. sorry. I hope this helps.

---

### Post by PartyTaco on 2007-05-17
Thanks, I will keep that in mind.

Would it just be easier if I went back to 6.10? It seems that version has its act together.

---

