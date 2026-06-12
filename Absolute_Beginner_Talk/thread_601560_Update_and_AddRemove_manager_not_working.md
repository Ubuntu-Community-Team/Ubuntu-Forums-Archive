---
title: "Update and Add/Remove manager not working"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by bbharatsony on 2007-11-03
When I go on the Add/remove programs app and I try to check an application to install the add/remove programs app says click reload and when I do the same thing happens again and again. Can someone help me with this?

---

### Post by taurus on 2007-11-03
What do you plan to install?  What happens if you try to install it from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install **package_name**
```

---

### Post by Hendrixski on 2007-11-03
> **bbharatsony said:**
> When I go on the Add/remove programs app and I try to check an application to install the add/remove programs app says click reload and when I do the same thing happens again and again. Can someone help me with this?

If you don't HAVE to reload then just go ahead and try installing something. It should just work.

If the Add/Remove program doesn't do the trick for you, there is also a similar program called Synaptic, which instead of mentioning a few programs, will mention hundreds and thousands of packages, It's found in the administrative menu.  If that is also doing something similar (with the reloading) then perhaps you have an internet problem, or you made some changes to your /etc/apt/sources.list file.

---

### Post by Hendrixski on 2007-11-03
> **taurus said:**
> What do you plan to install?  What happens if you try to install it from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install **package_name**
```

there's always the old-fashioned way of doing it from the terminal.

If you get an error message at the tail end of the "sudo apt-get update" command, then post it on here, and people will help you decipher it. :-)

---

