---
title: "Firewall install help"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Trebuchet on 2007-03-25
I just installed Ubuntu 6.10 on my PC yesterday, and since I don't have a router I want to install a software firewall. I've seen Firestarter, but I'm not sure how to get it installed or even downloaded.

Can someone walk me through the process from download to finish? I'm a complete noob with regard to Linux, so I don't know *anything.* Assume you're trying to explain this to your mom. :redface:

---

### Post by mcduck on 2007-03-25
Go to System/Administration/Synaptic package manager, search for 'firestarter', right-click it and select 'Mark for installation' and then click the 'Apply'-button. That will install Firestarter for you. 

When it's finished installing go to System/Administration/Firestarter and start it. This will enable default configuration (it's good, no need to change anything) and set the firewall to start automatically on boot. That's it. :)

Alternatively, open a terminal, run 'sudo apt-get install firestarter' and then 'gksudo firestarter' to do the same thing from command line.

---

### Post by Trebuchet on 2007-03-25
Thanks! That worked just fine. :)

---

