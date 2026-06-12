---
title: "problems with Brother MFC-420CN printer install"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by randiroo76073 on 2006-12-30
I received a Brother MFC-420CN printer for christmas and am trying to get it installed.  Went to website & dowloaded drivers, install instructions say: 

"You need to have C-Shell installed on your PC for the installation of the driver.
Fedra Core, RedHat , SuSE and Mandrake have it preinstalled, but Debian does not.
Please be sure to install it if you are Debian User." 

Can someone tell me what this is & where can I get it?
Thanks for any replies :)

---

### Post by Sef on 2006-12-30
> You need to have C-Shell installed on your PC for the installation of the driver.
Fedra Core, RedHat , SuSE and Mandrake have it preinstalled, but Debian does not.
Please be sure to install it if you are Debian User."

Can someone tell me what this is & where can I get it?

Open the terminal (Applications > Accessories > Terminal) and type

```
sudo aptitude update
```

then 

```
sudo aptitude install c-shell
```

That should download it for you.  If not, then you will need to [add the repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by randiroo76073 on 2006-12-30
Thanks for the rapid reply Sef, I'll get that installed asap :)

---

### Post by Sef on 2006-12-31
You're welcome.  If you have any more problems, please post them.

---

### Post by randiroo76073 on 2007-01-02
Have updated & aquired all kinds of repositories per link above, still get error msg when trying to install "c-shell"

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
"c-shell" is a virtual package provided by:
  tcsh-kanji csh tcsh
You must choose one to install.

Where do I go from here???

---

### Post by randiroo76073 on 2007-01-02
Ah, got it, thought it was software author, Duh, not too smart this morning!

---

