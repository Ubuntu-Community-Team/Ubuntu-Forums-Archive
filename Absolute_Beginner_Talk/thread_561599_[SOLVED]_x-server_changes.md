---
title: "[SOLVED] x-server changes"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-09-27
I used this procedure to change the screen resolution for my monitor: 
 Re: Screen resolution
Open up a terminal and run
Code:

sudo dpkg-reconfigure -phigh xserver-xorg

Select the resolutions you want as available by hitting the spacebar and then validate with Enter. Finally restart X with Ctrl+Atl+Backspace, and you should be done.
What key or keys do I use to remove the resolutions that I don't want to show under "Preferances/fonts?

---

### Post by overdrank on 2007-09-27
> **skyjacker said:**
> I used this procedure to change the screen resolution for my monitor: 
 Re: Screen resolution
Open up a terminal and run
Code:

sudo dpkg-reconfigure -phigh xserver-xorg

Select the resolutions you want as available by hitting the spacebar and then validate with Enter. Finally restart X with Ctrl+Atl+Backspace, and you should be done.
What key or keys do I use to remove the resolutions that I don't want to show under "Preferances/fonts?

Hi do you mean under preference, resolution? If so you can use the command 
```
gksudo gedit /etc/X11/xorg.conf 
```
And remove the resolutions you don't want.
But first you will want to back up you xorg first
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup if something goes wrong then use this command
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by skyjacker on 2007-09-27
> **overdrank said:**
> Hi do you mean under preference, resolution? If so you can use the command 
```
gksudo gedit /etc/X11/xorg.conf 
```
And remove the resolutions you don't want.
But first you will want to back up you xorg first
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup if something goes wrong then use this command
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
I meant i used the spacerbar to select the items I wanted. This placed a + in front of them. What key would I use to remove the ones I don't want??

---

### Post by overdrank on 2007-09-27
It should be using the spacebar again. once to select the resolution and if you hit it again it should be unselected .

---

### Post by skyjacker on 2007-09-27
> **overdrank said:**
> It should be using the spacebar again. once to select the resolution and if you hit it again it should be unselected .
The resolutions that have a blank square to the left are the ones I am talking about. If I want one of them, I hit the spacebar to choose it. it then places a + sign in the square. How do the ones with the blank squares get removed if I never picked them to start with???:confused:

---

