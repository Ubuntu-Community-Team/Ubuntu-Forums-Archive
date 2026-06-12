---
title: "Using Desktop settings (themes) for all Users"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Shawn Dineley on 2006-10-12
Hello

    I'm trying to set up a Kubuntu system for my Mom and Dad. There will be 4 users on the system. I got one account all setup. All the  themes and everything are just the way I want them. Now my question is " Is there a way to transfer the settings to all the other users"?

    Thanks

6.06 LTS with Kde

---

### Post by aysiu on 2006-10-12
Yes, it may not work 100%, but the clean up will take less time than redoing the settings four times.

```
sudo mv /home/username2/.kde /home/username2/.kde.old
sudo cp -R /home/username1/.kde /home/username2
sudo chown -R username2:username2 /home/username2
``` Repeat, substituting username3 and username4 for username2.

---

### Post by Shawn Dineley on 2006-10-12
Thanks I'll give it a try in a couple mins

---

### Post by Merlin 3 on 2006-10-17
Just interested ....did this work for you??

---

### Post by Merlin 3 on 2006-10-17
Dear Aysiu.... when I tried this for myself and one other user I fell at the first hurdle with this response:
mv: cannot stat `/home/username2/.kde': No such file or directory
Being new to Ubuntu I have not got a clue what this means! Could you interpret?? Many thanks

---

### Post by aysiu on 2006-10-17
You have to substitute in the actual username.

I don't know what that username is, so I put *username2*.

For example, if your username is merlin and the second user was arthur, it would be ```
sudo mv /home/arthur/.kde /home/arthur/.kde.old
sudo cp -R /home/merlin/.kde /home/arthur
sudo chown -R arthur:arthur /home/merlin
```

---

### Post by CatKiller on 2006-10-17
Also, if you aren't using Kubuntu, you won't have a .kde file anyway.

---

