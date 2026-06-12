---
title: "Out of Range"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by doom_fan on 2007-03-31
Hello I have 2.1 ghz processor and a PCI-E gefocre 6800 GS video card.I try to boot off the CD and every thing works good In till I try booting off my hard disk after installation.It boots to the Ubuntu logo then my monitor comes up as out of range for thirty minutes.Then I hit the reset button to repeat the same process.Thanks for any help.

---

### Post by Jorge32 on 2007-03-31
When the message appears press Ctrl+Alt+F4, then enter your user and password (the ones you created in the installation) and then type the following: "
```
sudo dpkg-reconfigure xserver-xorg
```
it will send you to configure a lot of things, practically leave everything the way it was until you find the resolution for your monitor, there select the last three (1024x768 , 800x600, and 640x480) and continue, when it asks you about configuring the monitor in easy, medium, or advanced mode select advanced, then on the horizontal frequency or range change the 30-55 to 31.5-47.5, and on the vertical change the 50-120 to 40-70, and select 24 bit depth. Try searching for the perfect values for your monitor, but anyway they sometimes doesn't work because of the problem, anyway i hope this helps you.
When it finishes all and there appears the line to write a command below the configuration you made, type: 
```
sudo /etc/init.d/gdm restart
```. 
This way it should work fine (at least it worked for me when I had the same problems with a Matrox video card), but you will only achieve a maximun resolution of 800x600.
Then search for the driver of your video card, and then install it, restart it and next time your resolution should be fine. Good luck

---

### Post by doom_fan on 2007-03-31
> **Jorge32 said:**
> When the message appears press Ctrl+Alt+F4, then enter your user and password (the ones you created in the installation) and then type the following: "
```
sudo dpkg-reconfigure xserver-xorg
```
it will send you to configure a lot of things, practically leave everything the way it was until you find the resolution for your monitor, there select the last three (1024x768 , 800x600, and 640x480) and continue, when it asks you about configuring the monitor in easy, medium, or advanced mode select advanced, then on the horizontal frequency or range change the 30-55 to 31.5-47.5, and on the vertical change the 50-120 to 40-70, and select 24 bit depth. Try searching for the perfect values for your monitor, but anyway they sometimes doesn't work because of the problem, anyway i hope this helps you.
When it finishes all and there appears the line to write a command below the configuration you made, type: 
```
sudo /etc/init.d/gdm restart
```. 
This way it should work fine (at least it worked for me when I had the same problems with a Matrox video card), but you will only achieve a maximun resolution of 800x600.
Then search for the driver of your video card, and then install it, restart it and next time your resolution should be fine. Good luck
Thxs that fixed it however now my internet does not work now.

---

