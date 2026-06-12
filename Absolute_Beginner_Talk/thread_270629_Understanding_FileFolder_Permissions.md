---
title: "Understanding File/Folder Permissions"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by walesmd on 2006-10-03
This question is in relation to a LAMP stack installation, so I will be using it as an example.

I am having a hard time wrapping my head around Linux file permissions, seeing as I am new to this and straight out of Windows. From what I can tell there is simply: owner, group, and others.

So, let's say I have /var/www with owner/group of root. I have a user mike with group mike.

What I would like to do is give mike (either the group or just the user) +rwx permissions to /var/www while keeping the owner/group as root.

Is this possible?

Can someone help explain linux permissions to me a little bit? I could probably best wrap my head around them if someone could relate them to Windows Permissions. I'm not wanting Linux to act like Windows, I'm loving Ubunut and very open-minded about changing how I do things - just trying to understand right now.

---

### Post by jaboua on 2006-10-03
Permissions are often written on the form 777
The first digit represents permissions for owner
The second digit represents permissions for group
The third digit represents permissions for everyone else

The 7 is composed by three other digits:
1 - Executable
2 - Writable
4 - Readable
These digits are added together to create a permission - for example readable and writable, but not executable is 2+4 = 6

In other words, the permissions 750 will give:
- the owner 1+2+4 = read, write, execute
- the group 1+4 = read, execute
- everyone else 0 = nothing

I hope that cleared up how the standard unix permission system works. In answer to your question: no. However there are some other systems available too, known as "ACL"s (Access Control Lists) - I don't know too much of them, but I belive what you described is how ACLs works. However if you want to stick to the standard permission model, I would have either made that folder belong to the group mike or created a special group that the folder should belong to, and put mike in that group.

---

### Post by walesmd on 2006-10-03
Can a user only belong to more than one group?

As it is now I simply gave the /var/www 777 permissions, recursively, and it's working.

I don't know, maybe I should just leave it working - noone else is really going to mess with it. I'm just trying to play and make things "to perfect" I guess.

Thanks for the quick rundown though - it answered my questions.

---

### Post by jaboua on 2006-10-03
A user can belong to as many groups as you want - your user probably belongs to lots of groups allready. If you look at the file /etc/group, you can find out what groups exist at the moment and what users are members of them. There should be a graphical tool allready installed for managing users and groups.

---

### Post by mn_kthompson on 2006-10-03
Is there a way that different groups can have permissions to a folder.  What if I had a folder full of documents and I wanted one group, editors, to have read/write permission but I wanted another group, viewers, to only have read permission.  Everyone else would have no permission.  Can that be done?

---

### Post by walesmd on 2006-10-03
Yeah - that's pretty much what I was looking for and it seems as if it can't be done.

In your particular example (which I'm sure was just theoretical): you could make a group, editors, give them read/write, then give 'others' only read permissions. Of course, this would not keep people outside of your theoretical 'viewers' group from reading as well.

---

### Post by jaboua on 2006-10-03
> **mn_kthompson said:**
> Is there a way that different groups can have permissions to a folder.  What if I had a folder full of documents and I wanted one group, editors, to have read/write permission but I wanted another group, viewers, to only have read permission.  Everyone else would have no permission.  Can that be done?I don't have any experience with ACL, but as far as I know, that's what ACLs do - With ACL you can specify different permissions for a list of groups or a list users instead of only one user and one group. 
[http://en.wikipedia.org/wiki/Access_control_list](http://en.wikipedia.org/wiki/Access_control_list)

---

