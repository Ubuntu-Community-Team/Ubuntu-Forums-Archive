---
title: "problem with permission"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by cele on 2007-04-08
I have 2 account's on my Ubuntu. I wanted to copy some music files (mp3) to the other account's desktop which is used by my girlfriend but it is saying that I don't have permission to do that. 
How to solve that? Or how to have some foldes which will be shared between two acc?

---

### Post by Famicommie on 2007-04-08
The quick and dirty way to move those mp3s would simply be to precede the terminal command with "sudo". So it would be something like "sudo cp -r /home/user/music /home/girlfriend/Desktop" where you would change the name of the paths based on what they actually are. Id est instead of /home/user/music it would be the location where you have the folder of mp3s that you are trying to copy.

If you want to make it so that certain folders are shared, go to the directory which contains those folders in a terminal, and type "sudo chmod 777 /home/user/music" (again replacing the path with the proper path).

---

### Post by ffxr on 2007-04-08
you just have to chnage the permissions on the folder to allow the other account access..  if you right click on folder, when logged in as your account.., select properties, there should be a permissions tab in there... look for the other users account and give it read permissions or whatever..  

you dont have to copy the entire folder to her desktop either,  just set up a sym link to the mp3 folder.. with a command something like this..

```

sudo ln -s /home/girlfriends-username/desktop /home/myusername/mp3folder
```


^change the paths as appropriate..

hope this helps.

---

