---
title: "updating manually installed azureus"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by erlingwl on 2007-03-28
Hi,

I'm fairly new to ubuntu. However I managed to install Azureus manually a few weeks ago, because it wouldn't work if I installed it with Synaptic. (there is lots of info on this "bug" around the web). 

My problem is that Azureus checks for updates, downloads the updates, but fails to install them. It says "Permission denied". So what do I do wrong? Do I have to log in as root to install the update, or has this something to do with my manual installation of Azureus? Is there a way to update Azureus manually to?

All help is appreciated ;)

---

### Post by nudnik on 2007-03-28
> **erlingwl said:**
> Hi,

I'm fairly new to ubuntu. However I managed to install Azureus manually a few weeks ago, because it wouldn't work if I installed it with Synaptic. (there is lots of info on this "bug" around the web). 

My problem is that Azureus checks for updates, downloads the updates, but fails to install them. It says "Permission denied". So what do I do wrong? Do I have to log in as root to install the update, or has this something to do with my manual installation of Azureus? Is there a way to update Azureus manually to?

All help is appreciated ;)

It wont install as it does in Windows because you and (if everything is working properly) anything else is attempting to perform tasks which require root permission in standard user mode. This is actually a good thing, because it prevents nasty files from having their way with your system. Unfortunately it does make things a bit more complex for the proper user. 

You will have to log in as root using the Terminal, uninstall your old Azureus and replace it with the latest version. There may be a way to program the system to do this automatically using the CLI, but I am unaware of any. You'll be doing a lot of this sort of thing with Ubuntu. Its the price we pay for such a secure system.

---

### Post by kolenkolen on 2007-12-03
> **erlingwl said:**
> Hi,

I'm fairly new to ubuntu. However I managed to install Azureus manually a few weeks ago, because it wouldn't work if I installed it with Synaptic. (there is lots of info on this "bug" around the web). 

My problem is that Azureus checks for updates, downloads the updates, but fails to install them. It says "Permission denied". So what do I do wrong? Do I have to log in as root to install the update, or has this something to do with my manual installation of Azureus? Is there a way to update Azureus manually to?

All help is appreciated ;)

I have the same problem.

---

