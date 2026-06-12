---
title: "Problems with SMEG &amp; System Log..."
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-16
I've been having problems with SMEG and System Log for awhile now.

Both of them run from the terminal, but neither initialize from the menu.  When clicked on, it shows at the bottom of the workspace "Starting Applications Menu Editor," or, "Starting System Log,"  but then that goes away and nothing happens.

I have a feeling that it has something to do with the Python script.  How can I tell which version of Python each program is using and how can I revert back to an earlier version of Python? 

Thanks in advance.

---

### Post by Pragmatist on 2006-03-16
You can check the dependencies of a package by opening up synaptic, use the search feature to find your package, right-click the package, select  properties, click the dependencies tab.  You can find out your version of Python either in synaptic or by typing **python -V **

What happens if you open smeg in a terminal and edit the entries for smeg and for the system logger. There is a checkbox for running them in a terminal. Check those boxes and try again. Is the problem still the same?

---

### Post by Cousindaddy on 2006-03-16
Thank-you for the response.

I altered the menu as you suggested and both programs boot from the menu with the terminal option selected.

I'm running Python 2.4, which, I believe is the latest.

While I can run both programs this way, I would like to be able to fix the problem with running it from the menu.

Any ideas?

---

### Post by Pragmatist on 2006-03-16
>  I altered the menu as you suggested and **both programs boot from the menu** with the terminal option selected.


I'm not sure I understand.  If you can run both programs from the menu...what is the problem?

---

### Post by Cousindaddy on 2006-03-16
In order to get it to run with the Terminal option selected, I have to run it as sudo and I must enter my password.

It would be nice not to have to do that.

---

### Post by Pragmatist on 2006-03-16
When you directly run those in a terminal (without using a menu at all, just open a terminal and run command), do you need to use **sudo** ?

---

### Post by Cousindaddy on 2006-03-16
yes, I must run them both under sudo.

---

### Post by Pragmatist on 2006-03-16
That is strange.  Mine have 755 permissions (rwxr-xr-x) 

-rwxr-xr-x  1 root root 81912 2005-10-04 10:20/usr/bin/gnome-system-log
-rwxr-xr-x  1 root root 22956 2005-09-09 09:51 /usr/bin/smeg

This is probably the root (pun intended :) ) of your problem

---

### Post by Cousindaddy on 2006-03-17
I checked, and I have the exact same 755 file permissions.  I still think it has to do with the python script.

---

### Post by Pragmatist on 2006-03-17
Who are the owner and group of the program files?

If you think the problem has to do with conflicting versions of python, take a look at the different dependencies. Just go into **synaptic** do a search for each program, right-click on the program, select properties, click the dependencies tab.
 
 As far as smeg is concerned here is my info:
 installed version = 0.7.5-0ubuntu = latest version
 Depends: python (>=2.4)
 Depends: python2.4-gtk2(>=2.6)
 Depends: python2.4-libxml2(>=2.6.17)
 Depends: python-xdg(>=0.14)
 Depends: python2.4-glade2(>=2.6)
 Depends: gnome-menus(>=2.10) | kdelibs-data(>=3.4)
 *Replaces: menueditor*

---

