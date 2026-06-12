---
title: "Shift+Insert on aluminum?"
date: 2010-03-02
forum: Apple Hardware Users
---

### Post by miatawnt2b on 2010-03-02
is there a way to Shift+Insert on the aluminum keyboard?

-J

---

### Post by linuxopjemac on 2010-03-02
what does that combination normally do? paste ?

---

### Post by miatawnt2b on 2010-03-03
yep, shift insert is paste.  I found a work around for me and that is to use minicom as my serial terminal emulation.  Minicom uses the standard terminal key bindings.

-J

---

### Post by linuxopjemac on 2010-03-03
what about CTRL-v ?

---

### Post by miatawnt2b on 2010-03-03
ctrl-v didn't work because of how the gnome clipboard is set up.  I believe there are two clipboard buffers.
-J

---

### Post by linuxopjemac on 2010-03-04
Maybe you can set the "insert" key with xmodmap like here:
[https://www.organicdesign.co.nz/Apple_wireless_keyboard_on_Linux](https://www.organicdesign.co.nz/Apple_wireless_keyboard_on_Linux)

NB I think you have to disable mouseemu or make another key "Insert" if you use mouseemu, otherwise you might have a conflict.

---

### Post by unikuser on 2012-12-18
There are the shortcuts on mac keyboard. 


fn + enter = insert
delete = backspace
fn + delete = delete  
So, 
shift + insert  =   shift + fn + enter

---

