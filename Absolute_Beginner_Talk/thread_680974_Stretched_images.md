---
title: "Stretched images"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by joey.dye1 on 2008-01-28
I am very new to using Ubuntu. I know that I'm using 7.04, Feisty Fawn on a computer that originally runs Windows Vista. My screen resolution is 1024x768 and whenever I view images on firefox and locally, they all seem to be stretched horizontally. Is there any way that I can fix this? If anyone can provide detailed and basic step-by-step instructions for me I would greatly appreciate it.

---

### Post by forrestcupp on 2008-01-28
Do you have a wide screen monitor?  If so, the resolution you are using is for a standard size monitor, and it will stretch everything to fit your screen.  Try going to your Preferences and see if you can change your screen resolution to a wide screen resolution (if that is what you have). If that doesn't work for you, you may have to edit xorg.conf or reconfigure x, and manually set resolutions that will work for you.  To reconfigure x, type in a terminal: 
```
sudo dpkg-reconfigure xserver-xorg
```
Then just answer the questions on screen according to what monitor and video card you have.

If you don't have a wide screen monitor, don't do any of this.

---

