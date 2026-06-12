---
title: "Finding who has accounts on my system."
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Cafwin on 2006-06-04
Hello all, new here.

What I'm trying to find out is how to find out who all has accounts on my system when I'm logging in from work.

I know how to see who's logged in at any time, but I need to know how to find all accounts created. Someone I trust has the main account access, but want to keep an eye on the system just to make sure I know who all has accounts.

BTW, I did change the password for my account, but not sure what type of account he created for himself.

So I'll start with that and go from there. Thanks in advance.

---

### Post by taurus on 2006-06-04
All accounts on a system is logged in /etc/passwd so that is a good place to start!

---

### Post by nanotube on 2006-06-04
[QUOTE=taurus]All accounts on a system is logged in /etc/passwd so that is a good place to start![/QUOTE]

and a good place to continue is in /etc/group, to see what users are members of what group. so if you want to see if your friend's account has admin privileges, for example, you would look in /etc/group and see if his username is listed in "admin" or "adm" or "root".

---

### Post by Cafwin on 2006-06-04
Hmmm, thanks for the responses, but I should mention I'm very green with Linux. I opened the terminal and just typed in "/etc/passwd" and got a message I don't have priveledge? :confused: 

I assume this is done from the terminal, correct? Does it require beginning the line with "sudo"? I apologize for my ignorance on this, but I'm trying to learn. :D 

Thanks again for the responses.

---

### Post by Cafwin on 2006-06-04
Actually, would it be something along the lines of "cd /etc.passwd" or is that way off the mark?

---

### Post by J0E0NE on 2006-06-04
Im also very new to linux but whenever I don't have priveledge put sudo infront of what your doing in the terminal so: sudo /etc/passwd for an example.
It will then ask for your password, just type it in and press enter.

Please note im very new to linux and if anything I've said is wrong im very sorry ;)

---

### Post by IYY on 2006-06-04
/etc/passwd and /etc/groups are just text files. You can view them in any editor. For example:

cat /etc/passwd

or 

nano /etc/passwd

or my favourite:

less /etc/passwd

---

### Post by nanotube on 2006-06-04
what IYY said is correct :)

in general, you guys might want to read up a bit about using the commandline. there are some good resources in the first link in my sig, under "other commandline resources" section.

---

### Post by Cafwin on 2006-06-04
Using cat, I was able to find the account but it doesn't really tell me what sort of account it is. 

I should note, I'm familiar (well, was until Windows made it so easy to just GUI everything) with command line OS', but not fresh and Linux is close enough to DOS to get me just confident to screw everything up at any moment. ;) 

I played around with the system log option and it appears it may have been a root account. Again, I'm not very concerned about it but want to start out of the gate knowing what I'm doing with assigning accounts and selecting levels of access.

So now the question becomes, based on what all is listed in /groups (No idea what 80% of the stuff listed is), how do I discover what the level of the account is? FWIW, it appears very similar as my main account, but really not sure if it's the same level. 

On top of that, is it possible a stealth account was set up? Does "/etc/groups" show every single "account"? Also, if it is a root account, how would I delete it and reassign a new account for him to access the system with selected priviledges?

If you need any other info, I'm more than happy to provide it.

---

### Post by kaamos on 2006-06-04
It would be easier if you would just paste the relevant part of the log here.

---

### Post by Cafwin on 2006-06-04
OK, went back to messing around with the directory using "nano". I'm listed as "adm", he's listed as "root".

So I guess it pretty much comes down to, how do I delete that, and how do I set up an account for him?

I'm sure I'll still need help in setting access level, but I'll worry about that later.

Thanks again for all this help. It's much appreciated.

---

### Post by taurus on 2006-06-04
His login name is root!!!  You don't want to remove that account.  If you don't want him to log in as root anymore, then change the password with this command from a terminal (Applications -> Accessories -> Terminal)
```

sudo passwd root
(your password)
(new root password)
(retype new root password again)

```
Then, just create a regular account for him and tell him to use that to log in UNLESS he needs to fix or installs something on your machine...

---

### Post by Cafwin on 2006-06-04
Thanks, **Taurus**. Got the password changed. Now, how do I:

1. Rename that login?

