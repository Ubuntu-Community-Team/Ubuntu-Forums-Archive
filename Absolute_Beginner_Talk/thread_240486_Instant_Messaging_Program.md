---
title: "Instant Messaging Program?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Zully Quirke on 2006-08-20
I've read a bit about Gaim, and I know AIM has a Linux release -- I seem to be having problems installing them, though. Can anyone help me out? AIM doesn't have a release for Ubuntu so I'm not sure which one I'm supposed to use, or which method. Gaim just confuses me -- I tried to follow a guide here, but when I downloaded the gaim-2.0cvx201-i386.deb file and attempted to open it, I get this message:

"Could not open gaim-2.0cvx201-i386.deb, Archive type not supported."

---

### Post by Marsolin on 2006-08-20
You should be able to install Gaim using synaptic. Opening a deb file will only show you the files it contains. deb files use the ar format.

You can find a list of Instant Messaging programs here: [http://linuxappfinder.com/communications/instantmessaging](http://linuxappfinder.com/communications/instantmessaging)

Gaim and Kopete are probably your best bets though.

---

### Post by kingbilly on 2006-08-20
I tried AIM for linux on Ubuntu and it was not very good.  It also took me day to get it to build correctly.  That was only my experience though.

Gaim however should have been installed by default on a ubuntu desktop installation.  Can you not find it?  Go to Applications > Internet > Gaim Instant Messenger

or in the terminal type:
```
gaim
```

If it is not currently installed you can type this in the terminal
[code] sudo apt-get install gaim[/gaim]
and then repeat the steps above to locate and run it.

I do notice that you are trying to install gaim2.0 which is still beta.  If you didn't choose to have the newest version of gaim for a reason, you can simply use the current release of gaim which should have been installed already, or you can use my instructions above.  Gaim 2.0 has a couple new features but you won't be missing anything by sticking to what works now.

---

### Post by Zully Quirke on 2006-08-20
Oh! .. I feel stupid. XD Thanks!

---

