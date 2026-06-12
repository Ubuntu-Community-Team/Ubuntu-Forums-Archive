---
title: "incorrect login - but it's correct (I swear)!"
date: 2006-06-29
forum: Apple PPC Users
---

### Post by coverup on 2006-06-29
Hello all,

I have never seen anything like this... I just installed Dapper on 4 identical machines (new world PowerMac G3 towers) and 3 of them went smoothly, but here's the problem with one of them, which is very strange..

When I set up the login and password, I did them as usual.  I tried to login with the correct username and password, and it gave the error "Incorrect username or password."  Here's what I have tried so far (in order):

1) Reinstall and be extra careful typing the username and pw... same problem!
2) Reinstall and try again with attention to the keyboard layout... same problem!
3) Boot rescue from the netinstall CD and mount hd, run passwd as root and change password successfully, reboot.... same problem!
4) Try login from tty1 text prompt... same problem

I'm just at my wits' end here trying to figure this out.  Advice would be MUCH appreciated, as I can't wait to have all 4 up and running.  I've googled extensively and no help.  I'm assuming that the problem is with the username...?

Thanks,
coverup

---

### Post by glotz on 2006-06-29
Sounds interesting enough...

So you always used the same combo? Try 3) again this time use simple/simple as login/pw.

I had a similar issue once. Was silly enough to use one special character in my password. It worked in some places but not all...

---

### Post by aysiu on 2006-06-29
Since the machines are identical, rather than reinstalling it on this fourth machine, just copy the partition image from one of the three properly functioning machines.

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

And if it still doesn't work, then you know it has nothing to do with your typing.

---

### Post by coverup on 2006-06-29
Thank you both for your suggestions.  There are no special characters in my password - just letters.  As for the partition image, I'm wondering before I try that if there is a cheap and dirty way to get the admin USERNAME off of the machine - something that would for instance show me all the users in /home/

Another option that I would need some help with is creating a NEW admin account via adduser?  Then I could just login and manage everything with a new name...  I tried the syntax for that as:

adduser $username admin

But it didn't work

I think that given my process it looks like it might be the username in question, though I know exactly what I typed when I set up the system 3 times.

---

### Post by coverup on 2006-06-29
Oh, I thought I should specify that adduser did "work", as in creating a new user, but that user did not have admin priveleges.  If that's the correct syntax, I may have messed up the system by creating another group called "admin" (I was following some other instructions....)

---

### Post by aysiu on 2006-06-29
This may help you with all that admin stuff: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

