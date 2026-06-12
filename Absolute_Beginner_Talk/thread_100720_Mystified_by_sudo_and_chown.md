---
title: "Mystified by sudo and chown"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by billd on 2005-12-08
I've been learning about users, groups, file permissions (chown, chgrp, chmod), etc.  Anything within my home directory I can change around at will.  But it seems like -- even with sudo -- there are a lot of things I can't do in other locations.  Or I'm doing them wrong.

For example, if I say...

chown bill /usr/local

... I get the error message that I'm not permitted to do that, which makes perfect sense because I'm running the command in the context of my user account.

But if I do this....

sudo chown bill /usr/local

... I get no message whatsoever and the directory ownership does not change.  I've noticed this lack of a message a few times -- doing sudo commands that just return right back to the prompt without any messages.  So two questions: 1) why is sudo sometimes so silent? and 2) why didn't my example of changing the ownership of /usr/local (using sudo) successfully change the ownership?

Note this also doesn't work and gives no error message:

sudo chmod o+w /usr/local

(Note: I know I shouldn't be changing ownership or access rights in /usr/local -- I just wanted to see if I could and, if not why not.)

---

### Post by ChrisTheGeek on 2005-12-08
I would test sudo stuff on a non-vital directory. You could create a directory owned by root under /tmp for example.

The command you typed looked like it should work to me.  Are you sure the changes didn't take effect?  What's the output of: 

ls -la /usr/local

You can also try chown with a "-v" option to make it output what it's up to.

What are the entries in the file /etc/sudoers?

---

### Post by billd on 2005-12-08
Uh oh, I see the problem is worse than I thought.  Now I cannot do anything that requires sudo.  For example, if (at the desktop) I try System - Administration - Synaptic Package Manager, I get prompted as expected for my password, and then nothing happens after I enter the password.  (I've run the package manager many times successfully)

So obviously I messed up big time.  And I cannot see inside sudoers (permission denied).  And since I cannot do anything with sudo, I really can't see inside sudoers!

The permissions for sudoers are
-r-- r-- ---
and the owner and group are root

The permissions for the group file (also in /etc) are
-r-- r-- r--
and the owner and group are root, and I CAN see inside this file.

So obviously my inability to see the contents of sudoers is because I am considered to be in the "other" permission category, which has --- permissions.

Have I somehow fallen out of a root group or something?  The only thing I can think of is yesterday I created a group named cvs and I put myself into it.  Did I remove myself from another group as I did that?

Assuming I've screwed up my ability for my user id to use sudo forever, is there anything I can do short of re-installing ubuntu?

Thanks much for your help.
bill

---

### Post by billd on 2005-12-08
Never mind... I noticed that when I boot I have a Ubuntu "recovery" option which takes me straight in as root.  Thank God for that, but i imagine it's a bit of a controversial feature, since it requires no password to go directly in as root and do anything you want.   But I imagine it's configurable somewhere.  I probably even had an option to turn it off when I installed Ubuntu, but ignored it.  (And now I'm glad for that.)

So once in as root, I did "man usermod" to read more about that, because yesterday I added myself to a new group I created.  Sure enough, with the -G option I forgot to keep myself in the admin group.  The man page (I now realize!) makes it clear that usermod -G will take the user out of any group that he belongs to unless you re-specify it.  So yesterday I did:

usermod -G cvs bill

which I guess put me into the cvs group and took me right out of the admin group.  Today, while root, I did

usermod -G admin,cvs bill

and then re-started and logged in as bill and now everything is just fine.


Many thx,b

---

### Post by ChrisTheGeek on 2005-12-09
Yeah, been there, done the same thing :-)  It's one of those lovely sinking feelings.  Fortunately not too hard to fix.  I resorted to a live CD to edit /etc/groups and add the 'admin' group to my name.

Might be worth creating a spare user who also has access to sudo.

Chris

---

### Post by doclivingston on 2005-12-09
[QUOTE=billd]The permissions for sudoers are
-r-- r-- ---
and the owner and group are root[/QUOTE]

That is normal, in fact if the permissions/owner are anything other than exactly that, sudo will assume that there is a potential security breach and refuse to give you root powers. If you do accidently change the permissions on /etc/sudoers to anything else, you will have to reboot in single user ("recovery" mode) to fix it.

---

### Post by steve.horsley on 2005-12-09
[QUOTE=billd]
But if I do this....

sudo chown bill /usr/local

[/QUOTE]

Er..... don't do that.

The absence of an error message means that you **did** succeed. To see, use the command **ls -ld /usr/local**. It should be owned by root. To change ownership of things in the directory too, you want recursive chown :- **chown -R bill /usr/local**. You definitely shouldn't do that.

If you are doing a lot of root work, you can do **sudo su** to get a root command prompt for as long as you need.

Below is a transcript of me doing the chown thing, just to prove it works. Y'know, I felt really uncomfortable doing that!

Steve

```

steve@StevesPC:~$ ls -ld /usr/local
drwxr-xr-x  9 root root 240 2005-10-20 22:18 /usr/local
steve@StevesPC:~$ chown steve /usr/local
chown: changing ownership of `/usr/local': Operation not permitted
steve@StevesPC:~$ sudo chown steve /usr/local
Password:
steve@StevesPC:~$ ls -ld /usr/local
drwxr-xr-x  9 steve root 240 2005-10-20 22:18 /usr/local
steve@StevesPC:~$ sudo chown root /usr/local
steve@StevesPC:~$ ls -ld /usr/local
drwxr-xr-x  9 root root 240 2005-10-20 22:18 /usr/local

```

---

