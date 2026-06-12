---
title: "[SOLVED] transfer users to other computer?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-02-05
I have a school.  We do not have a strong enough server to run Edubuntu with thin clients.  I am going to install Ubuntu on each computer.  I want each student to have his/her own login for obvious reasons.

Can I set up all the users and passwords on one computer and transfer them to the others?

I read [http://ubuntuforums.org/showthread.php?t=466387](http://ubuntuforums.org/showthread.php?t=466387) and I'm not sure if it's applicable.  If it is I don't get it.

Do I simply copy files?  If so, which ones? What needs to be modified?

Thanks for your help!

---

### Post by bobloblian on 2008-02-07
> **TJCIB said:**
> 
I read [http://ubuntuforums.org/showthread.php?t=466387](http://ubuntuforums.org/showthread.php?t=466387) and I'm not sure if it's applicable.  If it is I don't get it.
!

It is relevant, but I am not sure it is complete for you.  Each user must have a home directory, so if you are going to allow 20 users to use a computer, you are either going to have to allow 20 different home directories, or do some magic to make them share home directories.  This can be done by modifying the /etc/passwd and /etc/groups file.

The last poster at the link you put says that you should not copy the whole files for passwd and shadow from one computer to another, and he is correct, so to answer your question, no, don't just copy the files from one machine to another.  

As suggested by that poster, the passwd and shadow files need to be manipulated to be used as you suggest, and the group file will be easiest done manually.  If one is to manipulate any of these three files, it is best done with a thorough understanding of how they work, and not a set of instructions.  I would recommend starting with the man pages...

---

### Post by TJCIB on 2008-03-22
I was able to read up and figure out a nice way of transferring users, passwords, and groups from one computer to 14 others.

I basically copied the pertinent parts of the above stated files and pasted them at the bottom of its relative file on the new computer.
I then added a home directory for each new user, giving the proper ownership and permissions.

I did all of this via a script that I wrote, so it went fairly quickly as well.

I got one error on login having to do with the theme, but I think it was unrelated since I only got it on one of the 14 computers for one user.

Thanks...problem solved.

---

### Post by TJCIB on 2008-03-26
I found this as a good resource so far.

Using NIS and NFS to share logins as well as home directories

[http://www.debian-administration.org/articles/36](http://www.debian-administration.org/articles/36)

---

