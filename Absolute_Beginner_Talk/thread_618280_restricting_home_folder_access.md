---
title: "restricting home folder access"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by gnw23 on 2007-11-20
some days back i took a help for restricting home folder in edubuntu to that perticular user only

like restricting trinity home folder to trinity only
and neo home folder to neo

by using the following command




sudo chmod 700 /home/mike /home/trinity /home/trinity1 /home/trinity12
ls -la /home

but now i want to go back to my original system configuration ie neo can see trinity home folder and trinity can see neo home folder

how can i do this 

plz help me with this

---

### Post by natehatewindows on 2007-11-20
never mind...i have no idea what im talking about :)

---

### Post by Skefflock on 2007-11-20
You got to be Morpheus at least:)
Try
sudo chmod 750 /home/mike /home/trinity /home/trinity1 /home/trinity12 - so all the other users can just read
sudo chmod 770 /home/mike /home/trinity /home/trinity1 /home/trinity12 - so all the other users can do everything, read, write and execute

---

### Post by natehatewindows on 2007-11-20
right....770 i was thinking 777 for some reason.

---

### Post by hyper_ch on 2007-11-20
> **Skefflock said:**
> You got to be Morpheus at least:)
Try
sudo chmod 750 /home/mike /home/trinity /home/trinity1 /home/trinity12 - so all the other users can just read
sudo chmod 770 /home/mike /home/trinity /home/trinity1 /home/trinity12 - so all the other users can do everything, read, write and execute

That's not quite correct:

750 --> you can rwx and all other users in your group can rx
770 --> you and all users in your group can rwx

the second number is the group permissions, not world....

---

### Post by nick_h on 2007-11-20
Beginners may find it easier not to use octal notation.  For permissions of 750 you could do :
```
chmod u=rwx,g=rx,o= file
```

Just an alternative.

---

### Post by Skefflock on 2007-11-20
> **hyper_ch said:**
> That's not quite correct:

750 --> you can rwx and all other users in your group can rx
770 --> you and all users in your group can rwx

the second number is the group permissions, not world....

Oh yep, that what I meant. Course he sad he want to add user group rights, so he's own rights was obvious. 740 - for user group to read, 750 - to read and write, 770 - read, write and ex.

---

