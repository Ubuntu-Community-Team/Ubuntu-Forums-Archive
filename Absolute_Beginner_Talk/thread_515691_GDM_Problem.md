---
title: "GDM Problem"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Vanish00 on 2007-08-02
I just installed 7.04.  I updated all the system updates, then I notice my monitor resolution was a big.  My monitor is wide screen and wasn't using all the screen.  I tried to figure out how so I go to 
System->(something)->Desktop Effects.  It had me install i think a driver for my nvidia care which is Nvidia GeForce 8600.  I reboot my computer and now I boot up to:

"(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found"

The message also talks about X server ( I know nothing about ).  I must reconfigure GDM properly...but how from the terminal???

I press ok, then i'm sitting at what seems to be the terminal but at full screen.

---

### Post by asmoore82 on 2007-08-02
login with your normal username/passwd and type this command
at the "$" prompt ...
```
~ $ sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by NilsE on 2007-08-02
You are probably in a terminal so enter the following commend and answer the questions.
```
sudo dpkg-reconfigure -phigh xserver-xorg

```
Basically it will ask for your display adapter and screen sizes your display can handle. 

Try Nvidia and if that does not work try NV and if that does not work try Vesa.

You will use the cursor to move around and space to select.

---

### Post by AlexenderReez on 2007-08-02
hm....run this black screen-->


> sudo dpkg-reconfigure -phigh xserver-xorg

> sudo reboot

you should able to login
restart ...install nvidia-glx-new and restricted modules for your kernel...

then in terminal -->

> sudo nvidia-xconfig --add-argb-glx-visuals

> sudo reboot

you should be able to run desktop effect now....how bout give a try compiz fusion :)

---

### Post by Vanish00 on 2007-08-02
Thanks for all the help that did get me back into the visual ubuntu and out of the terminal.

I went to Desktop Effects again but it says I need to enable my nvidia driver.  I got a feeling if I say install driver i'll be going in circles.  Do you have any advice?  Is there another way to enable the nvidia driver?

---

