---
title: "Starting A MUD"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by camRW on 2006-06-28
I'm trying to start a MUD server on my Dapper Drake, but I can't seem to get one working.  I have Mordor, and every time I run the daemon it says:
Unable to bind socket, giving up. (try -r to keep trying)
I don't think it's a permission problem because I run it with sudo.
Does anyone have any ideas?

---

### Post by gerbman on 2006-06-28
[QUOTE=camRW]I'm trying to start a MUD server on my Dapper Drake, but I can't seem to get one working.  I have Mordor, and every time I run the daemon it says:
Unable to bind socket, giving up. (try -r to keep trying)
I don't think it's a permission problem because I run it with sudo.
Does anyone have any ideas?[/QUOTE]It might be trying to bind to a port that is already taken. I'm not familiar with MUD, but there's probably a configuration file somewhere where you can specify the port. Just a hunch.

---

