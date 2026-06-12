---
title: "Max Screen resolution"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ryana on 2007-08-28
1024x768 just isn't cutting it for me, but its the maximum resolution I can choose through the menus...how can I get a higher resolution?

ubuntu feisty, pentium 4, nvidia geforce fx 5500 graphics card, and an intel integrated thing I dont use.

---

### Post by eeeeepuk on 2007-08-28
You can edit your xorg.conf file to add the resolution you want. Type gksudo gedit /etc/X11/xorg.conf into the terminal, then edit your mode lines. Initially, they will look something like:
Modes      "1024x768" "800x600" "640x480"
You need to add the mode that you want to the start of these lines, so for example to add 1280x1024 your mode lines would look like:
Modes      "1280x1024" "1024x768" "800x600" "640x480"
Add any resolutions that you want to be able to choose between, making sure your preferred resolution is the first one, as this is the one that X will default to.

---

### Post by diatribe on 2007-08-28
I believe there is an nvidia configuration tool for ubuntu also, try using google or searching the forums

---

### Post by ryana on 2007-08-28
I'll try that in a bit, thanks for the really quick replies!

---

### Post by Hobo Joe on 2007-08-28
You'll want to use the nVidia control panel for that, it's easier and less likely to break something.

To run, type this in the terminal:
```

sudo nvidia-settings

```

---

### Post by ryana on 2007-08-29
Ah yes!!! thanks a million this is just what I was looking for. I really appreciate all the help there is for new users on these forums.

---

