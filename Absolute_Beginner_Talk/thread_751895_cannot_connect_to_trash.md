---
title: "cannot connect to trash?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by BossGreen on 2008-04-11
when ever i try to access the trash, it says this

failed to connect to the Trash: Failed to connect to socket /tmp/dbus-SYPAO9Fw3p:  Connection refused.


how do i fix it?

---

### Post by swoll1980 on 2008-04-11
try removing your trash from the panel then re adding it

---

### Post by buried on 2008-04-11
If that doesn't work try accessing your trash manually or using Ubuntu Tweak to add the trash can as a Icon on the desktop

---

### Post by BossGreen on 2008-04-11
nothing, i still get the same error message after i did that

any more suggestions?  
Thank you in advance for any help. :)

---

### Post by buried on 2008-04-11
hmm It's very weird..can you access the trash via Nautilus (file manager)?

---

### Post by BossGreen on 2008-04-11
i can connect to it there...
i guess thats fine, i dont really need it to be a shortcut icon or on the task bar.  
thank you for the help. :)

---

### Post by buried on 2008-04-11
Well it seems like a bug to me, I'll search for a fix for you.

---

### Post by buried on 2008-04-11
Remove the trash Icon from the panel, then you can either make a shortcut (launcher) on your desktop with this location:
```
trash:
```
Try removing it from the panel and adding it again making sure that the address is
```
trash:
```

---

### Post by benrboone on 2008-05-18
I am also having this problem and can't seem to get it fixed.  I tried the suggestions in this post, didn't work

this happened on an upgrade from gusty to hardy

---

### Post by frankob on 2008-05-20
I have this issue too, on Xubuntu Hardy. In Ubuntu Hardy I didn't have this issue, but I still want to keep Xubuntu because my computer is a bit old, and Gnome runs slow. After all, I don't use that Trash very much, I usually delete with shift+delete, so I didn't even care, initially.

So, I tried to install the Screenlets on my Xubuntu Hardy, and it didn't work... I didn't get it initially, I have everything installed... So I started it from the terminal to see what it spits. Among other stuff, it gives me the same error as in the Trash panel applet: "Failed to connect to socket: /tmp/dbus-... : Connection rejected". So I tried other applications, and found out that every application that normally uses dbus gives me the same error, and in Compiz I can't activate dbus.

I think I have everything installed, dbus is checked in the Services window, I don't know how to fix this even I am very much sure that it is a dbus issue.

So I tried to run the Live CD, and there is no problem with it... I tried to reinstall it, guessing there might have been some arrors during last installation. Before that, I even checked the integrity of the CD, and it was OK. But after I reinstalled it I found the same error, again - dbus is not working properly.

Now I started to guess that it is because of something written in my home partition, remained from my Ubuntu (Gnome) install, and that conflicts with my actual Xubuntu (Xfce) install.

I would like to avoid another installation, especially I would like to avoid formatting my home partition, so I am asking you if someone knows how to fix this?

I repeat, I think we all (the three of us, here) have the same dbus issue, just check it out. I think playing aorund with the Trash will never solve the problem.

EDIT: I found out now that in my /tmp/ there is no dbus files. I also found out that I can run some dbus commands as root (but still with no effect, anyway), and I can run Screenlets daemon as root (but it is unusable like that. I didn't find out how to run the Trash panel applet as root). I futhermore found out that my ~/.dbus folder is owned by root and is not accessible to the user. Is that normal? Is it possible that the folder contains files form my old (Ubuntu) install, and are now conflicting with my new (Xubuntu) one?

---

### Post by frankob on 2008-05-22
OK, replying to myself...

I solved the problem for me, and I believe it's the same for all the three of us.

As I said, my ~/.dbus folder was owned by root, and was inaccessible by the user. That's why all the user-run processes couldn't connect to dbus, including the Trash applet. ~/.dbus folder should be owned by user to make dbus work properly.
I solved the problem by simply removing my ~/.dbus folder and then rebooting. That renewed my ~/.dbus folder, and now everythin dbus related works normally, including the Trash.

To remove ~/.dbus you will have to use sudo, as the wrong permissions will not allow any acces to that folder otherwise. So, open a terminal. While in home (~), type:

sudo rm -r .dbus

And then restart.

That should do the trick. Of course, presuming we are talking about the same problem. here, which I am quite sure of. There is nothing to lose if trying out, anyway.

---

