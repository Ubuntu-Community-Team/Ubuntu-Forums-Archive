---
title: "&#8220;Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-01-18
I hve searched and red threads on this topic .

But I am still lost

cna somebody give me a step by step lesson on how to fix this error
?


what exactly doe sit mean by the way? what happens if I just ignore it?

Thanks

Robi

---

### Post by taurus on 2007-01-18
Boot into recovery mode from GRUB menu and see what is the permission of that file, _assuming_ beanco is your login name.

```
ls -la /home/beanco/.dmrc
```

---

### Post by steve.horsley on 2007-01-18
Try this command:
**sudo rm ~/.dmrc**

---

### Post by beanco on 2007-01-19
> **steve.horsley said:**
> Try this command:
**sudo rm ~/.dmrc**

this is what I got

robi@robi:~$ sudo rm ~/.dmrc
rm: cannot remove `/home/robi/.dmrc': No such file or directory


I also tried 

robi@robi:~$ ls -la/home/robi/.dmrc
ls: invalid option -- /


and this:

robi@robi:~$ sudo chown robi $home/ .dmrc
Password:
chown: cannot access `.dmrc': No such file or directory

so what does all this mean?

|What will the consequences be?

Thanks

Robi

---

### Post by riven0 on 2007-01-19
> **beanco said:**
> this is what I got
I also tried 

robi@robi:~$ ls -la/home/robi/.dmrc
ls: invalid option -- /


Hey, that should be **ls -la /home/robi/** <-- watch out for the space :)

and then look for the file .dmrc in the results it brings up.

---

### Post by beanco on 2007-01-19
> **riven0 said:**
> Hey, that should be **ls -la /home/robi/** <-- watch out for the space :)

and then look for the file .dmrc in the results it brings up.

ok thanks

while waiting for a reply i searched  the forums again and found this

sudo chmod 700 <home folder> 

which I did, rebooted and I did not get the error msg so this command worked for me,

I have no idea why... 

could you tell what i did and what your suggestion would have done?

Thanks

robi

---

### Post by riven0 on 2007-01-19
> **beanco said:**
> ok thanks

while waiting for a reply i searched  the forums again and found this

sudo chmod 700 <home folder> 

which I did, rebooted and I did not get the error msg so this command worked for me,

I have no idea why... 

could you tell what i did and what your suggestion would have done?

Thanks

robi

How about trying one of these:

> sudo chmod 777 /home/robi/.dmrc

or if that doesn't work:
> 
sudo chmod a+x /home/robi/.dmrc  ^ though I'm not sure how secure this is since it gives all users administrative abilities over the file.

---

### Post by beanco on 2007-01-19
I got this

-rw-------  1 robi root      26 2007-01-19 08:44 .dmrc


is that good or bad?

what happens if I try the  chmod 777 option.. i mean what is it that  I would be attempting with that?

robi

---

### Post by pistcivet on 2007-01-19
> **beanco said:**
> I got this

-rw-------  1 robi root      26 2007-01-19 08:44 .dmrc


is that good or bad?

what happens if I try the  chmod 777 option.. i mean what is it that  I would be attempting with that?

robi
The permissions seem to be correct (they are the same as mine)
The group is wrong though. I don't know if this is a problem, but don't chmod anything.
try this:```
sudo chown robi:robi ~/.dmrc
```

---

### Post by benson444 on 2007-01-19
Permissions are the same as mine too. To change the group try

sudo chgrp robi ~/.dmrc

Some info on file permissions in Linux [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

### Post by steve.horsley on 2007-01-19
> **beanco said:**
> ok thanks

while waiting for a reply i searched  the forums again and found this

sudo chmod 700 <home folder> 

which I did, rebooted and I did not get the error msg so this command worked for me,

I have no idea why... 

could you tell what i did and what your suggestion would have done?

Thanks

robi

You just gave yourself full access and read/write permissions to your home folder. That is very odd - you should have had full access anyway. Something must have got screwed. Just as a double-check, do ls -l /home/ and make sure you are the ownser of your home directory.

---

### Post by az on 2007-01-19
> **steve.horsley said:**
>  Something must have got screwed. Just as a double-check, do ls -l /home/ and make sure you are the ownser of your home directory.

AFAIK, Gnome will throw that message when your home folder is world-writeable.  It's a bug.  There should be two different error messages (.dmrc incorrect permissions versus home folder incorrect permissions)

---

### Post by bodhi.zazen on 2007-01-19
.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown user_name /home/user_name

	OR, if that fails:

> 	sudo chown  user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

---

### Post by ComplexNumber on 2007-01-19
i had the same problem about a month or so ago. it went like that suddenly, but i can't remember what i suspected caused it. i got round it by changing the permissions of "/" to 755 by 'sudo chmod 755 * /' (do NOT do 'sudo chmod -R * /'). somehow, the permissions of some directories in / got changed.
its nothing to do with the .dmrc file.

---

### Post by beanco on 2007-01-19
> **steve.horsley said:**
> .... ... Just as a double-check, do ls -l /home/ and make sure you are the ownser of your home directory.


this is what I got

drwx------ 35 robi  robi  4096 2007-01-19 17:56 robi


robi

---

