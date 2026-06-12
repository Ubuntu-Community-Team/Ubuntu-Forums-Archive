---
title: "Xubuntu installation on a Toshiba satellite 4070"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Aart on 2007-03-04
I have 2 questions:
I tried to run the live Xubuntu 6.10 CD on my Toshiba satellite 4070 CDT. It has a Trident Video Accelerator 9525DVD. Everything seems to work apart from the fact that the size of the display does not fill the entire TFT screen. Before installing I would like to know how to adjust  this or does this mean that the graphics card is not recognized?
2 I have a sitecom WL 011 card. Does someone has a suggestion how to make this work?
  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Aart

---

### Post by Kateikyoushi on 2007-03-04
The display does not fill the screen because the correct resolution is not set.
Configure it with the following command.
```
sudo dpkg-reconfigure xserver-xorg
```

---

