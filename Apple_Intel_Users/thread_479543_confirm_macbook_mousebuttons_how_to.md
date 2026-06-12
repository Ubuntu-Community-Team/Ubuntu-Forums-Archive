---
title: "confirm macbook mousebuttons how to"
date: 2007-06-20
forum: Apple Intel Users
---

### Post by kzm. on 2007-06-20
hey i tried the fix for the mouse buttons from:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

but it shows no effects. does anybody has this running and an idea whats going on with me, as i have no idea, what i am actually doing here:

to change lower Enter key = Right Mouse Button, Alt Gr key + lower Enter key = Middle Mouse Button 

```

    sudo sed -i~ 's/KP_Enter/Pointer_Button3, Pointer_Button3, Pointer_Button2, Pointer_Button2/' /etc/X11/xkb/symbols/pc
    gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/enable true 
    gconftool-2 --type bool --set /desktop/gnome/accessibility/keyboard/mousekeys_enable true

```

thanx a lot!

---

### Post by ivesjd on 2007-06-20
I just whiped this code together. It is modified from what I use to suit your needs.
```
 
#makes lower enter key right click.
xmodmap -e 'keycode 108 = Pointer_Button3'
#makes right apple key middle click.
xmodmap -e 'keycode 116 = Pointer_Button2'

```
You will want to put it in a file and then have the file run on startup.
I know its not exactly what you wanted but it should at least help. :)

---

### Post by kzm. on 2007-06-20
thanx a lot. i can live with this perfectly but i am not sure where to put this?

---

### Post by ivesjd on 2007-06-20
I just created a folder in /bin called scripts, then create a file, put the code in the file. Then go to properties then permissions and select the execute box. Then add the file to the startup list. That is in the System drop down menu. System>Administration>Sessions Then just add new. Hope that helps

---

### Post by kzm. on 2007-06-20
awesome! works like a charm!

---

