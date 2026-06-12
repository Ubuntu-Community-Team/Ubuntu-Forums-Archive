---
title: "users home"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-21
hi all,this is not a major problem but after i log in i get this message,
  user's $home /.dmrc file is being ignored this prevents default session and language being saved.
file should be owned by user and have 644 permissions.
 users home directory must be owned by user and not writable by outhers.
 
 i use ubuntu 6.o6 and when this message shows i click ok and can do what i want but i dont know what it is trying to tell me .i have obviously ticked a box somewhere i shouldnt have,so if some one could direct me to the place to fix this it would be appreciated.:confused:

---

### Post by furiousV on 2006-10-21
> **STREETURCHINE said:**
> hi all,this is not a major problem but after i log in i get this message,
  user's $home /.dmrc file is being ignored this prevents default session and language being saved.
file should be owned by user and have 644 permissions.
 users home directory must be owned by user and not writable by outhers.
 
 i use ubuntu 6.o6 and when this message shows i click ok and can do what i want but i dont know what it is trying to tell me .i have obviously ticked a box somewhere i shouldnt have,so if some one could direct me to the place to fix this it would be appreciated.:confused:

In a shell (Terminal or Konsole - whatever) type in
**ls -la|grep dmrc**

It should show something similar to

```

-rw-------  1 viktor viktor        24 2006-09-14 16:37 .dmrc

```

If not, do
**chmod 644 .dmrc**

If you get permission errors, do
**sudo chown *yourname*:*yourname* .dmrc**

replace *yourname* with your username. example I would use:
**sudo chown viktor:viktor .dmrc**

That will make you the owner and group owner of the file.

That should get rid of the error message. Let us know how you get on.

---

### Post by STREETURCHINE on 2006-10-21
rex@Linux:~$ ls -la|grep dmrc
-rw-------  1 rex  rex    26 2006-10-18 13:11 .dmrc
rex@Linux:~$

  this is the code i got when typed in it looks like i have permissions do i need to type in anouther command:-D

---

### Post by lloyd_b on 2006-10-21
> rex@Linux:~$ ls -la|grep dmrc
-rw------- 1 rex rex 26 2006-10-18 13:11 .dmrc
rex@Linux:~$

The right owner (assuming you're "rex"), but the wrong permissions.

> file should be owned by user and have 644 permissions.

What you've got is 600 permissions.

To fix:

"chmod 644 .dmrc"

The permissions should show as "-rw-r--r--"


Lloyd B.

---

### Post by STREETURCHINE on 2006-10-21
rex@Linux:~$ ls -la|grep dmrc
-rw-------  1 rex  rex    26 2006-10-18 13:11 .dmrc
rex@Linux:~$ "chmod 644 .dmrc"
bash: chmod 644 .dmrc: command not found
rex@Linux:~$ chmod 644 .dmrc
rex@Linux:~$ ls -la|grep dmrc
-rw-r--r--  1 rex  rex    26 2006-10-18 13:11 .dmrc
rex@Linux:~$




that is the reply .if that is correct,then i thank you for your time and help
i shall do a reboot and check 8)
 i have done a reboot but still get the same message at the start.i went to the home file and clicked on propeties ,but it tells me i dont have permissions to write this file

---

### Post by lloyd_b on 2006-10-21
> i have done a reboot but still get the same message at the start.i went to the home file and clicked on propeties ,but it tells me i dont have permissions to write this file

Now that's interesting :confused: 

If you can "chmod" that file, how can you not have write permission?
:-k 

Okay - looking back over your original post I spotted something else:

> user's $home /.dmrc file is being ignored this prevents default session and language being saved.
file should be owned by user and have 644 permissions.
users home directory must be owned by user and not writable by outhers.

We've been fixated on ".dmrc", but the problem could be in the ownership of the *directory* that the file is in, not the file itself.

In a terminal window:

```
cd ..
ls -l
```

You should see something like this:

```
drwxr-xr-x 28 rex rex 4096 2006-10-21 18:23 rex
```

