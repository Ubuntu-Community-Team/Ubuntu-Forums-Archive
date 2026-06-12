---
title: "How do you define a user Group's permission?"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-14
I can define users' file permissions through chmod 777 (aka all rwx). However, how do we define permissions for 'Groups'? How is 'Groups' normally used in the security aspect? What is 'Groups' 's purpose?

Thanks !

---

### Post by throntax on 2005-11-14
do you mean change the group's permissions? or add users to groups?
you can change a file's group permissions with 
chmod g+wrx filename
i think groups are used in particular for ease of allowing ( or denying ) access to files on large multi user systems, which is what Linux is designed to be able to handle..
hope this has some relevance to your question! :)
also you can subtract permissions! with the minus sign instead of the plus sign! ;)

---

### Post by Akhran on 2005-11-14
Assuming I have a directory with all the files having the permission 754 (rwx-rx-r), will the group of users have rwx permission or rx permission (as owners of the files they have rwx permission but they are in a group which has rx permission)?

Thanks!


[QUOTE=throntax]do you mean change the group's permissions? or add users to groups?
you can change a file's group permissions with 
chmod g+wrx filename
i think groups are used in particular for ease of allowing ( or denying ) access to files on large multi user systems, which is what Linux is designed to be able to handle..
hope this has some relevance to your question! :)
also you can subtract permissions! with the minus sign instead of the plus sign! ;)[/QUOTE]

---

### Post by odin on 2005-11-14
The first 3 bits are for the owner of the file (rwx),the second 3 bits for the users who belong to the group owner of the file(rx) and the 3 bits left are for the rest of the users.So in your case the the group would have read and execute permisions (rx).

As an advice I would use the format of chmod (u,g,o) +/- (pernisions) file to change the permissions.From my point of view is easier to understand.

u means owner of the file,g group owner of the file and o the rest of the users.If you use + you would add permissions and - to remove them.

For example if you have a file which is own by a user with rwx and you wanna remove all permissions but reading the command would be something like this:

chmod u-wx file


hope this helps

---

### Post by Akhran on 2005-11-14
If I have a file (payroll) with the following permissions and ownership:

-rwxrw-r-- 1 John Accts 100 2005-11-05 07:50 payroll

and John belongs to Accts group, would he have rwx or rw permission on the file?

Thanks for your patience :)



[QUOTE=odin]The first 3 bits are for the owner of the file (rwx),the second 3 bits for the users who belong to the group owner of the file(rx) and the 3 bits left are for the rest of the users.So in your case the the group would have read and execute permisions (rx).

As an advice I would use the format of chmod (u,g,o) +/- (pernisions) file to change the permissions.From my point of view is easier to understand.

u means owner of the file,g group owner of the file and o the rest of the users.If you use + you would add permissions and - to remove them.

For example if you have a file which is own by a user with rwx and you wanna remove all permissions but reading the command would be something like this:

chmod u-wx file


hope this helps[/QUOTE]

---

### Post by odin on 2005-11-14
[QUOTE=Akhran]If I have a file (payroll) with the following permissions and ownership:

-rwxrw-r-- 1 John Accts 100 2005-11-05 07:50 payroll

and John belongs to Accts group, would he have rwx or rw permission on the file?

Thanks for your patience :)[/QUOTE]

Ok,as the owner of the file John would have rwx.In this situation it doesnt matter how you set the permissions for the group as Jonh is the owner of the file.The rw would apply to users belonging to Accts gruop.

This could be usefull for example if you want that john has more pernissions in that file than the rest of the members of Accts.

So about your question,John would have rwx.

and dont worry,as the rest of the members of the community I'm glad to help.Today for you,tomorrow for me. :)

---

