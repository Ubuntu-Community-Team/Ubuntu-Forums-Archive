---
title: "Evolution 2 - Help please!"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by t.septekin on 2007-10-06
My Evolution 2, running in Feisty, has just developed a habit of closing itself whenever I attempt to look up Preferences either by clicking on the icon under Edit menu or by using the shortcut shift+ctrl+S. I'd been trying to find out how to avoid an attachment on the received message auto-attaching itself to my reply. I have done a Restart, still the same. What have I done wrong?
By the way, the same thing happens not only in Mail but in Contacts and Calendars as well.

---

### Post by Perfex on 2007-10-06
run it in terminal.. what does it say?

---

### Post by t.septekin on 2007-10-06
CalDAV Eplugin starting up ...

(evolution-2.10:10876): evolution-mail-WARNING **: ignored this junk plugin: not
 enabled or we have already loaded one

(evolution-2.10:10876): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed
to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:10876): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:10876): DEBUG: mailto URL command: evolution
process 10876: The last refernce on a connection was dropped without closing the
connection. This is a bug in an application. See dbus_connection_unref()
documentation for details.
Most likely, the application was supposed to call dbus_connection_close() since
this is a private connection.

---

### Post by Perfex on 2007-10-06
Well lets first try the easy way..               
> sudo apt-get install evolution
type into terminal
if that doesnt work then will digg into it

---

### Post by t.septekin on 2007-10-07
I opted for the easy way out: re-installed the system, retaining my home partition.
And you may guess: the problem persisted! So, I copied the morning's backup of the home folder and back to normal now.

Thanks a lot for your assistance. A re-installation, including all the additional packages, takes about an hour and a half, I think it is the best general solution although it was not the right one in this instance. Whatever caused the problem I'll never know.

All the best,
teoman

---

