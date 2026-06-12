---
title: "linking a hidden folder"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-06
i installed realplayer in /home/username/realplayer and linked it with alacarte.

i want to get this folder hidden and i should do this:

mv /home/username/realplayer /home/username/.realplayer

when i create a link in alacarte, in command, if i type:

/home/username/.realplayer

it just doesn't open the program. on the other hand, if i keep the folder visible and link it like /home/username/realplayer it works with no problems.

what should i do to open the program with a hidden folder?

---

### Post by jaboua on 2006-10-06
Did you remember to run the command name? If .realplayer is a folder, it should not run:
/home/username/.realplayer

It should run:
/home/username/.realplayer/realplayer
Or something like that (if the app is named "realplayer"). However I don't see why you installed realplayer manually as realplayer is available in the repos (you may have to enable some extra repos though, if you haven't allready)

---

### Post by CatKiller on 2006-10-06
> **cmaranhao said:**
> i want to get this folder hidden and i should do this:

mv /home/username/realplayer /home/username/.realplayer

You could just ```
gedit .hidden
``` and write **realplayer** into it.

---

