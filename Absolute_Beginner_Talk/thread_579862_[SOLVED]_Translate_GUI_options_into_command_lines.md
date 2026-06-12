---
title: "[SOLVED] Translate GUI options into command lines?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-10-18
I'm coming from a windows world so bear with me on this one but here's the question: 

In Ubuntu 7.04, the Applications menu lists a variety of applications. How do I figure out what commands to use to launch those utilities from the command line? If this were windows, I would right-click on the name of the application and choose properties and it would show me where the application is installed and what command line is being used to launch it. Is something simliar available in Ubuntu?

Here are a couple of specific examples:

I'm logging in as a normal user and want to edit a file. So I click on Applications > Accessories > Text Editor. I browse to the file and open it only to find my user account doesn't have permissions to edit the file. 

With my limited understanding of Linux, the only way I know how to do this would be to log off, log back in as root and edit the file but I'm learning about the SUDO command which is launched from terminal.

So how would I start Text Editor as SUDO? Same goes for any other application that is avaialble on the Applications Menu.

---

### Post by p_quarles on 2007-10-18
It works nearly the same as it does in Windows. First, right-click on the "Applications" menu, and then choose "edit menu." There, you'll be able to look at the properties of each item and find out what the command is.

By the way: to run a *graphical* application as root, you should use "gksudo" instead of sudo. In your example:
```
gksudo gedit *filename*
```
There's a small chance that running a graphical app with regular sudo will screw up permissions on the system.

---

### Post by shad0w_walker on 2007-10-18
You should be able to find the command to run in a couple of ways:

1. Right click on the applications menu and create a shortcut on the desktop/panel and then right click that shortcut and view the launcher tab.

2. Right click on the applications section of the panel and select Edit menus. You can find your applications entry in the list and open the properties to it so you can view the command.

---

### Post by vortex0007 on 2007-10-18
Thanks p_quarles,

so follow up question: when I launch "gksudo gedit" the application launches but in the terminal window I have the following:

(gedit:29177): GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

But the app launched in the background.

What does this warning mean?

---

### Post by p_quarles on 2007-10-18
That's a false warning. It's a known bug. For more info:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by philinux on 2007-10-18
It just opens blank document for me

They must have fixed the bug in gutsy

---

### Post by vortex0007 on 2007-10-18
Thanks for the answers. Both of these solved my issue.

---

