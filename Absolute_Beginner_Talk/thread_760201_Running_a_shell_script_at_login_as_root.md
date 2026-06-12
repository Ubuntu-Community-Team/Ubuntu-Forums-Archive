---
title: "Running a shell script at login as root"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by DavidFromCanada on 2008-04-19
Ok I'm overclocking my downclocked Asus Eee PC. It requires a shell script (.sh file) to overclock the front side bus. It works perfect and I've tested it by running glxgears overnight without a crash. I want to do one of two options. The only problem is that I have to run it as sudo in terminal manually

1. I want to run the script on login not on boot, because if something does go wrong I want to be able to go to a failsafe session. 

2. Create a way to be able to turn the script on or off using a launcher or key command (fn-f6). Kind of like the compiz-switch program if you've heard of it.

Any help is appreciated. 

The script is 
```
sudo sh -c 'echo 85 24 1 > /proc/eee/fsb'
sudo sh -c 'echo 100 24 1 > /proc/eee/fsb'
echo "FSB overclocked to 100MHz"

```

---

### Post by PinkFloyd102489 on 2008-04-19
To run at login, make a new entry in System > Preferences > Sessions.

---

### Post by DavidFromCanada on 2008-04-20
Sorry I didn't mention I'm using xubuntu

---

### Post by aktiwers on 2008-04-20
Put the script in our  /etc/rc.local
After the comments (at the very bottom), then it will run as root on bootup

Edit: Sorry didnt see the "not on bootup" part..  I'm pretty sure rc.local is loaded on bootup.

---

