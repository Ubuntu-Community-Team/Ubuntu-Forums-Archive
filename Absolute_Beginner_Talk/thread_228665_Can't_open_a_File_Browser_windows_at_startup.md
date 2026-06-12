---
title: "Can't open a File Browser windows at startup"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by mikebarnes on 2006-08-03
I'm trying to get a File Browser window to open up automatically every time I log in. (I'm a Windows user, and in Windows I have Explorer in the Startup group. Now I'm dabbling with dapper and trying to achieve something similar.)

In **System: Preferences: Sessions: Startup Programs** I added this command:

[INDENT][FONT="Courier New"]nautilus --no-desktop --browser %U[/FONT][/INDENT]

But when I log out and in again, no file browser window opens.

I'm guessing that the reason is because nautilus is already running as a session-managed application. Is that right, or have I misunderstood something more fundamental? And what should I do to make things work as I'm expecting?

---

### Post by moma on 2006-08-03
Type this:

/usr/bin/nautilus --no-desktop --browser

---

### Post by mikebarnes on 2006-08-03
Thanks, that worked perfectly!

For bonus points, can anyone tell me how to get the File Browser window to open maximised? No big deal if it's not possible, but if it *is* possible, I'd like to do it.

---

### Post by jackpennello on 2006-08-09
Hi all, I have the opposite problem, I would like to not open the browser at startup, but I would like to have nautilus to run at the startup.

I look in the man page, but I don't find any paramter that permit to "disable" the browser at startup.
Someone could help me?

---

