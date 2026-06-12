---
title: "No shutdown at log out"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by yaitedog on 2007-11-02
when I click the logout button shut down no longer comes up as an option. So this has come up before but the answers I've seen don't help in my situation. I've checked in the sessions menu and I don't see any option to return shut down to the menu.

---

### Post by amingv on 2007-11-02
Hi,

Maybe it's just a misconfiguration: it's your pc configured so that regular users can turn off the system, or just root?

if you type:
```
sudo shutdown now -h -P
```

what do you get? will the pc halt/turn off?

---

### Post by yaitedog on 2007-11-02
> Maybe it's just a misconfiguration: it's your pc configured so that regular users can turn >off the system, or just root?
It was default configuered so any user could shut it down. I did do some messing around in  root when I was getting the wireless card and my zen mp3 player to be nice. I didn't intentionally change and root shut down settings.
>if you type:
>Code:

>sudo shutdown now -h -P

>what do you get? will the pc halt/turn off?
She shuts right down.
Any Idea what I did?

---

### Post by amingv on 2007-11-02
Right now I can't be as specific as I would like to, since i use Kubuntu (i assume you use Ubuntu) I don't remember the correct path for Gnome. And I am at work right now, in a windows pc, so i can't run the system to refresh my mind. As soon as i get home (a couple hours) I will give you better information.

Still you may try this in the meantime: in your system settings try to find the session manager, check the options and make sure something that says "offer shutdown options" (please bear with me, it's just an approximate) it's marked. If it's not mark it and save your settings. That should do the trick.

There's a way to do this through the console, and  that would save you some time searching through menus, but they're in the back of my mind right now. As soon as I can check them I'll give them to you.

Sorry for not being as helpful right now.

---

### Post by amingv on 2007-11-03
My, I couldn't answer yesterday.
Here is all I could get: this option (for Gnome users) lays inside /etc/X11/gdm/gdm.conf (or in /etc/gdm/gdm.conf), search for the line SystemMenu, which must be =true.

I am not much of a Gnome user, and at any rate not a GNU/Linux master, so I would prefer that someone who knows better than me gives his/her opinion in case the following is not true, but if you feel adventurous/desperate you may try it (I can tell I would even if it screwed my pc, but that's me).

It's this: reconfiguring gdm:

```
sudo dpkg-reconfigure gdm
```

Something I would like to know, it just came to me as a flash: do you have both KDE and Gnome installed? I may not remember well, but if you have both you will only see shutdown options for the default desktop manager.

Also I don't think the conf files for wireless/mp3 devices have anything to do with shutdown options, but in case it comes from there, do you remember some of the files you modified? their paths? programs/commands you might have used?

Please let me know how this turns out for you.
I think I'll make a partition for Ubuntu and get cracking.

---

