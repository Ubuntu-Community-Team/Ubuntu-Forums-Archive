---
title: "Website Containing Certain Java Content Won't Load In Ubuntu"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Kralnor on 2007-08-21
I have a relatively simple problem.

Whenever I try to load the site [http://www.aktivsuperaarhus.dk/](http://www.aktivsuperaarhus.dk/) in WinXP it loads fine but in Ubuntu it hangs at "Waiting for..."

I'm running 7.04 Feisty Fawn and have updated with the latest Java version, using Firefox.

I suspect it's some Java content that might be getting blocked.

What's going on?

---

### Post by nitro_n2o on 2007-08-21
Do you have the java plug in for firefox?
sudo apt-get install sun-java6-plugin

---

### Post by alienexplorers on 2007-08-21
I tried the page you are having trouble with and it worked fine.  Are you sure you have the link for the java plugin in your firefox plugin directory.

---

### Post by Kralnor on 2007-08-21
Cheers. I didn't have the Java plugin installed.

However, the page still won't load.

> **alienexplorers said:**
> I tried the page you are having trouble with and it worked fine.  Are you sure you have the link for the java plugin in your firefox plugin directory.

How do I make sure the link is present?

EDIT: I should probably mention that I am able to use Java-based online banking in Firefox without any problems.

---

### Post by ItsAmazazazing on 2007-08-21
I;m having problems with the DVD issues that everyone else has posted here. I've tried all the comments that were left, and I still can't play a DVD in either Totem or MPlayer. I don't think I have a decoder, but I can't seem to find one either.....any ideas?

---

### Post by Trampis on 2007-08-21
post deleted for idiocy

---

### Post by Kralnor on 2007-08-22
> **ItsAmazazazing said:**
> I;m having problems with the DVD issues that everyone else has posted here. I've tried all the comments that were left, and I still can't play a DVD in either Totem or MPlayer. I don't think I have a decoder, but I can't seem to find one either.....any ideas?

Say what?

---

### Post by WebSiteGuru on 2007-08-22
> **ItsAmazazazing said:**
> I;m having problems with the DVD issues that everyone else has posted here. I've tried all the comments that were left, and I still can't play a DVD in either Totem or MPlayer. I don't think I have a decoder, but I can't seem to find one either.....any ideas?

Hurh? Wrong forum.

---

### Post by Vadi on 2007-08-22
> **Kralnor said:**
> Cheers. I didn't have the Java plugin installed.

However, the page still won't load.



How do I make sure the link is present?

EDIT: I should probably mention that I am able to use Java-based online banking in Firefox without any problems.

The easiest way for me to install java (and flash) was to install the restricted package, and it set up all the links needed itself. Search for "restricted" in the add/remove program.

---

### Post by Kralnor on 2007-08-22
> **Vadi said:**
> The easiest way for me to install java (and flash) was to install the restricted package, and it set up all the links needed itself. Search for "restricted" in the add/remove program.

I grabbed the package called "Ubuntu restricted extras" but that did not seem to resolve the issue.

---

### Post by Vadi on 2007-08-22
:/

Another way is to try and install Java via the instructions on their site, but I found them somewhat confusing... I'll see what else I can help with though.

---

### Post by Kralnor on 2007-08-22
Aye I tried that as well although I got an error at some point.

I'll try to give a more detailed explanation soon.

---

### Post by Vadi on 2007-08-23
What I would try in your case would go to the synaptic package manager, search for "java" and remove and package labelled with it that you have installed. And then install the restricted drivers from the add/remove.

---

