---
title: "I changed my home directory, now i cant log back in"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by oxymoronic on 2007-05-23
Hello there. Can anyone please help? 
I recently tryed changing the default username from oem to my name, chaz. I then changed my home directory from /home/oem to /home/chaz. 
Now, when I try to log in i get there error  (gnome-session:9387): libgnomevfs-WARNING **: unable to create ~/.gnome2 directory: Permission denied
Could not create per-eser gnome configuration directory '/home/chaz/.gnome2/': permission denied

I have no idea what to do, can someone please help me?

---

### Post by Sparkster185 on 2007-05-23
Which user is the owner of the directory /home/chaz ?  If it's anyone but "chaz", I would imagine it wouldn't work.

If you do ```
ls -l /home | grep chaz
``` that should tell you.  You might need to boot to recovery mode, or login as your old username.

---

### Post by steve.horsley on 2007-05-23
You probably missed changing your home directorys name. I don't think you can do that while you are logged in as that user (which you can't do now anyway), so you need to boot into recovery mode (which makes you root) and do:
**mv /home/oem /home/chaz**
You may still have problems with some programs that have saves the fact that they should store their data in /home/oem/whatever.

Alternatively, make a new home directory:
mkdir /home/chaz
chown chaz:chaz /home/chaz

If you have trouble with the group name chaz, use:
**nano /etc/group**
and change the group name from oem to chaz

---

### Post by paparucino on 2007-05-23
> **steve.horsley said:**
> 

If you have trouble with the group name chaz, use:
**nano /etc/group**
and change the group name from oem to chaz
it should be better if he uses 
```

sudo adduser

```
to create the new user which allows him to logins, then remove the old one.
In most cases it's better use the command,IMHO

---

### Post by steve.horsley on 2007-05-24
Nope. He's trying to rename the group, not add the user to a non-existent group.
And he doesn't need sudo since he's going to have to do this in recovery mode.

---

