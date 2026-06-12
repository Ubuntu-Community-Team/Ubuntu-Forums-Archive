---
title: "Quick question"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Hurricane on 2006-12-06
Hi all
Just a quick question.

Should System>Administration>Users & Groups prompt for a password?  The help file seems to suggest it should, however it doesn't on my system, allows me to change any passwords without being prompted (including root).

Synaptic package manager prompts for password, as does doing any sudo commands.

Thanks
Matt

---

### Post by bodhi.zazen on 2006-12-06
did you recently enter your password ?

If so, there may be a grace period...

---

### Post by Hurricane on 2006-12-06
No unfortunately, happens all the time, every time.

---

### Post by peterj on 2006-12-06
Once you key in the admin password it won't ask for it again for 15 minutes. maybe you keyed it in for synaptics within 15 minutes before admin-groups?

---

### Post by Hurricane on 2006-12-06
I've left the computer for a couple of hours (straight from booting up), and then gone straight to users and groups, and it doesn't prompt me ](*,) 

Thanks for the help so far though.

---

### Post by Hurricane on 2006-12-09
Hi all,
Just wondering if anyone has any insight into this?

Much appreciated,
Matt

---

### Post by bodhi.zazen on 2006-12-09
I can not reproduce this behavior on my system.

This is not the behavior on either a fresh install of 6.06 or feisty, both of which I have done in the last few days.

---

### Post by aln on 2006-12-09
Is your user in the "sudo" group? AFAIK members of this group are not prompted for password when issuing a command with sudo or kdesu (I'm on Kubuntu).

---

### Post by Hurricane on 2006-12-09
Hi, thanks for the replies.

The user is just the standard account created at install, and doesn't appear to be in the group "sudo" (or root for that matter).

I'm prompted every time when issuing sudo commands, or opening administrative tasks, **except** when opening the users/groups dialogue or typing users-admin into terminal (this works withOUT sudo on my box, can just type users-admin with no sudo in terminal).

---

### Post by Hurricane on 2006-12-09
Just to add to this, the permissions for users-admin is as follows:
[http://img220.imageshack.us/img220/6775/permissionsse5.jpg](http://img220.imageshack.us/img220/6775/permissionsse5.jpg)

Double clicking this in nautilus just opens it however.

---

### Post by bcom on 2006-12-09
This is just a guess, but:

The account that you created when you installed Ubuntu was automatically given the privilege to administer the system.  Look under User Settings - Properties - User Permissions.

It might be that the "Administer System" privilege includes the ability to add users and groups.

Not sure though, just a guess.

---

### Post by Hurricane on 2006-12-11
Thanks for the reply.  It is this account yes, but I was still under the impression it should require sudo for performing these tasks?

---

### Post by Hurricane on 2006-12-14
Hope you don't mind me giving this topic a bump.

---

### Post by bcom on 2006-12-14
I don't mind at all.

Here is another thought.  

If you go to System-Administration-Users&Groups-User Settings,  select the account in question and go to Properties-User Privileges, you will see that the account has the privilege of "Administer System."  

As stated earlier, maybe in Ubuntu that privilege includes adding users--a task unlike running Synaptic Package Manager which allows you modify essential parts of your system.  In other words, no password required to add a user because adding a user does not modify an essential part of the OS.

It could be, maybe, perhaps, with Ubuntu that "Administer System" is somewhat analogous to a Power User in Windows.  A Windows Power User can perform many administrative tasks, yet can't do everything an Administrator can do.  

Again, I'm new at this so I really don't know.  It would be nice to hear from someone with more experience.

---

### Post by Hurricane on 2006-12-15
Thanks for the reply.  To see if this was the case I created a new account with all the same permissions except administer system.

On this account, I just get a dialog saying I didn't have enough privileges, but no request for a password (the users and groups didn't open of course).

I find it's really strange that it's happening on only Users and Groups, but synaptic, update, sudo, and most other administrative tasks prompt me for the password.

---

