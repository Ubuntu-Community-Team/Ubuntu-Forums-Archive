---
title: "Desktop AND Server - Which Installer?"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by CharlieSummers on 2007-09-11
I know it's a silly question, and I looked around here but couldn't find a suggested method. I want to install a desktop system, which also contains LAMP for internal use (web-based calendar and such) not exposed to the Net at large (the only port on this machine exposed through the router to the world will be SSH). Is it better/easier/suggested to install the Desktop system then install the server parts, or install the Server then install the Desktop?

(I'm sure this isn't the first time this came up, but I couldn't find a suggested method. A pointer to an existing discussion on the issue would be sheepishly appreciated...)

---

### Post by mlentink on 2007-09-11
In your case I'd install desktop first, then Server. You don't seem to be using it for production purposes, so make it easy on yourself.

---

### Post by CharlieSummers on 2007-09-11
> **mlentink said:**
> In your case I'd install desktop first, then Server. You don't seem to be using it for production purposes, so make it easy on yourself.

Production, yes; high-volume, no. I should have mentioned that I'm familiar with linux (RH long before Fedora, Gentoo, others) although I have never before used Ubuntu (there are bets going on how long it will be before I add a password to the root account ;) and am using this machine to gain experience in this distro while using it internally. I've heard nothing but good things about Ubuntu, so I wanted to learn more about it, and actually *using* it on a daily basis seemed to be the best way.

Thanks for the advice!

---

### Post by KCPokes on 2007-09-11
Install the desktop.  At that point you are only talking about a few additional packages to set up your LAMP environment.  I only recommend this from the standpoint that it is an internal only webserver, otherwise you'd want to go server install with limited additions.

---

