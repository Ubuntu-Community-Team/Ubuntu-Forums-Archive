---
title: "Samba Share V User"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Richard210363 on 2007-08-30
Hi there,
I've just this week started with Linux so please bear with me if I have got concepts wrong.

I've set up Samba on ubuntu using the examples found on the forum.

I can see my Linux machine and the shares from my XP box if I use
security=share
But if I change to 
security=user
then I can only see the Linux machine and no shares.  And I get a permission denied message if I try to browse.

My windows user is called Richard (because I am :-)
but my ubuntu user is richard because it insisted on lower case user names.

Using share is OK but i would prefer user level securit
I have already looked at all the posts I ould find on this issue.

Cheers for any help
Richard

---

### Post by steve.horsley on 2007-08-30
You need to specifically add the users to samba, I think. Try this link:
[http://www.comptechdoc.org/os/linux/manual4/sambausers.html](http://www.comptechdoc.org/os/linux/manual4/sambausers.html)
[http://www.samba.netfirms.com/addusers.htm](http://www.samba.netfirms.com/addusers.htm)

---

