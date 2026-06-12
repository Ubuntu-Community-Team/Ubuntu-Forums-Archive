---
title: "Enabling CUPS Admin web pages?"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by falcon15500 on 2006-10-02
Hi all,

  I am trying to setup CUPS on a headless server I have.  The server doesn't run X, so everything has to be done either by command-line, or preferably by the builtin CUPS web pages.  The problem I am running into, is that the ADMIN sections of the CUPS pages are disabled via upstream as there are some licensing wrangles with OpenSSL etc.
  I am not in the position to compile my own, with the needed OpenSSL support (the server doesn't have devel environment).  Has anyone out there rolled their own, with SSL support?  If so, care to share your deb? ;)

falc

---

### Post by bluefrog on 2006-10-02
sudo adduser cupsys shadow
should do the trick for you but indeed that way may be risky as if I recall well, anybody will be able to access cupsys administration that way.
You may activate it just for the time being though, configure the stuff and delete cupsys from shadow group afterwards.

James

---

### Post by falcon15500 on 2006-10-02
> **bluefrog said:**
> sudo adduser cupsys shadow
should do the trick for you but indeed that way may be risky as if I recall well, anybody will be able to access cupsys administration that way.
You may activate it just for the time being though, configure the stuff and delete cupsys from shadow group afterwards.

James

  Thanks for the help James, but I have already tried this after reading it elsewhere.  I can get INTO the admin pages fine, the problem comes when I try to make changes using it.  When I try, I get...
```
426 Upgrade Required

You must access this page using the URL https://host.net:631/admin.
```
This just hangs, as from what I have read, Debian stripped the SSL/TLS support from the package.

falc

---

### Post by falcon15500 on 2006-10-02
(sigh) I eventually installed build-essential, downloaded the lastest stable CUPS and compiled it with TLS/SSL support.  After a few tweaks, it worked fine - I could do all the CUPS admin from the web pages.  However, after about a half hour, it all went to hell and wouldn't let me authenticate anymore?  Research tends to indicate a long outstanding upstream problem.
 
I uninstalled the self-rolled version, re-installed the ubuntu cupsys package and performed all the cups admin by command line.  It seems you need to omit the -E from common instructions as this causes the attempt to connect to the cups server with encryption (which doesn't work with the default Ubuntu package).  Got my printer up and connected and then just started printing via Samba.

falc

---

### Post by stevieb on 2007-12-24
something that may be a clue- under System-Administration-Users and Groups-Manage Groups, there is no mention of 'shadow.'  does this mean anything?  does shadow need to be up there in that list?  is it a matter of just adding it?

thanks,

steve

---

