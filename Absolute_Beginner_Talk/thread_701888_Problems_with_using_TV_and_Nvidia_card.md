---
title: "Problems with using TV and Nvidia card"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by akschnare on 2008-02-19
Hey, I just installed the Nvidia legacy drivers from their website for my G4 MX420 and everything seems to work fine. Now I want to connect a television to the composite connection on the back and have it clone my desktop. I have that working. But when I want to watch a video on my computer it shows up on both screens just like it should, until I make it go full screen. Once I do that, the tv disables itself and I have to go back into the Nvidia xserver settings and reconfigure everything again. 

Its getting to be a real pain and if anyone could help it would be really great. Thanks.

---

### Post by ArchangHell on 2008-02-19
It´s a common problem not having a video playing in two desktops at the same time. Try this.

I have my PC connected to a TV in another room and works perfectly in ubuntu, far better than in windows.

Do way I have done it? Simply enable the restricted drivers (7.10) and run nvidia-settings in the terminal. I really recommend doing this everytime you wish to change configurations, in spite of the screen-resolutions in gnome menu.
The option I use is separate X screen, because it let me control the desktops independently, so I can work  in PC and watch a movie on TV at same time.

And I give some suggestions that are quite easy to setup (even for a newbie like me):
I use my cell-phone as a bluetooh remote control and often use MythTV on the TV what brings simplicity and many options in a simple navigation system for the remote control. As you see It's like having two PCs


If you really want something simple:
configure your video player to have a full-screen resolution 800x600) probably you TV don´t support more (also common especially with the composite out)

---

