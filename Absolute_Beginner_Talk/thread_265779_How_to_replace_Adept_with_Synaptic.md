---
title: "How to replace Adept with Synaptic?"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by ccheaton on 2006-09-26
Hi, I'm using Kubuntu and would like to use Synaptic instead of Adept.  What is the proper order for making the switch?  Remove Adept first and then apt-get installl synaptic?  Install Synaptic first?  I just want to make sure that I don't mess things up by doing it in the wrong order.

---

### Post by Bachstelze on 2006-09-26
Heh, *sudo apt-get install synaptic* :)

And do **not** remove Adept.

---

### Post by aysiu on 2006-09-26
Why not remove Adept?

```
sudo aptitude update
sudo aptitude install synaptic
sudo aptitude remove adept
``` You'll be warned you're uninstalling *kubuntu-desktop*, and that's fine. Just make sure you reinstall it before you upgrade to Edgy.

---

### Post by Bachstelze on 2006-09-26
It was the safe bet, I was unsure about whether it would remove some KDE important stuff.

---

### Post by Marsolin on 2006-09-26
The main reason to not remove Adept is that it runs the automatic update notification. If you don't care about that I don't see any problem.

---

### Post by ccheaton on 2006-09-26
Ok, thanks.  What is the different between apt-get and aptitude?

---

### Post by aysiu on 2006-09-26
> **ccheaton said:**
> Ok, thanks.  What is the different between apt-get and aptitude?
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

