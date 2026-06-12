---
title: "So I crippled my system..."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by lsweet on 2007-08-11
Some late  night tinkering led to some late night hair pulling last evening when I was navigating the command line.  Whatever I did, it messed up the .dmrc file.

Through some research here, I came across a fix and got back in to find all my settings gone.  During the process of setting everything back up, I see what I may have done.  It seems (or appears) that I've managed to move the contents of my /home/<user> to another folder....

During setup, I saw my <user> folder in an odd location, opened it and voila! my things.

So the question is, would it kill me to copy all those files back to /home/<user> or should I just suck it up, delete the folder in question and chalk it up as lesson learned?

---

### Post by SOULRiDER on 2007-08-11
You should be able to move the files with no problems, however, if you actually changed your user to have your home directory in another location, youre gonna ahve to edit your user.

```
usermod --help
Usage: usermod [options] LOGIN

Options:
  -a, --append                  append the user to the supplemental GROUPS
                                (use only with -G)
  -c, --comment COMMENT         new value of the GECOS field
  -d, --home HOME_DIR           new home directory for the user account
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP as new primary group
  -G, --groups GROUPS           new list of supplementary GROUPS
  -h, --help                    display this help message and exit
  -l, --login NEW_LOGIN         new value of the login name
  -L, --lock                    lock the user account
  -m, --move-home               move contents of the home directory to the new
                                location (use only with -d)
  -o, --non-unique              allow using duplicate (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new password
  -s, --shell SHELL             new login shell for the user account
  -u, --uid UID                 new UID for the user account
  -U, --unlock                  unlock the user account
```

What i think you should do would be:
```
sudo usermod -d /home/USER -m USER
```
Replace USER with your username.

Good luck!

---

### Post by lsweet on 2007-08-11
Originally the error I got was a write error upon load (Write permissions of ~/.gnome or something) plus some .dmrc errors.

I corrected the issue by booting to console and:
```

touch /home/<user>/.dmrc

```

then:

```

sudo chmod 644 /home/<user>/.dmrc
sudo chown <user> /home/<user>/.dmrc
sudo chmod -R 700 /home/<user>
sudo chmod -R <user> /home/<user>

```

This gave me write access back to the folder -- if I understand the process of what I did.

Now; if I were to copy all the folders and files, do I just go to the directory they reside in and do a 

```

sudo mv *.* /home/<user>/

```

?

---

### Post by SOULRiDER on 2007-08-11
Not *.*, do * instead
```
sudo mv * /home/<user>
```

---

### Post by lsweet on 2007-08-11
> **SOULRiDER said:**
> Not *.*, do * instead
```
sudo mv * /home/<user>
```

Well that probably explains how I may have moved my /home/<user>...

---

