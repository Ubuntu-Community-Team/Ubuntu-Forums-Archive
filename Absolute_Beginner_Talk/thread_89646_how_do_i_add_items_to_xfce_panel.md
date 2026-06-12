---
title: "how do i add items to xfce panel?"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-11-13
i want to add firefox and thunderbird. firefox was on there, but the icon opened up 1.0.7, but i need one for 1.5rc1 (i removed the 1.0.7). when i right click on the panel and click 'add new item', then click launcher, i don't get an option to add the two i mentioned above.

---

### Post by Xian on 2005-11-13
You should have been able to just edit the command issued instead of removing the shortcut. I have to do that with Gimp when there are major version upgrades. I think the command right now is gimp-2.2 or something, but in any case you get the idea. When you add a new launcher to the panel it should present you with a default shortcut that you can then customize with command, icon, parameters, and so forth. This is all done with a simple right-click. Do you not see that on your box?

---

### Post by fuscia on 2005-11-13
[QUOTE=Xian]When you add a new launcher to the panel it should present you with a default shortcut that you can then customize with command, icon, parameters, and so forth. This is all done with a simple right-click. Do you not see that on your box?[/QUOTE]

i do see that, but i have no idea about what to put in those boxes. i, pretty much, don't know what i'm doing.

---

### Post by Xian on 2005-11-13
Sure, that's fine. Only I don't use FF or Tbird so I can't tell you what the command is for those apps. Can someone help out with this?? If you will just right-click on some of the default launchers that are associated with installed programs, and look at that format, then really all you have to do is duplicate it with your custom launcher, save that the command will be obviously different and you may want to choose a different icon.

---

### Post by Xian on 2005-11-13
Okay, I looked it up. 
For Firefox the command you want is:
firefox %u

For Thunderbird it is:
mozilla-thunderbird

---

### Post by aysiu on 2005-11-13
My guess is that, depending on how you installed 1.5, *firefox* as a command won't open the one you want. You should specify the direct path. For example, if you installed Firefox 1.5 to your home directory, the command might look like ```
~/home/username/firefox/firefox
```

---

### Post by padu on 2007-11-28
This proposed solutions are to open a launcher menu but as I understand the question is how to add an icon direct under the firefox one to reach an app in one click... I am also trying this since some hours. Launcher is nice but needs 2 clicks...
Thanks in advance for some advice...
Padu

---

