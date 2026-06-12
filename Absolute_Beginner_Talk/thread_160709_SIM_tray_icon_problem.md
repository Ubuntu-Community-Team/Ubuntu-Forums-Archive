---
title: "SIM tray icon problem"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by darkarchon on 2006-04-15
i use SIM (simple instant messenger), which is simply awesome.
right now i am using the latest version compiled from cvs, but the same problem occured with the repositories version as well.
sometimes, quite frequently, SIM's tray icon disappears from tray, but not completely, i can still see a small portion of it.
now, SIM is KDE app, so i guess it could be sort of incompatibility with gnome.
any1 knows?

---

### Post by nekr0z on 2006-04-24
Well, never had such a problem using SIM, but I use KDE anyway.

I'm of a little help to you here, but I hope you can help in solving my problem since you're using SIM already. I really don't know where else to ask for help.

The porblem is I was searching for a decent IM client, and found that SIM suits me best. But as installed from ubuntu repositories it has no auto-away module in it, which is a problem.

I then downloaded a .deb from official SIM page, and forced it install (it has 2 unsolvable dependencies, but being forced to install works with no problems and has the auto-away module in it). The problem is, these 2 dependencies are still considered to be unsolved, so I cannot install or remove anything at all with apt-get, because it tries to remove SIM every time.

Is there any way out of this situation? Or maybe you know some place I could get the nessesary information?

---

### Post by darkarchon on 2006-05-02
sorry for not answering your question, i just havent been around for a while.
i think what u should do is download the source, compile it and checkinstall. thats what i did and thus have no problems with dependencies. try that, and if u have any troubles with compilation, let me know. also do "sudo checkinstall" instead of "make install", this way u will have SIM in synaptic (and it will also create .deb package in source files directory).

---

### Post by nekr0z on 2006-06-05
Well, I think this now it's time I'm ready to try, but SIM does not configure on my system at all... After ./configure at some point it says: checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

What package do i lack?

---

