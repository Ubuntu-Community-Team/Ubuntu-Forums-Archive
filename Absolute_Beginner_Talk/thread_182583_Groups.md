---
title: "Groups"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-26
Very newbie question.

Ubuntu has users and groups. 

How do I change the owner of a file?
How do I change the group a file is a member of?

What is the purpose of groups in linux?  Where are they useful?

Do you know of any websites that does a good job of explaining this?

Thanks

---

### Post by tkjacobsen on 2006-05-26
chown user:group filename

The idea with users and groups is that you can set different permissions for user, groups and others
eg:
the user have read/write permission to the file
users in the group have read permission to the file
others can't read or write to the file

for more info see the manual:```
man chown
man chmod
```
chmod is uset to change the permissions

---

### Post by morequarky on 2006-05-26
You give a great example:

the user have read/write permission to the file
users in the group have read permission to the file
others can't read or write to the file

Can you give me an example of when this would actually be used?  I mean, group seems to be a setting for large companies with many users on one large linux server.  The average user or desktop situation, group is completely useless it seems to me, unless there are a few places where linux forces it on you.

I feel like the high school student asking the teacher why we learn this 300 year old math we will probably never use again.  What problem does groups solve?  How can I USE them to my benefit?

Thanks for your answer.  I never knew about chown.

---

### Post by meng on 2006-05-26
I would say your guesses are more or less correct. If your computer was only for your own use, then groups probably aren't going to mean much. If you had two regular users and a guest user account, then you may use groups in a rather limited fashion (e.g. stop guests from seeing personal photos that your two users would be allowed to see).

One of the things about Linux is that with freedom comes more choice. You don't have to exercise or take advantage of all choices if it doesn't suit you.  Unlike some commentators, I don't believe in freedom _from_ choice.

---

### Post by morequarky on 2006-05-26
thanks.

Is it possible to have  group and owner set in such a way that ROOT can't access it?  I hope not.

---

### Post by tkjacobsen on 2006-05-26
the root can allways change the permissions to he/she can access the file..

---

### Post by PriceChild on 2006-05-26
You could also right click the files and choose the permissions tab for a graphical tool to change permissions.

Remember that the following:
> the user have read/write permission to the file
users in the group have read permission to the file
others can't read or write to the file
Isn't always true!

---

### Post by eeclark on 2006-06-05
How would one change the group of .local to root?
Tried using sudo chgrp root .local but it will not let me.
I thought root is a group as well.

---

### Post by eeclark on 2006-06-05
[QUOTE=eeclark]How would one change the group of .local to root?
Tried using sudo chgrp root .local but it will not let me.
I thought root is a group as well.[/QUOTE]

I needed to do the following:

sudo -H -s

and then 

root@smallville:/home/edward# chgrp root .local
root@smallville:/home/edward# chown root .local

---

