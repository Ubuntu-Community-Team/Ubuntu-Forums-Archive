---
title: "Stuck in brown splash screen"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by rspear on 2008-03-19
new install today. i can login successfully but then it takes me a to a blank brown screen that i have turn the power off in order to get out.

What am i doing wrong? Like i said, it is a brand new install so i should need to type a bunch of code at the command line, right?

---

### Post by cdaringe on 2008-03-19
what version are you installing?
if you get to the graphical logon screen id assume gdm is running successfully...

i'm not pro, but id say to at least get you started, lets see if its gnome that is the problem or not.  trying installing xfce real quick. 

if you have a broadband connection and your networking is properly configured, do at Ctrl+Alt+F2 (or F3 or F4..) at the login screen

login using your info

then run ```
sudo apt-get install xubuntu-desktop
```

when its done, we need to restart gdm

```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

if it doesn't automatically bring you back to the login screen, hit ctrl+alt+F7

under session, choose xfce.  then logon!

---

### Post by rspear on 2008-03-19
i can't download anything as my operating system is not working.

when i hit ctrl+alt+f1 it takes me to the command line where it asks for the login; I enter it successful and then i am unable to type anything when it asks for a password.

I am however able to enter login and password at the normal GUI.

I have wasted alot of time on this. Can you suggest next best linux operating system for me?

thanks,

---

### Post by FuturePilot on 2008-03-19
When you go to type your password it is accepting the input, however you don't get any feedback from the command line.
[http://www.psychocats.net/ubuntu/passwordinterminal]("http://www.psychocats.net/ubuntu/passwordinterminal")

If this is a fresh install, it might be corrupted for some reason like because of a bad CD or something.

---

