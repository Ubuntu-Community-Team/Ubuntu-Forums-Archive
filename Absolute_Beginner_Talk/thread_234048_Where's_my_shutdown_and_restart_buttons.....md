---
title: "Where's my shutdown and restart buttons....?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2006-08-10
I have just installed ubuntu 6.06 the other day and i like it, then i last night when im about to shut it down...... the shutdown and restart button is missing..... can somebody tell me what's going on... :-( 
Thanks!

---

### Post by agc on 2006-08-10
You can right-click on your desktop and at
the bottom of the list you will see the 'Log Out'
option ... you can shutdown from there.

Or type 'ctrl-alt-delete', that should work too.

Hope that helps.

---

### Post by jms392 on 2006-08-10
If the shutdown button is missing from your toolbar, you can right click (on the toolbar) and select "Add to panel", then under desktop and windows, select "Quit".

---

### Post by Nhatz on 2006-08-10
when i click the quit button the menu just displays... logout, lock, switch
users, and hibernate..... the restart and shutdown buttons are gone.:sad:

---

### Post by Flying caveman on 2006-08-13
Same thing happened to me. It happened just after I added the Kubuntu desktop.

---

### Post by junglepeanut on 2006-08-13
do a search on how to get them back in the forums it is in there. If you run kde, gnome, xfce, fluxbox etc ( alot of window managers) you will find they occasioanly rearrange stuff. As I searched and did the fix. THen after a while happened again. I narrowed it down to when I was switching between window managers. I think gnome and kde maybe xfce to store a few things in slighty different areas and so this happens, or maybe xfce and gnome store settings in the same area and overwwrite the others. Whatever it can be fixed just don't be surprised if it happens again.

You can use shutdown from the terminal if you like.

sudo shutdown -h now     !shutsdown right now

sudo shutdown -r now     !restarts right now

---

### Post by infoseeker on 2006-08-13
If you are using Ubuntu with KDM as login manager this seems to happen, but if you use Ubuntu with GDM this problem should be cleared up.

You can select GDM with this command:

> sudo dpkg-reconfigure gdm

---

### Post by dolphinsonar on 2006-09-19
Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]

---

### Post by brickferd on 2006-09-26
> **dolphinsonar said:**
> Go throught these steps first, it might be this simple:

System > Administration > Login Window .... [x] Show Actions menu (check this)

[IMG]http://static.flickr.com/86/247725707_ac81551db9.jpg?v=0[/IMG]


I cannot believe this fix was this easy for me...  Gotta love the little nuances of Ubuntu!

Thanks for the help Dolphinsonar](*,)

---

