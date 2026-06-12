---
title: "How can i Fix this X display error?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by alon_pex on 2008-02-07
i want to install driver for my video card. (ATI Radeon 9600).
i edited codes in the terminal as the install guide said.
Then i reboot the system t activate the effects and i get an error on X display.
it says no screen found :(

---

### Post by Rocket2DMn on 2008-02-07
If you aren't already at a terminal, do CTRL+ALT+F1 and login.  Then run this command to automatically reconfigure X
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then do
```
startx
```

---

### Post by alon_pex on 2008-02-07
hey, tnx for the quick reply..
ill try this one..
thanks so much

---

### Post by alon_pex on 2008-02-07
hey, it works.. thank you so much..
ill be back for more questions..
hehehehhe thanks  lot

---

