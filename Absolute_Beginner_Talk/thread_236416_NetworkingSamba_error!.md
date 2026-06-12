---
title: "Networking/Samba error!?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2006-08-14
So I go to Places -> Network Servers to get to my Windows shared folder, but when I click on the Windows Network, I get "'smb///' is not a valid location. Please check the spelling and try again." The problem just started and I have made no changes to my network! What does this error mean? I'm still not too familiar with how Ubuntu works on networking.

---

### Post by djsroknrol on 2006-08-14
First question (and none are stupid) is Samba installed?

If so, you might try this in Nautilus:

Open Nautilus

CTRL + "L" should open a address bar..type in:

```
smb///XXX.XXX.XXX.XXX
```

replacing the x's with IP of the other computer you're trying to connect to...if it connects, then you have a possible configuration problem with Samba. Check your networking settings in:

System>Administration>Networking as well

---

