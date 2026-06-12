---
title: "[SOLVED] Can't install firestarter or guardog in Kubuntu"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by astromech on 2007-07-21
When I try to install firestarter or guardog  firewalls adept says it will "break install' is there any way to install firestarter?

---

### Post by swoll1980 on 2007-07-21
try "sudo apt-get install" in terminal do not include pakage name this clears up some dependency problems see if that works I dont know if it will or not after that do same command but add a space then " firestarter"

---

### Post by Al3xK3aton on 2007-07-21
Step 1: Provide more details; it's not really clear what the problem is.

---

### Post by astromech on 2007-07-21
> **Al3xK3aton said:**
> Step 1: Provide more details; it's not really clear what the problem is. O.k I had already tried apt-get for firestarter also and it didn't work ,but i just tried it again and here are the results  :


Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  firestarter: Depends: libatk1.0-0 (>= 1.9.0) but it is not installable
               Depends: libavahi-glib1 (>= 0.6.0) but it is not installable
               Depends: libbonobo2-0 (>= 2.13.0) but it is not installable
               Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
               Depends: libgconf2-4 (>= 2.13.5) but it is not installable
               Depends: libglade2-0 (>= 1:2.5.1) but it is not installable
               Depends: libgnome-keyring0 (>= 0.4.3) but it is not installable
               Depends: libgnome2-0 (>= 2.8.0) but it is not installable
               Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not installable
               Depends: libgnomeui-0 (>= 2.13.0) but it is not installable
               Depends: libgnomevfs2-0 (>= 2.13.92-0ubuntu4) but it is not installable
               Depends: libgtk2.0-0 (>= 2.8.0) but it is not installable
               Depends: libpango1.0-0 (>= 1.12.2) but it is not installable
               Depends: gksu (>= 0.8.5) but it is not installable
E: Broken packages

---

### Post by swoll1980 on 2007-07-21
try "sudo apt-get update" then do the apt-get install command with out a package  "sudo apt-get install" then "sudo apt-get install firestarter" see if that works. im no expert but iv had simular problems and this worked for me maby it will work for you

---

### Post by astromech on 2007-07-21
> **swoll1980 said:**
> try "sudo apt-get update" then do the apt-get install command with out a package  "sudo apt-get install" then "sudo apt-get install firestarter" see if that works. im no expert but iv had simular problems and this worked for me maby it will work for you


Yeah, I tried that a few minutes ago and posted the results.What I just realized is that I forgot to do "apt get upgrade" maybe that will help .I'll do that then try again I will post results when I'm done.It might take a while (on dial up).

---

### Post by astromech on 2007-07-22
> **astromech said:**
> Yeah, I tried that a few minutes ago and posted the results.What I just realized is that I forgot to do "apt get upgrade" maybe that will help .I'll do that then try again I will post results when I'm done.It might take a while (on dial up).


Well, what else can I say but: DUHH! . I think I will chalk this one up to lack of sleep!  In Kubuntu the repositories are not enabled by default as they are in Ubuntu.My mistake; I assumed they would be . Did all the updates then installed firestarterand Firefox.These two should really be installed by default.The repos should also be enabled like they are in Ubuntu.How many would not want them enabled?


Thank you to all who responded!

---

