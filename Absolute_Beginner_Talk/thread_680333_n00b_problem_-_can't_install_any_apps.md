---
title: "n00b problem - can't install any apps"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by ridgeback on 2008-01-27
Hello!

I used Ubuntu Edgy a year ago very lightly but I couldn't get my wireless card to work so I gave up, but I recently was inspired to try again, and now my wireless is fine.  My sound now doesn't work, but that's not important.

PROBLEM:  I go into add/remove apps, and no matter what I try to install, I get this message:

"The list of applications is not available
Click 'Reload' to load it.  To reload the list you need a working internet connection."

I click Refresh, and it appears to do something with 6 files, checks installation, and I'm back to square one.  Any help would be greatly appreciated!!

Jerod

---

### Post by taurus on 2008-01-27
Sounds to me like you don't have any repo available in /etc/apt/sources.list.  Close Add/Remove and open synaptic in System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark on everything except the last line, Source code and Cdrom in the bottom window.  Close it and click Refresh.  

You should be good to go now.

---

### Post by ridgeback on 2008-01-27
Thanks a lot!!  Worked perfectly.  Dunno why that was off..

Jerod

---

### Post by taurus on 2008-01-27
Maybe because during the installing process, your network was either off or not working so the installer moved on.  Bet you got a message on the screen something about unable to check for security updates when you installed it!

---

### Post by rzrgenesys187 on 2008-01-27
> **taurus said:**
> Maybe because during the installing process, your network was either off or not working so the installer moved on.  Bet you got a message on the screen something about unable to check for security updates when you installed it!

So that's why they are always disabled on my system.  I can't set up the internet until I install.  I've always wondered why they were commented out.

---

