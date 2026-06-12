---
title: "switching identities"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Thymen on 2005-11-19
Hi folks;

been using RedHat on and off, and now installed Ubuntu. Looks great!

Dowloaded updated driver for my video card, opened terminal and typed "sh - name of package-"

However... it requires root privileges to install... and if I try to switch Identities using 'su', the password I supply return a message that autentication failed.

Dusing installation I supplied only one name and password..(being not root/pwd). Now how do I switch id to root?

Thnx,

Thymen

---

### Post by invalid on 2005-11-19
```
sudo sh file
```
or you can
```
sudo su
```

Cheers,
Cb

---

### Post by Thymen on 2005-11-19
Apologies first... I should have searched the forum first...

Understand that standard root is not available as in other Linuxes, and that I need to use sudo.

But... when I want to install the driver I downloaded from Nvidia, then key in:

sudo sh < name of package>, it says I need to quit X Server to be able to install. So I logged out, and in again in a failsafe terminal session. Still get the same message......

I assume I need to explicitly exit the Xserver.... how do I do that? Other people here who installed new video drivers from Nvidia?

Thymen

---

### Post by invalid on 2005-11-19
You can make the "normal root" available if you really need to, with
```
sudo passwd root
```

As far as the nvidia drivers, I might suggest the ubuntu packaged drivers, which make the process a whole lot simpler.
```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```and then restart X by ctl-alt-backspace.

If you still need prefer to use the ones from nvidia directly, you can kill Xserver by
```
sudo killall Xorg
```

Cheers,
Cb

---

### Post by Thymen on 2005-11-19
Thanks, it worked.

However, the standard Ubuntu drivers allow my video card to run at 60Hz only, and I would like to have it run at 85 Hz - less screen flickering.

I will forget about installing the drivers I donwloaded from Nvidia, for it requires me to re-compile part of the kernel - and that is just a little bit too much asked from a newbie.

My card is a simple GForce MX, with 32 MB or RAM. I will search this forum a bit more thoroughfully for more info, but if anyone here recognizes my problem, and knows a solution, please respond!

Edit:

I edited the Xorg.conf file, and removed the super hires modes (1600 x 1200) from the screen profiles. Now everything appears to be ok: I can select 85 Hz refresh rate, and also at startup I get a proper resolution login screen.

I like this forum.

Thymen

---

### Post by MichaelM on 2005-11-19
For future reference: [HOWTO: Latest NVIDIA drivers]("http://www.ubuntuforums.org/showthread.php?t=75074").

---

