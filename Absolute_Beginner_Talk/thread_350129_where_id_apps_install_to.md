---
title: "where id apps install to"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-01-31
I installed wxGlade, pyCrust, and a couple of other python wx GUI builders through the package manager, but I don't see where they installed to.  I remember seeing someone recommend installing the Debian menu in order to see all apps, so I installed it through Automatix.  In the edit menu list, though, I can't check the box to display the Debian menu.

So, the questions then are:
1)  How can I find where these applications installed to?
2)  How do I get the Debian menu working?

Thanks,

---

### Post by PointSource on 2007-01-31
If you're interested in manually adding menu items then the command for the application should just be the name of the application. First try typing in the name in a console/terminal.

---

### Post by Brunellus on 2007-01-31
the debian menu is an installable package:

```

sudo apt-get install menu

```

Apps usually install somewhere in /usr, typically something like /usr/local.

---

### Post by Ba66e77 on 2007-02-04
I managed to find wxGlade and add a link to it in my Applications menu, but I'm still having trouble with the Debian menu.  It's an option in the Menu Layout screen, but it's unchecked and clicking the checkbox doesn't do anything.  

I ran the sudo line Brunellus suggested, but got the following result:

ba66e77@ba66e77-desktop:~$ sudo apt-get install menu
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

