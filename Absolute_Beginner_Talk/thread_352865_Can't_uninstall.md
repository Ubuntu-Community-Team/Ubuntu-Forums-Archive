---
title: "Can't uninstall"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Chuckmeister on 2007-02-03
Hi :) I have just installed Ubuntu and came across a post here for Automatix. I installed it but I accidently installed the breezy version instead of the dapper version. I am now having problems uninstalling. I have looked under the add/remove app but Automatix does not appear on the list. When I click on automatix, it just comes up with a page saying that it will only work with breezy and locks on that page with no option or reference on how to uninstall.
Could someone please help me with how to remove this so that I can install the correct version??

Thanks
Chuck :)

Sorry for the noob question:confused:

---

### Post by %hMa@?b&lt;C on 2007-02-03
> **Chuckmeister said:**
> Hi :) I have just installed Ubuntu and came across a post here for Automatix. I installed it but I accidently installed the breezy version instead of the dapper version. I am now having problems uninstalling. I have looked under the add/remove app but Automatix does not appear on the list. When I click on automatix, it just comes up with a page saying that it will only work with breezy and locks on that page with no option or reference on how to uninstall.
Could someone please help me with how to remove this so that I can install the correct version??

Thanks
Chuck :)

Sorry for the noob question:confused:
what comes up when you type in terminal/konsole 
aptitude search automatix

---

### Post by Chuckmeister on 2007-02-03
Hi. It comes up with....

i   automatix2     - Automatix is a graphical interface for automating the installation of the most commonly requested

Chuck :)

---

### Post by taurus on 2007-02-03
Applications -> Accessories -> Terminal
```
sudo aptitude remove automatix2
```

---

