---
title: "Cannot use my password"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by locosmurf on 2007-02-21
Can anyone help me? I tried to intall kdelibs4c2a_3.5.5a.dfsg.1-6_i386.deb and got a dependency problem. when I tried to open adept and install the missing package, I wasn't able to use my password. I am still able to login but I cannot do any administrative tasks. Is there a way to fix this?

---

### Post by taurus on 2007-02-21
What's the output of this command from a terminal?

```
id
```
Which release are you running right now, dapper or edgy?

---

### Post by locosmurf on 2007-02-21
edgy

---

### Post by taurus on 2007-02-21
> **locosmurf said:**
> edgy

And the output of that command?

---

### Post by locosmurf on 2007-02-21
sorry about that

uid=1000(smurf) gid=1000(smurf) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),113(admin),1000(smurf)

---

### Post by taurus on 2007-02-21
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by locosmurf on 2007-02-21
"sudo aptitude update" worked fine and it accepted my password. "sudo aptitude upgrade accepted my password but gave me these dependency errors.

```
kdelibs4c2a: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is installed.
               Depends: libcupsys2 (>= 1.2.7) but 1.2.4-2ubuntu3 is installed.
               Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed.
               Depends: liblua50 (>= 5.0.3) but 5.0.2-6 is installed.
               Depends: liblualib50 (>= 5.0.3) but 5.0.2-6 is installed.
               Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed.
               Depends: libqt3-mt (>= 3:3.3.7) but 3:3.3.6-3ubuntu3 is installed.
               Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed.
               Depends: libxslt1.1 (>= 1.1.18) but 1.1.17-2build1 is installed.
               Depends: kdelibs-data (> 4:3.5.5a.dfsg.1) but 4:3.5.5-0ubuntu3.1 is installed.
               Depends: menu-xdg but it is not installable
  kdelibs4-dev: Depends: kdelibs4c2a (= 4:3.5.5-0ubuntu3.1) but 4:3.5.5a.dfsg.1-6 is installed.

```

---

### Post by taurus on 2007-02-21
Instead of using adept, you should use synaptic/apt-get/aptitude to install or update your machine then.

Are you trying to upgrade your KDE library to a new version?

---

### Post by locosmurf on 2007-02-21
unfortunately the only package manager I have installed is adept. I was going to install the gnome desktop when I was finished this little project. 

the little project actually wasn't updating my kde libraries, I was trying to install kooldock_0.4.5-1_i386.deb to give my comp. a little eye candy. how might I install any of the others you mentioned? do you know a link to a command list like I did with Automatix?

---

