---
title: "Move oem to usual user?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-12
Hello i have been using oem as login to my ubuntu verison a have created an "real user" with name and login and all but is there any way for me to move all my programs and upgrades to my new user? ](*,)

---

### Post by darrenm on 2006-09-12
```
sudo cp -fvR ~oem/* ~new_user/
``` :)

---

### Post by haxer on 2006-09-12
> **darrenm said:**
> ```
sudo cp -fvR ~oem/* ~new_user/
``` :)



What should i tyoe in when i get to the ~new_user/[/code] ? :S

---

### Post by haxer on 2006-09-12
Oh lol what should i type in..  new_user? My other user that i want to move the files to?

---

### Post by ruedu on 2006-09-12
> **darrenm said:**
> ```
sudo cp -fvR ~oem/* ~new_user/
``` :)

Actually, this will not copy all of the settings over because you're going to miss all of the "hidden" files.  You will also need to run:

```
sudo cp -fva ~eom/.[a-zA-Z0-9]* ~new_user 
```

---

### Post by haxer on 2006-09-12
new_user :S is it ther im going to insert my other user name?

---

### Post by bulldog on 2006-09-12
Yes :)

---

### Post by 3rr0r on 2006-09-12
> **haxer said:**
> new_user :S is it ther im going to insert my other user name?

instead of "new_user" you would substitute the new user's name that you have created.

---

### Post by haxer on 2006-09-12
Thx guys ;)

---

### Post by 3rr0r on 2006-09-12
> **ruedu said:**
> Actually, this will not copy all of the settings over because you're going to miss all of the "hidden" files.  You will also need to run:

```
sudo cp -fva ~eom/.[a-zA-Z0-9]* ~new_user 
```

So would you have to run both of these commands, or would you just have to run the latter of the two ?  Just making sure I got it right.

---

### Post by haxer on 2006-09-12
I run the 2 of them hmm... first one and then one toke me about 20 min

---

### Post by ruedu on 2006-09-12
You would run both commands, as my command is going to grab and copy all of the . files, AKA hidden files

---

### Post by 3rr0r on 2006-09-13
So just to reiterate for clarity.  What this will do is copy one profile to a new user, so they will have access to all the programs the original user has?  I'm trying to see what exactly these 2 commands do.  Thanks.

---

### Post by ruedu on 2006-09-13
The parent poster didn't like running under the user OEM and wanted their own user that was more personalized.  They had been using the OEM user for awhile and so there are many program preferences that have been saved.

In your home directory you will find an amazing number of .files and .directories all related to the settings of various programs you run.  One of the beauties of Unix/Linux is that programs keep their user preferences in your home directory in text files.  This makes it extremely easy to backup and move those preferences to different machines or what ever.

The reason you need two different commands to copy the files and hidden files is the way globbing works.  Using cp ~oem_user/* does not match anything that starts with a . because . also refers to the current directory. If you did a recursive copy of . then you'd copy the current directly over and over because you'd reference . over and over, it's a vicious cycle. In a command shell, type ls -lh and you'll see a long listing of the the directory you're in.  At the top of the listing you'll see:

.
..

. refers to the current directory and .. is a link to the parent directory.  This is also why you sometimes need to refer to a program that is not in your PATH variable with a ./.  All programs in Unix/Linux are started from a full path, always, you're just not always aware of it.  So, start/run a script in your home directory (which is not part of your path) you type ./scriptname which in the system expands to your home directory + the script name.  

By using my cp command I'm using globbing to tell the system to copy all files with a name that begins with a . but ALSO contains valid characters after the dot.  so .[a-z] would match a file or directory called .gaim or .mozilla but NOT .Gaim or .0123.

---

### Post by darrenm on 2006-09-17
Oops sorry slight typo ;)

```
sudo cp -fvR ~oem/ /home/newuser
```

will include every file in the directory including hidden.

---

### Post by ruedu on 2006-09-18
> **darrenm said:**
> Oops sorry slight typo ;)

```
sudo cp -fvR ~oem/ /home/newuser
``` 
will include every file in the directory including hidden.

This would copy the oem directory into the newuser directory so the end result would be /home/newuser/oem...

---

### Post by darrenm on 2006-09-18
> **ruedu said:**
> This would copy the oem directory into the newuser directory so the end result would be /home/newuser/oem...

No it won't. You're thinking of mv

```
darrenm@darrenm-desktop:~$ sudo cp -fvR ~darrenm/ /home/newuser
Password:
`/home/darrenm/' -> `/home/newuser'
`/home/darrenm/Examples' -> `/home/newuser/Examples'
`/home/darrenm/.bash_logout' -> `/home/newuser/.bash_logout'
```

---

### Post by edrodgers731 on 2006-09-18
Tmtowtdi.

How about mv /home/oem /home/new_user ; chown -R new_user /home/new_user ?

How about piping a tar to gzip and then piping gunzip to tar?

:)

---

### Post by ruedu on 2006-09-18
> **darrenm said:**
> Oops sorry slight typo ;)

```
sudo cp -fvR ~oem/ /home/newuser
``` 
will include every file in the directory including hidden.

> **darrenm said:**
> No it won't. You're thinking of mv

```
darrenm@darrenm-desktop:~$ sudo cp -fvR ~darrenm/ /home/newuser
Password:
`/home/darrenm/' -> `/home/newuser'
`/home/darrenm/Examples' -> `/home/newuser/Examples'
`/home/darrenm/.bash_logout' -> `/home/newuser/.bash_logout'
```

Apparently cp works differently on Red Hat then

```
cp -fvR ~ruedu/ /home/dsl
`/home/shares/users/ruedu/' -> `/home/dsl/ruedu'
`/home/shares/users/ruedu/test.html' -> `/home/dsl/ruedu/test.html'
```

What do you get from an 'alias cp' ?

---

### Post by darrenm on 2006-09-18
> **ruedu said:**
> Apparently cp works differently on Red Hat then

I just assumed the guy was running ubuntu ;)

> **ruedu said:**
> ```
cp -fvR ~ruedu/ /home/dsl
`/home/shares/users/ruedu/' -> `/home/dsl/ruedu'
`/home/shares/users/ruedu/test.html' -> `/home/dsl/ruedu/test.html'
```

What do you get from an 'alias cp' ?

Don't like redhat personally.

```
darrenm@darrenm-desktop:~$ alias cp
bash: alias: cp: not found

```
what were you expecting to see?

---

### Post by ruedu on 2006-09-18
> **darrenm said:**
> I just assumed the guy was running ubuntu ;)



Don't like redhat personally.

```
darrenm@darrenm-desktop:~$ alias cp
bash: alias: cp: not found

``` what were you expecting to see?

Under red hat you'd get 
```
alias cp 
alias cp='cp -i'
```

I'll have to try this out under Ubuntu because I'm really curious as to why it'd behave differently.

---

