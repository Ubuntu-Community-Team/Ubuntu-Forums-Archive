---
title: "Synaptic won't launch"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Ningyo on 2006-04-28
I just installed Breezy 5.10 today, and it's been working great.

But I wanted to watch some stuff on VLC, so I went to the Synaptic Manager thingie, but it won't launch at all.  Everything else works, but the Terminal couldn't find the VLC package or whatever when I tried doing it manually (with help).

Can anyone tell me why Synaptic won't work at all?  And how to fix it?

Because I REALLY kinda need it to work.

---

### Post by ajgreeny on 2006-04-28
You need to add universe and multiverse repositories to your sources.list file.
Go to synaptic-Repositories- Then click on the add button, and tick the boxes for universe and multiverse.  Click OK then click reload (the far left icon on the toolbar.  Now when you search for vlc it should be there.  For more info go to:-
[http://help.ubuntu.com/starterguide/C/ch03s06.html#id2528834](http://help.ubuntu.com/starterguide/C/ch03s06.html#id2528834)

Sorry I've just reread your thread, and I think you may mean that you can't even open synaptic.  Are you using a server install without gnome desktop, because if so you won't have synaptic installed and will need to use apt-get instead, though without a GUI desktop you will not be able to use vlc.  If I'm right and you need a desktop, ie Gnome or KDE, enter "sudo apt-get install ubuntu-desktop" or "sudo apt-get install kubuntu-desktop" and then get vlc using synaptic.

---

### Post by r4ik on 2006-04-28
Try,

gksudo synaptic  in a Terminal  and hit enter,

When asked for your password type it and Synaptic should run.
Note that this is a temp solution (if it works)

Good luck !

---

### Post by Sef on 2006-04-28
> gksudo synaptic in a Terminal and hit enter,

You will be root when you run gksudo.  Don't do anything else after you are done with it.  Just close it, so root is not running.

---

### Post by r4ik on 2006-04-28
Forgot to mention that my bad.
Thanks.

---

