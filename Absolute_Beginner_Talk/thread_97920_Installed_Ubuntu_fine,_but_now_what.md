---
title: "Installed Ubuntu fine, but now what?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by JoeMittler on 2005-12-01
Hello,
I have used linux before (RH 8.1 to be exact) the install was gui based and I got it working on a dual boot machine (one hdd) with xp. 
Now I have a laptop and verison 5.0.4 of Ubuntu. I installed it. But it brings me to the command line. 
Im taking linux in college, but atm we are just doing the simple stuff like whoami, the vi editor, grep, and file and directory management. 

Is there something more I have to install? 
Or just a simple command that I have to enter to get to the "gui" version of Ubuntu, as I am not sure if it even has one. :confused: 
So yea any help would be greatly appreciated :smile:

---

### Post by aysiu on 2005-12-01
startx

---

### Post by akiro.yamamoto on 2005-12-01
If your having errors when starting the Xsever (Window Manager).
You can try : 'dexconf' without the quotes
To auto configure the Xserver configuration file and possible correct any missed or mis-configured video system hardware with basic ones that should work on most systems..
Regards

---

### Post by JoeMittler on 2005-12-02
I rebooted my laptop selected Ubuntu Linux (v5.0.4) and logged in using the username and password I created during the setup. I typed startx and I got something similair to this: "the command: startx doesn't exist". 
Is there something im still missing?
Would an upgrade to v5.10 fix this problem?

---

### Post by aysiu on 2005-12-02
You must have done a server install or an expert install.
Try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by vasudevank on 2005-12-31
that is probably right

---

