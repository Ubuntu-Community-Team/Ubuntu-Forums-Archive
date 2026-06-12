---
title: "Trouble installing"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by dragonmine on 2007-01-14
I try to install my Enemy territory game and get this ......      File name is et-linux-2.55.x86.run
i get this problem below:

what does this mean?

It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password:
su: Authentication failure
Sorry.
/home/bras/.setup10856: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
Reply With Quote


Plz help

---

### Post by Third Thoughts on 2007-01-14
> **dragonmine said:**
> I try to install my Enemy territory game and get this ......      File name is et-linux-2.55.x86.run
i get this problem below:

what does this mean?

It is recommended to install as the super user
Please enter the root password or hit enter to continue as is
Password:
su: Authentication failure
Sorry.
/home/bras/.setup10856: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
Reply With Quote


Plz help

In Linux there are two kinds of users, the normal users and the administrators, or "super users." By default, you spend most of your time as a normal user because its harder to screw things up that way, but to install things you need to be a super user. In order to do this, open up your terminal and go to the folder where the installer file (I assume its et-linux-2.55.x86.run) and then type
```
sudo et-linux-2.55.x86.run
```

You'll be asked for you password, enter it. That should do the trick.

The sudo stands for Super User DO. In other words you're telling Ubuntu to do the next thing as a super user.

~Andrew S.

---

