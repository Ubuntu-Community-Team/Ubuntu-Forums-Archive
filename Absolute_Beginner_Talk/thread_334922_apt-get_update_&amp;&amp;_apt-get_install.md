---
title: "apt-get update &amp;&amp; apt-get install"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by bone2006 on 2007-01-09
I'm just kind of wondering why when I look at instructions, sometimes I see "apt-get update && apt-get install" and other times I see only apt-get install?

Is it better to do "apt-get update && apt-get install" instead?  I'm really not sure what the difference is, I thought that just doing apt-get would take the latest from the repository anyway, so what does the update first do?

---

### Post by justin whitaker on 2007-01-09
> **bone2006 said:**
> I'm just kind of wondering why when I look at instructions, sometimes I see "apt-get update && apt-get install" and other times I see only apt-get install?

Is it better to do "apt-get update && apt-get install" instead?  I'm really not sure what the difference is, I thought that just doing apt-get would take the latest from the repository anyway, so what does the update first do?

Yes, it's better to run apt-get update first.

Think of it like an external registry: there is a list of applications on the repository server which apt mirrors on your harddrive. Generally apt will grab the latest version of any application that is on the list, but if someone checks in something new, apt will not know it is there unless you update.

---

### Post by Sqwishy on 2007-01-09
'apt-get update' just checks for updates, 'apt-get upgrade' applies them!

---

### Post by tonyr1988 on 2007-01-09
To put it another way, "apt-get update" is like refreshing a webpage - you get the latest information (in this case, the newest packages from you repositories). You should ALWAYS, no exceptions, "apt-get update" after you change your repositories.

---

### Post by bone2006 on 2007-01-09
thanks everyone for clearing that up for me

---

