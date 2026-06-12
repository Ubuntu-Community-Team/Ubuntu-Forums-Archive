---
title: "Trying to adjust screen resolution"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by M.Mizery on 2007-05-28
Hello all,

I am new to Ubuntu, I was wondering if some one could help me out with fixing my monitor resolution. After my Ubuntu install I am stuck with a big monitor resolution of 640 x 480. Everything on my screen is extra big. I got directions last night on how to get the the x server, but now I need help trying to select the resolution?


I am already in the x server configuration:


The x server asks me to:



Select the video modes you would like the X server to use. [ ] 1920x1440 [ ] 1920x1200 [ ] 1856x1392 [ ] 1792x1344 [ ] 1680x1050 [ ] 1600x1200 [ ] 1440x900


the problem is I do not know how to fill in the blanks. It does not explain to you how to fill them in or let alone deselect an option. 

How do I do this? I am lost and do not know what to do on this screen?


Any help I could get would be really appreciated.


MM

---

### Post by taurus on 2007-05-28
Use the space bar on your keyboard to put a * in front of the resolution you want to use.  Use the arrow keys to move around.

---

### Post by M.Mizery on 2007-05-28
> **taurus said:**
> Use the space bar on your keyboard to put a * in front of the resolution you want to use.  Use the arrow keys to move around.

Thank you very much, I will let you know how it goes.

---

### Post by M.Mizery on 2007-05-28
> **taurus said:**
> Use the space bar on your keyboard to put a * in front of the resolution you want to use.  Use the arrow keys to move around.



Ok, I did what you said and that helped.

I answered the rest of the questions in x server...having to do with my monitor.

Now I just have another question.

I am no longer in the x server and i am back at the terminal.

After the x server shut its self off up came this line in my terminal window that saids:


^[[24~xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070528125351

and then after that there is the user@user-desktop: ~$


What I am wondering looking at this??

I am wondering is there something else I need to do for the changes to take effect?

I really appreciate any help I could continue to get from you or anyone else on the board.

Thank you all,

MM

---

### Post by Outrunner on 2007-05-28
Try typing

```
startx
```

---

### Post by taurus on 2007-05-28
The original /etc/X11/xorg.conf (before you configured it) is now saved to /etc/X11/xorg.conf.20070528125351.

What happens if you type this in a prompt to start a GUI login screen?

```
sudo /etc/init.d/gdm start
```

---

### Post by M.Mizery on 2007-05-28
> **taurus said:**
> The original /etc/X11/xorg.conf (before you configured it) is now saved to /etc/X11/xorg.conf.20070528125351.  

Ok, I understand this, it makes sense, gut I am lost on the other stuff you are talking about...see you quote:

What happens if you type this in a prompt to start a GUI login screen?

```
sudo /etc/init.d/gdm start
```


I just wanted to know if there where anything I should do after this or is that what the code is for? 

Could you please specify this for me?


Thank you.

---

### Post by M.Mizery on 2007-05-28
> **Outrunner said:**
> Try typing

```
startx
```


what happens after this?

---

### Post by M.Mizery on 2007-05-28
> **taurus said:**
> The original /etc/X11/xorg.conf (before you configured it) is now saved to /etc/X11/xorg.conf.20070528125351.

What happens if you type this in a prompt to start a GUI login screen?

```
sudo /etc/init.d/gdm start
```

Did this in the terminal and the terminal saids:


* Starting GNOME Display Manager...                                 [ ok ]

user@user:~$



Is there anything I have to do next?

Any help I could get would be great appreciated.


thank you

---

### Post by taurus on 2007-05-28
Press <Alt>F7 to switch to GUI login screen.

---

### Post by M.Mizery on 2007-05-28
> **taurus said:**
> Press <Alt>F7 to switch to GUI login screen.

<alt>f7 just makes it so I can move my terminal box around. It does not switch to my GUI login screen.

I don't know why it would do this sorry.

Do you have any other suggestions?

---

### Post by taurus on 2007-05-28
Try to reboot your machine and see if it boots into GUI login screen now.

```
sudo shutdown -r now
```

---

### Post by M.Mizery on 2007-05-28
ok I will try this one and let you know how it goes.

---

