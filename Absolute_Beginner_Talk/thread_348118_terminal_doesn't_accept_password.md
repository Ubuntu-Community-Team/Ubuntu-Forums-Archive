---
title: "terminal doesn't accept password"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-01-28
Dear friends, Ubuntu is not accepting password while writing any command in the terminal.
Actually, I can't write anything while it seeks password. 
Kindly help me.
Regards,
Saurav

---

### Post by Pobega on 2007-01-28
Well for one, are you in the adm/admin groups when you try to do this? I believe those are the groups you need to be in to be able to use sudo commands.

To cancel a command you can try Ctrl+C, it forces the current running command to cancel no matter what point it's at. Keep in mind if you do this during something like an installation or an ugprade, you *can* negatively effect your system. But for cancelling password input it works just fine, I use it all of the time.

---

### Post by meng on 2007-01-28
Just type the password and press Enter. Nothing echoes to screen. It's a security measure.

---

