---
title: "Security and Ubuntu: Newbie"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-09
From what I understand Ubuntu is pretty secure but I would like to understand the
permission structure.

It is to my understanding Root has full control just as the Admin account in Windows.
I have heard that in Ubuntu the 1st user created is an Admin not Root.
so when you do something that needs privileges it's asks you for a password.
Now the second user created is strictly a User with no privileges except for
Their home folder.  So anything created after the 1st account is a User

Is this true?
Ubuntu is different from other Linux's I have tried.
It was to my understanding that you had Root and Users.

---

### Post by MenZa on 2007-08-09
The first user has the same priveleges as root, but the difference from other distros, is that Ubuntu doesn't have a user account called root by default. This can, however, be created. Any user can be given 'admin' or 'root' priveleges by being added to the group 'admin'.

---

### Post by Orbital75 on 2007-08-09
I'm new to linux so please forgive my ignorance.

So...... Should I create another account to run under or is Ubuntu safe
right out of the box.... I never liked running as Admin in Windows so
I run myself as a limited User.... I would find running as Root would be
as dangerous.

---

### Post by MenZa on 2007-08-09
No, that's the beauty of it; as long as you keep a secure password and don't use sudo unless you truly have to, running the default setup is safe enough.

---

### Post by AlexenderReez on 2007-08-09
but if you still scare about security ....give a look at [firestarter]("http://www.fs-security.com/") ...it is available in repo:)

---

### Post by MenZa on 2007-08-09
> **AlexenderReez said:**
> but if you still horiblellly scare about security ....give a look at [firestarter]("http://www.fs-security.com/") ...it is available in repo:)

That's a completely different type of security, though; that's a frontend to iptables' firewall.

---

### Post by AlexenderReez on 2007-08-09
> **MenZa said:**
> That's a completely different type of security, though; that's a frontend to iptables' firewall.

well...the most dangerous security situation can come from networking administration ....that why i said just give a look:)

---

### Post by Orbital75 on 2007-08-09
Yep..... I did install FireStarter when I was looking for a nice easy to use Graphic Firewall.
I've messed around with IP Tables on my SmoothWall and sometimes it can get a little frustrating.
I like have a personel firewall for some reason it just make me feel a little safer from
internal threats.

I found this article on Ubuntu Accounts..... Could you tell me if it's pretty accurate.
thanks

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by aysiu on 2007-08-09
> **Orbital75 said:**
> 
It is to my understanding Root has full control just as the Admin account in Windows.
I have heard that in Ubuntu the 1st user created is an Admin not Root.
so when you do something that needs privileges it's asks you for a password.
Now the second user created is strictly a User with no privileges except for
Their home folder.  So anything created after the 1st account is a User Mostly correct.

> **MenZa said:**
> The first user has the same priveleges as root, but the difference from other distros, is that Ubuntu doesn't have a user account called root by default. This can, however, be created. Any user can be given 'admin' or 'root' priveleges by being added to the group 'admin'. Incorrect.

The first account is not root. The admin accounts are not root. No user is root except root. The admin accounts can temporarily assume root privileges for particular tasks with the use of *sudo* (for terminal commands) or *gksudo* (for graphical applications) and password authentication. Root can make root-privileges changes for any task and with no additional password authentication.

New users may or may not be admins or regular users, depending on how they're added. Any admin user can add a new user as another admin or as a regular user.

---

### Post by xpod on 2007-08-09
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Have a read of that to get a better understanding of Ubuntu & security.........in fact it`s a good read regardless of os:)

---

### Post by MenZa on 2007-08-09
> **aysiu said:**
> The first account is not root. The admin accounts are not root. No user is root except root. The admin accounts can temporarily assume root privileges for particular tasks with the use of *sudo* (for terminal commands) or *gksudo* (for graphical applications) and password authentication. Root can make root-privileges changes for any task and with no additional password authentication.

This is correct. I was merely attempting to put it out in layman's terms, because with that account you can, as you state yourself, temporarily assume the privileges the root user would have.

---

### Post by Orbital75 on 2007-08-09
Thanks guys..... I have a much better understanding of it now.

Root is Root  ( Full access )
You have to log in as Root to be Root
Either by Command line or ( If enabled by GUI )

The 1st User ( default ) is a User but is added to the Admin Group
This gives the User Temporary limited Root Rights if the Users Password is entered
as it pops up on certain situations that require more privilege. 

Now you can become Full Root temporary for 15 minutes by entering in
sudo or ( F2 ) gksudo.  This will limit you just to the one window open or
command prompt open. Any other window open does not have that
privilege. 

Now the 1st User ( after a password is entered ) can add a 2nd user to the Admin
group that will then give him the same rights/powers as the 1st user.

I'm a newbie with Linux so please correct me if I'm wrong this is all a learning experience.

---

### Post by aysiu on 2007-08-09
You're right on.

---

### Post by tjsullivan1 on 2007-08-09
The problem I have with sudo is that *if* one were to be hacked, the admin user password would allow the hacker to assume root control, assign root a password, and then disable sudo in visudo. To me, it just seems to be easier to disable sudoing in visudo and enable root. I also prefer to ban any outside connection from logging in as root (you must first log in as a user).  Besides su -c "COMMAND" seems to be just as easy to type as sudo COMMMAND, except you have to know the root password (not just the admin) to actually do anything signigicant.

---

