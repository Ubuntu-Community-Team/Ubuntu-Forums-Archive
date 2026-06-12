---
title: "Setting Default Programs"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-16
I'm trying to figure out how to set default programs in Ubuntu.

I don't mean opening .mp3s, I mean default browsers/mail clients. I want to change my default mail client to Firefox at [http://gmail.com/](http://gmail.com/) if possible, because everytime I open a mailto: link a mail client opens up.

Also, another question: How do I force an uninstall for programs I don't use that won't uninstall like Evolution mail

---

### Post by daniminas on 2006-12-16
System>Prefences>Preferred Applications ;)

---

### Post by Pobega on 2006-12-16
What would I have to put after the command "firefox" to tell it not only to go to [http://gmail.com](http://gmail.com) but to create a new mail? I currently have the command as "firefox http://gmail.com/" but I don't know what else to put to make it create a new mail.

---

### Post by Sabrage on 2007-01-24
I copied this:> http://mail.google.com/mail/?view=cm&fs=1&to=^T&su=^S&body=^M&cc=^C&bcc=^B
from the Firefox webmail-compose addon (which does not work for me with Fx 2.0). Now It opens a compose-window but without the recipient email and subject.....

anyone?

---

### Post by Pobega on 2007-01-24
This I would like to know too, since I use the gmail web client. Anyone have any ideas?

---

### Post by konryd on 2007-02-11
Similar thingy for opera System->preferred aps->mail app->custom

```
opera -newpage 'http://mail.google.com/mail/?view=cm&fs=1&to=%s'
```

---

### Post by d_thrasher on 2007-03-03
This site outlines the procedure.  It worked for me - 6.10.

[http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html](http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html)

---

