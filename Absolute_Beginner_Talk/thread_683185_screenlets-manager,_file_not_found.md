---
title: "screenlets-manager, file not found"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-01-30
Hi folks
I'm hoping for some Screenlets install help.  

I had initially installed an old version of screenlets, and needed to remove all Old Versions and bzr Screenlets-new.

The install seemed to go well.  But, I've uninstall it twice and reinstalled with the same error.
After the 'sudo python setup.py install' is complete.  The instructions tell me to:
Run
Code:
screenlets-manager

Terminal returns
bash: /usr/local/bin/screenlets-manager: No such file or directory

I'm not even in directory /usr/local/bin/
I ran screenlets-manager from /home/bill/Screenlets-new

Any ideas?  Would be great appreciated

Bill

---

### Post by mattismyname on 2008-01-31
Worked fine for me with Synaptic -> Install Screenlets -> Wait for it to install -> Applications Menu -> Accessories -> Screenlets

---

### Post by LeDechaine on 2008-01-31
err, just updated the Synaptic packets list, and screenlets is NOT in the list. Not in the Add/Remove "thing" neither.

---

### Post by jan quark on 2008-01-31
try this guide
[http://www.screenlets.org/index.php/FAQ](http://www.screenlets.org/index.php/FAQ)

---

### Post by bmachia on 2008-01-31
*bump*

---

### Post by jan quark on 2008-01-31
did the guide help you ? have you followed the install instructions depicted there?

or are you stil having the problem?

---

### Post by bmachia on 2008-01-31
I want to thank everyone, as I worked my way through this problem.  I pulled the hair out of my head until I had a fix.  That's quite a trick considering I'm bald.

My problem eventually boiled down to the installation of 'python-gnome2-desktop' through Synaptic.  After this was installed, I'm able to start Screenlets-Manager without file not found errors.

Bill

---

### Post by mattismyname on 2008-01-31
Maybe the reason it wasn't in synaptic is because it's only available in Hardy.  If so, my apologies....

---

### Post by LeDechaine on 2008-02-01
No problem, thanks, I found a way to install it anyway and I now have screenlets. :)

---

