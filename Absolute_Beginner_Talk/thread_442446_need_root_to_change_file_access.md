---
title: "need root to change file access"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by DiJEH on 2007-05-13
I need to change my Wine/Steam folders access from Root to my user account so I can change the permissions.

The problem is I don't know how to change permissions, could someone give me a quick run down on how to change it please?

---

### Post by taurus on 2007-05-13
Use sudo if you need to access or change something outside your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by raylu on 2007-05-13
> **DiJEH said:**
> I need to change my Wine/Steam folders access from Root to my user account so I can change the permissions.

The problem is I don't know how to change permissions, could someone give me a quick run down on how to change it please?
chown changes the owner, chmod changes the permissions. taurus is correct, you should use sudo to do the first; the second can be done from your own account.

---

### Post by DiJEH on 2007-05-13
The problem is I don't know how to do this, hence why it's in beginner talk. :)

All I know is "Sudo COMMAND HERE" :(

---

### Post by taurus on 2007-05-13
What exactly are you trying to do?  Perhaps if you describe what you have in mind, moving files from so and so directory to so and so directory, maybe somebody can tell you exactly how to do it.

Again, changing permissions or ownership without knowing what you are going can trash your system.  Then, you would have a bigger problem then.

---

### Post by DiJEH on 2007-05-13
My steam folder in wine (user/.wine/program files/steam denies me access since I am not root. I need to change the permission on this folder so I can run steam.

---

### Post by taurus on 2007-05-13
_Assuming_ your login name is **john** (replace john with your actual login name, okay), do

```
sudo chown -R **john**:**john** /home/**john**/.wine
```

---

### Post by steve.horsley on 2007-05-13
Yes, but your .wine stuff should be yours anyway. There is something else going on here. How come they're owned by root? Is he trying to modify /root/.wine? We need more details to be sure.

---

### Post by aysiu on 2007-05-13
> **steve.horsley said:**
> Yes, but your .wine stuff should be yours anyway. There is something else going on here. How come they're owned by root? Is he trying to modify /root/.wine? We need more details to be sure.
Probably because of running a graphical application with *sudo* instead of *gksudo*:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

