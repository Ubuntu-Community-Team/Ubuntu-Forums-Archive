---
title: "Add Cool stuff to my desktop"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by chaoscomic on 2006-09-12
Ok so I just downloaded and installed Ubuntu
and I see all these great screen shots of peoples desktops
and how they have a cool looking calander and other widgets I guess on there, the question is where do I get them from or are they already installed and I just don't know where to look for them. I really want to access all the cool stuff but I have no idea how to. Any help is appreciated thanks again

chaoscomic

---

### Post by wrob on 2006-09-13
gdesklets is what you're looking for

sudo apt-get install gdesklets gdesklets-data

---

### Post by Metacarpal on 2006-09-13
> **chaoscomic said:**
> Ok so I just downloaded and installed Ubuntu
and I see all these great screen shots of peoples desktops
and how they have a cool looking calander and other widgets I guess on there, the question is where do I get them from or are they already installed and I just don't know where to look for them. I really want to access all the cool stuff but I have no idea how to. Any help is appreciated thanks again

chaoscomic

Hi chaoscomic,

Welcome to Ubuntu!

The gdesklets package has some fun stuff for Ubuntu's default Gnome desktop, but if you're really into eye candy, you might check out Kubuntu, which runs the KDE desktop.

**ANTI-FLAME NOTICE**
I'm not a gnome-basher.  I love gnome.  I don't use KDE 'cause my laptop is too old to run it well.  But it really is very pretty.

*ahem*
Sorry 'bout that.  There are enough Gnome vs KDE threads on this forum already, didn't want to start a new one by accident.
[URL="http://www.psychocats.net/ubuntu/kdegnome"]
Here's a good comparison of the two[/URL].

If you want to test drive KDE for a while, open a terminal (Applications menu > Accessories > Terminal) and type:
```
sudo aptitude install kubuntu-desktop
```
then enter your login password when prompted.

You can have both on one machine and switch between them at the login window.  Just click on Select Session and choose which one you want to run.

If you don't like KDE, you can easily remove it by typing this into a terminal:

```
sudo aptitude remove kubuntu-desktop
```

Just wanted to put the option out there.

---

### Post by chaoscomic on 2006-11-06
thanks for the heads up on the kbuntu I am installing as I type here 
hope it;s cool

---

### Post by ewl1217 on 2006-11-06
Some of the screenshots you saw might also be using Beryl, a different window manager which uses compositing to achieve some spectacular visual effects. Beryl, which is a fork of Compiz, is under constant development and isn't really completely stable or bug-free, but it does look awesome. If you're interested (and you have a good graphics card...), I'm sure that someone could point you in the right direction. I'm not really up on using unstable software (not to mention my graphics card isn't too good), so I can't help you much personally.

---

### Post by FrancesL on 2008-02-19
> **wrob said:**
> gdesklets is what you're looking for

sudo apt-get install gdesklets gdesklets-data
After this command how do you actually access to use the 'pretties'? Please.

---

### Post by FuturePilot on 2008-02-19
They should be under Applications&#8594;Accessories&#8594;GDesklets

---

### Post by FrancesL on 2008-02-20
Yep they are thanks..now to work out how to actually get the most from them

---

### Post by chewit on 2008-02-20
There are some "gadgets/widgets" built into GNOME already. If you right click on the taskbar, you can add little gadgets like system monitor or calender.

If you want fancy stuff, have you get Compiz installed, but it does take up alot of CPU and RAM.

---

### Post by hyper_ch on 2008-02-20
if you want to ahve system stats being displayed on your desktop, search the forum for Conky.

---

### Post by P0CKETS on 2008-02-20
> **wrob said:**
> gdesklets is what you're looking for

sudo apt-get install gdesklets gdesklets-data

After doing this I got the gDesklets icon under my applications menu but when i go to click it starts a gDesklets shell and thats it? I am unable to do anything other than that. What did I do wrong or not do?

---