If "rex" isn't the owner, then:

```
sudo chown rex rex
```

If the permissions do not match what you see above:

```
chmod 755 rex
```

Let's see if that gets anywhere...

Lloyd B.

---

### Post by STREETURCHINE on 2006-10-22
rex@Linux:~$ cd ,,|s -|
> sudo chown rex rex
bash: s: command not found
bash: cd: ,,: No such file or directory
Password:
chown: cannot access `rex': No such file or directory
rex@Linux:~$ chmod 755 rex
chmod: cannot access `rex': No such file or directory
rex@Linux:~$


there dont seem to be a file for rex,this little problem just dont want to go away.

---

### Post by jordanmthomas on 2006-10-22
your commands didn't get typed in correctly.
Try copying them by selecting them, and then middle clicking in your terminal to paste.

You a) used commas instead of periods and b) used pipes instead of ls and c) put the cd and the ls on the same line.  You need to press enter between them.

---

### Post by STREETURCHINE on 2006-10-22
rex@Linux:~$ cd ..
rex@Linux:/home$ ls -l
total 4
drwsr-xr-x 26 rex rex 4096 2006-10-22 10:34 rex
rex@Linux:/home$ chmod 755 rex
rex@Linux:/home$



right sorry about that,very new to linux was not sure how to put the first comand in tried several ways but the result was always the same,the only differance i can see is ,,drswr-xr-x 26 .your post had drswr-xr-x 28 .

---

### Post by lloyd_b on 2006-10-22
> rex@Linux:~$ cd ..
rex@Linux:/home$ ls -l
total 4
drwsr-xr-x 26 rex rex 4096 2006-10-22 10:34 rex
rex@Linux:/home$ chmod 755 rex
rex@Linux:/home$



right sorry about that,very new to linux was not sure how to put the first comand in tried several ways but the result was always the same,the only differance i can see is ,,drswr-xr-x 26 .your post had drswr-xr-x 28 .

I'll have to remember in the future to make commands bold, or in a larger font.  This isn't the first time I've seen someone mistake a period for a comma (The most common one I've seen is mistaking capital letter eye for a lowercase letter ell).

Now for the bad news:  There was nothing wrong with the directory either.  The "26" versus "28" was simply because of the differences between your machine and mine.  What was important was the "drwxr-xr-x", which are the permissions, and the "rex rex", which indicate ownership.

One (really silly) question:  you are logging in as user "rex", aren't you?

Assuming that's true, I have one (and only one) idea left - if you can't fix it, KILL IT:

```
[SIZE="2"]**mv .dmrc dmrc2**[/SIZE]

```
then reboot the machine.

What "mv" does is move the file from one name to another.  The next time you start up, there won't be a ".dmrc" file for it to complain about - there's a reasonable chance that it will simply create a new one for you.

If for some reason you need the old one back, use the above "mv" command, only reverse the order of ".dmrc" and "dmrc2".

Lloyd B.

---

### Post by STREETURCHINE on 2006-10-22
rex@Linux:~$ cd ..
rex@Linux:/home$ ls -l
total 4
drwsr-xr-x 26 rex rex 4096 2006-10-22 10:34 rex
rex@Linux:/home$ chmod 755 rex
rex@Linux:/home$ mv .dmrc dmrc2
mv: cannot stat `.dmrc': No such file or directory
rex@Linux:/home$



thanks for your help,dont look like i can kill it either, as i said it isnt stopping me doing anything .just an annoyance but thanks for all your help

---

### Post by jordanmthomas on 2006-10-22
to move it, you would need to 
```
cd ~
```
to get back in your home directory.  Then try moving it again.

---

### Post by STREETURCHINE on 2006-10-22
thankyou for your time and effort,all fixed no longer have that annoying little popup:D

---

### Post by furiousV on 2006-10-22
> **STREETURCHINE said:**
> thankyou for your time and effort,all fixed no longer have that annoying little popup:D

Glad you got it sorted man :-D

---

