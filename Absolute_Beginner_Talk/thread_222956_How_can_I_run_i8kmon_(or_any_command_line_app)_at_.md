---
title: "How can I run i8kmon (or any command line app) at boot?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Zoinks on 2006-07-25
I'm running dapper on a Dell 700m laptop and using the i8kmon daemon from the command line to keep the fans running properly.  This works, but I'd like the system to launch i8kmon automatically in the background upon bootup, whether I login to Gnome or not, etc.

Can I do this?  Thanks!

---

### Post by NewDisciple on 2006-07-25
Look at the readme file and you will find:To have the module loaded atomatically at boot you must manually add the
line "i8k" into the file /etc/modules or use the modconf utility, if
available in your distribution, and select the i8k module.

---

### Post by Zoinks on 2006-07-30
That just loads the i8k module (I think?) but does not seem to activate the i8kmon daemon, and not with the specific settings I need.

Let's make this more general - what's the normal way to launch a daemon or command line app at startup on a linux system?

---

### Post by Mike Tomasello on 2006-07-30
> **Zoinks said:**
> That just loads the i8k module (I think?) but does not seem to activate the i8kmon daemon, and not with the specific settings I need.

Let's make this more general - what's the normal way to launch a daemon or command line app at startup on a linux system?
System->Preferences->Sessions->"Startup Programs" tab, I believe. That's how I added checkgmail anyway. :)

---

