---
title: "how to install when no graphics visible?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-09-09
yesterday I got the following error msg

/etc/x11/x is not executable .... the X server is now disabled. Restart GDM when it is configured correctly. (see my thread yesterday)



SInce I have not been able to do such, ie recongifure it I was wonderig if I could just install?

I was going to upgrade from Dapper to Fesity next week. Might as well do it now...

but I really do not know what do do when I have no graphic interface...

...



so, how can I do it?

robi

---

### Post by artir on 2007-09-09
when you see something like username@youtcomputer:
(use control+alt+f1) enter sudo dpkg-reconfigure xserver-xorg
Then click accept like a crazy man and let the installer select the dafaults

---

### Post by swoll1980 on 2007-09-09
y

---

### Post by beanco on 2007-09-09
> **artir said:**
> when you see something like username@youtcomputer:
(use control+alt+f1) enter sudo dpkg-reconfigure xserver-xorg
Then click accept like a crazy man and let the installer select the dafaults

this is what I got


[HTML]perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
Language = "en_AU:en",
LC_ALL = (unset),
LANG =en_AU.UTF-8"

are supported and sintalled on your system.

perl: warning: falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory /usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed[/HTML]

---

### Post by beanco on 2007-09-09
bump


anybody out there?

---

### Post by steve.horsley on 2007-09-09
I think it's time to install Feisty. Your existing setup seems badly broken. You could use the command line to copy your important data to a USB disk before reinstalling.

---

### Post by beanco on 2007-09-10
Thanks Steve,


I got feisty up and running... still some things to sort out... but at least i have a machine I can work on.

robi

---

