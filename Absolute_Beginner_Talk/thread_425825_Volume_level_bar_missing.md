---
title: "Volume level bar missing"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-27
Please, look at the attachment and tell me what happened to the volume level bar.:confused:

This just happened today for the first time in over 20 Linux installs.

Do you know how to fix it? Thanks for your help.
kh

---

### Post by deadgobby on 2007-04-27
I do not know. Have you click on the speaker icon and adjust your levels there?

---

### Post by kittyhawk63 on 2007-04-27
> **deadgobby said:**
> I do not know. Have you click on the speaker icon and adjust your levels there?

I know that works. Thanks. I would like to use the volume controller on my keyboard. It is much faster.
kh

---

### Post by Najand on 2007-04-27
Assign a shortcut key for it. (System -> Preferences -> Keyboard Shortcuts)

---

### Post by kittyhawk63 on 2007-04-27
> **Najand said:**
> Assign a shortcut key for it. (System -> Preferences -> Keyboard Shortcuts)

I can adjust the volume with my keyboard. I am just missing the visible blue bar that shows me how low or high the volume is.
kh

---

### Post by Najand on 2007-04-27
First, backup your xorg.conf.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

print out these instructions. after you finish editing xorg.conf, if you have problems after restarting x (ctrl>>alt>>backspace) then do this...

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

now open up your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

and make sure you have this...

```
Section "DRI"
Mode	0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection

```

somewhere in your xorg.conf. it doesn't have to be in this exact configuration, just make sure it's in there somewhere. in addition to enabling the volume icon, it should boost the 3d performance of your computer. but i'm just a noob speaking from limited experience.

---

### Post by kittyhawk63 on 2007-04-28
> **Najand said:**
> First, backup your xorg.conf.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```print out these instructions. after you finish editing xorg.conf, if you have problems after restarting x (ctrl>>alt>>backspace) then do this...
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```now open up your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```and make sure you have this...
```
Section "DRI"
Mode    0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
Option "RENDER" "Enable"
EndSection
Section "ServerFlags"
Option "AIGLX" "on"
EndSection

```somewhere in your xorg.conf. it doesn't have to be in this exact configuration, just make sure it's in there somewhere. in addition to enabling the volume icon, it should boost the 3d performance of your computer. but i'm just a noob speaking from limited experience.

Najand,
I've been having trouble with my ATI video card ever since I installed Dapper, Edgy, and now Feisty. I was told to "disable" Composite and turn "off" AIGLX.
We will see what happens. I may have to turn them back off if I start crashing again.
Thanks for the suggestion.
Thread remains open for now.
kh

---

### Post by Najand on 2007-04-28
Tell me the result.

---

### Post by kittyhawk63 on 2007-04-28
> **Najand said:**
> Tell me the result.

No crash ......yet.

There is still no volume level bar in the pop up volume screen. You know, I think the bar is there, I just think it is invisible. The same color as the background or is transparent.
kh

---

### Post by paparucino on 2007-04-28
> **kittyhawk63 said:**
> No crash ......yet.

There is still no volume level bar in the pop up volume screen. You know, I think the bar is there, I just think it is invisible. The same color as the background or is transparent.
kh
Did you try to change the theme?
For some reason, it could be an error in the theme

---

### Post by kittyhawk63 on 2007-04-28
> **paparucino said:**
> Did you try to change the theme?
For some reason, it could be an error in the theme

OK! Changing the theme has given me the volume level slider bar back. That means that there is something wrong with the "Human" theme. So, there must be a fix. Is there a way to reinstall the "Human" theme? 

Edit. I found the theme in Synaptic Package Installer.

Thanks Paparucino for the heads up. :)
kh

---

### Post by paparucino on 2007-04-28
> **kittyhawk63 said:**
> 
Thanks Paparucino for the heads up. :)
kh

You're welcome.

---

