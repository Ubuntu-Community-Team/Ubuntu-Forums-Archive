---
title: "Google Earth"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Johnged on 2007-07-05
Hi,
     I am a first time user, I am running Linux 7.04, I have downloaded Google Earth,and have an icon for it on my desktop, can anyone please explain how to open it and run the application, just need to know what to type and where to type it,
                                                                                       Many Thanks, Johnged.

---

### Post by scragar on 2007-07-05
ifyou have the .bin file then open the terminal and type:


```
cd ~/Desktop
sudo chmod ogu+x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

entering your password when prompted, then follow the steps as google provides.

---

### Post by Johnged on 2007-07-05
Did this and seemed to work up until I was asked for my password, I have tried all the passwords I
have used as far as Linux goes and have been told wrong, which password to use?

---

### Post by scragar on 2007-07-05
you should use the same password you log in with if you have admin access, if you don't then proberly going to have to ask whoever owns the computer(has admin access to enter if for you).

if you need some-elses password then change the steps to:

```
cd ~/Desktop
su _Admins username here_
chmod ogu+x GoogleEarthLinux.bin
./GoogleEarthLinux.bin
```

---

### Post by bsawler on 2007-07-05
Go to Applications > Internet > Google Earth.

If you have an intel video and your driver is set to "vesa", you may need to change this to "i810" to run Google Earth.

---

### Post by Johnged on 2007-07-05
> **bsawler said:**
> Go to Applications > Internet > Google Earth.

If you have an intel video and your driver is set to "vesa", you may need to change this to "i810" to run Google Earth.

I Am not having any luck here, I have check. password is correct but no go, will check on video card
 asap.

---

### Post by chemtut on 2007-07-05
right click icon
in new window click permissions
click box  make file executable
close window
double click icon--------------worked for me

---

### Post by Johnged on 2007-07-05
Thankyou All, I have finally opened Google Earth, looks a bit pale though and I think I will now have to find my video card and see if it can be upgraded, also try to set display properties to a greater 
setting.

---

### Post by Drakkor on 2007-07-05
I also have Applications>Internet>Google Earth

---

### Post by bobbyy on 2007-07-06
> **bsawler said:**
> Go to Applications > Internet > Google Earth.

If you have an intel video and your driver is set to "vesa", you may need to change this to "i810" to run Google Earth.

How to set intel video driver to vesa, pls help me.:popcorn:

---

### Post by Nezing on 2007-07-06
Just installed Google Earth,and "flew" to my road,via Vladivostok!!  :D

---

