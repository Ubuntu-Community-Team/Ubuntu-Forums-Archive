---
title: "User/Group Privilages"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by ClayPTino on 2007-02-20
I am hosting an ftp server using proftpd for use as a file server for a school design team.

I need to give users access to the ftp server, but nothing else.

I know I can make them part of a group, and restrict privileges to that entire group, I just don't know the syntax.

Thanks

---

### Post by tocleora on 2007-02-20
If I remember correctly, you would do something like (in terminal):

chown user:group foldername

user can be you or the admin.
group would be the group you will put everyone in.

then you would set settings something like:

chmod 660 foldername

first number is owner, gives him read/write with 6.
second number is group, gives them read/write with 6.
third number is everyone else, gives them no access with 0.

---

### Post by dwblas on 2007-02-20
Groups are in /etc/group.  Try "man group" also.  There are GUI interfaces as well depending on which flavor of Ubuntu you are using.  For Gnome Ubuntu see
[http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_system_groups](http://ubuntuguide.org/wiki/Dapper#How_to_add.2Fedit.2Fdelete_system_groups)
[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)

---

