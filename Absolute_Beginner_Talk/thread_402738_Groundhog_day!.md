---
title: "Groundhog day!"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-04-06
Hi

I hope someone can help me here...

Each time I boot my computer I get prompted to enter my login details and password... then it looks as hough things are about to get going until I'm prompted to login once again.  If I enter my details again it goes through the same thing time and time again.  

Until yesterday, prior to a security update, I didn't have to login.  I had set up my computer so that it booted straight into Ubuntu.

Thank you, in advance, for your help.

Mark

---

### Post by justleen on 2007-04-06
is this ubuntu asking for a login, or your system (your BIOS)?

---

### Post by xopher on 2007-04-06
Sure you entered your credentials correctly? If you entered eh. the wrong password, it'll just ask you to login again.
You could try to change the password through a terminal [ctrl+alt+F1, (...F7 to get back)] by issuing: ```
 sudo passwd username
```

Or do you get to the part where it actually starts to login? Then you might wan't to reset your session to fix it.

---

### Post by Norfolk 'n' Good on 2007-04-06
Hi,

Yes it is Ubuntu I am trying to log onto, not the BIOS.  My details are also correct, because when I did do a typo I got the usual red writing, warning me that my username, password or whatever was wrong.  

When I enter my details it looks like it's about to start-up because I get the usual Ubuntu splash screen bar thingy with the little pictures on it including the emerald logo.  It then reverts to a blank screen with a flashing curser, which lasts about 30 - 60 seconds and then once again I am prompted for my username and password.

---

### Post by Spike-X on 2007-04-06
A lot of people are having this issue after that damn update. Here's how I fixed it:

When you get to the login screen, click on Options down the bottom, then select Failsafe Terminal.

Enter the following commands:

```
cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so
```

Then restart. You should be good to go.

---

### Post by Tux Aubrey on 2007-04-06
Sounds like something is causing X to log you out.

This happened to me yesterday after I updated the x-server (or sumth'n).  Apparently the nvidia/xorg ongoing battle is at fault (again!)

Get into recovery mode (from grub), log in and and put these lines in one at a time:

> cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

If  that fails, reinstall the nvidia driver.

Good luck.

(Spike-X beat me!)

---

### Post by Norfolk 'n' Good on 2007-04-06
I'll give that a try and I'll keep you posted... thank you.

---

### Post by justleen on 2007-04-06
you can also trying removing beryl from the autostart (if the Beryl-emerald is the last thing you see being loaded in the splasg screen...)

---

