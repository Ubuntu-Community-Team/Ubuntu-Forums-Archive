---
title: "$HOME/.dmrc &quot;error message&quot;"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by staib on 2007-04-09
Hi

Could someone please explain (slowly) how I can remove the warning message from my wife and son's shared log on.  It currently reads something like:

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user... etc.   It's not a biggie, as they just ignore that, but aesthetically it bugs me!

Not sure what I did originally, but I suspect I was trying to refile some of my son's homework!

I've since realised that I can use nautilus to do much the same, if I ever need to again.

Thanks!

---

### Post by aidanr on 2007-04-09
you should open a terminal (applications -> accesories -> terminal)
and type in the following line by line

```
sudo chown -R [username] /home/[username]
sudo chmod -R 755 /home/[username]
sudo chown [username] $HOME/.dmrc
sudo chmod 644 $HOME/.dmrc
```

replace [username] with the username of the account you are trying to fix, and type in the password for that user when asked for it

edit:// do this from within the account you are trying to fix, so log into your sons first and do it, and then log into your wifes and do it

---

### Post by bapoumba on 2007-04-09
[http://ubuntuforums.org/showthread.php?t=371052]("http://ubuntuforums.org/showthread.php?t=371052")
Hello :)
One of the many threads on that subject you can check ;)

---

### Post by tonyr1988 on 2007-04-09
EDIT: I was too late. aidanr's should work perfectly.

---

### Post by staib on 2007-04-09
Thanks guys - as ever you trip over each other to be helpful - thanks a ton!

---

### Post by staib on 2007-04-09
And, now that I've tried it and tested it, I can confirm that it all worked fine =D>

Thanks again!

---

### Post by pohlipit on 2007-04-10
> **aidanr said:**
> you should open a terminal (applications -> accesories -> terminal)
and type in the following line by line

```
sudo chown -R [username] /home/[username]
sudo chmod -R 755 /home/[username]
sudo chown [username] $HOME/.dmrc
sudo chmod 644 $HOME/.dmrc
```

replace [username] with the username of the account you are trying to fix, and type in the password for that user when asked for it

edit:// do this from within the account you are trying to fix, so log into your sons first and do it, and then log into your wifes and do it
Hi,

I had the same problem and it worked fine. However I have no clue what happened or what the commands mean I entered. Would like to learn more though. Anyone can explain what those lines mean?

Cheers, 
P!

---

### Post by ComplexNumber on 2007-04-10
> **pohlipit said:**
> Hi,

I had the same problem and it worked fine. However I have no clue what happened or what the commands mean I entered. Would like to learn more though. Anyone can explain what those lines mean?

Cheers, 
P!
it may case, it appeared to have no logic. i seem to remember that i installed some innocuous package from source, but thats the only event in that session that i remember that involved changed something outside of my home directory. its not as if i had manually changed the root partition's permissions or anything (obviously), but for some unknown reason they changed.
in some/most cases, the permissions on the home directory(ie /home) or the users home directory(ie /home/username) change.....and thats what gives the error. why? unfortunately, i dont know as yet.

---

### Post by az on 2007-04-10
> **ComplexNumber said:**
> 
in some/most cases, the permissions on the home directory(ie /home) or the users home directory(ie /home/username) change.....and thats what gives the error. why? unfortunately, i dont know as yet.

I had filed a bug about this over a year ago.  I think the message should be split in two.  One message to complain about the .dmrc file in the event that that is the problem and the other message to complain about the home directory being writeable by other users if that is the problem.  Currently only one message is displayed for both those conditions.

Since GDM runs as root, both of those situations are a potential security risk.

---

### Post by peleg on 2008-01-29
Hey aidanr...

I tried to follow your instructions, as you wrote them here, because I had the same problem (this is a post you have posted almost a year ago...).
Here are your instructions:

> **aidanr said:**
> you should open a terminal (applications -> accesories -> terminal)
and type in the following line by line

```
sudo chown -R [username] /home/[username]
sudo chmod -R 755 /home/[username]
sudo chown [username] $HOME/.dmrc
sudo chmod 644 $HOME/.dmrc
```

replace [username] with the username of the account you are trying to fix, and type in the password for that user when asked for it

edit:// do this from within the account you are trying to fix, so log into your sons first and do it, and then log into your wifes and do it

Well, I have done it, but while typing:
```
sudo chown [myusername] $HOME/.dmrc
```
I got the following response:
```
chown: cannot access `//.dmrc' - no such file or directory
```

Weird... So I have tried:
```
sudo chown [myusername] /home/[myusername]/.dmrc
```
and it didn't response (didn't write the error), so I guess it was ok.

STILL: it didn't let me login.

I'm in a very bad situation now, because I just can't access GNOME.

Maybe more info about the problem will help?

This is the exact message (with my comments) I get when trying to log in with gnome:
```

User's $HOME/.dmrc file is being ignored.

```
well... maybe it is because it doesn't exist?
```

This prevents the default session and language from being saved.
File should owned by user and have 644 permssions.
```
well... the file /home/[myusername]/.dmcp probably have the correct ownership+permissions; though, it looks like ubuntu searches for another file, probably `/.dmrc`, which means that ubuntu probably thinks that $HOME is `/` (for my user), which is REALLY weird, isn't it? (what do you think about my assumptions?)
```

User's $HOME must be owned by user and not writeable by other users

```
(same as above)

In a different place, after I press enter, I get this error:
```

Unable to create ~/.gnome directory: permission denied

```

Probably a consequence of the above.

Well, I was wondering if you could try to help me to solve this problem... this is my second day ever with linux! (and I have already fell inlove).

Thanks ahead,
Peleg.

(UPDATE: I thought it should be added automatically with my signature, but here it is:
This is my ubuntu:
Ubuntu 7.04 - Feisty Fawn
Dell Inspiron 6400 2GB Ram

Cheers!)

---

### Post by peleg on 2008-01-30
Update (more info):
I have tried also the instructions here:
[http://liltux.wordpress.com/2007/06/04/how-to-fix-errors-with-the-dmrc-file/](http://liltux.wordpress.com/2007/06/04/how-to-fix-errors-with-the-dmrc-file/)
but while doing ```
chmod 644 ~/.dmrc
``` I got a message that says that this file does not exist.

Listening to a friend's advice, I **created** this file and inserted new data to it, using:
```

touch ~/.dmrc
pico ~/.dmrc

```
and then inserting the lines:
```

[Desktop]
Session=default

```
and saving (and validating).

Still I get the same error exaclty.

My estimation:
Ubuntu still thinks that $HOME is "/" (why?), and "/" probably owned by "root" and not by "username".

I am quite nervous about doing:
```
chown [username] /
```

What do you say?

Thanks!

Peleg.

---

### Post by crawall on 2008-01-30
the original code did the trick for me

---

### Post by peleg on 2008-01-30
> **crawall said:**
> the original code did the trick for me

Thanks...

It seems like - as I said - my $HOME variable went wrong... :-)

I mean, I have probably set my home directory to "/" instead of "/home/username/", mistakenly...

I have reinstalled ubuntu, and now it works.

Peleg.

---

