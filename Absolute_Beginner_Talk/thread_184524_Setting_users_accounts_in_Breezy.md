---
title: "Setting users accounts in Breezy"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-05-30
Hi there,
so far I've been using Ubuntu 5.10. Now my brother wants me to create a user for him. How do I do this? Further more - I hope that every options in the programs remain safe, untouched and not shared among other users? Will the other user have separate directory in /home? If yes, what access will he have for my current directory?

---

### Post by badrinarayan on 2006-05-30
Go to "System > Administration > Users and Groups" menu action and add user in the regular fashion. Nothing will happen to your programs. He can't access your home directory. He will have a separate directory in /home. (You can however access his directory as you have sudo privileges ;) )

---

### Post by Zdravko on 2006-05-30
Thanks. Is there a way to deny other users completely access to my data?

---

### Post by badrinarayan on 2006-05-30
[QUOTE=Zdravko]Thanks. Is there a way to deny other users completely access to my data?[/QUOTE]
I think I don't understand your question. Like I mentioned, this is the default behavior. The new user will have no access to your data.

---

### Post by Zdravko on 2006-05-30
But this "sudo" is too much "mighty". Anyway, thanks for the information.

---

### Post by sudomania4 on 2006-05-30
just dont give out the sudo password if you think it gives other users too much access...

---

