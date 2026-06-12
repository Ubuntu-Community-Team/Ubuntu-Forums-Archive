---
title: "Video Card"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by hardXcore on 2006-05-10
I just installed my new video card! :D Only problem is, I'm not sure how to get it working with Ubuntu. I have a radeon 9250.


Any help is appreciated. :)

---

### Post by Sutekh on 2006-05-10
In what way do you need to get it working?  What's your current situation?  

No graphics/can't get Ubuntu to even display things properly?

Or, can get the display working but want/need accelerated graphics?


 - **Can't get display even working?**  Try using the **vesa** graphics driver temporarily.  To do this use this command from a Terminal window (Applications -> Accessories)
```
sudo dpkg-reconfigure xserver-xorg
```
Use your password when prompted

You will be asked a string of questions regarding the input devices (keyboard, mouse and monitor) on your PC.  If you are unsure what to answer, just use the default/suggested options.

When you get to the question about which driver you wish to use for the X Windows server. Choose **vesa**.  When the reconfiguring is finished, press Alt + Ctrl + Backspace, to restart the GUI. 



 - **Need accelerated graphics?**  You should look into installing the proprietry ATI drivers for Linux.  You can try either this HOWTO

[Ubuntu Document Storage Facility - Install ATI Driver](http://doc.gwos.org/index.php/Install_ATI_driver)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

---

### Post by hardXcore on 2006-05-10
Just wondering, if I haven't installed ubuntu yet and have the video card in will ubuntu be able to pick up the video card?

---

### Post by Sutekh on 2006-05-10
With ATI's I'm afraid I have no direct experience.  

I think the installation tries to use the free (freedom) **ati** driver, which can be a problem with some cards.  The **vesa** driver seems to work well with most cards.  

Non-free (proprietry) drivers are needed for 3D and accelerated graphics.

Ubuntu will definately 'pick-up' the card, its just a matter of *how well* the free **ati** driver works with that card.

---

### Post by joshrobinson on 2006-05-10
[QUOTE=Sutekh]With ATI's I'm afraid I have no direct experience.  

I think the installation tries to use the free (freedom) **ati** driver, which can be a problem with some cards.  The **vesa** driver seems to work well with most cards.  

Non-free (proprietry) drivers are needed for 3D and accelerated graphics.

Ubuntu will definately 'pick-up' the card, its just a matter of *how well* the free **ati** driver works with that card.[/QUOTE]

the ati video card in my laptop was picked up and used the ati driver. seems to work fine, resolution is good also

i installed the non-free drivers and had problems watching videos on my laptop, so i went back to the ati driver

if you install ubuntu with the video card in and enabled it should pick it up fine and set everything for you,, if ubuntu is already installed then you have to use the reconfigure command sutekh posted above

---

