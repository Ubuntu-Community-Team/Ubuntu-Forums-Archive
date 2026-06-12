---
title: "enabling cupsys web interface?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by threegremlins on 2006-05-24
is there someone who can walk me through it?

---

### Post by dmizer on 2006-05-24
it's enabled by default ... just browse to [http://localhost:631](http://localhost:631)

---

### Post by threegremlins on 2006-05-24
heres' what it says when you hit the home page
--------------------------------------------------------------------------------------------------
**Welcome!**

  These web pages allow you to monitor your printers and jobs as well as perform system administration tasks. Click on any of the tabs above or on the buttons below to perform a task.
   [[IMG]http://localhost:631/images/button-help.gif[/IMG]]("http://localhost:631/help/") [[IMG]http://localhost:631/images/button-add-class.gif[/IMG]]("http://localhost:631/admin?OP=add-class") [[IMG]http://localhost:631/images/button-add-printer.gif[/IMG]]("http://localhost:631/admin?OP=add-printer") [[IMG]http://localhost:631/images/button-manage-classes.gif[/IMG]]("http://localhost:631/classes") [[IMG]http://localhost:631/images/button-manage-jobs.gif[/IMG]]("http://localhost:631/jobs") [[IMG]http://localhost:631/images/button-manage-printers.gif[/IMG]]("http://localhost:631/printers") [[IMG]http://localhost:631/images/button-manage-server.gif[/IMG]]("http://localhost:631/admin") 
  *Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing). /usr/share/doc/cupsys/README.Debian.gz describes the details and how to reenable it again.*
  [B]---------------------------------------------------------------------
[/B]

no matter what I do there, or try, I can't get it to set up my printer.

---

### Post by dmizer on 2006-05-25
i haven't changed anything, but i know that i am unable to do any admin tasks.  i was reading some things the other day about enabling that, and i will look for it again, but i don't think you need it to add a printer.

try here: [http://localhost:631/printers](http://localhost:631/printers) and click on the button below that says "add printer".

---

### Post by linear on 2006-05-25
Have another look at the message:
[quote=threegremlins]*/usr/share/doc/cupsys/README.Debian.gz describes the details and how to reenable it again*.[/quote]
Have you tried that?

---

