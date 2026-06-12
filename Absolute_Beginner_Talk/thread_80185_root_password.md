---
title: "root password"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by HJThis on 2005-10-21
Hello,All

Well after having a look around the site looking
for info to copy down for myself.

i'm lost as far as the password gos in Ubuntu
so i will ask here ok so there is just one password????

the one you use at install i don't get it i don't
remember using a root password at install time
if it is just one passwd for both root & user.

could someone tell me how would you go about
changing say user passwd so i'm thinking that
doing this will also change the root passwd????

Yes not sure about this anyone at all please help

Thank you

---

### Post by Kyral on 2005-10-21
Root Account is disabled. Ubuntu uses Sudo.

Look here for more info

[https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29)

---

### Post by rykel on 2005-10-21
[QUOTE=Kyral]Root Account is disabled. Ubuntu uses Sudo.

Look here for more info

[https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29)[/QUOTE]

hey kyral, are u japanese? or do u come from japan?    :D

---

### Post by HJThis on 2005-10-21
Hi,Kyral

First thanks for the reply & yes i am having a look
at the link you posted.

but what i was trying to find out is if you go &
change the user passwd will this also do the same
for the root passwd or sudo as you put it.

i am asking because i don't like the passwd i used
at install. well not for the way that Ubuntu has it setup

Thank you

P.S

But i have to say that i do like this Ubuntu a lot

---

### Post by Kyral on 2005-10-21
[quote=rykel]hey kyral, are u japanese? or do u come from japan?    :D[/quote]

Nope, just an Anime Fanboy ;P

HJThis: If you change your user password your password for sudo will become that.

---

### Post by HJThis on 2005-10-21
Hey,Kyral

Ok i thank you big time have a great one

Thank you

---

### Post by darth_vector on 2005-10-22
the root account is not disabled. it just has no password.

you can become root by:

sudo su -

you can change the root password by modifying /etc/shadow

---

### Post by paddyg on 2005-10-22
If you need to log in as root:

1. give root a password:
system-->administration-->users and groups (show all users and groups)--> root -->properties

2. select:
system-->login screen setup -->security-->allow root to login with GDM

---

### Post by HJThis on 2005-10-22
Hey,To

First thanks for all the replys to this but
it's not so much i need to login as root
i just do not like the password i used at
install time.

but it's cool i found a way around this 
one problem.

Thank you

---

