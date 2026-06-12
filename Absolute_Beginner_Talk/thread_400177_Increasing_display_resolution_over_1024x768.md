---
title: "Increasing display resolution over 1024x768"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-03
Hello,

I've recently installed ubuntu. You know, I'm gnome fan and I knew gnome long before installing linux, I liked it very much. Now, after installation I found that everything's bigger, larger than I expected: icons, text letters, window thickness.. 

My laptop has 15' display with 4:3 proportions, so the default resolution is 1024x768. And when I check it here, it's 1024x768 too. So, theoretically it would be ideal to have higher resolution like 1400 x 1050 as an option - then everything would get smaller and thinner. but the biggest resolution as an option is 1024x768. how can I still set 1400 x 1050?

---

### Post by mikeyphi on 2007-04-03
Have a look under SYSTEM - PREFERENCES - SCREEN RESOLUTION  and see if the higher resolution is available for selection.

---

### Post by taurus on 2007-04-03
Have you installed a driver for your graphic card?

---

### Post by O-pos on 2007-04-03
in System>preferences>resolution the maximum resolution is 1024x768. I haven't installed any driver extra, I just installed ubuntu linux and nothing more. It works by itself now. (However, I think I will need certain drivers, like wireless, because I couldn't bring it to work)

---

### Post by renzokuken on 2007-04-03
well assuming that your grafix card/chipset supports 1400x1050 you could simply add it to your xorg.conf

```
 sudo gedit /etc/X11/xorg.conf
```

and add them to the section at the bottom, it is fairly self explanatory when you see the file

---

### Post by O-pos on 2007-04-03
Wow, I't so flexible!! :)

OK, I did what I tokd you and I have one more question:

what entry should I make for "depth"? last highest one? (24)

And after I enter everything, what should I click? I don't see anything to click "ready", "finish", nothing.. should I just close it?

---

### Post by taurus on 2007-04-03
Use 24 and please use gksudo when you use gedit.

```
gksudo gedit /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by O-pos on 2007-04-03
I did it and I saved the file in file>save. but then I turned back to preferences and there's still nothing more than 1024x768.

Should I restart ubuntu?

---

### Post by compmodder26 on 2007-04-03
You need to restart the xserver.  Quick and dirty method is to use Ctrl+Alt+Backspace key combo.

---

### Post by O-pos on 2007-04-03
xserver? what is that? I restarted ubuntu, but it's still the same: maximal resolution appears 1024x768. maybe I should change depth?

---

### Post by taurus on 2007-04-03
Maybe you should install a driver for your graphic first to see if you can change the resolution then.  What graphic card do you have on that laptop?

---

### Post by arbulus on 2007-04-03
The Xserver is what manages windows on your system.  It's what tells the basic shell how to translate what it does in to a windowed format.  Gnome, KDE, Fluxbox, etc. sit on top of that to manage how your windows and other GUI environment pieces appear on the screen.  So if you make a change to the Xorg.conf file, you will need to restart the Xserver to apply the changes that you made.  Rebooting of course will work, but I think someone mentioned before Ctrl+Alt+Del will restart X without having to reboot.  It'll give you a black screen for a few seconds and then take you back to your login screen.

---

