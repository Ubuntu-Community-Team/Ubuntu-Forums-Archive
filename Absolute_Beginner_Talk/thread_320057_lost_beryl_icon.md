---
title: "lost beryl icon"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by mells on 2006-12-16
how good is beryl! love it.

however, being a donkey I have deleted the red icon at the top of the screen.

Anyone know how to get it back? 

I've done the right click > add to panel > application launcher route but its only an icon not an icon I can mess with settings etc.

---

### Post by jvc26 on 2006-12-16
Do you mean the red crystal at the top right? (next to the clock?) thats showing that beryl manager is running. It could be just that you closed the manager? In which case:

```

$ beryl beryl-manager

```

in Terminal should bring it back.

Il

---

### Post by mells on 2006-12-16
tried that. beryl is running still but no icon. 

tried rebooting but its not there. :-?

---

### Post by jvc26 on 2006-12-16
Have you got both beryl and beryl-manager in your startup programs?

Go to:
<System><Preferences><Sessions><Startup Programs>
and add:
beryl 
beryl-manager
to the list... Perhaps they're both not there at boot?
If they're both there not sure!

Il

---

### Post by xpod on 2006-12-16
Eeee awww:D 

Another donkey here who did the exact same thing earlier thinking it was something else i was deleting from the panel..

Although i done the "add to panel>custom launcher" thing with the icon from usr\share\pimaps.
Works ok though even if it does work in a slightly different way

---

### Post by mells on 2006-12-16
thanks for your help, just added beryl into the startup but its not appeared when the system has come up. even though the splash screen appears and beryl works fine etc.

---

### Post by jvc26 on 2006-12-16
did you add the beryl-manager too? If so I'm afraid I dont know whats happening, but the symbol which appears in the top right is the beryl-manager running, but otherwise can't think of any other ideas sorry bout that!
Il

---

### Post by mells on 2006-12-16
yup beryl-manager is in the start up, cant figure it out either I'll have to have a play in the morning..

---

### Post by jvc26 on 2006-12-16
Just one other thing... how did you manage to delete it? When you right click the icon it comes up with a drop-down menu with no delete option aside from 'quit' which merely shuts it?
Il

---

### Post by STREETURCHINE on 2006-12-16
go to preferences>beryl manager right click and the click on add launcher to panel,
you will see a new icon on the top panel right click on icon and choose propeties.
then on the drop down screen you will see a no icon button hit this button choose the beryl icon and you are done

---

### Post by mells on 2006-12-16
sorted it! Sorry if I was being dense Illuvator this is how I fixed it:

[IMG]http://i25.photobucket.com/albums/c77/cmelia/berylscreenshot.png[/IMG]

---

### Post by mells on 2006-12-16
> **Illuvator said:**
> Just one other thing... how did you manage to delete it? When you right click the icon it comes up with a drop-down menu with no delete option aside from 'quit' which merely shuts it?
Il

right click on the red icon and click remove from panel, not recommended!

---

### Post by jvc26 on 2006-12-16
lol - no worries mate good to see you recovered it!
Il

---

