---
title: "Logout button with all 5 icons?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-12-22
On a normal GNOME, there are seperate buttons, in Ubuntu, there is about 5 or so icons when you hit the logout button.
Anyone know how or where to do the 5 icon thing?

---

### Post by Ben Sprinkle on 2006-12-22
Anyone?

---

### Post by roachk71 on 2006-12-22
Are you looking for a way to disable this and use just the logout button without confirmation?

The logout option buttons work as follows:

Logout: Returns you to the login screen (of course),

Hibernate: Saves the contents of RAM to your hard disk and shuts down, (hopefully) restoring your session along with running apps,

Suspend: Same as Hibernate, except the information is kept in RAM,

Shutdown and Reboot: You already know what these are for...

I say hopefully for hibernate and suspend, since they don't work correctly on all machines (my HP Pavilion xt125 notebook is a perfect example of their failures.) Please use EXTREME CAUTION with these. :neutral: 

If yours is a trouble machine for hibernate and suspend, and you don't want to click twice for logout, that panel can be disabled using Sessions in your System menu.


If this post is a bit verbose, it's simply because I like covering all the bases... ;)

---

### Post by Pobega on 2006-12-22
I think he wants to know the command to initialize a logout, not what each of them do.

---

### Post by jvc26 on 2006-12-22
What exactly do you want to know?
Il

---

### Post by Ben Sprinkle on 2006-12-23
I need to know how to ADD all 5 icons to the logout button like in Ubuntu.

---

### Post by Ben Sprinkle on 2006-12-27
No one knows?

---

### Post by matthew on 2006-12-27
I can't help you. I actually have 7 options on my logout dialog box and I didn't do anything special. Here's the list of what I have available to me (granted this is a laptop).
```
logout
lock screen
switch user
suspend
hibernate
restart
shut down
```

EDIT: make that 8 options...I forgot to include "cancel."

---

### Post by Ben Sprinkle on 2006-12-28
That's what I need. ;)
All I got now is logoff or switch user. + Cancel

---

### Post by Ben Sprinkle on 2007-01-03
Anyone know how to do what I need, which is a logout dialog like matthew's?

---

### Post by psycosmyth on 2007-01-03
what distro are u using? 
There is a file in the Ubuntu Desktop pakage that creates this but I don't know where to look.
Xfce has multiple choices as well. You could bind each command to an icon on the desktop or taskbar (something I did in Windows).

---

### Post by Ben Sprinkle on 2007-01-04
Debian etc Rc1.

---

### Post by Ben Sprinkle on 2007-01-05
Bump.

---

### Post by Ben Sprinkle on 2007-01-07
Bump.

---

### Post by Theimon on 2007-01-08
My suggestion: open a terminal and enter:
```

sudo gedit /etc/gdm/gdm.conf

```
Look for the entry: SystemMenu=true. It'll probably be commented (#). Remove the comment and make sure it says true instead of false. Save and exit.
You'll probably have to reboot to activate the setting but once you did that, you'll have all the options back at the "Exit" panel (or whatever you wanna call it ;))

---

### Post by Ben Sprinkle on 2007-01-08
I am not talking about the gdm..
The logout button on the taskbar AFTER you login. ;)

---

### Post by borland-c on 2007-01-08
please look anyone - I have another problem
I have in gdm menu 3 buttons - Loout, Suspend, Hibernate
but there are no buttons Restart and Shutdown
command```
sudo dpkg-reconfigure gdm
```don't help me
I CAN'T SHUT DOWN MY COMPUTER ! (in normal way)

---

### Post by Ben Sprinkle on 2007-01-08
Wrong thread.
But go in your x desktop and in Desktop > Administration > Login Window
You can change all those settings.

---

