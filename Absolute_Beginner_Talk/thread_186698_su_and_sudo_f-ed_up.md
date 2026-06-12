---
title: "su and sudo f-ed up"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-06-02
sudo anything doesnt work as well as su, i installed dabber made me account called administrator then tried su, dont work wdf, i tried doing sudo hostname ubuntu to change it to @ubuntu but sudo says command not found when i try hostname ubuntu says permission denied log in as another user.

:confused: :confused: :confused:

---

### Post by Jussi Kukkonen on 2006-06-02
First, it would be nice if you clearly included the full commands you tried and the error messages you received. Helping is quite difficult if one has to decipher what happened first...

Now, there is obviously something that has gone wrong with your setup. Please run e.g. *sudo hostname* on your original (first) user account. If you get errors copy-paste them here.

General advice: If you just want a root console, use
```
sudo -i
```
If you really, really want to enable root account, do this 
```
sudo passwd root
```
This is all explained in [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Ben Sprinkle on 2006-06-02
ok ty ill try it when i get home, what happened was i typed in 'sudo hostname ubuntu' i got error command not found

---

### Post by bluefrog on 2006-06-02
hostname has to be run under root console not sudo.

so sudo -i then hostname

James

---

