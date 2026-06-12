---
title: "Need help with user groups and sudo"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by stephster on 2006-08-08
Hello,

I have just installed Linux-Ubuntu for the first time and have been enjoying it through the KDE environment.  However, I've gotten myself in a bit of a jam.  Here's my problem.

I have it set up with only one user (me).  I could invoke superuser-type commands with sudo.  But this morning, I decided to play with the 'usermod' command and now I regret having done so.

I modified the list of groups for my user:

'usermod -G some_group my_username'

I now assume I should've included all the groups to which my user account previously had access to.

The result is that all the superuser level applications won't run anymore (sudo and apps requiring su password).  I've tried adding mu user account to the sudo group as well, but my situation hasn't improved.

I'm tempted to scrap the entire partition and start over, but this would deny me the opportunity to learn from others.

Can anyone help?

---

### Post by Indras on 2006-08-08
If you mess up your permissions for your main user account, you can boot into single user mode (select the second option at the grub menu) and change them back.  Make sure you are a member of your own group, with the same name as your user, and the admin group.  My user is also a member of scanner (GID 110) and lpadmin (GID 106), but I'm not sure if they are necessary... these are just the default settings.

---

### Post by stephster on 2006-08-08
Thanks for the help, very appreciated.

I've also noticed a group 'sudo'.  Should my main user be part of that group as well or does admin do the trick for su-level command access?

Thanks again.

---

### Post by aysiu on 2006-08-08
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) will help you.

---

