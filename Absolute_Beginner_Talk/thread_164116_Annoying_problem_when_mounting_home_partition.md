---
title: "Annoying problem when mounting /home partition"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Charax on 2006-04-22
I tried to mount a partition as /home using the method suggested around the forum (copy /home to /oldhome, mkdir /home, mount partition as /home, copy /oldhome to /home, add mounting to fstab, delete /oldhome)

Now every time I try to login I get that damned $Home /.dmrc permissions error - I've tried to chmod both ~/.dmrc and /home/username, with no luck at all (I tried with both 655 and 755 permissions) . I tried removing the mounting from /fstab, now I just get "Would you like to use /root as your home directory" before the same .dmrc error message.

Getting a little sick of this now. will creating a new user (and thus, I would assume, a new .dmrc file) work? how will I do this from the terminal?

This is probably the most recurring error I've been getting with Ubuntu. if you can eliminate it for me, I will be very, very grateful.

---

### Post by Charax on 2006-04-22
Nobody? This is kinda urgent, I might reinstall in about an hour, and I'd rather not

---

### Post by stansaraczewski on 2006-04-22
Have you searched the forum for .dmrc ? I'm having the same problem - had it last week... just found a reply prior to your entry.

---

### Post by Charax on 2006-04-22
I did a search of both this forum and the internet in general, I tried everything - I can't even find how to create a new user using the terminal, so I'm reinstalling Dapper from a fresh install CD (The GUI installer tends to hang a bit for me)

---

### Post by louis_nichols on 2006-04-22
[QUOTE=Charax]I tried to mount a partition as /home using the method suggested around the forum (copy /home to /oldhome, mkdir /home, mount partition as /home, copy /oldhome to /home, add mounting to fstab, delete /oldhome)

Now every time I try to login I get that damned $Home /.dmrc permissions error - I've tried to chmod both ~/.dmrc and /home/username, with no luck at all (I tried with both 655 and 755 permissions) . I tried removing the mounting from /fstab, now I just get "Would you like to use /root as your home directory" before the same .dmrc error message.

Getting a little sick of this now. will creating a new user (and thus, I would assume, a new .dmrc file) work? how will I do this from the terminal?

This is probably the most recurring error I've been getting with Ubuntu. if you can eliminate it for me, I will be very, very grateful.[/QUOTE]

I think you have to delete ~/.dmrc and then try again. If I remember well, that's a file that locks a session Also, besides checking chmod for those files, check the owner, too. If you did all that moving and copying as root, that may be a reason. So you'll have to ```
chown <user-name> -R /home/<user-name> 
```

---

