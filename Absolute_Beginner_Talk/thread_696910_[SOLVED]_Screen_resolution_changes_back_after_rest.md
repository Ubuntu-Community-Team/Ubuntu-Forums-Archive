---
title: "[SOLVED] Screen resolution changes back after restart"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by jonatan5 on 2008-02-14
I know that there is already one question just like this,_ but I do not understand witch line I must change in xorg.conf file_. There are lists of* lines with all possible resolutions, but there is none, with Default* written or something.
Should I just delete all resolutions what I do not want.
Ok, I guess then I would have a black screen after next restart.
__________________
specs 
Radeon 9250
monitor Philips Magnavox 
Resolution 1024x760  75Hz   Settings are set in,, screens and graphics', but changes back after restart.

---

### Post by Rocket2DMn on 2008-02-14
Modifying xorg.conf manually can be dangerous, and just usually doesn't work.  First, let's try the automatic way to reconfigure X:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Then do CTRL+ALT+BACKSPACE to restart X (make sure everything is saved and close since this will restart your GUI).

If that fails to give you the correct screen resolution (or option to select it from System->Preferences->Screen Resolution), then you should reconfigure X using this tutorial (which will have you run the command without phigh and will ask you hardware questions): [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
There is no "default" for xorg screen resolutions.

---

### Post by jonatan5 on 2008-02-16
It is all set, only Screen resolution changes back after restart.

---

### Post by Rocket2DMn on 2008-02-16
I've seen people have trouble with the 9250 before, I don't even remember if we ever got it right.  However, we shall keep trying.  Can you please post your xorg.conf file?
```
cat /etc/X11/xorg.conf
```
Also, did you every try to install the restricted drivers (you shouldn't have, they won't work.)?  If so, we're going to have to make sure we remove them.

---

### Post by jonatan5 on 2008-02-20
Stupid mistake from mine side. I missed, that under system, is resolution setting, where you must mark default settings. I only saw Screens and Graphics.

---

### Post by Rocket2DMn on 2008-02-20
So do you have it working properly now?

---

### Post by jonatan5 on 2008-03-02
Yea it works well

---

