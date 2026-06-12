---
title: "Linux Init Process / PC Boot Procedure info"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by bmachia on 2008-04-01
I’m looking to read/learn about the ‘Init Process / PC Boot Procedure’ for Ubuntu/Kubuntu.  A Heavy IBM Unix friend suggested this link; [http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)

But, the link specifically says the information is primary for Redhat and Fedora and other distributions often differ.

Can anyone tell me how different Ubuntu is from this document, or suggest another link for Ubuntu/Kubuntu?

Bill

---

### Post by Cypher on 2008-04-01
THose setps are good until #4 where it says the Linux looks for /sbin/init. In Ubuntu, [upstart]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fupstart.ubuntu.com%2F&ei=wULyR97nDKbgigG9sc2NAQ&usg=AFQjCNF5bjGZVKjKSontHnVXBHQoQ2lm5g&sig2=4UnwdYmS6wVzDM74tkJaHw") replaces that and loads the run-level scripts.

---

