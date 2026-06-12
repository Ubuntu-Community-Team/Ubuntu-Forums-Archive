---
title: "Screenlets Help"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-06-29
Hey! I just installed and started Screenlets, but I have no idea to launch a desklet. :P

I typed this in:

Code:

alec@AlecDesktop:~/screenlets-0.0.7$ screenletsd add control
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
No handlers could be found for logger "dbus.proxies"
Error: Screenlets-Backend (screenletsd) not found.


What's wrong; how do I get them workiing?

---

### Post by supersonicdarky on 2007-06-29
```
screenlets-control
```

---

### Post by alecwh on 2007-06-29
Sorry? I typed that in and I got:

alec@AlecDesktop:~$ screenlets-control
bash: screenlets-control: command not found
alec@AlecDesktop:~$

---

### Post by supersonicdarky on 2007-06-29
works for me =/

```
kernel@laptop:~$ screenlets-control
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL

```

and then a window pops up

---

### Post by alecwh on 2007-06-29
where did you downlload it?

---

### Post by supersonicdarky on 2007-06-29
i added the repos
[quote=http://hendrik.kaju.pri.ee/screenlets/?q=node/5]
Alternatively, there is a debian repository for i386 and amd64 available with the latest version. To use it please add the following to your sources.list file:

deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) edgy screenlets
or
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
if you are using feisty.

Then run this in a terminal:

wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then you can install screenlets with 'sudo apt-get install screenlets'. The package also includes updated third-party screenlets and utilities (Control panel, tray-icon)
[/quote]

---

### Post by fontenot_1031 on 2007-07-01
Hmm, I got Screenlets working, but the problem is that, for example, the Clock had no hands and the CPU tempeture thing did not change.  However the CPU perentage thing did change

---

