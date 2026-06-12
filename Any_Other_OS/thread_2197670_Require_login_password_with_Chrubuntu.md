---
title: "Require login password with Chrubuntu?"
date: 2014-01-04
forum: Any Other OS
---

### Post by Jackie_Treehorn on 2014-01-04
Hello all,

I have the wonderful Chrubuntu installed on my Acer C710 Chromebook and running Plex Media Server for my network video viewing. Currently, Chrubuntu loads directly after hitting the power button with no username or password required. I'd like to change that. The current username and password is user:user. I'd like to at least change the password and additionally require a username and password when Chrubuntu is loaded. Is this possible?

Thank you.

---

### Post by jamesisin on 2014-01-05
Assuming it behaves like vanilla Ubuntu, you will do that in **System Settings --> User Accounts**.

---

### Post by Jackie_Treehorn on 2014-01-05
> **jamesisin said:**
> Assuming it behaves like vanilla Ubuntu, you will do that in **System Settings --> User Accounts**.

Unfortunately, it doesn't behave the same. In the user accounts system setting, automatic login is NOT enabled, yet Chrubuntu logs in automatically at startup.

I think the default user:user is embedded into the script the the author of Chrubuntu wrote. Chrubuntu behaves as expected when waking after going to sleep. A password prompt is required.

UPDATE: Just to see what happens, I created a new standard user account in Chrubuntu. I then shut the machine down. Then powered back up. Well the creation of the new user account completely killed the Chrubuntu script. Now the machine won't start back up at all. I'm left with a blank screen with a flashing dash in the upper left hand corner of the screen.

I think I'll just wipe the machine and just use it as a regular old Chromebook. I'll just use an old laptop as my Plex Media Server. It sips a little more energy than does the Chromebook, but without having to hack anything.

---

### Post by jamesisin on 2014-01-05
Can't you install Ubuntu?  Does it have to be Chrubuntu?

If you can figure out what the name of the script is, you may be able to simply delete it.  Also, a flashing cursor on a blank screen may be a GRUB issue.  You could try running *update-grub* from a LiveCD.

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Other OS/Distro Support**.*

---

