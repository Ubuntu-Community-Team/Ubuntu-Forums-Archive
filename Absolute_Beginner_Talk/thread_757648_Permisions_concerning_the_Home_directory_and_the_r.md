---
title: "Permisions concerning the Home directory and the rest of the filesystem"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by hovzio on 2008-04-17
Hi, I am new to linux and I've been learning about the linux hierarchy and and permissions. I understand how to change the octal permissions for u,g,o and suid, sgid, sticky and so forth.My questions concern  this o (other, "world") that I've been reading about. First of all I dont use SSH or remote desktop or anything of the sort and am not interested in allowing the world to access any of my files.

When I create files most of the times user permissions are set to 664. This allows owner and group the read and write but what I don't understand is that world has permissions to read. Why is this? Please keep in mind that I'm new to linux. (In case my questions seem garbled or irrelevant.) Does this mean that Im allowing the world to view this new file? If not, what does it mean?

Is it a good idea to deny the world all access (chmod -r 660 ~/) to my home directory and its contents? If so are there any other directories I should apply this to? I could imagine that there are directories throughout the filesystem you  would definitely not want to apply these permissions to. I'm asking this question from a security standpoint.  So, if this does apply why does Ubuntu automatically give these permissions to files?

Like I said I'm new to Ubuntu, I hope i have properly expressed myself but I guess what what the main question would be; what am I really allowing to happen when read permissions are in place for world, what is taking place?

---

### Post by Trail on 2008-04-17
I think what you are expressing as "world" is commonly referred to as "others". In that sense, 664 is rw for owner, rw for group, and r for others, which includes all users not belonging to your group.

Suppose I have a PC shared between several people, some of them administrators, some of them plain users. I am an admin named "trail" and belong to the "admin" group. I create a file named "message_of_the_day.txt" (which belongs to trail:admin) and set permissions to 664. This means I can read and write, the fellow admins can also read and write, but regular users can only read it.

If that makes sense, imagine a regular desktop PC running Ubuntu, and a family consisting of a brother and a sister each make an account for logging in. They don't bother forming a group because they don't know about it. The default 664 permissions guarantee that the sister can view her brother's files, but not mess with them. Which should cover a lot of cases. If the brother sets his home directory to 660, his sister cannot view anything inside there. Well, if the brother has something to hide it might make sense :)

The "world" word should not confuse you in relation to SSH; when someone tries to log in remotely to your PC, he still has to log in as a valid user, just as if he had logged in physically.

Personnally, I don't believe giving read-only access to your files is a bad thing, unless it is specifically private data. Some of such files are automatically unaccessible for others, but if you create directories where you store for example personal documents, you have to specify this manually.

---

