---
title: "restore/reinstall?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by 02wrx on 2007-04-25
Hi,

I've been using Edgy 6.06 for a couple of weeks.  I was fooling around and trying to install some themes.  Long story short, I added gtk 2.0 (i think?) and now have lost terminal and add/remove programs button...so i can't do anything!  Is there a way to restore the system to an earlier point to fix this, or a step-by-step way?

Before I lost add/remove, I was trying to undo everything I had done in the "History" but it wouldn't allow me to install Terminal for some reason.  Also, I installed Ubuntu package?

Please help...
Thanks!

---

### Post by igknighted on 2007-04-25
try hitting alt+F2 to open the run dialog, then type in "terminal", no quotes.  It should load up the terminal for you.  If it does, than all you need to do is right click the applications menu and click edit and re-add the terminal to it.

---

### Post by 02wrx on 2007-04-26
When I run terminal using ALT + F2, I get the following error:
Could not open location 'file:///terminal'
The location or file could not be found.

How do I re-install terminal?  I also am missing the Add/Remove Programs!!! Do I need to re-install the whole system? :confused:  And if I do, how can I keep the files in my home folder?

---

### Post by igknighted on 2007-04-26
> **02wrx said:**
> When I run terminal using ALT + F2, I get the following error:
Could not open location 'file:///terminal'
The location or file could not be found.

How do I re-install terminal?  I also am missing the Add/Remove Programs!!! Do I need to re-install the whole system? :confused:  And if I do, how can I keep the files in my home folder?

While the system certainly COULD be fixed, the work sounds like it would be enormous.  I might go ahead and reinstall for a fresh start.  To back up your home folder, either burn it to a disk (and then copy/paste it to your new /home folder) if it is on the same partition, or if you set it up as a separate partition, simply use you old partitions, setting the proper mount points (/ and /home) and choose to format / but not /home.  Then use the same username/password as before.

---

### Post by 02wrx on 2007-04-26
Thanks, I figured this would probably be the easiest method.  Can you please give further direction on how to do the mounting/partitioning so I can keep my home folder?  i.e. is this done in Ubuntu before re-installing or during the install? and what are the steps....?  I have downloaded about 10GB of stuff and would like to reinstall without burning.

---

### Post by Vaidya on 2007-11-07
Well,  the post above yours explains what you want in part:

What you need to figure out is where your /home is, if is in a separate partition, then you are better off, else you need to back up /home.

using installer, you will get option to format, here if you have 2 partitions, / and / home, uncheck /home (hence it will not format the same, use the same login and password you used earlier and you should be home.

---

