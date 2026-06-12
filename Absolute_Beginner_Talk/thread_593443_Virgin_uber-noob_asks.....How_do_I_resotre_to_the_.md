---
title: "Virgin uber-noob asks.....How do I resotre to the default desktop?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by JedMeister on 2007-10-27
Ok people.....firstly I'd like to declare that I am **THE** Ubuntu uber-noob! I consider myself fairly good with XP, with well above average knowledge but I am a bit lost with Ubuntu (steep learning curve)! I've just installed 7.10 Xubuntu on an old Compaq Armada 1500c (Intel Celery 366Mhz with 128MB RAM and 4GB HDD). Please skip down to the bold if you can't be bothered reading the history, otherwise please read on.......

 I had my 2nd PC (AMD 3200+ 1GB RAM 250GB HDD) running off the 6.10 Ubuntu LiveCD for a little while (just for web surfing and played some of the simple games) until I got around to installing XP on it, but never jumped over the edge into the Ubuntu/Linux world. I was going to have a go at installing it (6.10) on my Main PC (4400+ 2GB RAM and 2x 320GB HDD) but the ethernet ports wouldn't work out-of-the-box and I was too lazy at the time to bother! 

This time is different because the lappy struggled to run nicely with win98, so I figured I had nothing to loose. And if I can get my head around it, I'll probably try again with my main PC. So I've done a clean install (had to leave the BIOS partition intact) and although the install took forever and it boots up much slower than win98 (I'm sure there's tweaks to speed that up so if you've got any off the top of your head they'd be appreciated too!). Other than that it runs like a treat (after I got the ethernet card working). Its so much more responsive than win98! I've blundered around and now it finds the ethernet card on boot. During that learning curve I found the terminal window, the sudo command and other fun stuff. I've edited my grub file (menu.lst) and now it finds the ethernet card every boot, which I'm pretty proud of! (Even though it was pretty simple in the end)

**.....anyway enough history and background - to the problem at hand.......**

After I got it all functional (well I still haven't got sound but that can wait for now) I started playing around with the desktop. I shuffled stuff about and changed options wildly.....until I noticed I had none of the bars (top and bottom by default) that appear to be called 'panels' in Ubuntu ('task bar' - windows speak). Now I can make new ones, but then I have to put all the stuff, like time, shutdown switch etc back on. I was wondering if there is a really simple way of just putting them back the way they were at install? Then perhaps I could play around (a little more sensibly). I tried logging in a default session (I think it said 'Default Xfe' or something similar) but it came back to the desktop with no 'panels' (thats the right term eh?). I was almost going to just reinstall but it took forever the first time! I'm guessing there is some simple way of doing it but I can't for the life of me find it (either on Xubuntu or the net).

---

### Post by tehet on 2007-10-27
All changes to your personal environment go into hidden files in your home directory. Simply removing them gives you back the defaults. In your case it'll probably be something like ~/.xfce ('~' = your home, '.' makes a dir hidden, 'xfce' holds the config files) but I've never used XFCE so it might be called something slightly different.

---

### Post by ed-koala on 2007-10-27
Also, the keyboard shortcut ALT + F1 should show panels.

---

### Post by JedMeister on 2007-10-27
Wow, thats a fast reply! Thanks heaps for that...I'll just fire it up and have a go at those suggestions:grin: I'll let you know how I go.

---

### Post by mali2297 on 2007-10-27
> **tehet said:**
> All changes to your personal environment go into hidden files in your home directory. Simply removing them gives you back the defaults. In your case it'll probably be something like ~/.xfce ('~' = your home, '.' makes a dir hidden, 'xfce' holds the config files) but I've never used XFCE so it might be called something slightly different.

In Xfce, the configuration files are hidden in **.config** . 
There is an option to show hidden files/directories in the file manager.

---

### Post by JedMeister on 2007-10-27
Thanks everyone,

Yeah I found the folder xfce4 and xfce4-session in the ~/.config folder and deleted them both. I then rebooted and the panels remained unchanged. I was thinking perhaps does it save the current settings as it shuts down? Perhaps I need to log on to the recovery terminal to do this to make it stick? Or perhaps it backs up the current settings somewhere? (thats what I thought xfce4-session may have been).

I'll play some more.....thanks again for everyones input.

---

### Post by proalan on 2007-10-27
You could try creating a new user account. This usually creates a new account with default settings. 

And If your happy you can delete the old account.

---

### Post by mali2297 on 2007-10-27
> **JedMeister said:**
> Thanks everyone,

Yeah I found the folder xfce4 and xfce4-session in the ~/.config folder and deleted them both. I then rebooted and the panels remained unchanged. I was thinking perhaps does it save the current settings as it shuts down? Perhaps I need to log on to the recovery terminal to do this to make it stick? Or perhaps it backs up the current settings somewhere? (thats what I thought xfce4-session may have been).

I'll play some more.....thanks again for everyones input.

When you shut down through the xfce menu there should be an option to save the session or not. If you don't have that, reboot through the terminal instead:
```

sudo reboot

```

EDIT: Also, remove the directory **.cache** . I don't think it will do any difference but just as well.

---

### Post by JedMeister on 2007-10-29
Ok, thanks very much for your replys, they are muchly appreciated! I still haven't done it yet, been too busy working to 'play' on the old clunker. But I just wanted to acknowledge the input! :) I should get onto it over the next day or two and let you know how I go.

---

