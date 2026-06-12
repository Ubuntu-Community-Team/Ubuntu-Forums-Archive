---
title: "[SOLVED] umask and its controlling setting"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by say2sky on 2007-12-25
I have google a lot and read a lot about umask and try different setting in configure file.

Now I understand there are three main configure files controlling file permissions. These three configure files are
1. /etc/profile, 
2. /etc/login.defs 
3. .bash_profile

And I have tried create file in both console and xterm and have following result:

1. create file in console, new file permission is controlled by umask setting in .bash_profile
2. create file in xterm, new file permission is controlled by umask setting in /etc/profile

So I set umask in both .bash_profile and /etc/profile to 077, it will achieve all new file have 600 permission which have higher level security. 

But problem is 077 umask in /etc/profile will cause permissions of pppd's pid file also become 600 which result in ppptray can only be run by root but not by user.

My question is:
How to set umask so that all new file user create have 600 permissions but permissions of pppd's pid file keep as 644. 

Thanks for help in advance!

---

### Post by say2sky on 2007-12-26
I indeed need your help. Any one have any suggestion and clue about this umask problem.

---

### Post by wormser on 2007-12-26
Nobody else has help and I am not an expert at umask but I will give it a shot.  Umask is suppose to create the permissions of new files.  If you change the files that you need to have different permissions then umask should not effect them.  

> This mask will affect the initial value of the file permission bits of subsequently **created** files.

If you can give us more information it would help. I am just confused why umask would effect files that are already created.  Maybe another work around could involve groups.

---

### Post by Abu_Dayya on 2007-12-26
Changing umask will change the default file creation permitions in newly created files. It will not change the permitions on old created files.

I don't know alot in linux. But in unix AIX, if you type ' umask <*umask value*>, the umask will change in the current session only. If I want the umask to change permenantly if have to either type 'chuser' command or do it through smitty. Try to find the equvalent command to 'chuser' in linux.

Hope this helps

---

### Post by say2sky on 2007-12-26
All my ask above is about the default file permission newly create by user. But is default file permission is controlled by several different configuration file in Ubuntu system. I hope to find a way to set umask to let all the user newly created file have 600 permission. But pid file's permission will still keep as 644.

But I don't know which configuration file will let me reach this goal.

---

### Post by Abu_Dayya on 2007-12-26
Try changing the umask in /etc/profile, then type umask 077. Then logout and login back again and see if the umask is changed or not. (you can find out by just typing umask with no parameters)

---

### Post by asmoore82 on 2007-12-26
> **say2sky said:**
> So I set umask in both .bash_profile and /etc/profile to 077, it will achieve all new file have 600 permission which **have higher level security**.

This is unnecessary; In order for another user to actually have read permission on a file,
they must have read permission on the entire path that the file is in.
So, even though I feel that setting a umask is not necessary,
I highly recommend 700 permissions on each user's home folder.
In fact, this is one of the first things I always do on new installs.

```
$ chmod 700 "$HOME"
```
-OR-
```
$ sudo chmod 700 /home/*/
```

> **say2sky said:**
> 
But problem is 077 umask in /etc/profile will cause permissions of pppd's pid file also become 600 which result in ppptray can only be run by root but not by user.

My question is:
How to set umask so that all new file user create have 600 permissions but permissions of pppd's pid file keep as 644. 

Thanks for help in advance!

If you want to stay on this course, I would suggest that you have the very **last** statement
of your "/etc/profile" set the umask back to 022 **only** for *root*;
something like ...
```
/etc/profile:
...
if [ $UID -eq "0" ]; then
  umask 022
fi

```

---

### Post by say2sky on 2007-12-27
> **Abu_Dayya said:**
> Try changing the umask in /etc/profile, then type umask 077. Then logout and login back again and see if the umask is changed or not. (you can find out by just typing umask with no parameters)

You are right. When umask in /etc/profile is set to 077, all new file user create will have 600 permission which is a higher security situation. But now the problem is all the new file including new process' pid file just like pppd will also have 600 permission. Like following output

> 
-rw------- 1 root coolguy 5 2007-12-25 03:42 /var/run/ppp0.pid


But now I have another program ppptray which need /var/run/ppp0.pid with 644 permission so as to ppptray can be run as normal user(not root). 

I think umask in /etc/profile is global setting which will cause all new file have same permission no matter it is user created file or a process's pid file. 

But what I want is a umask setting which only influence user's created file's permission but not process's pid file's permission. So umask in /etc/profile CANNOT achieve my goal.

I also try umask in ~/.bash_profile but this umask only influence new created file when this new file is created in console but not on xterm.

---

### Post by say2sky on 2007-12-27
> **asmoore82 said:**
> This is unnecessary; In order for another user to actually have read permission on a file,
they must have read permission on the entire path that the file is in.
So, even though I feel that setting a umask is not necessary,
I highly recommend 700 permissions on each user's home folder.
In fact, this is one of the first things I always do on new installs.

```
$ chmod 700 "$HOME"
```
-OR-
```
$ sudo chmod 700 /home/*/
```



If you want to stay on this course, I would suggest that you have the very **last** statement
of your "/etc/profile" set the umask back to 022 **only** for *root*;
something like ...
```
/etc/profile:
...
if [ $UID -eq "0" ]; then
  umask 022
fi

```

I appreciate your suggestion which can totally meet my goal. Thanks you very much. :)

---

### Post by say2sky on 2007-12-27
After asmoore82 give the good solution to my umask problem, I still want to think umask configuration file a little bit deeper. 

