---
title: "editing read-only file"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by firebolt77 on 2006-07-21
hi all...I want to edit some read-only file such as /etc/wvdial.conf, /etc/modem/options for create a connection in the system using a handphone. I've tried it, but it can't save the changes because the files are reas-only.
Can somebody tell me how to edit it?
thx

---

### Post by Paerez on 2006-07-21
you will need admin rights to edit it. Press ALT+F2 to run a command, and type:
```
gksudo gedit
```
this will give you an admin editor, then you can open the files you want and change them.

---

### Post by Arisna on 2006-07-21
You have to edit them with administrative permissions by using the "sudo" program.  I suggest opening a terminal (Applications > Accessories > Terminal) and typing the following:

```
sudo nano /etc/wvdial.conf
```

Then pressing enter.  You'll have to enter your password, and then you'll be able to edit the file.  Navigate with arrow keys and save with Ctrl-o.

I suggest that command in lieu of the prettier, graphical command `gksudo gedit /etc/wvdial.conf' because a lot of people seem to have problems launching gedit as administrator.

EDIT:  Yeah, beaten again. :) Try the above suggestion first, and use this as a fallback.

---

### Post by Paerez on 2006-07-21
heheh, if you want to answer the easy posts you gotta be fast, cause everyone goes for them :D

@firebolt77:
My way is the gui way, but arisnas will work in a terminal if you ever loose your gui (god forbid).

Both methods are correct.

---

### Post by SilverDragon on 2007-07-30
I tried this method but it does not work for me :-(
I believe the reason is because the file is on a separate hard drive?

 I did <sudo nano "file name">

I can't open the file using <gksudo gedit> because it only shows the root's desktop,  and network servers.

edit: I can save the file on my desktop and its not read-only anymore? I'm not sure if this how its intended to work so other ideas are still welcome :-)

---

### Post by NT4usB on 2007-07-30
Is the separate HD formatted NTFS?

---

