---
title: "Kubuntu: Setting default (preferred) mail and webbrowser"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Xvani on 2007-03-21
Hi!

I'm trying to change the default mailclient in kubuntu. I've tried using the "System Settings" - default application, (and yes, I have selected the correct program) without luck.

I was however able to change the default browser by changing the x-www-browser symlink. I was unable to find the corresponding symlink for mail.

Why doesn't the GUI option work? and how do I fix this issue?

Thank you in advance

---

### Post by zvacet on 2007-03-21
I don´t know ansver toyour first question but for second look 
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by Xvani on 2007-03-22
Uhm.. KDE is definately installed, its the "system settings" menu that does not.

---

### Post by Xvani on 2007-04-07
bump :)

---

### Post by Xvani on 2007-04-14
so what ur saying is that there is no solution to this?

---

### Post by therandman on 2007-05-07
Check [this]("http://kb.mozillazine.org/Default_mail_client") out, 

Scroll down to "Setting Firefox's email client"

Follow directions except use "mozilla-thunderbird" instead of "kmail" (without quotes).

---

### Post by Xvani on 2007-05-23
Actually, Opera is my preferred browser, although I am still using thunderbird (for now) - when opening links in thunderbird, it opens firefox... (I have that installed too)

Kopete opens Konqueror when viewing my inbox.

So:
How do I make them both open Opera? (Or at least Kopete opening FF...)

---

### Post by teknosexual on 2007-05-29
> **Xvani said:**
> So: How do I make them both open Opera? (Or at least Kopete opening FF...)

Some applications don't bother to check KDE's preferences. All KDE applications should check (Kopete, for example). So give this a shot...

[LIST]
[*]Open a Terminal (or Konsole) and type **sudo kcontrol**
[*]Expand **KDE Components**
[*]Click **Email Client** and set your preferred client there 
[*]Click on **Web Browser** and set your preferred browser there
[*]Save/Apply all changes
[/LIST]

That should at least get all KDE applications to opening Opera and Thunderbird for you. For non-KDE applications you'll probably have to set your preferences within the application (if it's even an option).

---

