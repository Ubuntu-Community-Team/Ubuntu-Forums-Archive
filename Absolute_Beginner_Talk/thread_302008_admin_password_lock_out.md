---
title: "admin password lock out"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by xhozican on 2006-11-18
Dumela
As a green user some where some how while trying to change my username and login password I am now locked out of all my admin accounts, I cannot locate users and groups interface,in system pulldown,and when I run the command ,the password required to access users and groups is eveidently not the ONE. how do I reset passwords or profiles and start afresh,this problem is preventing acces to updates.-Xhozican't...oooooooooand that command window.....hmmmm
please keep this simple for me.

---

### Post by BaffledMollusc on 2006-11-18
> **xhozican said:**
> Dumela
As a green user some where some how while trying to change my username and login password I am now locked out of all my admin accounts, I cannot locate users and groups interface,in system pulldown,and when I run the command ,the password required to access users and groups is eveidently not the ONE. how do I reset passwords or profiles and start afresh,this problem is preventing acces to updates.-Xhozican't...oooooooooand that command window.....hmmmm
please keep this simple for me.
Okay, I'm not sure I can help you, but I'll try. First off, your description of your problem is a bit confusing.

When you set up Ubuntu, you are asked to create a user and assign a password. This first user has special privileges, kind of like an administrator. More accurately, they have the right to use "sudo" which means that whenever they try to do something that might screw up their system they're asked for a password. This is just a way of making you think twice about what you're going to do. Enter your password and you are allowed to do whatever you want.

Now, when you create additional users on the system, they don't have sudo privileges. That is, if you're logged in as one of these other users, and try to do something "administrator-like", you won't be able to, because that user doesn't have special privileges.

Now, is your problem that when you're logged in with the user account you created during the Ubuntu install (i.e. the sudo account; the kind-of-like-administrator account), and you try to do something that requires special privileges and are asked for the password, the password doesn't work?

If that's the case, are you using the password for that first user? Have you ever changed that user's password? Are you doing all this correctly, but you're saying you've forgotten that first user's password?

---

### Post by aysiu on 2006-11-18
This link may help you recover admin privileges:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

