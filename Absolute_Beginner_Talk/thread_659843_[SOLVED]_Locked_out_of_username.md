---
title: "[SOLVED] Locked out of username"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-06
I have been locked out of Ubuntu due to the massive Title bar/Login Screen problem i know how to fix it but i cant get into it to do so!! ([http://ubuntuforums.org/showthread.php?t=583915&highlight=Login+screen+font&page=2](http://ubuntuforums.org/showthread.php?t=583915&highlight=Login+screen+font&page=2))

It is because i changed the login screen to plain and it is now so big i cant get down to the login box. any suggestions?

---

### Post by adam.tropics on 2008-01-06
If you are referring to the fix at the end of post 13 on that page, reboot into recovery mode, and you will end up at a root command promt. From there enter 'nano /etc/gdm/gdm.conf', make your edits, then <CTRL>o, <enter>, <CTRL>x, enter....all done! Reboot.

---

### Post by Fraser from Scotland on 2008-01-06
i booted into recovery mode but it just comes up at the same massive screen 
:S

---

### Post by Fraser from Scotland on 2008-01-06
aww crap, it might be because the last time i botted into recovery mode i entered "startx" so i got some graphics.

---

### Post by adam.tropics on 2008-01-06
ok, well can you not <ctrl><alt>F1 and login and edit the file from there then? (again...no X)

---

### Post by Fraser from Scotland on 2008-01-06
i will try that just now, thanks. :)

---

### Post by Fraser from Scotland on 2008-01-06
ok it worked and im back into ubuntu, thanks alot! :D. But, i need to change the login screen options and i dont remember how to do it :S can you help?

---

### Post by adam.tropics on 2008-01-06
System-->Administration-->Login Window for the graphical version. Will need to enter your password. Or the non graphical version is actually on the post you linked to.

---

### Post by adam.tropics on 2008-01-06
Hang on did you mean you're back in gnome? or logged in without gnome?

---

### Post by Fraser from Scotland on 2008-01-06
hmmm i went to system>administration but Login Window isnt there :S and i don't know what the non graphical version is or how to do it, sorry im totally new.

---

### Post by adam.tropics on 2008-01-06
Well this isn't my fix, it's the 'permanent' fix directly from the site you linked, but the steps are:
```

1. sudo gedit /etc/gdm/gdm.conf (<--from terminal)
2. find the section [server-Standard] in that file
3. You should see a line that says "-command=/usr/bin/X -br -audit 0". Change it to read "-command=/usr/bin/X -br -audit 0 -dpi 96".
4. Save, quit, and restart
```

Give that a bash!

---

### Post by Fraser from Scotland on 2008-01-06
I'm logged back in with GNOME.
here is a screenshot cause im not 100% sure. [http://img508.imageshack.us/img508/332/screenshotpv6.png](http://img508.imageshack.us/img508/332/screenshotpv6.png)

---

### Post by adam.tropics on 2008-01-06
Try system-->preferences-->Main Menu. I am not sure why Login window isn't there, but you should be able to enable it from  Main menu preferences. It has a fairly intuitive interface, just find and check the appropriate box. Check attached screenie.

---

### Post by Fraser from Scotland on 2008-01-06
i did the changes but when i press the power button to bring up the box of thngs to do like shut down and stuff, it says "Action forbidden Policy timeout is not valid."

---

### Post by Fraser from Scotland on 2008-01-06
Login Window isnt even in the menu checker thing. Ill try manually rebooting it.

---