2. Set up the new account? (I realize he can tell me, but I'd rather do it and surprise him that I found out how to do it. It's a guy thing I guess) ;)

Also, with control over the root account, how much different is it from the Adm account? And is there a way to see if a shadow or backdoor account is present? It's a PITA to go back and change all Windows passwords so I want to get everything setup so I only have to do it once.

Thanks again, so much, for the help. You guys rock!

---

### Post by taurus on 2006-06-04
You can't rename root to something else.  Just change the password and you should be fine.  If he tries to log in as root the next time, he will find out soon enough that his old password doesn't work and you can't log in as root anymore...  ](*,) 

And if you want to create a regular account for him, you can use the useradd command that looks something like
```

sudo useradd -m -G users -s /bin/bash <username>
sudo passwd <username>

```
Don't put him in groups adm and/or admin because he can just change root's password again...  That would be suck for you!  ;)

---

### Post by nanotube on 2006-06-04
[QUOTE=taurus]You can't rename root to something else.  Just change the password and you should be fine.  If he tries to log in as root the next time, he will find out soon enough that his old password doesn't work and you can't log in as root anymore...  ](*,) 

And if you want to create a regular account for him, you can use the useradd command that looks something like
```

sudo useradd -m -G users -s /bin/bash <username>
sudo passwd <username>

```
Don't put him in groups adm and/or admin because he can just change root's password again...  That would be suck for you!  ;)[/QUOTE]
also check /etc/sudoers, to see if his username was listed separately in that. usually, /etc/sudoers lists entire group "admin" as able to use sudo. then, anyone in the admin group can get root privileges, and nobody else. so if you jsut remove his username from admin group, and from root group, his account will turn into a regular user account.

---

### Post by Cafwin on 2006-06-05
OK, so I kept him out of the root but gave him an Adm account. Now what I need to do is get access to changing the password on that account and doing the above mentioned steps to create just a regular user account.

I was using the "man -k" commands and saw what I wanted to get to, just can't figure out how to get to the functions.

I'm feeling a little more comfortable already with this style of OS, but still stuck with accessing even the basic help files.

Again, I can't tell you how much I appreciate the help. Though this is all coming back bit by bit.

---

### Post by nanotube on 2006-06-05
[QUOTE=Cafwin]OK, so I kept him out of the root but gave him an Adm account. Now what I need to do is get access to changing the password on that account and doing the above mentioned steps to create just a regular user account.

I was using the "man -k" commands and saw what I wanted to get to, just can't figure out how to get to the functions.

I'm feeling a little more comfortable already with this style of OS, but still stuck with accessing even the basic help files.

Again, I can't tell you how much I appreciate the help. Though this is all coming back bit by bit.[/QUOTE]
well, post the output of "sudo cat /etc/sudoers" here. we will see what is says. if the sudoers file says that members of adm group can sudo, then effectively he still has a root level account. 

but at any rate, why did you put him into adm? if you want him to be regular user, just take him out of all groups besides the group with the same name as his username.

---

### Post by Cafwin on 2006-06-05
Dang it, I keep forgetting that sudo command. Anyway, here's what I got, it appears I need to use another command/app?


 sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


No idea what all that means.

---

### Post by Cafwin on 2006-06-05
Tried the sudo before entering the request and got the same result.

---

### Post by nanotube on 2006-06-05
[QUOTE=Cafwin]Dang it, I keep forgetting that sudo command. Anyway, here's what I got, it appears I need to use another command/app?


 sudo cat /etc/sudoers
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


No idea what all that means.[/QUOTE]

that "sudo cat" command just says "output the contents of this file on the screen". according to what you have, it looks good (no changes from the default). so if a user is not in admin group, he has no sudo privileges.

---

### Post by Arndt on 2006-06-05
[QUOTE=Cafwin]Hello all, new here.

What I'm trying to find out is how to find out who all has accounts on my system when I'm logging in from work.

I know how to see who's logged in at any time, but I need to know how to find all accounts created. Someone I trust has the main account access, but want to keep an eye on the system just to make sure I know who all has accounts.

BTW, I did change the password for my account, but not sure what type of account he created for himself.

So I'll start with that and go from there. Thanks in advance.[/QUOTE]

There is a Users and Groups administration tool under the System->Administration menu. Is that what you want?

---

