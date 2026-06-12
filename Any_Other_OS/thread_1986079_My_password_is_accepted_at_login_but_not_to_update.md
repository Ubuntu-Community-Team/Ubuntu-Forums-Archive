---
title: "My password is accepted at login but not to update or run sudo!"
date: 2012-05-24
forum: Any Other OS
---

### Post by Rytron on 2012-05-24
Hi.

Hi. I just installed Linux Mint 13 Cinnamon. I can login in but it wont accept my password to update. It seems my login password is different to my sudo password. I installed with manual partitions but did not format /home. I previously ran Ubuntu 10.04.

Also it would not accept my password for the keyring. How can I get to add a new keyring password?

---

### Post by Perfect Storm on 2012-05-24
Moved to Other OS/Distro Talk.

---

### Post by papibe on 2012-05-24
Hi Rytron.

It looks like a case of mis configured gksudo (the graphical sudo). Go into a terminal and run:
```
gksu-properties
```
It'll open a window. Under Behavior there's a field called 'Authentication mode'. If it says su, change it to sudo.

I hope it helps,
Regards.

---

### Post by Haneef Mubarak on 2012-05-25
If it worked, please change the topic prefix to [SOLVED]. This helps us keep track of what still hasn;t been solved.

---

### Post by Rytron on 2012-05-26
I reinstalled LM 13 and have not had the same problem. Therefore I cannot know if it would have worked or not. Although it more than likely should have. If anyone else can confirm it then please leave a comment and I will mark this thread as solved. Thanks.

---

