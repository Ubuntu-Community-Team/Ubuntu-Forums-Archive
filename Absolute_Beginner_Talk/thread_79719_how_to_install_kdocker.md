---
title: "how to install kdocker"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by gold4tune on 2005-10-20
Hello, i want to try kdocker to put sunbird, xmms...  in my systray...  But i really dont know how to install it.

I have already downladed the tar.gz file and read the install text...  but i realy don't understant how to install it...

Is someone can help me...

thx!!!

---

### Post by michael1977 on 2006-07-26
Have you tried using synaptic to get kxdocker that is how I got it.  If you are running gnome as opposed to kde you need version .37 or higher.  I got mine from synaptic but I have added beerorkid repositories which may be why I have access to them.  try that you will need kxdocker, kxdocker-data, kxdocker-configur, kxdocker-wizard, which everone refers to the panel applet etc. etc. just download and install the other ones if needed.  The one problem I encountered is that under gnome it does not install in the menu, I just created a starter on the panel.

Right click the panel click add to panel click starter name it kxdocker and in the command field put in kxdocker that will start it.

Hope this helps, if you want to add the repositories I can't realy help I just followed a tutorial on the forums to do that so search around for adding those repos.

Since you have the tar ball try the unofficial ubuntu doc search for it on google there are step by step exp. of how to install from a tar file.  Also if that doesn't help try starting a new thread titled how to install a tar file.  alot of people on here want to help but if the title is somewhat ambiguous then they may just skip over it.

---

### Post by aysiu on 2006-07-26
Step 1: [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

Step 2: Paste this command into the terminal ```
sudo aptitude update && sudo aptitude install kxdocker
```

---

### Post by Ptero-4 on 2007-01-17
Actually it is kdocker what the OP wanted. (kdocker is an app to put apps in the notification area, kxdocker is a OSX-like Dock for KDE).

---

### Post by aysiu on 2007-01-17
> **Ptero-4 said:**
> Actually it is kdocker what the OP wanted. (kdocker is an app to put apps in the notification area, kxdocker is a OSX-like Dock for KDE).
Thanks for the clarification, but the same principle applies, assuming gold4tune is using Edgy:

Enable extra repositories and then ```
sudo aptitude update && sudo aptitude install kdocker
```

---

### Post by aysiu on 2007-01-17
What is up with this thread? gold4tune posts in October 2005, michael1977 bumps it in July 2006, and then Ptero-4 bumps it again in January 2007?

This has to be the longest-lasting short thread in the history of the forums!

---

### Post by MkfIbK7a on 2007-01-17
someone should fix the title...

---

### Post by MkfIbK7a on 2007-01-17
i put aysius last post into altavista babel fish and translated it to spanish then back to english and this is the output

> Which is for above with this thread of spiral? the posts of gold4tune in October of 2005, michael1977 run into it in 2006 July, and then Ptero-4 again runs into it in January of 2007? This one must be the long-lasting thread of short spiral in the history of the forums!

im sorry if this is off topic

---

