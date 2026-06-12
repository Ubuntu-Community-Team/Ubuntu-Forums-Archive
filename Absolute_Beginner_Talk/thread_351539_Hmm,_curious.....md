---
title: "Hmm, curious...."
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2007-02-02
Hey guys, guess what! I have a problem again! I was trying to adjust the time the GRUB menu was up for upon boot, but gedit wouldn't let me edit the file because I "didn't have permissions to edit or delete the selected file". I am the only user on this computer, and I am the administrator, so it should work.

Help would be appreciated,

---

### Post by Bachstelze on 2007-02-02
From a terminal or the Run dialog :

```
gksudo gedit /boot/grub/menu.lst
```

will prompt for your password and open the file in gedit with root privileges. You are not in Windows anymore, the account you use for daily tasks does *not* have permission to access the system files.

---

### Post by sloggerkhan on 2007-02-02
you can always type:
$sudo command 
to do to it as an administrative user.
I believe if it bothers you enough, you can set up launchers to include sudo.

---

### Post by ardchoille42 on 2007-02-02
> **sloggerkhan said:**
> you can always type:
$sudo command 
to do to it as an administrative user.
I believe if it bothers you enough, you can set up launchers to include sudo.

Just a suggestion, using sudo with GUI apps can be quite dangerous: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by tbasherizer on 2007-02-02
Thanks guys. YEah, I just got back from playing halo on my windows partition, so it may take a day to get back used to Ubuntu again.

---

### Post by sloggerkhan on 2007-02-02
so I guess use launchers with gksudo
and command line with sudo.
Didn't realise using sudo was bad in that instance. Thnks.

---

