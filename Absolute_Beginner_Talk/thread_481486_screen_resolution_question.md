---
title: "screen resolution question"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-06-22
i recently had to clean slate reinstall feisty now it seems to be running at a lower resolution (i can tell because the falcons eye window is unadjustable and it is bigger than before

 i checked the resolution tool and it doesn't go any higher (there was a higher setting before i reinstalled)

i tried installing the nvidia settings tool (i have an geforce 4 ti) but when mark it for installation it marks the nvidia-glx driver for removal 

so my problems are the mysterious disappearance of a resolution and hirer than 1024x768 and that thing with the nvidia setting package i mentioned above

please help

---

### Post by Kobalt on 2007-06-22
You can try this : open up a Terminal and enter the following command line ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Select the driver for your card, which should be nvidia since you installed this driver (leave default if you don't know) and then, in the resolution list, select the ones you want as available by hiting the spacebar. Validate with Enter. Restart X with Ctrl+Alt+Backspace so that the changes take effect, and now you should have a proper resolution.

---

### Post by 900donuts on 2007-06-22
if i were to accidentally select a resolution to high for my display whats the worst that could happen?

---

### Post by 900donuts on 2007-06-22
new problem i have it set to 1280x1024 and when i turn on either compiz or beryl the title bar on all the windows disappears i can't minimize from the panels either 

please help

---

### Post by 900donuts on 2007-06-22
update it has the same problem at the old 1024x768 resolution as well

---

### Post by Kobalt on 2007-06-22
This is not linked to your resolution, it comes from a lack in your Xorg configuration file. See [this]("http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29") to solve it.

---

### Post by 900donuts on 2007-06-22
thanks that fixed it :D

---

### Post by Nezing on 2007-06-22
Just dropped in on this thread.I was having Nvidia blues,as well.Cheers Kobalt,you've solved my 1024 as well (now 1152). :popcorn:

---

### Post by Kobalt on 2007-06-22
Two in a row : wouhou !! :p

You're welcome guys.

---

