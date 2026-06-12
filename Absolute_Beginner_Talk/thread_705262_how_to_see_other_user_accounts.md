---
title: "how to see other user accounts"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-02-23
i want to know hoe to see the other user accounts

and i want to know where the programs go if i install it in the home directory

of my account(i.e the program get installed in the current directory, or it goes in /usr)

and how should i get the EXE file of some of my programs i installed in /home

---

### Post by ubername on 2008-02-23
> **phanipalagummi said:**
> i want to know hoe to see the other user accounts

and i want to know where the programs go if i install it in the home directory

of my account(i.e the program get installed in the current directory, or it goes in /usr)

and how should i get the EXE file of some of my programs i installed in /home

If you have a normal set-up (i.e. the users have been set up using defaults), go to 'places' menu and select 'home directory'. When that opens, click the 'up' arrow. That should take you to /home, which should have a directory for each user.

Or go to terminal, then type 'cd /home' <enter> then type 'ls' <enter>.

Also, in nautilus (file browser), if you enable 'Show hidden files' from the view menu (or ctl+H) you will see a whole load of directories where various programs get installed (not exclusively, but a useful starting point).

---

### Post by SOULRiDER on 2008-02-23
Applications arent installed in your ~, they usually go in /usr.  Check out thsi link, it explains the filesystem a bit [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html) Some files ARE stored in your ~, they are cimply configuration files for the programs you use.

Also, remember when you install something the package manager will put the files where they need to go, so you rprobably will never have to go look for an executable yourself.

---