1. Why ubuntu let umask in ~/.bash_profile only control file permission user creating from console but not from xterm.   
2. What is the necessary ubuntu treat the user create file's permission differently by the place of console or xterm.
3. I think this ubuntu's arrangement have its reason, but from user's view, it is a little confusable. Why not let local umask setting control all user creating file.:confused:

---

### Post by asmoore82 on 2008-01-01
Ahh, I see.

The effect you are seeing is caused by whether or not the BASH shell has been invoked
as a true login shell or not. On the console, of course, it **is** a login shell.
From within X, however, it can go either way, but most X terminal apps on modern
linux systems will not invoke a login shell unless you tell them to.

**The quick fix**, is to have your favorite X terminal always invoke a login shell...
For `gnome-terminal`
click "Edit -> Current Profile"
click the "Title and Command" Tab
and check the first option under **Command**: "Run command as a login shell"

For `xterm` you need to pass it the command line switch "-ls"
(you may need to create a "Custom Laucher") so that the
complete command used to invoke xterm is `xterm -ls`

**The Real Solution** involves a key file that was missing from your original list... "$HOME/.bashrc"

Whilst BASH as a login shell will execute the contents of "/etc/profile" and "$HOME/.bash_profile"
on startup,a non-login BASH shell will read and execute the contents of "$HOME/.bashrc"
and nothing else. So, any customizations to your Environment that you wish to keep,
need to be *moved* to this file (and if you are using the user account created by the
Ubuntu installer, you will see this file is already populated with some "gooddies").
At this point, you will have solved the ppp problem by never creating it in the first place.
However, you have a new problem: BASH as a login shell (like from the console)
will not read "$HOME/.bashrc"
**Quick Fix**: naturally you could put your umask setting in both files; but this could
become hard to manage as you want to do more advanced customizations of your Environment.
**Real Solution**: what we really need here is a cascading effect whereby settings in
.bashrc are universal for all shells and .bash_profile is reserved for super-specific
tweaks that are needed only for login shell instances. Therefore, It is **highly customary**
to achieve exactly this by simply having the .bash_profile call the .bashrc. And thus on
modern desktop Linux systems where true console login shells are becoming more and
more archaic, it is commonplace to see a .bash_profile that does nothing but call .bashrc.
So, unless you really need them specifically for login shells and nothing else,
*move* your customizations in .bash_profile to .bashrc and then *change* your
.bash_profile to simply this:
```
#.bash_profile

if [ -f "$HOME/.bashrc" ]; then
  source "$HOME/.bashrc"
fi
#End of File
```

After you absorb all of this, you could take a step back and see the true beauty of it...
Your .bash_profile does nothing but cascade into .bashrc, so you can make all future
customizations in one convenient location("$HOME/.bashrc").
Assuming that umask is all you had changed, your "/etc/profile" has been restored to
its vanilla "out-of-the-box" state. This in turn means that you could have modified this
setting for yourself without ever needing root privilege.

---

### Post by say2sky on 2008-02-17
> **asmoore82 said:**
> Ahh, I see.

The effect you are seeing is caused by whether or not the BASH shell has been invoked
as a true login shell or not. On the console, of course, it **is** a login shell.
From within X, however, it can go either way, but most X terminal apps on modern
linux systems will not invoke a login shell unless you tell them to.

**The quick fix**, is to have your favorite X terminal always invoke a login shell...
For `gnome-terminal`
click "Edit -> Current Profile"
click the "Title and Command" Tab
and check the first option under **Command**: "Run command as a login shell"

For `xterm` you need to pass it the command line switch "-ls"
(you may need to create a "Custom Laucher") so that the
complete command used to invoke xterm is `xterm -ls`

**The Real Solution** involves a key file that was missing from your original list... "$HOME/.bashrc"

Whilst BASH as a login shell will execute the contents of "/etc/profile" and "$HOME/.bash_profile"
on startup,a non-login BASH shell will read and execute the contents of "$HOME/.bashrc"
and nothing else. So, any customizations to your Environment that you wish to keep,
need to be *moved* to this file (and if you are using the user account created by the
Ubuntu installer, you will see this file is already populated with some "gooddies").
At this point, you will have solved the ppp problem by never creating it in the first place.
However, you have a new problem: BASH as a login shell (like from the console)
will not read "$HOME/.bashrc"
**Quick Fix**: naturally you could put your umask setting in both files; but this could
become hard to manage as you want to do more advanced customizations of your Environment.
**Real Solution**: what we really need here is a cascading effect whereby settings in
.bashrc are universal for all shells and .bash_profile is reserved for super-specific
tweaks that are needed only for login shell instances. Therefore, It is **highly customary**
to achieve exactly this by simply having the .bash_profile call the .bashrc. And thus on
modern desktop Linux systems where true console login shells are becoming more and
more archaic, it is commonplace to see a .bash_profile that does nothing but call .bashrc.
So, unless you really need them specifically for login shells and nothing else,
*move* your customizations in .bash_profile to .bashrc and then *change* your
.bash_profile to simply this:
```
#.bash_profile

if [ -f "$HOME/.bashrc" ]; then
  source "$HOME/.bashrc"
fi
#End of File
```

After you absorb all of this, you could take a step back and see the true beauty of it...
Your .bash_profile does nothing but cascade into .bashrc, so you can make all future
customizations in one convenient location("$HOME/.bashrc").
Assuming that umask is all you had changed, your "/etc/profile" has been restored to
its vanilla "out-of-the-box" state. This in turn means that you could have modified this
setting for yourself without ever needing root privilege.




Thank you very much, and your explanation is very helpful to me to understand this shell and umask stuff. you're great!  :):popcorn:

---

