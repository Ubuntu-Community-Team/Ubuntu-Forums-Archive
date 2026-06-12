---
title: "Root priviledges"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by bbahar on 2008-02-17
I do have a very strange issue. 

I am using Ubuntu 7.10 on my PC and I am getting very weird situation. When I want to run an application which needs an root password doesn't accept the one I type. But when I type thru command line (e.g. sudo...) the same password it does accepts and I can run this application well.

In that case, I have to know the application name and where it runs from ..

Any help ...?

Baruch

---

### Post by Joeb454 on 2008-02-17
You mean when it brings up the password prompt in the middle of the screen...it doesn't accept the correct password?

Also by default - the root password should be the password for the user you created when you installed the system

---

### Post by aysiu on 2008-02-17
That is strange.

There is no root password set.

By the way, if it's a graphical application, you should use *gksudo* or *kdesu*, not *sudo*.

For example... 
**Good**: ```
gksudo gnome-app-install
``` **Bad** ```
sudo gnome-app-install
```

---

### Post by bbahar on 2008-02-17
> **Joeb454 said:**
> You mean when it brings up the password prompt in the middle of the screen...it doesn't accept the correct password?

Also by default - the root password should be the password for the user you created when you installed the system

Yes, it's exactly what happens... The same password works on command line...

---

### Post by bbahar on 2008-02-17
> **aysiu said:**
> That is strange.

There is no root password set.

By the way, if it's a graphical application, you should use *gksudo* or *kdesu*, not *sudo*.

For example... 
**Good**: ```
gksudo gnome-app-install
``` **Bad** ```
sudo gnome-app-install
```

That will be fine if I run from command line. In shell, I have no problem it works. The point is to enter the root password in GUI ...

---

