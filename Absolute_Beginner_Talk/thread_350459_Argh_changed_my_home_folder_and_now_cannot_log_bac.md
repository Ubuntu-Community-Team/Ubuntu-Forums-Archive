---
title: "Argh changed my home folder and now cannot log back in"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by bifter on 2007-01-31
In System > Admin > Users and Groups > Properties I just changed my home dir from /home/username to /home. (I realise now that it was probably a stupid thing to do) 

Now when I try and log in I get this message.
[INDENT]
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.[/INDENT]

It then logs me out with a message telling me that there is an installation problem.

Log says 

[INDENT]"Could not create per user gnome config dir '/home/.gnome2/': permission denied"[/INDENT]

It seems I can only get into the failsafe terminal. Which is cool if I knew how to revert things back to normal from here. Alas I don't :(

Can someone talk me through the steps? Please bear in mind that I'm new to Linux.

Many thanks if anyone can help me get back in there - I have the latest episode of Heroes waiting for me :)

---

### Post by annda on 2007-01-31
what about typing
```
sudo chown -R your_username /home
```
and then:
```
sudo chmod -R 644 /home 
```

after that you should be able to log in and get your usual /home/your_username directory set up again (including reverting ownership of /home to root).

EDIT: i'm not sure if you need sudo in failsafe mode - i haven't used in a LONG time now.

---

### Post by yabbadabbadont on 2007-01-31
Just run the usermod command from the failsafe terminal.  "man usermod"

Example: usermod -d /home/oldusername oldusername

---

### Post by bifter on 2007-01-31
thanks guys but i'm afriad i still cannot enter

annda

i tried this and got no errors.

now when i log in the first error i mentioned does not appear but i still get logged out with the second error message and the same log error (.gnome2 access denied).

yabbadabbadont

when i type in usermod -d /home/username username i get the error

usermod: unable to lock password file

---

### Post by yabbadabbadont on 2007-01-31
sudo usermod -d /home/oldusername oldusername  :)

---

### Post by bifter on 2007-01-31
aha of course

ok now i get this message

[INDENT]your home dir is listed as:
'/home/username'
but is does not appear to exist. do you want to log in with the / (root) dir as your home dir?

it is unlikely anything will work unless you are in failsafe session.[/INDENT]

when i log in with gnome failsafe 

i get the old error again 

"user's $home/.dmrc file is ignored blah blah"

then i get logged out again with the same log error about .gnome2 permission denied.

---

### Post by LKRaider on 2007-01-31
post the output of:
```
 ls -la /home 
```

---

### Post by bifter on 2007-01-31
?--------- ? ? ? ?                   ? /home/.
?--------- ? ? ? ?                   ? /home/..
?--------- ? ? ? ?                   ? /home/username

---

### Post by LKRaider on 2007-01-31
Could you please do it again, now with sudo instead?

Is your user actually called "username" or are you replacing the name there?


Do this:
```
sudo chown -hR username:username /home/username
```
Replace username as appropriate.

---

### Post by bifter on 2007-02-01
thank lk, here are the results with sudo

[INDENT]total 12
drw-r--r-- 3 username root 4096 2007-01-26 23:14 .
drwxr-xr--x 21 root root 4096 2007-01-26 22:58 ..
drw-r--r-- 34 username username 4096 2007-01-31 22:20 username

[/INDENT]

yes i am replacing username with my actual username

after entering sudo chown etc as per your instructions below i get the following errors:

[INDENT]your home dir is listed as /home/username but does not appear to exist. do you want to log in as root?[/INDENT]

when i click yes i get:

user's $home/.dmrc file is being ignored etc see first post for full text

i click ok then get logged out and the same gnome2 error permission denied in the log.

i'm starting to think that a reinstall maybe the best solution. is there a chance to recover any of the personal files on the old build? it's not the end of the world if no.

thanks everyone for your efforts so far. when i was a kid i would always fiddle with stuff till i broke it. seems that i did the same with my ubuntu install.... i'm learning loads tho so that's gr8 :)

