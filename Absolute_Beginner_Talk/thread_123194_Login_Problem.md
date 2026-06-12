---
title: "Login Problem"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by njmarine2001 on 2006-01-29
Ok i received my cd's in the mail today.

I got breezy installed using expert mode since i didnt want to destroy my already dual booting system (win98/winxp) that part works well, grub allows me to boot into windows still. 

the problem comes in that i didnt create a user during install, and it gets to the ubuntu login and tells me system administrator can not log in from this screen. 

now i cant find a way to get into the system.

---

### Post by bernardfrancois on 2006-01-29
If you press CTRL+ALT+F1, you get another terminal. There you can log in as root, and add a user (using the **adduser** command, see *man adduser* for more information).

If you created the new user, press CTRL+ALT+F7 and log in with the newly created user.

[edit]
If you can't log in like that, you can choose a different option in grub to get a root terminal (there are different ways there to start ubuntu, at least one of them opens a root terminal I think), and then add a user.
[/edit]

[edit2]
Installing ubuntu the default way wouldn't have destroyed your dual boot configuration. Grub would have recognised all available operating systems.
[/edit2]

---

