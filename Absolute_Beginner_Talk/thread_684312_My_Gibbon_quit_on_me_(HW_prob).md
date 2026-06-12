---
title: "My Gibbon quit on me (HW prob)"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Splat! on 2008-02-01
Did a fresh install of G-Gibbon earlier today and all was working fine.
Then I added a CD-RW device to the system and now everything's
gone bonkers. Ubuntu boots past the usedID/Password and gets 
to the desktop BACKGROUND, then quits. No icons, no trays, nada.
Just the background I selected earlier today.

Ctl-Alt-Del let me shut down so I disconnected the CD-RW and
restarted. Again, userID, Password, background, stop.

What did I do wrong (so I don't do it again) and how can I fix it, please?

Splat

---

### Post by randy78 on 2008-02-01
Try creating another user profile by booting into grub, selecting recovery mode...
When it comes up root@Ubuntu (or whatever), type: startx
then if that brings up a desktop environment, go to menu>system>administration>Users and Groups and then click the Add User button and give it the user privileges you wish to have.

After that, try restarting and logging into the new user account you just created.

If that doesn't work, try unplugging the new device and booting up again to see if it's conflicting somewhere.

Hope that helps

---

### Post by Splat! on 2008-02-01
Think I found the problem - it has to do with
screen resolution - somehow it got set to MAX
and the desktop was "bigger" than my screen.

In the process, tho, I lost my Gnome Panel.
Working on that now.

Splat

---

