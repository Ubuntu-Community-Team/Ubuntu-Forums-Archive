---
title: "bleeding edge repository?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-07-31
is there a repository that contains the latest software updates? i would like to have the latest versions of my software (i.e. apache). i know ubuntu isn't necessarily set up for that, but i would like to make it so.

thanks for any help in advance!

---

### Post by benplaut on 2006-07-31
It's called Backports.  Uncomment it in your /etc/apt/sources.list   .

It's not really bleeding edge, but it's definately newer.  If you really want *bleeding* edge, this isn't the right distro.  Consider gentoo or arch.

---

### Post by shanepardue on 2006-07-31
well, not necessarily bleeding i suppose..i am not for a bunch of buggy programs, i just mean at least a newer apache version than .55. i would think at least .59 would be in there. i have backports already, but i guess that's the latest ubuntu offers?

don't get me wrong, i love ubuntu..i would just think simple software updates would be more frequent.

---

### Post by verbatim210 on 2006-07-31
if you want the latest apache, there is no need to do any of that
by default the manager will install the latest version

if in doubt... "sudo aptitude update"

cant remember if the sudo is necessary but it cant hurt

a tougher question would be, how to install the 2nd latest version.

---

### Post by shanepardue on 2006-07-31
> **verbatim210 said:**
> if you want the latest apache, there is no need to do any of that
by default the manager will install the latest version

if in doubt... "sudo aptitude update"

cant remember if the sudo is necessary but it cant hurt

a tougher question would be, how to install the 2nd latest version.
the latest apache i see is .55 not .59...am i missing something?

and apache isn't the only thing...stuff like picasa coming out for linux would be nice and stuff like that.

---

