---
title: "need to know how to create a file to disable XGL"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Evil Wayz on 2007-11-08
* Add a killswitch to disable Xgl on a per-user basis. If the file
    ~/.config/xserver-xgl/disable exists, Xgl will not be automatically
    started.

I need to know how to do the above to turn xgl off i am pretty sure thats why my gnome terminal doesn't work.

---

### Post by xyphur on 2007-11-08
Hit Ctrl+Alt+F1, login, and type the following:

touch /.config/xserver-xgl/disable

reboot, and things should be in order. This only takes effect for the user you log in as under the tty1 console. To re-enable XGL, replace 'touch' with 'rm' in the above example.

The tilde (~) character represents your home directory, so ~/.config would be /home/your_user_name/.config - just for future reference.

---

### Post by Evil Wayz on 2007-11-08
w00t! finally an answer to one of my posts!

---

### Post by Evil Wayz on 2007-11-08
says canot touch, no such file or directory

---

### Post by jordanmthomas on 2007-11-08
That means you don't have the folder xsever-xgl.  Do this to get the file there:
```
mkdir ~/.config/
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
```
If the first mkdir give you an error (it probably should), just ignore it and continue on.

---

### Post by Evil Wayz on 2007-11-08
Success! I guess i will leave ati config and dual head alone til they fix it to where fools armed with a little knowledge can mes with it without a total fuxxor occuriing. Many thanks.

---

### Post by eeclark on 2007-12-02
> **xyphur said:**
> Hit Ctrl+Alt+F1, login, and type the following:

touch /.config/xserver-xgl/disable

reboot, and things should be in order. This only takes effect for the user you log in as under the tty1 console. To re-enable XGL, replace 'touch' with 'rm' in the above example.

The tilde (~) character represents your home directory, so ~/.config would be /home/your_user_name/.config - just for future reference.

Should be 
```

touch ~/.config/xserver-xgl/disable

```

You missed the tilda (~) which indicates the home directory of the current user.

---

### Post by xyphur on 2007-12-02
> **eeclark said:**
> Should be 
```

touch ~/.config/xserver-xgl/disable

```

You missed the tilda (~) which indicates the home directory of the current user.

Good catch

...I guess proofreading my posts would help, eh? ;)

---

### Post by dashnak on 2007-12-03
Is there a way to disable XGL specifically for a session?
I have GNOME and openbox.
I want XGL to be enabled by default in GNOME and disabled by default in openbox, as the whole point of having openbox is to be as light as possible.
I've looking for a solution to this and have been unable to find it.

---

### Post by benevolent on 2008-02-03
> **jordanmthomas said:**
> That means you don't have the folder xsever-xgl.  Do this to get the file there:
```
mkdir ~/.config/
mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
```
If the first mkdir give you an error (it probably should), just ignore it and continue on.

if i want to enable this, I just delete this file, right????

---

### Post by jordanmthomas on 2008-02-03
I would assume so.  This would only enable XGL if this file was the only reason it was disabled to begin with, though.

---

### Post by spiderbatdad on 2008-02-03
```
sudo apt-get install gnome-compiz-manager
```

---

### Post by jordanmthomas on 2008-02-03
> **spiderbatdad said:**
> ```
sudo apt-get install gnome-compiz-manager
```
XGL is not synonymous with compiz.  You can run XGL and not have compiz running.

---

