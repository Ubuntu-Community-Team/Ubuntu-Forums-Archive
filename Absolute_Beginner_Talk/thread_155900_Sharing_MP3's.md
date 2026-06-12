---
title: "Sharing MP3's"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by NGDanny on 2006-04-05
Hello,

My son, wife and I share the same computer.  Each has their own user account.

I have sound juicer working fine and have converted several MP3s.

I there a way we can all share a file that has the MP3 in it so I don't have to convert the same MP3 to each users account?

/thanks

---

### Post by htinn on 2006-04-05
You could do what I do, go to a terminal and type:

sudo mkdir /share
sudo chmod 777 /share

At that point, anything you copy to the /share folder is accessible to everybody who uses the computer.

---

### Post by IYY on 2006-04-06
Then also link it for each user, so that it appears to be in their home directory:

ln -s /share /usr/home/yourname

---

### Post by Sutekh on 2006-04-06
Just to point out that the link should be ```
ln -s /share /home/username
```
instead of /usr/home/username

---

### Post by hw-tph on 2006-04-06
Also, it can be useful to set up a group to own that share and let all users that should have access to the files belong to that group.

First, create the group: **sudo groupadd music**
Then change the ownership of the /share directory: **sudo chown root:music /share**
...and decent permissions: **sudo chmod 770 /share**
Set the group sticky bit so files created in that directory will inherit the ownership ("username:music"): **sudo chmod g+s /share**

Add all users that should have access to this directory (and the files in it) to the  music group. I usually edit /etc/group and add a comma-separated list of usernames:
```
music:x:1004:hakan,bosse,jenny
```

The user must log out and then log in again in order for the changes to take effect if logged in when adding access to a new group.


Håkan

---

