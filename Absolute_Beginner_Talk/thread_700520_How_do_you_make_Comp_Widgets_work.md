---
title: "How do you make Comp Widgets work?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Nick8692 on 2008-02-18
is it possible to have comp widgets working without an internet connection? :confused:
if so how?

Thanks

---

### Post by Nick8692 on 2008-02-18
and what is the difference between screenlets and widgets?
what would you recommend? :confused:

---

### Post by Nick8692 on 2008-02-19
(bump)

---

### Post by Nick8692 on 2008-02-20
(bump)

---

### Post by Nick8692 on 2008-02-22
i don't think anyone really knows :(

---

### Post by PeterJS on 2008-02-22
> **Nick8692 said:**
> is it possible to have comp widgets working without an internet connection? :confused:
if so how?

Thanks

Probably not, if they aren't installed now, they need to come from some where, that some where is traditionally the internet. If you've got a bit of free time and are willing to put up with a bit of aggravation, because it's going to take a couple of iterations of trial and error, you could download the debs to a flash drive, ferry them over and do the dependency resolution by hand.

> **Nick8692 said:**
> and what is the difference between screenlets and widgets?
what would you recommend? :confused:

Widgets is a broad category that can describe any number and type of on screen elements, and takes on different meanings in different contexts. When talking about GTK themes, widgets describe things like buttons, scroll bars, tabs, text input fields, etc. Your question is getting at the idea of Desktop Wdigets, which more people know about and so they tend to use the terms widget and desktop widget interchangeably (don't mind my grumbling this is just my least favorite element of langauge). Desktop widgets are any group of graphical interactive things that can be placed on the desktop above or below existing windows, that with the advent of compiz can also be put on a floating invisible layer you can make visible at will.

Screenlets are a specific group of widgets that all use a common core set of libraries and are written in python.

So you can't just get "widgets" because they are an abstract concept, but in getting screenlets you will have a set of desktop widgets.

---

