---
title: "Installation question"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by drsox1899 on 2008-03-12
I'm installing onto a HD from a live CD and find it odd that I am not asked anything about the "root" or"Administrator" account.  Is there a default setting for this Name and Password that I can access and change?

I have set up my account with name and password, but isn't there a facility for doing the same for root ?

Thanks

---

### Post by mikeyphi on 2008-03-12
> **drsox1899 said:**
> I'm installing onto a HD from a live CD and find it odd that I am not asked anything about the "root" or"Administrator" account.  Is there a default setting for this Name and Password that I can access and change?

I have set up my account with name and password, but isn't there a facility for doing the same for root ?

Thanks

Root is automatic - you can use root privlage by using the command 'sudo' followed by your user password - when requested. 
Read more here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sandysandy on 2008-03-12
in ubuntu the first account that is created during installation (the one ur using right now for example) is of super doer.

whenever u want root privileges, u can use the code [COLOR="Blue"]sudo[/COLOR].

u will be asked to authenticate with password.

regards

---

### Post by EnergySamus on 2008-03-12
Just type 

Su

into the terminal. You are now Root!

EnergySamus

---

### Post by drsox1899 on 2008-03-12
Hey, thanks for all the replies.

So I guess that I am unable to login as root ?  On other versions of Linux there was a separate account called "ROOT"  with its own password.  This is not what happens here ?

One of the benefits of having a unique root login account was that if the user account was corrupted (happened to me within a week of starting), I could login as root and retrieve my user data prior to reinstalling.  What happens on Ubuntu if the user account is corrupted ?

Regards

---

### Post by sandysandy on 2008-03-12
> **drsox1899 said:**
> Hey, thanks for all the replies.

So I guess that I am unable to login as root ?  On other versions of Linux there was a separate account called "ROOT"  with its own password.  This is not what happens here ?

One of the benefits of having a unique root login account was that if the user account was corrupted (happened to me within a week of starting), I could login as root and retrieve my user data prior to reinstalling.  What happens on Ubuntu if the user account is corrupted ?

Regards

just make one more account. that account should work fine.

if u want  - keep one more account standby with admin privileges.

regards

---

### Post by drsox1899 on 2008-03-12
Thanks.  Don't all accounts have admin priviliges ?  Where do I specify that an individual account can/can't do ?

Regards

---

### Post by sandysandy on 2008-03-12
> **drsox1899 said:**
> Thanks.  Don't all accounts have admin priviliges ?  Where do I specify that an individual account can/can't do ?

Regards

Go to Systems ---> Administrations ------> Users and Groups

u will get users settings.

click on add users

u will get New User Account.

click on user privileges tab.

various option are there what the new user can do including ´ Administer the System´

if u tick this u get admin account.

regards

---

### Post by Oldsoldier2003 on 2008-03-12
> **drsox1899 said:**
> Thanks.  Don't all accounts have admin priviliges ?  Where do I specify that an individual account can/can't do ?

Regards
you can specify priveledges in system>administration> users and groups. Bby default the account you created is part of the admin group, you have to specifically make a new account part of that group if you want it to be able to fully administer the machine

---

### Post by drsox1899 on 2008-03-12
I'm having problems here !

I have a Terminal open.
I type in su
It asks me for a password
I type in my account password
It says (Raspberry sound) - Authentication failure, Sorry

This is the sequence when I try to add a new user.
What am I doing wrong.

Regards

---

### Post by sandysandy on 2008-03-12
> **drsox1899 said:**
> I'm having problems here !

I have a Terminal open.
I type in su
It asks me for a password
I type in my account password
It says (Raspberry sound) - Authentication failure, Sorry

This is the sequence when I try to add a new user.
What am I doing wrong.

Regards


its sudo ( and not su)  followed by command u want to execute with root privileges.
 for adding new user please see my post above. you can do it from GUI. no need for CLI.

regards

---

### Post by drsox1899 on 2008-03-12
OK, thanks.

I guess I was using the wrong approach to adding users.

I used the other method from sandysandy and Oldsoldier2003 and I now have another - spare - user account.

Regards

---

### Post by thisiam on 2008-03-12
I was having this problem when i would try to make my user root. 
with su "username" --> password incorrect but i would use the same password as i would with sudo, which was wrong.
this thread explaines it good. [http://ubuntuforums.org/showthread.php?t=34089](http://ubuntuforums.org/showthread.php?t=34089)

---

### Post by drsox1899 on 2008-03-12
OK.  Clear.

BUT different to what I expected - that's OK as long as there is a way though it all.

Thanks to Ubuntu for having such helpful forum collaborators.

Regards

---

### Post by drsox1899 on 2008-03-12
PS.  Is there a User Manual in the Ubuntu archives somewhere that would explain this sort of stuff.  

There must be a better way than to trawl through the Newbie User Forum ?

Regards

---

### Post by sandysandy on 2008-03-12
> **drsox1899 said:**
> PS.  Is there a User Manual in the Ubuntu archives somewhere that would explain this sort of stuff.  

There must be a better way than to trawl through the Newbie User Forum ?

Regards

here are some links

[COLOR="Blue"]Ubuntu specific[/COLOR]

[https://help.ubuntu.com/7.10/](https://help.ubuntu.com/7.10/)

[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

[COLOR="Blue"]
Linux / Unix[/COLOR]

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

[http://lowfatlinux.com/linux-directories.html](http://lowfatlinux.com/linux-directories.html)

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=1](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=1)

there are lot of ebooks also available on the net. just google it.

regards

---

