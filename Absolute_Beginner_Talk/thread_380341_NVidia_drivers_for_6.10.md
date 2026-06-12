---
title: "NVidia drivers for 6.10"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Seany.exe on 2007-03-09
i cant find them someone help i dont know how to install either :(

-Sean

---

### Post by o_fortuna on 2007-03-09
Here you go:

Click System, Administration, Synaptic Package Manager.

Enter your password and look for nvidia-glx. Click the box next to nvidia-glx and select install; then hit apply.

The faster option would be this: open up a terminal (Applications, Accessories, Terminal) and copy in this command:
```
sudo apt-get install nvidia-glx
```
You'll need to type your password. You will not see any stars or anything appear next to the password: prompt -- this is normal.

EDIT: Oh yeah, you'll also need to run
```
sudo nvidia-xconfig
```
Like progrockusa said.

---

### Post by progrockusa on 2007-03-09
```
sudo apt-get install linux-restricted-modules-generic
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```
this is another way

---

### Post by maddog39 on 2007-03-09
Or just go to: Applications > Add/Remove... and search "nvidia" then choose the regular nvidia for a fairly recent card, or legacy for really old cards. Hit apply and install it. Then run

sudo nvidia-xconfig

By hitting: Alt+F2 and typing that command in the text box, then check off "Run in Terminal" then hit Run. 

Why does everyone insist on pressing the command line against all the new comers. Thats what makes them hate linux, at least in my experience. They learn it eventually but it was the most furstrating hurtle to get through when I first started.

---

### Post by Seany.exe on 2007-03-10
ok guys all installed but how do i get the nvidia control panel up?

-Sean

---

### Post by ubername on 2007-03-10
> **Seany.exe said:**
> ok guys all installed but how do i get the nvidia control panel up?

-Sean

I should be in Applications > System tools > Nvidia settings.

Although I installed using Automatix which is an alternative to Synaptic Package manager. Check it out on these boards. I can't remember how I installed it but it adds a lot of extra functionality.

---

### Post by noynac on 2007-03-10
> **Seany.exe said:**
> ok guys all installed but how do i get the nvidia control panel up?
-Sean

I type nvidia-settings in a terminal window.

---

### Post by Delvien on 2007-03-10
Try a nifty little program called ENVY, works flawelessly for my Dell D820 with Nvidia 7400 go

---

