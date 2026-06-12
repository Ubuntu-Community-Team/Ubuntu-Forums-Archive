---
title: "GRUB issues"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Selrach on 2007-06-25
I am trying to edit my boot parameters, but when I try to do so via the GRUB boot interface, my changes do not appear to be saved. Could someone help me here? I need to try some parameters to see if I can use them to boot my new installation.

---

### Post by Sandlst on 2007-06-25
The easiest way to do this is to boot up, then from within ubuntu, opening a terminal (Applications/Accessories/Terminal) and typing in```
sudo gedit /boot/grub/menu.lst
```Scroll down to the bottom, then scroll up a bit until you see this section: ```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
Be sure to keep all comments (#) in place, and add/change the options you need under the line: ```
# defoptions=quiet splash
```
If you want the same paramaters to be used on recovery options, do the same thing in this section a little bit below the first one: ```
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single
```
Save and close when done, then run this command: ```
sudo update-grub
```Your settings should be saved and used on next boot. Good luck, post back if you have any problems!

---

