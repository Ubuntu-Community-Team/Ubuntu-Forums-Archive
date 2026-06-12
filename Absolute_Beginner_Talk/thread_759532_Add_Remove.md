---
title: "Add Remove"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Sanoski on 2008-04-19
Strange problem; it just started happening. When I click 'Add/Remove' under applications, something weird happens. It populates ok, but if I try to add or remove anything it gives me the following error.

[B]
An error occured[/B]

_The following details are provided:_
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Does anyone understand this?

---

### Post by bumanie on 2008-04-19
Type > sudo dpkg --configure -a followed by enter into terminal and it should download the rest of the package you were installing. That message appears when there has been an interruption to a package download.

---

### Post by Sanoski on 2008-04-19
never mind....

I did what it told me to do, and now it works.

---

### Post by Sanoski on 2008-04-19
> **bumanie said:**
> Type  followed by enter into terminal and it should download the rest of the package you were installing. That message appears when there has been an interruption to a package download.

Yea thanks, bro. But I figured it out. I should really pay more attention.

---

