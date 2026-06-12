---
title: "session manager/selector"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by wolf.b on 2007-11-14
I have spend many hours over the last few days to find again what I once saw:

There is a linux distro with a preconfigured menu that says something like this:
- restart with Gnome desktop 
- restart with KDE desktop
- restart with Xfrce desptop
...

Now I have installed Ubuntu 7.10 with Gnome window manager as default. When I log out, I can choose to start a gnome, kde, Xfrce and Enlightenment session. My question is this:
Is there a possibility to have a session selector (window manager switcher) that works from within the current window manager (without logging out first)? And hopefully log me in as the same user automatically.

I hope my poor english makes sense.


Greetings
Wolf

---

### Post by Inxsible on 2007-11-14
I don't think so. When you change the DM to log in, it releases all the files and packages associated with the DM that you are currently logged in with.

For instance, if you log in with gnome, the GDM packages are loaded into memory. When you log in with KDE, KDM packages are loaded and GDM ones are released. 

I do not think the GDM packages will transfer user information from itself to the KDM packages or vice versa.

You will have to restart the machine.

---

### Post by wolf.b on 2007-11-14
Sorry, my bad english.

I am looking for a tool that gives me the opportunity to click on a menu entry while I am inside a gnome session. That tool then remembers my username, logs me out, shuts down gnome window manager, selects the next session to be KDE, logs me in again, and launches a new X window session using KDE window manager. At present I have to log out manually, select the desired window manager manually, log in again manually, enter my password manually, and KDE appears as desired. There is no shutting down, or restarting involved in this process. It is easy to do with mouse clicks. BUT I remember that I have once seen a linux distro that offered a startmenu entry called logout, with submenus as described in first post.

Please forgive me. I don't want to impress anybody with bad attitude, but I used these short sentences in the above fashion in my despair to make my situation understood. I lack a lot of adequate terminology to be able to come up with a polite request/explanation.
I don't think the startmenu is called startmenu for example, but I don't know better yet. Can anybody maybe mention a non-ubuntu distro of linux that has those menu entries, so I go and study it and its terminology. Maybe this is a question that does not belong onto a ubuntu forum?

Thanks in advance

Greetings
Wolf

---

