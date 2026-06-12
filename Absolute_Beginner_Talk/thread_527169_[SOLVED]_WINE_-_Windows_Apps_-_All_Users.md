---
title: "[SOLVED] WINE - Windows Apps - All Users"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by WebSiteGuru on 2007-08-16
Hi everyone,

A question had pop up (myself asking) since I just setup Ubuntu (newbies here) and loaded WINE to use Windows Apps.

Icurrently have 2 users account setup:
me (superuser)
my wife (normal user)

I would like to know if it is posible to set up Windows Apps programs in WINE from my profile and still let the other user use the program.

Is it posible?

Thanks in advance! :guitar:

---

### Post by jspangler on 2007-08-16
I think it should be possible. First, map the wine drive to a folder that all users can access. Perhaps, /home/winedrive and then:

```
sudo chmod -R 777 /home/winedrive
```

Then, setup the wine config file the way you want it on your user account. Then, copy the .wine directory (this is all the wine configuration files) to the other account's home directory as well. Make sure that you map "C:" in winecfg to /home/winedrive.

---

### Post by asmoore82 on 2007-08-16
I think symbollic links (shortcuts) could accomplish the same thing more cleanly.

move your .wine folder to /home/wine and make a symbollic link named .wine to /home/wine in the 2 user's homes
I would make the global wine folder owned by a group that both users will be in; like `cdrom'

```
~ $ ln -s /home/wine .wine
~ $ chown -R 1000:cdrom /home/wine
~ $ chmod -R o-rwx /home/wine
~ $ chmod -R ug+rw /home/wine
```

---

### Post by bogolisk on 2007-08-16
> **asmoore82 said:**
> I think symbollic links (shortcuts) could accomplish the same thing more cleanly.

move your .wine folder to /home/wine and make a symbollic link named .wine to /home/wine in the 2 user's homes
I would make the global wine folder owned by a group that both users will be in; like `cdrom'

```
~ $ ln -s /home/wine .wine
~ $ chown -R 1000:cdrom /home/wine
~ $ chmod -R o-rwx /home/wine
~ $ chmod -R ug+rw /home/wine
```

That's a very good post. Remember you have to start with a .wine directory in your home dir *first*, then move it to its final destination such as /home/wine and create the soft-link.

---

### Post by WebSiteGuru on 2007-08-16
> **asmoore82 said:**
> I think symbollic links (shortcuts) could accomplish the same thing more cleanly.

move your .wine folder to /home/wine and make a symbollic link named .wine to /home/wine in the 2 user's homes
I would make the global wine folder owned by a group that both users will be in; like `cdrom'

```
~ $ ln -s /home/wine .wine
~ $ chown -R 1000:cdrom /home/wine
~ $ chmod -R o-rwx /home/wine
~ $ chmod -R ug+rw /home/wine
```

So, let me get this straight before I dive in and screwed everything up. (just want to make sure)

1st - I move .wine folder from my useraccount to /home/wine folder.

2nd - Create a Global Group to give access to /home/wine folder.

3rd - Run the code as indicated above.

Is that right? :D

---

### Post by bogolisk on 2007-08-16
> **WebSiteGuru said:**
> So, let me get this straight before I dive in and screwed everything up. (just want to make sure)

1st - I move .wine folder from my useraccount to /home/wine folder.
```

mv ~/.wine /home/wine
ln -s /home/wine ~/.wine

```

> 
2nd - Create a Global Group to give access to /home/wine folder.


Reusing a group like plugdev or cdrom should be ok. Because your wife is allowed to use the usb keys and cdroms isn't she?
> 
3rd - Run the code as indicated above.
```

chgrp -R plugdev /home/wine
chmod -R o-rwx /home/wine
chmod -R ug+rw /home/wine

```

---

### Post by WebSiteGuru on 2007-08-16
OK! I am having a little problem. /home/wine folder does not exist, and when I tried to create it. It said permission denied.

What do I do now. I am using my superuser account.:confused:

---

### Post by panther_sn on 2007-08-16
Ok try in terminal
```

sudo mkdir /home/wine

```
Should work perfectly

---

### Post by bogolisk on 2007-08-16
> **panther_sn said:**
> Ok try in terminal
```

sudo mkdir /home/wine

```
Should work perfectly

Careful here, it's better to do:
```

sudo mv ~/.wine /home/wine

```

Because
```

sudo mkdir /home/wine
mv ~/.wine /home/wine

