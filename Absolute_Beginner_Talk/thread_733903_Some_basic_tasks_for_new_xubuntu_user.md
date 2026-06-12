---
title: "Some basic tasks for new xubuntu user"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Azmandius on 2008-03-24
Hello,
I am very new to Linux world and i guide a office transition from windows to [LEFT][COLOR=green][FONT=serif]**_Linux_**[/FONT][/COLOR][/LEFT].
I have just successfully setup [LEFT][COLOR=red][FONT=serif]**_Xubuuntu_**[/FONT][/COLOR][/LEFT] 6 and have some basic but important questions.
First of all i am wondering how to update display drivers because [LEFT][COLOR=green][FONT=serif]**_Linux_**[/FONT][/COLOR][/LEFT] has installed drivers that allow 60 refresh rate only. Thus its so [LEFT][COLOR=green][FONT=serif]**_painful_**[/FONT][/COLOR][/LEFT] to look at the screen. I need to set monitor refresh rate as 75 minimum.
Is there a way to do that?
2. My [LEFT][COLOR=red][FONT=serif]**_HDDs_**[/FONT][/COLOR][/LEFT] and DVD [LEFT][COLOR=red][FONT=serif]**_ROMs_**[/FONT][/COLOR][/LEFT] are accessible from system settings but i just can't figure out how to make shortcuts on desktop for browsing partitions an optical devices.
3. When i try to use Samba for network files sharing and access i get error:
```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu3.1_i386.deb
  404 Not Found
```
4. Add more languages so i could type for example in Russian or Romanian when using office or [LEFT][COLOR=green][FONT=serif]**_Internet_**[/FONT][/COLOR][/LEFT].
5. Lock station when going for 10 min. to have a cup of coffee. You know that way of locking station using windows logo+l key combination in windows. Is there anything similar in [LEFT][COLOR=red][FONT=serif]**_xubuntu_**[/FONT][/COLOR][/LEFT]?
Sorry for overloading with questions, its just the way it is, i am total newbie for [LEFT][COLOR=green][FONT=serif]**_Linux_**[/FONT][/COLOR][/LEFT] concept of using [LEFT][COLOR=green][FONT=serif]**_computer_**[/FONT][/COLOR][/LEFT].
Thank you a lot,
Regards

---

### Post by neurostu on 2008-03-24
So I can answer a couple of your questions.

To Lock your Screen try:
```

Ctrl+Alt+L

```

As far as the refresh rate goes, what video card are you using?  Under System-->Administration-->Screen and Graphics you can setup Ubuntu to use your specific monitor model.

---

### Post by Samurai Penguin on 2008-03-24
for display drivers, go to SYSTEM > ADMINISTRATION > Restricted Drivers Manager
You'll know what to do from there. After it updates the drivers you will be able to
set the refresh rate where you want it to be ( I use 85Hz )

---

### Post by Azmandius on 2008-03-24
> **Samurai Penguin said:**
> for display drivers, go to SYSTEM > ADMINISTRATION > Restricted Drivers Manager
You'll know what to do from there. After it updates the drivers you will be able to
set the refresh rate where you want it to be ( I use 85Hz )
Thanks.

---

### Post by jken146 on 2008-03-24
If enabling the restricted driver (if there is one) doesn't give you the right options in the display settings config app, you may need to do press ctrl+alt+F1, log in and do ```
sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure xserver-xorg

sudo /etc/init.d/gdm start
```


If ctrl+alt+L doesn't lock the screen, install the package **xlockmore** and try it again.

---

### Post by Azmandius on 2008-03-25
> **jken146 said:**
> If enabling the restricted driver (if there is one) doesn't give you the right options in the display settings config app, you may need to do press ctrl+alt+F1, log in and do ```
sudo /etc/init.d/gdm stop
 
sudo dpkg-reconfigure xserver-xorg
 
sudo /etc/init.d/gdm start
```
 
 
If ctrl+alt+L doesn't lock the screen, install the package **xlockmore** and try it again.
Thank you,
Will be trying that.

---

