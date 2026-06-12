---
title: "Running a sudo command"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by uniuk2000 on 2008-04-19
I'm experiencing problems with connecting to my wireless network. Before I can connect to internet I have to run (in Terminal) 'sudo ifup eth1'
My question is "is there an automated way to run this command when I start ubuntu? By the way, I'm running ubuntu 8.04 but had similar problem with 7.10

---

### Post by natirips on 2008-04-19
Try adding it under system->settings->sessions (I think, I have a localized version of ubuntu)

---

### Post by StOoZ on 2008-04-19
im not sure, you should wait for someone which is more experienced, but my wild guess is that it should be entered here:
/etc/network/interfaces

insert "ifup eth1" in that file.
can anyone confirm this??
this is not the startup file, but still , I guess it belongs there

---

### Post by cardinals_fan on 2008-04-19
> **StOoZ said:**
> im not sure, you should wait for someone which is more experienced, but my wild guess is that it should be entered here:
/etc/network/interfaces

insert "ifup eth1" in that file.
can anyone confirm this??
this is not the startup file, but still , I guess it belongs there
I believe that that is correct for Debian-based systems...

---

### Post by StOoZ on 2008-04-19
Ubuntu is debian based , so basically , if my assumption is correct, you should open for edit that file (/etc/network/interfaces) with super user permission and add that line in there.

---

### Post by uniuk2000 on 2008-04-19
Thanks for your replys. Looking at the contents of that file would suggest that this is the right place. The problem I now have is when I come to save the modified file it won't let me. What is this 'super user permission'? How do I use it?

---

### Post by natirips on 2008-04-19
Super user /root permission usage:
"sudo command" for example. Or "su" than "command". Or "gksudo command" etc. I personally recommend the first one (just add the word "sudo " in front of a command).

---

### Post by uniuk2000 on 2008-04-19
Thanks guys, this didn't solve the problem but it's given me a starting point. I'll see how it goes from here.

---

