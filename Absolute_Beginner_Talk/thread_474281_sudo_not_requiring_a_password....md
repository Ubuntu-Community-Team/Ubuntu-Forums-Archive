---
title: "sudo not requiring a password...?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by patrickk on 2007-06-14
Hey guys

another question for you...i was playing around with sudo and I messed something up.

I typed the command

```
sudo passwd
```

intending to change the root password and thus the password required by sudo, but i'm not sure what it did...i logged in as root and changed my password back to what it was before, then i changed my password on the user account to something different...and now sudo doesnt require a password to operate...whether im logged on as root or just myself, when i type a sudo command it just does it...no prompting for a password.

any advice?  id like it to prompt for a password.

thanks a ton

--patrick

---

### Post by drs305 on 2007-06-14
How long has it been? In terminal, the password remains valid for 10 minutes...

---

### Post by freebird54 on 2007-06-14
I don't know if you've done something weird or not... is there any chance that all your testing took place within the sudo timeout limit?  It doesn't need it again till it times out....

just a thought! :)



EDIT: too slow.. :)

---

### Post by ryanVickers on 2007-06-14
Yeah, I think the terminal stays good for about 10 minutes, and the window that dims the screen is an hour?
Don't know about the last one, but you won't need it again for a few minutes, so wait awhile.

---

### Post by jfinkels on 2007-06-14
> **patrickk said:**
> Hey guys

another question for you...i was playing around with sudo and I messed something up.

I typed the command

```
sudo passwd
```

intending to change the root password and thus the password required by sudo, but i'm not sure what it did...i logged in as root and changed my password back to what it was before, then i changed my password on the user account to something different...and now sudo doesnt require a password to operate...whether im logged on as root or just myself, when i type a sudo command it just does it...no prompting for a password.

any advice?  id like it to prompt for a password.

thanks a ton

--patrick

The default timeout for sudo asking for a password is fifteen minutes. Take a look at the man page for sudo:```
man sudo
```

And to answer your question...what happens when you login as your regular username and then do ```
sudo passwd
``` again? That may fix it... if not, come back and post the output of this command:```
sudo cat /etc/sudoers
```

---

### Post by patrickk on 2007-06-15
ok so basically sudo now requires a password (you guys were right about the timeout) but it requires the wrong one...i have a root password and a password for username 'patrick', and sudo requires the password for username 'patrick', not the root password....

any ideas now?

i ran that statement mentioned above and here is the output:

```

patrick@patrickServer:~$ sudo cat /etc/sudoers
Password:
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```


thanks again for any help you can provide.

---

### Post by YoG%*@ on 2007-06-15
> **patrickk said:**
> and sudo requires the password for username 'patrick', not the root password....


well, that's exactly how it's supposed to work ;) 
try [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
for more information about sudo!

hth
mux

---

### Post by patrickk on 2007-06-15
> **mux said:**
> well, that's exactly how it's supposed to work ;) 
try [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
for more information about sudo!

hth
mux

oh wow!  ok...im an idiot.  I had no clue that was the point...I'm a little new to sudo, i've always just logged in as root and done it that way.

so I'm confused...this means a regular user can run any command with su privileges without the su password...isnt that the whole point having a separate password for su?

--patrick

---

### Post by Papi-KB7VGW on 2007-06-15
I'm sure someone will correct me if I'm wrong but I believe that only the first user account is given admin privileges...

---

### Post by eternalsword on 2007-06-15
Your personal login is like super user but you need to keep entering your  password to do anything and you have to use sudo or some similar alternative.  When logged in as su, no password is ever needed beyond the login.  You can also create other user accounts that can't use sudo either.

---

### Post by jfinkels on 2007-06-15
> **patrickk said:**
> oh wow!  ok...im an idiot.  I had no clue that was the point...I'm a little new to sudo, i've always just logged in as root and done it that way.

so I'm confused...this means a regular user can run any command with su privileges without the su password...isnt that the whole point having a separate password for su?

--patrick

Don't feel stupid, it's counter-intuitive. 

The program "su" will log you in to a root terminal, so you will login as 'root' with the password for that user.

The program "sudo" is a special program that allows certain users (specifically designated in the configuration file at /etc/sudoers) to run programs AS the root user, without requiring a traditional login. This is good for a few reasons, the most significant being that you can perform administrative actions without completely logging in (after logging out if necessary) as a different user.

---

### Post by jfinkels on 2007-06-15
> **eternalsword said:**
> Your personal login is like super user but you need to keep entering your  password to do anything and you have to use sudo or some similar alternative.

Um, not exactly...the user you created when you installed Ubuntu is not like the super user...in fact, NO user is like the super user (or "root" user); the super user is unique on the system.

You only need to use sudo to run programs or edit files if your user does not have sufficient rights to execute or read or write that file, because the super user has rights to do all of that :D

---

