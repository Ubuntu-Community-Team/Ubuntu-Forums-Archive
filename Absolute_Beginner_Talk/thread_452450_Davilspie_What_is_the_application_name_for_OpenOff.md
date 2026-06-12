---
title: "Davilspie: What is the application_name for OpenOffice?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-23
Ok, for some reason, I can't find how to make a script for any of the OpenOffice applications with application_name.  

I've tried soffice, ooffice, office, calc, and a myriad of other names to try and get OpenOffice to only open on certain workspaces.  Any ideas?

---

### Post by Inxsible on 2007-05-23
Go to Applications --> Office and then right click on the one that you want to create the launcher of. Select Create Launcher on Desktop (or is it Add Launcher to Desktop :-k )
 
After that right click on the newly created launcher and click Properties. One of the tabs (i forget which) shows you the command it uses to launch the application. You can do what you like with it then :)
 
Hope that helps !

---

### Post by lazyart on 2007-05-23
ooffice -base     
ooffice -impress   
ooffice -writer 
ooffice -calc

---

### Post by argie on 2007-05-24
To match OpenOffice in devilspie, I needed to do this.

ooffice.ds:
```
(if
        (matches (application_name) "OpenOffice.org 2.0")
        (begin
                (set_workspace 4)
        )
)

```

oofficesplash.ds:
```

(if
        (matches (application_name) "OpenOffice.org")
        (begin
                (set_workspace 4)
        )
)

```

Apparently, the devilpie application_name isn't obvious. You may have to run devilpie in debug mode to find the stuff you can match against. The README suggests to make a 
test.ds:
```

 (debug)

```

Unfortunately, I don't think you can put a spreadsheet on one workspace and a word processor on another with OO.org . If you are really crazy about this feature and are comfortable with working with Linux, perhaps you should try another window manager. Some (like E17) make stuff like this really simple (point-and-click).

---

