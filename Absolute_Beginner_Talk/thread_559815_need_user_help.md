---
title: "need user help"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2007-09-25
Ok so I have finally convinced the univ that I work at to put a ubuntu machine in the lab. Because of the nature of the lab, Im working towards getting Ubuntu Studio on the machine.
I installed Ubuntu Studio, but the xorg was horrible. Like 300x200 resolution. I got it to 640x480, but it still looked terrible. So I figured the best way to get studio working well was to re-install off a live cd the base ubuntu system and update into the studio packages so I could get around the xorg problems.
Currently I have 780x1024 (or whatever is close to that) and that's fine.
However, in doing the re-install i transferred a user over (migration assistant) and the user name was miesner.
In the previous install, miesner was admin.
Now, as best I can tell, there are no admin privledges assigned to anyone.
Cant su anything. How do I create a user with admin priv?
Is there a back way around the fact of ubuntu not having a root user that a user w/o admin priv can edit?

Thanks guys,
Miesnerd

So in summary, Im on 7.04 and I dont know that any created account (only one account; miesner) can access admin priv.

---

### Post by skymera on 2007-09-25
you dont need an admin account.

admin rights can be temporarily gasined using Sudo and entering your passwod

---

### Post by lambros on 2007-09-25
Boot into recovery-mode (press Esc as the operating system starts to boot up, then choose one of the "recovery mode" kernels).  At the '#' prompt, enter these commands:

```
adduser miesner admin
reboot

```

Hope that helps,
Lambros

---

### Post by miesnerd on 2007-09-25
> **lambros said:**
> Boot into recovery-mode (press Esc as the operating system starts to boot up, then choose one of the "recovery mode" kernels).  At the '#' prompt, enter these commands:

```
adduser miesner admin
reboot

```

Hope that helps,
Lambros

Thanks man. Good to go.

---

