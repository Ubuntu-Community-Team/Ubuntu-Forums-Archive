---
title: "Simple (hopefully) smb.conf question."
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by nomad1970 on 2007-11-20
Hi, 

New to the forums, new to linux.

I've setup a file server using ubuntu server 7.10.  It's a basic setup, 15 users or so, all have access to one shared directory, and to their individual home folders. Some of the users only have access to a private directory.  Rather then use groups (which I probably should use, but havn't quite figured the permissions aspect), I'm using the admin users = and write list = commands.   This seemed a simpler way to do it since I don't have 100's of users.  

My question is, when I add users I just leave a space between, so I have like:

------------------------------------

[everyone]
path= /DATA
browseable = yes
public = yes
write list = test1 test2 test3 bill
admin users = test1 test2 test3 bill

[private$]
path = /private
browesable = no
public = no
writelist = bill, cathy
admin users = bill, cathy

------------------------------------------

The problem is, if I exceed the character width of the screen, the users on the next line below do not have proper access.  user15 16 and 17 for example, below.

---------------------------------------

write list = test1 test2 test3 bill test5 test6 test7 test8 user9 user10 user11 user12 user13 user14
user15 user16 user17

admin users =test1 test2 test3 bill test5 test6 test7 test8 user9 user10 user11 user12 user13 user14
user15 user16 user17

----------------------------------------
Can i just add another write list and admin users?  or is there another way to format them using commas or : etc between the users?

This may be a silly way to achieve what I'm trying to do, but it seems to work ok, and I can understand it which is the important part.  I'm sure there is a better way, and I'd be interested to hear about that as well.

Thanks,

Emeric

---

### Post by dstew on 2007-11-20
Just end the line with a "\" and it will continue to read the next line:```
admin users =test1 test2 test3 bill test5 test6 test7 test8 \
user9 user10 user11 user12 user13 user14 user15 user16 user17
```
See the smb.conf man page, either with your terminal or [here]("http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").

---

### Post by master_kernel on 2007-11-20
> **nomad1970 said:**
> Hi, 

New to the forums, new to linux.

I've setup a file server using ubuntu server 7.10.  It's a basic setup, 15 users or so, all have access to one shared directory, and to their individual home folders. Some of the users only have access to a private directory.  Rather then use groups (which I probably should use, but havn't quite figured the permissions aspect), I'm using the admin users = and write list = commands.   This seemed a simpler way to do it since I don't have 100's of users.  

My question is, when I add users I just leave a space between, so I have like:

------------------------------------

[everyone]
path= /DATA
browseable = yes
public = yes
write list = test1 test2 test3 bill
admin users = test1 test2 test3 bill

[private$]
path = /private
browesable = no
public = no
writelist = bill, cathy
admin users = bill, cathy

------------------------------------------

The problem is, if I exceed the character width of the screen, the users on the next line below do not have proper access.  user15 16 and 17 for example, below.

---------------------------------------

write list = test1 test2 test3 bill test5 test6 test7 test8 user9 user10 user11 user12 user13 user14
user15 user16 user17

admin users =test1 test2 test3 bill test5 test6 test7 test8 user9 user10 user11 user12 user13 user14
user15 user16 user17

----------------------------------------
Can i just add another write list and admin users?  or is there another way to format them using commas or : etc between the users?

This may be a silly way to achieve what I'm trying to do, but it seems to work ok, and I can understand it which is the important part.  I'm sure there is a better way, and I'd be interested to hear about that as well.

Thanks,

Emeric
Those users actually do have admin access. If your resolution is wider, then you will see that it is on one line.

---

### Post by nomad1970 on 2007-11-20
Thanks for the fast replies.

dstew:  I'll give that a try, thank you.

master_kernel:  Yes with the window maxed out it would of worked, what I tried was just hitting return and putting more users on the next line.  My main concern was what to do if I needed to add more users in the future.  Thanks for your reply.

---

