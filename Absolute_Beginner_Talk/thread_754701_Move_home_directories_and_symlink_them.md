---
title: "Move home directories and symlink them"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by Conky2000 on 2008-04-14
Hi!

I really enjoy Ubuntu and these Forums. I have a question and would be really happy if someone could answer it for me or point me in the right direction.

I have ubuntu set up as a file, email, web and database server and it's been running really well for over a year.

All the users files are on /var which is a huge parition and has lots of room left on it (I set up samba shares there for all the clients on the network).

All the emails are in the /home/username directories. I'm using dovecot and getmail / exim4.

Now there is no more room left on the partition which contains the home directories so I would like to move /home to /var/home.

I don't want to fool around with creating or resizing any partitions because I have >20 people using the server daily and I can't risk any extended downtime.

I was thinking I could do something like:

cp -a /home /var/
then rmdir the old home directory and do:
ln -s /var/home /home

would that work?

should my dovecot/exim4/getmail automatically follow the symlink to /var/home?

if I create a new user will that cause the users home directory to be created in /var/home?

Phillip

---

### Post by PinkFloyd102489 on 2008-04-14
It'll work. Your programs will follow the symlinks.


If you create a new user, you'll either have to create it then move the dir or specify the home dir when creating the user then create the symlink.

---

### Post by Trail on 2008-04-14
Edit: I am wrong here, skip this post :)

Should work. But I think you mean cp -r instead of -a (recursive versus archive mode). Check the manual of cp.

---

### Post by scorp123 on 2008-04-14
> **Conky2000 said:**
>  cp -a /home /var/
then rmdir the old home directory and do:
ln -s /var/home /home

would that work? Yes, but I suggest you don't do it when the server is running and people might be logged in .... Either go into maintenance + single user mode or boot your system via a Live CD and do this from there. Don't forget to adjust **/etc/fstab** and the user accounts in **/etc/passwd** (their entries for the home directories! ... I am not sure if the system will allow a login if the home directory is a symbolic link to another location so better play safe and edit their home directory locations. Shouldn't take too long ....). The copy process might take a while until it's finished, but the rest (e.g. editing /etc/passwd and /etc/fstab) can be done in a couple of minutes.

---

### Post by scorp123 on 2008-04-14
> **Trail said:**
> Check the manual of cp. You may want to do that as well. "cp -a" is the same as "cp -dpR" ... So it will copy recursively and it will include the permissions which a mere "cp -r" does not! You are giving bad advice here.

---

### Post by Trail on 2008-04-14
Yeah, you are correct. Memory does not always serve well :(

---

### Post by scorp123 on 2008-04-14
> **Trail said:**
> Yeah, you are correct. Memory does not always serve well :( Next time, suggest "rsync -av" .... that will give you bonus points :)

---

### Post by Conky2000 on 2008-04-29
Thanks for all your help!
What I've done now is start out by moving just one of the home directories to /var/home/username and symlinking to it. That has been working fine for the past 2 weeks so now I've begun moving all the other users as well.

> I am not sure if the system will allow a login if the home directory is a symbolic link to another location so better play safe and edit their home directory locations.
I wasn't worried about that since I had all the users set to "-s /bin/false" and I think that means they can't login to shell :D ?

I've also been looking into rsync and it totally rocks :D so special thanks to scorp.


Unrelated to my original question I've been using the following command to rsync my server to another computer on the lan:
```
rsync -avW --progress --delete /var/ ipaddress:/home/blah/backup/var 2> /someuser/Desktop/rsync_err.log
```
Is there anything obviously wrong with that?

---