---

### Post by yabbadabbadont on 2007-02-01
Try:

sudo chmod a+x /home
sudo find /home -type d -exec chmod a+x {} \;

---

### Post by bifter on 2007-02-01
absolutely fantastic! it works :)

thank you very much to everyone who helped me.

---

### Post by LKRaider on 2007-02-03
Well spotted, yabbadabbadont


Just so people know what those commands mean, is that in linux the directories need to have executable permissions for the contents to be accessible.

Somehow bifter's home directories lost that permission, so he could not access the data inside his home folder anymore. Setting the execute permission back to those directories fixed that (chmod +x).

:)

---

### Post by happy_tux on 2008-02-16
> **yabbadabbadont said:**
> Try:

sudo chmod a+x /home
sudo find /home -type d -exec chmod a+x {} \;

Is this second line correct ? 
I keep getting the following error:

find: missing argument to '-exec'

Having a similar problem :-(

---

### Post by yabbadabbadont on 2008-02-16
> **happy_tux said:**
> Is this second line correct ? 
I keep getting the following error:

find: missing argument to '-exec'

Having a similar problem :-(

Obviously it is, since it worked for the OP.  ;)

Cut and paste the command, don't retype it, just to be sure.

---

### Post by steveneddy on 2008-02-17
> **yabbadabbadont said:**
> Try:

sudo chmod a+x /home
sudo find /home -type d -exec chmod a+x {} \;

Could you explain what each step in this chain means to the user and to the computer?

Obviously we are changing permissions and trying to find the /home directory.

What are the symbols and can you explain what we are doing here?

---

### Post by yabbadabbadont on 2008-02-17
Yes, I can.  But I'm not going to.  :p

OK, put down the pitch forks.  I'll talk.  "man chmod" and "man find"  :twisted:

Owwwwww!  Those tar and feathers really hurt!  :lol:

```
chmod a+x /home
``` Adds execute permission for all users to the /home directory.  Directories need to be executable in order for users to traverse them.

```
find /home -type d -exec chmod a+x {} \;
``` Does the same for every sub-directory found in /home.

Read the previously mentioned man pages for details on the options used with these commands.  :D

---

### Post by steveneddy on 2008-02-17
> **yabbadabbadont said:**
> Yes, I can.  But I'm not going to.  :p

OK, put down the pitch forks.  I'll talk.  "man chmod" and "man find"  :twisted:

Owwwwww!  Those tar and feathers really hurt!  :lol:

```
chmod a+x /home
``` Adds execute permission for all users to the /home directory.  Directories need to be executable in order for users to traverse them.

```
find /home -type d -exec chmod a+x {} \;
``` Does the same for every sub-directory found in /home.

Read the previously mentioned man pages for details on the options used with these commands.  :D

You're gonna make me read again.

*sigh*

But thank you for the answer.

---

### Post by yabbadabbadont on 2008-02-17
find - find files, directories, symbolic links, hard links, ...
/home - start in the /home directory and descend into all subdirectories.
-type d - only match directories
-exec - for each match, execute the following command.
chmod a+x - add execute permission for all users.
{} - replaced by find with the matching entity.
\; - the command to be executed must end with a semi-colon.  It has to be escaped or the shell will interpret it instead of passing it as an option to the -exec command.

(I'm in a good mood tonight.  And bored.)

---

### Post by steveneddy on 2008-02-17
> **yabbadabbadont said:**
> find - find files, directories, symbolic links, hard links, ...
/home - start in the /home directory and descend into all subdirectories.
-type d - only match directories
-exec - for each match, execute the following command.
chmod a+x - add execute permission for all users.
{} - replaced by find with the matching entity.
\; - the command to be executed must end with a semi-colon.  It has to be escaped or the shell will interpret it instead of passing it as an option to the -exec command.

(I'm in a good mood tonight.  And bored.)

You are certainly a man among men.

Thank you for the answer and the added explanations.

I'm sure that it will help myself and others.

---

