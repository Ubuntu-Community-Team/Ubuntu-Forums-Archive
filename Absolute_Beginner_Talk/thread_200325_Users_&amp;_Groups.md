---
title: "Users &amp; Groups"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by pear on 2006-06-20
Hi, I've been using Ubuntu on my laptop for a very long time now and even installed Kubuntu at home when Dapper was released. So now I would like to try and operate it in my work environment which is a school.

Currenty I am having problems with user accounts, I am very familar with windows, documents and settings folders and group policies so coming over to the linux side of things I really need to understand groups better.

The questions I would like answers to:
Can groups be added to groups ?
Is there a way to script user and group management via php webpages ?
If a user is in two groups, one with read allow, one with read deny, will they have read access ?
can groups be disabled for a period of time ? (between 10 and 11am for example)

An example of the questions above is a scenario where there is a group for a class of 20 students - This class is not allowed to access Firefox.
But some of the students from the class are also in another group for a different class - This class is allowed to access Firefox.

---

### Post by %hMa@?b&lt;C on 2006-06-20
im not that great at networking, only know enough to set it up myself.
but i know that you can use SQUID to allow and deny users access to the internet.
I have a Linux Format Magizine with an article on how to do just that. I will take a picture of the article for you.

---

### Post by ifokkema on 2006-06-21
[QUOTE=pear]Currenty I am having problems with user accounts, I am very familar with windows, documents and settings folders and group policies so coming over to the linux side of things I really need to understand groups better.

The questions I would like answers to:
Can groups be added to groups?[/QUOTE]
Nope. Just users. Users and groups may have the same name, though. As a user, you are always a member of the group with the same name as your username.

[QUOTE=pear]Is there a way to script user and group management via php webpages ?[/QUOTE]
You can do that, but it's quite insecure. Apache runs as the user www-data. The commands to use when changing group members, need to be run as root. You can get around this, but again, it may allow other users to mess with your group settings.

[QUOTE=pear]If a user is in two groups, one with read allow, one with read deny, will they have read access ?[/QUOTE]
Hm.... this will never happen, I think. A file can be owned by just one user, and just one group. Access per file/directory are set in three: user owner, group owner, all others. So you can allow access to a file/directory to the file's user owner, the files group owner, or just everyone. Denying a user and allowing the rest is, as far as I know, not possible using the filesystem permissions.

[QUOTE=pear]can groups be disabled for a period of time ? (between 10 and 11am for example)[/QUOTE]
This is not available in Linux by default. Possibly there are programs to do this, and possibly you can script this yourself. But do you really want to mess with this? I don't know what will happen if you just disable and enable groups left and right.

[QUOTE=pear]An example of the questions above is a scenario where there is a group for a class of 20 students - This class is not allowed to access Firefox.
But some of the students from the class are also in another group for a different class - This class is allowed to access Firefox.[/QUOTE]
I think the only way to do this, is create a group that is allowed to run Firefox. Add the users that are allowed to run it to this certain group (such as 'firefox_allow' or whatever) and then disable everybody to run firefox, exept the user owner and group owner. Then you have to change the group owner of the firefox executable. But maybe the article jeffc313 mentioned can help you out with this certain issue.

---

### Post by Arndt on 2006-06-21
[QUOTE=ifokkema]
> 

Originally Posted by pear
If a user is in two groups, one with read allow, one with read deny, will they have read access ?

Hm.... this will never happen, I think. A file can be owned by just one user, and just one group. Access per file/directory are set in three: user owner, group owner, all others. So you can allow access to a file/directory to the file's user owner, the files group owner, or just everyone. Denying a user and allowing the rest is, as far as I know, not possible using the filesystem permissions.

[/QUOTE]

Using groups to let all users in one group except those who are also in another group have access is not possible, as you say, but the answer to your last statement is: yes, it's possible to deny access for a user but allow it for anyone else.

This is because access is not the most permissive one allowed given the file permissions - it's the most specific one. User is checked first, then group, then others. To deny read access for user1 but allow it for everyone else, put user1 in a group group1 of his own, set the group of the file to group1, and then set the file's read permission for user and other but not for group.

Technically, it works for user versus group too, but in that case the user owns the file and can raise his own permissions to subvert the intentions of the adminstrator.

---

### Post by ifokkema on 2006-06-21
[QUOTE=Arndt]This is because access is not the most permissive one allowed given the file permissions - it's the most specific one.[/QUOTE]
Ah, thanks! Good to get educated myself, too :)

---

