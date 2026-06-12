---
title: "Uninstall Package?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-09-27
I have a curious problem.  I converted a .rpm package to .deb with alien, then installed it.  Now I am having some trouble, and want to get rid of it.  

When I go into synaptic to remove it, it gives me an error.
E: armagetronad: subprocess pre-removal script returned error exit status 127

I navigated to the folder where the executable file is: /usr/local/bin
There is an armagetronad-uninstall executable text file that, when run, does nothing.  That file contains this:
#! /bin/sh
rpm -e armagetronad

Whenever I try to run that in a terminal, whatever directory I am in, it says this: 
error: package armagetronad is not installed

Sometimes, when I am executing things such as aptitude or apt-get, I get an error message saying that:
errors occured while trying to process armagetronad
even when what I am doing has nothing to do with armagetron.

help?? :confused:

---

### Post by think13 on 2006-09-27
anyone? help?

---

### Post by Sef on 2006-09-27
Did you install it via synaptic or the terminal?

Please have some patience.  Most posts are answered within 24 hours.

---

### Post by think13 on 2006-09-27
I converted it to .deb with alien in the terminal.  I know I didn't use synaptic to install it.  I believe I simply double-clicked on the package and  it installed (with package manager I believe).

---

### Post by think13 on 2006-09-27
Maybe my only option is to manually remove the files?  I could download the package again, see what is in it, and delete those files?  

Is there a way to search your entire filesystem for files, not just the directory you are in, using the search option in file browser?

Also, is there a way to set a 'system restore point' like in Windows.

---

### Post by think13 on 2006-09-28
go to thread
"bad package?"

---

