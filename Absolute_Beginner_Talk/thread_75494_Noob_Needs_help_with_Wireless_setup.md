---
title: "Noob Needs help with Wireless setup"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by MoLeak on 2005-10-13
I have ubuntu installed finally but I don't know much about it.  I want to get my Airlink+ wireless network going but I have no idea where to start.  Help!

-MoLeak

---

### Post by casper_2095 on 2005-10-13
Did an extremely brief google around on your behalf.
Got the general impression that the manufacturer is uncooperative.  The workaround is to use "ndiswrapper" which enables you to use the windows driver.  Research for yourself.  These might help...

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)
[http://www.linuxelectrons.com/article.php/20040507104718960](http://www.linuxelectrons.com/article.php/20040507104718960)

---

### Post by MoLeak on 2005-10-13
[QUOTE=casper_2095]Did an extremely brief google around on your behalf.
Got the general impression that the manufacturer is uncooperative.  The workaround is to use "ndiswrapper" which enables you to use the windows driver.  Research for yourself.  These might help...

[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)
[http://www.linuxelectrons.com/article.php/20040507104718960](http://www.linuxelectrons.com/article.php/20040507104718960)[/QUOTE]

I appreciate that.  I'll look at these links and see if I can't get this working.

-MoLeak

---

### Post by MoLeak on 2005-10-14
4. Untar the ndiswrapper-1.1.tar.gz file to your /usr/src directory. NOTE: the location where you untar the source doesn't really matter, but the rest of these instructions will assume /usr/src.

I am not allowed to drag a folder into the src folder.  No permissions.  How does this part happen?

-MoLeak

---

### Post by drogoh on 2005-10-14
Install ndiswrapper-utils through Synaptic/Aptitude/etc. or 'sudo apt-get install ndiswrapper-utils'

You don't have to futz with compiling it.  apt-cache is *great* for finding packages.

EDIT:  That wiki page should really be updated, it shows you the "Unix way", not the "Ubuntu way".

---

### Post by MoLeak on 2005-10-14
[QUOTE=drogoh]Install ndiswrapper-utils through Synaptic/Aptitude/etc. or 'sudo apt-get install ndiswrapper-utils'

You don't have to futz with compiling it.  apt-cache is *great* for finding packages.

EDIT:  That wiki page should really be updated, it shows you the "Unix way", not the "Ubuntu way".[/QUOTE]

I feel like I'm 6 years old with these questions.  

After running the apt-get install, it tells me ndiswrapper-utils is already the newest version.

Now what?  I hate to keep bugging folks with these questions but is this the first time this question has ever come up?  I thinking this should be written out somewhere or something already.  I don't no, maybe this is the way you learn the Linux way.  **waiting for it to click in**

-MoLeak

---

