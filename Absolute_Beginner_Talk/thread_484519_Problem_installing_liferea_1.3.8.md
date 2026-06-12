---
title: "Problem installing liferea 1.3.8"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by tolremeno on 2007-06-25
This is my first week on Linux, so sorry for the n00b question.

I want to install the development version of liferea - 1.3.8. But when I try, I get this at the end of the install/config.log:

> *** You must have either the GtkHTML2, XulRunner or the Mozilla
*** development libraries installed in order to build Liferea!

The make command then gives a file not found error. Any help?

---

### Post by p_quarles on 2007-06-25
Why do you want to install the development version? I use the stable version (1.2.10) and it works very well. Plus, it's available in the repositories. Just open a terminal and type ```
sudo apt-get install liferea
```

If you're new to Linux, you should go for the stable version, not the development.

---

### Post by Seisen on 2007-06-25
You can install it using apt

```
sudo apt-get install libgtkhtml2-dev libgtkhtml2-0
```

---

### Post by BobCFC on 2007-06-25
I used to use liferea... it is one of the best but like all offline readers it only picks up your feeds while you computer is switched on.  If you have any downtime you will miss stuff.

Google Reader picks up your feeds 24x7 and lets you scroll back into infinity to read stories before you even subscribed.  Also the *river of news* effect marks stories as read as you scroll down your inbox so no clicking.

---

### Post by p_quarles on 2007-06-25
> **BobCFC said:**
> I used to use liferea... it is one of the best but like all offline readers it only picks up your feeds while you computer is switched on.  If you have any downtime you will miss stuff.

Google Reader picks up your feeds 24x7 and lets you scroll back into infinity to read stories before you even subscribed.  Also the *river of news* effect marks stories as read as you scroll down your inbox so no clicking.
The current stable version, actually, picks up everything you haven't seen since you last logged in. 

IMHO: It's better than Google because A) It doesn't track what you're reading, and B) It's not censoring things in China.

---

### Post by BobCFC on 2007-06-25
What I mean is some sites only put the last 10 or so items in the feeds.  It depends how long your downtime is.  As google checks millions of feeds every few minutes it grabs everything so I can take a break for a week if I want.

---

