---
title: "Compiz Startup"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-10-31
I just installed Compiz on Edgy form this HowTo: [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

I was wondering, how can I get it to start on startup? Like what I mean is Automaticly have it in the system tray and have the GL Desktop already to go? Is there any way of doing that?

Thanks for the help.

---

### Post by daou on 2006-10-31
Compiz is old and is no longer being developed. Beryl is the new fork of Compiz.

[http://forum.beryl-project.org/index.html]("http://forum.beryl-project.org/index.html")

---

### Post by PPAAUULL on 2006-10-31
But Beryl is SOOOO slow on the same sytem as compiz is. It slows typing down and everything. besides I still think Compiz is being developed just by a diffrent source. Fedora or something like that.

---

### Post by daou on 2006-10-31
It could be that the default settings Beryl ships with are slower on your system than the ones that came with Compiz. Beryl seems faster on my system than Compiz.

---

### Post by PPAAUULL on 2006-10-31
I am using a built in Graphics card. The intel ones.

---

### Post by iceseyes on 2006-10-31
Compiz is still alive! Now, you can choose between compiz (see gandalfn blog) and Beryl. I prefer Compiz because I think it's more fast and simple! But compiz it's a little bit hard to install. I can't start it in gnome-session, 'cause every time I add compiz-tray-icon in gnome-session but everytime disappear! ](*,)

---

### Post by redpointpete on 2006-11-08
> **PPAAUULL said:**
> I just installed Compiz on Edgy form this HowTo: [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

I was wondering, how can I get it to start on startup? Like what I mean is Automaticly have it in the system tray and have the GL Desktop already to go? Is there any way of doing that?

Thanks for the help.

To start compiz at startup is the same as starting any program in Sessions Manager. System->Preferences->Sessions->Startup Programs Tab  Add:

compiz-tray-icon

to the list and restart. You should now have the sys tray icon and Compriz activated everytime you login.

---

### Post by aka5ha on 2006-11-10
I also have this problem:

when I add compiz-tray-icon to system>sessions>startup, it works only once.  The compiz entry is not there on next boot and compiz does not start up.  

Any ideas?  Thanks!

---

### Post by aka5ha on 2006-11-12
I solved it:

Must tick off "save this session" box, that's it.

---

