---
title: "Unable to empty trash!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Feck on 2007-04-15
SOLVED

Hello!
    I'm trying to get rid of a folder I moved to the trash, since I don't need it any longer. I have all permissions set on it, and have no problem moving it to the Trash. However, I can't empty it from the trash, because it tells me that i don't "have permissions to alter the parent folder. Any ideas?

Cheers,
Feck

---

### Post by BobbyBionic on 2007-04-15
Hello

You can do it in a shell, removing files in /home/user/.Trash, with sudo.

---

### Post by Feck on 2007-04-15
And what is the command, exactly, for removing files? I tried a few obvious candidates, but none worked :P

---

### Post by BobbyBionic on 2007-04-15
Be sure that files you want to delete are in /home/user/.Trash (user is your username ;)).

If you can see it doing : ```
ls /home/user/.Trash
```
Then you can do : ```
sudo rm /home/user/.Trash/*
```
And if they are some folders : ```
sudo rm -R /home/user/.Trash/name of the folder
```

Be careful with rm -R with sudo, you can do a lot of fatal errors with this ! Be sure when you press enter !

---

### Post by Subban on 2007-04-15
sudo rm -R /home/username/.Trash/*

That should see you right, personally I have that on a cron job, runs ever 10minutes. When I delete stuff I like it actually deleted

---

### Post by Feck on 2007-04-15
Thanks a lot, Subban!

suto rm -R worked just fine. And no fatal errors :P

Thanks again!

Cheers,
Feck

---

