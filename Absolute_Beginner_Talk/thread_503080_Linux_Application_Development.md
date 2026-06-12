---
title: "Linux Application Development"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by wilkesalex on 2007-07-17
Hello there,

I am looking to create an application (it's a *AMP bundle for Windows, Linux and Mac OS X).

With Windows, I used C++. With Mac OS X I used Cocoa.


What tool(s) should I use for writing such an application with ubuntu linux?

My main question is do I need to write / compile a different version for GNOME or KDE desktops?

Can someone explain to me how I can write an application that will display similar in GNOME or KDE?

Im a very big linux noob.


TIA
Alex

---

### Post by xen on 2007-07-17
There are many different toolkits you could use to develop your application. If you are looking for GNOME integration I suggest that you use GTK. If you are looking for KDE integration then I would use QT. You could also use wxWidgets which is useful for developing cross-platform applications.

GTK applications can also be ported to Windows fairly easily due to the Windows GTK runtime that can be installed.

---

### Post by LaRoza on 2007-07-17
> **wilkesalex said:**
> Hello there,

What tool(s) should I use for writing such an application with ubuntu linux?

My main question is do I need to write / compile a different version for GNOME or KDE desktops?

Can someone explain to me how I can write an application that will display similar in GNOME or KDE?

1. for C++ use g++, ```
sudo aptitude install build-essential
```
2. If you use ansii compliant code, no.
3. I have no experience in GUI programming, but KDE and GDE app usually work fine in the other DE.

You might get more information in the programming talk forum.

---

