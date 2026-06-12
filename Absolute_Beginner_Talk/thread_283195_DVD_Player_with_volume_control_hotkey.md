---
title: "DVD Player with volume control hotkey"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by sgardne on 2006-10-23
Hello,

This is the last thing. This is the only thing keeping me chained to Windows. 

I need a media player that will play a DVD *with* menus that will allow me to bind volume - and + to the mouse scroll wheel. VLC player has the option, but it does not work. Gxine has the interface to add keybindings, but I have no idea what the heck it wants me to type into the box to get it working.

I've tried updating VLC using the source packages but I gave up after the 50th dependency wasn't there. ](*,)

Can someone PLEASE help me delete my windows partition by giving me this last thing? More clearly:

Tell me what I'm supposed to put in the Gxine settings to make this work, or tell me what I'm doing wrong with VLC player. 

Thank you.

---

### Post by uchuunoyanushi on 2006-10-24
Of course, this is madly easy to do in mplayer.  Which, sadly, doesn't support DVD menus. 

Check out /usr/share/doc/gxine/Keybindings-HOWTO. If that doesn't help, you might take a look at the other Xine frontends and see if it's easier to change the keybindings under them.

As for VLC, have you tried getting the newest version from the backports?  I don't know if it's in there, but it's worth looking, especially if you have that many dependencies to load.

---

### Post by sgardne on 2006-10-24
Thank you for your reply. Unfortunately there is not a package in the backports list for VLC. The gxine keybindings howto doc was less than helpful. I guess I'll just have to wait until VLC v0.8.5  is available in the repositories. Hopefully they've fixed hotkeys in that version. Meanwhile, I'll check out some of the other  xine frontends like you suggested. Thanks.

---

### Post by sgardne on 2006-10-24
The xine-ui front end does the trick! Yay. Thanks again.:mrgreen:

---

