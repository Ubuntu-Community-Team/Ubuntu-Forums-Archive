---
title: "murrine has taken over my themes..."
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by wana10 on 2007-10-01
so i installed murrine, and used the themes, and had a jolly good time, but now when i want to change to a non-murrine theme i have a problem. the bar on every window where file, edit, etc go is a blue color, and no matter what i do i can't change that blue...human theme looks rather odd with a blue bar in the middle of it. any help in getting rid of that would be great, thanks for the help.

*edit, i found that if i change murrine themes the blue will change colors with the theme but if i choose a non-murrine theme it returns to the blue.

---

### Post by nowshining on 2007-10-02
once you change to a human theme open up a terminal and type

metacity --replace


do NOT close out by clicking ctrl + c if you do or want to afterwords alt + f4 the folders, windows ,etc.. to close and do a reboot..

---

### Post by wana10 on 2007-10-02
when i enter that in a terminal this is what comes back

```
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by nowshining on 2007-10-02
if I remember correctly I got those errors too, i just ignore them, if that doesn't work, go into ur home folder and find a folder named .gnome2 and then find a file name session, delete it and do a reboot.


edit: press ctrl + h to show hidden files first.

---

### Post by nowshining on 2007-10-02
the reason I asked to not close is because if you do the borders and the close, minimize and such will disappear. However after a reboot it should work..

---

### Post by wana10 on 2007-10-02
did the reboot after metacity --replace, nothing
went into ~/.gnome2, no file named session

thanks for the help thus far.

---

### Post by nowshining on 2007-10-03
again have you tried Uninstalling the program, or do you need help on how to do that?

---

### Post by wana10 on 2007-10-03
already tried uninstalling murrine, it changes the blue bar from looking glossy to looking flat.

---

### Post by nowshining on 2007-10-03
download and install gtkorphan it should be in the repos, install it and then open it up - system - administration and than anything in there check mark and then click okay, click yes, and then once it's done,click ok, from there if any more pop out or show up is what I mean keep removing until all is gone. Do not check the options underneath unless ur willing to take a risk, while the first option is fine, the second if checked ALONE will show orphaned programs which are NOT orphaned, :) i learnt that the hard way and ruint my ubuntu setup the first time. :P 

if both are checked then all should be will, then after all is done and well do a reboot.

---

### Post by nowshining on 2007-10-03
After that open up a terminal and then run the following command

```

sudo apt-get install -f

```

report back on what it says or you can take a risk ur self without a confirm and hit the y key and then enter. :)

---

### Post by wana10 on 2007-10-03
sudo apt-get install -f does nothing this is what it returns
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove

---

### Post by nowshining on 2007-10-03
hmmm all is well there, did you install the program I Asked u to?

---

### Post by wana10 on 2007-10-03
yes, i installed and ran gtkorphan, followed with a reboot

---

### Post by nowshining on 2007-10-04
gtkorphan gets some things, synaptic doesn't remove and the install -f command doesn't remove.

---

