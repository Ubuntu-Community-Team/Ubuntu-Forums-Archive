---
title: "ok to edit sudoers for logout shortcut workaround?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by DMcA on 2007-07-25
Having just installed feisty I was getting annoyed with the “logout” keyboard shortcut not working and found this bug: 

[https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/71620](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/71620)

as a workaround I added the following to the end of my /etc/sudoers file and then added the necessary custom commands via gconf-editor:

```
%admin   ALL=(ALL)     NOPASSWD: /sbin/poweroff
%admin   ALL=(ALL)     NOPASSWD: /sbin/reboot 
```

This seems to work fine and it's also quite cool because I can add icons for shutdown and restart to replace those that disappear after installing xgl. However, I was wondering how safe it is. Presumably shutdown requires a password-protected sudo for a good reason, but then when you use the graphical shutdown button no password is normally required. Is there some way I can improve this, say by making just one user able to shutdown without a password, or should it not be done at all?

Sorry if this is in the wrong forum, this is the first time I've asked a question here.

---

### Post by Arisna on 2007-07-25
I think administrative access is normally necessary to shutdown/reboot from command line because it would be a problem on large, multi-user systems if anyone could just take the system down at any time, since it would interfere with other users.  On a desktop system, this shouldn't be a concern.

---

### Post by DMcA on 2007-07-25
cool, thanks.

I was worried about someone being able shut me down maliciously by remote but if that's not a concern, all's good.

---

### Post by por100pre1 on 2007-07-25
I remember myself doing that for shutdown and firestarter startup...
```

%admin ALL=(ALL) ALL

por100pre1 ALL= NOPASSWD: /usr/sbin/firestarter
por100pre1 ALL= NOPASSWD: /sbin/shutdown

```

---

### Post by Nythain on 2007-07-25
yeah... if its a single user desktop system i wouldnt worry about it... i put apt-get, aptitude, shutdown, and reboot in my sudo'ers list

---

### Post by DMcA on 2007-07-25
great, thanks all.

---