```
would create /home/wine/.wine and not what you want.

---

### Post by diatribe on 2007-08-16
uhm I hope you do not intend to use a root-access account on a regular basis?  this is a terrible practice to start

---

### Post by WebSiteGuru on 2007-08-17
OK! Got it. I also had to put sudo in front of all command. Thanks!

> **diatribe said:**
> uhm I hope you do not intend to use a root-access account on a regular basis?  this is a terrible practice to start

Who said anything about using root access account.:confused:
.

---

### Post by WebSiteGuru on 2007-08-17
OK! One more quick question and it should be good to go.

Installing Windows Apps in WINE! Currently, it will install it to the user profile. How do I install it and have it install in /home/wine/.wine/ folder?

So, I dont have to keep moving all Windows apps everytime I install anything. Thanks in advance! :D

---

### Post by jspangler on 2007-08-17
Once you install wine and set up the symbolic links (as discussed above), you should be able to install any new programs without doing anything else.

---

### Post by bogolisk on 2007-08-17
Let's revise the steps:
[LIST]
[*] run winecfg. This will among other things create the ~/.wine directory if it doesn't already exist.
```
winecfg
```
[*] move/rename ~/.wine into /home/wine so it can be easily shared by other users. This likely requires admin priv thus the sudo prefix command.
```
sudo mv -T ~/.wine /home/wine  
```
if the above command gave an error it might be because /home/wine already existed. You then should try to remove the /home/wine directory first.
```
sudo mv /home/wine /home/old_wine
```
[*] now make ~/.wine a symlink (alias) to /home/wine
```
ln -s /home/wine ~/.wine
```
[*] make /home/wine and its contents usable by all users in plugdev group. First change the group of all the files under /home/wine to plugdev
```
sudo chgrp -R plugdev /home/wine
```
Now let everyone in plugdev group read and modify files under /home/wine
```
sudo chmod -R g+rw /home/wine
```
Remove access from users *not* in plugdev group
```
sudo chmod -R o-rwx /home/wine
```
[/LIST]

Hope that would help. Readers please review my steps because they're untested!

---

### Post by WebSiteGuru on 2007-08-17
Cool, I'l try that tonight when I get home. :D

---

### Post by diatribe on 2007-08-17
> **WebSiteGuru said:**
> OK! Got it. I also had to put sudo in front of all command. Thanks!



Who said anything about using root access account.:confused:
.

What do I do now. I am using my superuser account.

a superuser account has root-access

---

### Post by WebSiteGuru on 2007-08-17
> **diatribe said:**
> What do I do now. I am using my superuser account.

a superuser account has root-access

your user account do not have superuser access all the time (only when you tried to install things that is when it asked you for the password - one time privrage) it is not a root account, just have the priverage as root. Root account is hidden (to my knowledge).

---

### Post by diatribe on 2007-08-17
you asked what I was referring to I replied, and if you are using the sudo command then you are not using a superuser account, this would be accomplished either with sudo -i or logging in as root or using su

---

### Post by WebSiteGuru on 2007-08-17
> **diatribe said:**
> you asked what I was referring to I replied, and if you are using the sudo command then you are not using a superuser account, this would be accomplished either with sudo -i or logging in as root or using su

Sorry, I missed understood what you said. Message Understood Now. :D

---

### Post by diatribe on 2007-08-17
all good :D

---

### Post by WebSiteGuru on 2007-08-18
OK! Done all the steps. Hopefully everythings goes well.

---

### Post by WebSiteGuru on 2007-08-20
Works perfectly,  I'll tag this thread as SOLVE! :D

I only have one minor poproblem [full permission to the folders and files that was installed.]. If anyone can tell me how to fix that so, I dont have to change the permission of the files and folders everytime I install anything.

---

### Post by bogolisk on 2007-08-26
> **WebSiteGuru said:**
> Works perfectly,  I'll tag this thread as SOLVE! :D

I only have one minor poproblem [full permission to the folders and files that was installed.]. If anyone can tell me how to fix that so, I dont have to change the permission of the files and folders everytime I install anything.

```

cd /path/to/windows/installation/programs
sg plugdev 'wine setup.exe'

```

[list]
[*] using the 'sg plugdev' prefix will run the installation program (under wine) using the group plugdev. Thus, any files/directories created will be assigned to group plugdev.
[*] sg requires you to quote the command ('wine setup.exe'). Thus it's simpler if you 'cd' into the directory first to avoid complicated shell-quotings.
[/list]

---

### Post by krevuru on 2008-03-03
Linux Gurus, can anyone please consolidate these steps into a single shell script so that I can simply run it by changing a few paths and User-group?
Thanks in advance.

---

### Post by davbren on 2008-05-18
This is a great post but shouldn't this be part of the wine software already. These are hardly the instructions for a n00b.

---

