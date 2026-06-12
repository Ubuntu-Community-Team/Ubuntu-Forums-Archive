---
title: "[SOLVED] new to ssh need some help"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by pfwd.tech on 2007-10-26
I cant seem to log into my system remotely.  when I try It asks for a password but I haven't created a new user account with username and password (not sure how).
Is there any place where I can add a user/password to user accounts.
I take it that when the host machine is on, its logged in as root.  So  i would need to define a new user somewhere that I can use to log in remotely?  I am using windows/putty to log into my ubunu server.

---

### Post by atomkarinca on 2007-10-26
to create a root password you should

> sudo passwd root

and to create another user account you can go system > administration > users and groups

---

### Post by thelocust on 2007-10-26
use your login name and password of the computer your connecting to.

---

### Post by hyper_ch on 2007-10-26
> **atomkarinca said:**
> to create a root password you should
and to create another user account you can go system > administration > users and groups

Don't create a root password. It is not needed.

---

### Post by pfwd.tech on 2007-10-26
ok so the root username and password will be useracount that the host will have (the linux server) and the new username/password that i create using the system/admin/useracounts etc.. will be the account i use to login remotely .. correct?

---

### Post by thelocust on 2007-10-26
What ever you use to login to that computer normaly your doing the same just from a remote computer.

---

### Post by dwhitney67 on 2007-10-26
When you set up your Ubuntu system, you were prompted to create an account.  Do *not* confuse this account with the "root" account.  The account you created is a user-account, that just so happens to have sudo privileges, thus allowing the owner of the account to perform system administration duties.

Under putty, or whatever other system that has an SSH-client application, if you want to connect your Ubuntu SSH-server, run a command similar to the following where the *userID* is the account you created under Ubuntu, and the *IPaddress* is the IP address assigned to your Ubuntu system.  Here's the command:

[FONT="Courier New"]ssh *userID*@*IPaddress*[/FONT]

Note, if you want to create another account on your Ubuntu system that is fine, but it is not required.

P.S.  When you successfully connect to your Ubuntu system, you will be prompted for a password; use the password associated with the userID.

---

### Post by pfwd.tech on 2007-10-26
but wouldn't that mean that the Linux server is logged in as username1 passoword1 (the first user account that i made when installing Linux).
And
I am logged into the the linux server remotely using the same username and password as what is logged in to the server (username1, password1?

---

### Post by thelocust on 2007-10-26
correct and if you need to do any admin just sudo it just like your sitting at the server.

---

### Post by pfwd.tech on 2007-10-26
Cheers [thelocust]("http://ubuntuforums.org/member.php?u=156723") I will try that.
thanks for your help.  Hope this helps others too

---

### Post by n3tfury on 2007-10-26
> **hyper_ch said:**
> Don't create a root password. It is not needed.

agreed. bad idea.

---

### Post by pfwd.tech on 2007-11-03
Unfortunately i still can't do it.
I can connect to the sever fine but it keeps saying access denied when I enter in my password.

The user name and password i'm using in putty is the same as the one i created when I first installed Ubuntu (When it asked for a username and password).
Any ideas on how i can find out what is going on?

I have also just added a new user to the system and tried to access the server via that but it still says access denied once i put in their password.

---

### Post by n3tfury on 2007-11-03
did you mess with the ssh config at all?

---

### Post by schorsch on 2007-11-03
Did you configure putty to use SSH protocol version 2 as version 1 is not supported by the default ssh installation of gutsy?

---

### Post by pfwd.tech on 2007-11-03
Hi 
Its all sorted now.  
I googled deeper and found that if you set the protocol to '2 only' in putty
And change 'PasswordAuthentication' variable from 'no' to 'yes'. in the config file
Then restart ssh it all worked fine.
Thanks for your speedy replies and all your help.
I hope this thread helps some one else out to.

---

### Post by schorsch on 2007-11-03
Alright, could you please mark this thread as solved?

---

