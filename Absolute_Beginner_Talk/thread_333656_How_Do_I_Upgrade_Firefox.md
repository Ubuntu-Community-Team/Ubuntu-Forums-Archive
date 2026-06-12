---
title: "How Do I Upgrade Firefox?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by corypina on 2007-01-07
I installed Dapper yesterday.  It came packaged with Firefox 1.5.X.  At the Firefox website I can download the new version, but I don't know what to do with it after that.

Help?

---

### Post by oyvindaa on 2007-01-07
Have a look [here](http://www.psychocats.net/ubuntu/firefox)

---

### Post by corypina on 2007-01-07
Thanks!

---

### Post by manny0 on 2007-01-07
i had firefox 2 which i installed manually and ubuntu keeps trying to update my firefox from 2.0 to 1.5 or whatever. and i updated now im back to 1.5 from 2.0 what the heck happend?

---

### Post by oyvindaa on 2007-01-07
> **manny0 said:**
> i had firefox 2 which i installed manually and ubuntu keeps trying to update my firefox from 2.0 to 1.5 or whatever. and i updated now im back to 1.5 from 2.0 what the heck happend?

In Synaptic, you can lock the Ubuntu Firefox to its current version.

Just search for Firefox within Synaptic, mark it, then go to "Package" in the menu and "Lock Version".

---

### Post by MkfIbK7a on 2007-01-07
yes in synaptic search fire scroll down to firefox and do what oyvindaa said

---

### Post by aysiu on 2007-01-07
Just so people know--almost all the HowTos on installing Mozilla's Firefox do **not** remove Ubuntu's Firefox. The two are installed next to each other. From what I've read, removing Ubuntu's Firefox may take some functionality out of other parts of Gnome.

---

### Post by MkfIbK7a on 2007-01-07
> **aysiu said:**
> Just so people know--almost all the HowTos on installing Mozilla's Firefox do **not** remove Ubuntu's Firefox. The two are installed next to each other. From what I've read, removing Ubuntu's Firefox may take some functionality out of other parts of Gnome.

thats what i thought you type something like firefox-ubuntu to open firefox 1.5 right?

---

### Post by aysiu on 2007-01-07
> **wert613 said:**
> thats what i thought you type something like firefox-ubuntu to open firefox 1.5 right?
Yes, it's *firefox.ubuntu*

Some more details from [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) on what I was saying earlier: > Warning: If you use this guide, do not remove the Ubuntu version of Firefox. Doing so will break the following packages: Yelp (help viewer), Epiphany, Gnome-app-install (Add Applications), Liferea, Blam and any application requiring the gecko rendering engine.

---

### Post by awaqas on 2008-03-11
Hi guys i have been searching this stuff for a very long time and finally got to a point where i understand that the Firefox upgradation in Ubuntu 7.10 is fairly simple. you don't need to go to installing this and that or Packages like Ubuntuzilla for that purpose. Simply go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , select "gutsy update" and then select Web Software and click on the new firefox version download it and use the DEB package manager to update your firefox to the latest version. 
This is the simplest way to update any package who update is available :) 
When you install the latest firefox version after the installation is complete ignore any errors it gives, simply go to the terminal and write this "sudo apt-get install -f" and your good to go.:KS

Suggestions are welcome on this .... 

Let me know if you encounter any problem.

Cheers.

---

