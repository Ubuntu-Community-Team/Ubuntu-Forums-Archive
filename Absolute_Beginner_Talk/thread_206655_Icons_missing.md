---
title: "Icons missing"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by enyaw on 2006-06-30
The shut down and the restart icons are missing from the drop down menu.  Has this happened before with dapper?  

Thanks in advance:)

---

### Post by mscman on 2006-06-30
Are only the icons missing or are the actual entries gone?  Have you installed some other icon theme?  A lot of icon themes aren't complete and are missing certain icons.

---

### Post by kigina on 2006-06-30
right click, add to panel.  see if shutdown icon is in there and add it to the panel.

---

### Post by mscman on 2006-06-30
[QUOTE=kigina]right click, add to panel.  see if shutdown icon is in there and add it to the panel.[/QUOTE]
He mentioned that the icons from the dropdown menu were gone, not the panel buttons.

---

### Post by kigina on 2006-06-30
and what does "the drop down menu" mean? the top panel? if so then what i said could be a solution.

---

### Post by Eddie Wilson on 2006-06-30
This can also happen sometimes with apps when you update Dapper and nobody seems to know why. I've even had them change. Still a little buggy but workable.

---

### Post by enyaw on 2006-06-30
[QUOTE=mscman]Are only the icons missing or are the actual entries gone?  Have you installed some other icon theme?  A lot of icon themes aren't complete and are missing certain icons.[/QUOTE]

Thank you for responce:

I have not installed an additional theme  When I click on the red power button the drop down menu does not show entries icons nor entries for shut down or restart.

---

### Post by enyaw on 2006-06-30
[QUOTE=kigina]right click, add to panel.  see if shutdown icon is in there and add it to the panel.[/QUOTE]

Did as you suggested.  No luck. The red quit button was there but no Shut Down or Restart.:)

---

### Post by enyaw on 2006-06-30
[QUOTE=Eddie Wilson]This can also happen sometimes with apps when you update Dapper and nobody seems to know why. I've even had them change. Still a little buggy but workable.[/QUOTE]

I'm OK with changes, but without the shut down and restart icons in the drop down panel I need to use the on_off button of the computer to shut down the computer:roll:

---

### Post by mscman on 2006-06-30
[QUOTE=kigina]and what does "the drop down menu" mean? the top panel? if so then what i said could be a solution.[/QUOTE]
I wasn't trying to say you were wrong, I simply interpreted the OP's request as referring to the System menu (that's what I think of as "Drop Down", not the panel which on my machine is always there...)  That is a viable solution, unfortunately it didn't seem to work in this case. :( 

@ enyaw:
Can you try logging off/shutting down by clicking on the system menu on the panel and selecting "Quit..."?

If that doesn't work, you may try reinstalling the gnome-panel by running:
```
sudo aptitude reinstall gnome-panel gnome-panel-data
```

**NOTE** Feel free to replace aptitude with apt-get.  I'm using aptitude since it does a much better job of tracking dependencies.

---

### Post by enyaw on 2006-06-30
[QUOTE=mscman]I wasn't trying to say you were wrong, I simply interpreted the OP's request as referring to the System menu (that's what I think of as "Drop Down", not the panel which on my machine is always there...)  That is a viable solution, unfortunately it didn't seem to work in this case. :( 

@ enyaw:
Can you try logging off/shutting down by clicking on the system menu on the panel and selecting "Quit..."?

If that doesn't work, you may try reinstalling the gnome-panel by running:
```
sudo aptitude reinstall gnome-panel gnome-panel-data
```

**NOTE** Feel free to replace aptitude with apt-get.  I'm using aptitude since it does a much better job of tracking dependencies.[/QUOTE]

Great help here...Thanks:D 

I did as you suggested and I get the same display as with the panel quit icon; no restart or shut down icon.

I'll try the re_install  and get back to the post as soon as possible.

Thanks:D

---

### Post by enyaw on 2006-06-30
[QUOTE=mscman]I wasn't trying to say you were wrong, I simply interpreted the OP's request as referring to the System menu (that's what I think of as "Drop Down", not the panel which on my machine is always there...)  That is a viable solution, unfortunately it didn't seem to work in this case. :( 

@ enyaw:
Can you try logging off/shutting down by clicking on the system menu on the panel and selecting "Quit..."?

If that doesn't work, you may try reinstalling the gnome-panel by running:
```
sudo aptitude reinstall gnome-panel gnome-panel-data
```

**NOTE** Feel free to replace aptitude with apt-get.  I'm using aptitude since it does a much better job of tracking dependencies.:o 

Thanks for your help:) 

I did the reinstall and received no complaints' or direction to a reboot.  There is no change no restart or shut down. O:)

---

