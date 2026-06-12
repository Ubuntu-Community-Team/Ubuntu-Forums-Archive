---
title: "adept installer help"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-12-16
I tried to go into the adept package manager, after my text installation of Kubuntu.

this is the error message:The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.

I tried the command
```
sudo apt-setup
```
and the command 
```
sudo apt-get update
```

The first one told me that Konsole couldn't find the command.

The second downloaded a bunch of updates, but when I went to install them, Adept gave me the same error message.

Can someone help, please?

---

### Post by Capricori on 2007-12-17
Hmm, I've never heard of the apt-setup command... peculiar.

But, [this]("http://ubuntuforums.org/showthread.php?t=163720") thread talks about the same problem, and offers a solution. Run 'sudo debtags update' in a terminal, should fix the issue.

Regards, 

Capricori

---

