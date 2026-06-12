---
title: "Login scripting problem"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Leed on 2006-11-15
After hours of searching and trying out I'm still stuck with a rather embarrassing problem.

All I want to do is set up some commands, that shall be carried out upon logon. The only solutions I found in the Forums was the use of shell scripts or the startup list in System->Preferences->Sessions. 

The problem is, these problems both require admin rights, i.e. the usage of the sudo command. Upon adding them to the login sessions nothing happens, not even a prompt for entering the sudo password. The programs I'm trying to start up are wpa_supplicant and 3ddesk... I can hardly believe nobody else has this problem... makes me feel really stupid. :-k 

Can please someone tell me how to launch these programs on login, I don't feel like typing it every time in the console.

---

### Post by po0f on 2006-11-15
Leed,

Do you need this commands started upon *login* or *boot*?  If the latter, [this](http://ubuntuforums.org/archive/index.php/t-6963.html) was a hit I got off google.

---

### Post by Leed on 2006-11-16
Thx po0f

Worked fine with wpa_supplicant, 3ddesk however still doesn't start, guess it needs the UI booted up and must run on login.

I got the impression the program itself runs, but stops as soon as the system wants to access the graphics function. 

Hope someone knows a way to get 3ddesk running on boot

cheers
Dave

---

### Post by Leed on 2006-11-16
Yay, finally got it

created a file called "default" in 

/etc/X11/gdm/PostLogin

and filled it up with the code

```
#!/bin/sh
/usr/bin/3ddeskd --acquire 30

```

---

