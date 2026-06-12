---
title: "Accounts and Menu Structure for Family Computer"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by KeithWatson on 2007-02-03
This should be very straight forward, but I can't seem to find an answer for it anywhere.  My question is not very well defined because I am not yet comfortable with the way Ubuntu handles user accounts and groups.  

I read the chapter on Managing Users in Beginning Ubuntu Linux from Apress, but I did not walk away feeling like I understood the subject.  I have searched the forums and Google, but the terms accounts and groups are just used too my searches to turn up relevant material.

I just installed Edgy last night and I am trying to get everything set up properly with accounts for my wife and my daughter.  

As I see it we will probably need to have three accounts with the following directories:
/home/me   <editable by me and viewable by wife but not by daughter
/home/wife   <editable by wife and viewable by me but not by daughter
/home/wife/pictures   <editable by wife and by me but not viewable by daughter
/home/daughter   <editable by all three users

I created an account for my wife a few minutes ago, but she defaulted into the group that has my name.  It seems that I should create a group for her, but I don't want to over complicate things.  I have not yet created my daughter's account, but at this point it will just be used for educational games.

If anyone could point me to a good guide for the preferred security setup for a home computer like the one described above I would greatly appreciate it.

---

### Post by shareMenaPeace on 2007-02-04
You uawd System -> Administratin -> user and Groups todo this ?

Didf you set the parth right?

---

### Post by bonzini on 2007-02-04
I just use the user accounts manager to create individual logins with default permissions and groups.

Generally, I find different groups more of a pain in the neck than anything.  But you may want that :-)

You might, for instance, want to be in the same group with your wife but exclude your daughter.  You would do this if, say, you wanted your wife to be able to read all of your files (or maybe read & write them) but didn't want your daughter to have that access.  So you'd create a group called "parents", and you and your wife would be members, but your daughter wouldn't.

It's important to get the UMASK right, that's the default file creation mask.  In the example above, you would want to set it so that your default was to create files that were readable (or readable/writeable) by the group but no access to others.

Generally, I prefer my files to be rw-r--r-- and my directories to be rwxr-xr-x so that's why I don't get much use from groups.

---

### Post by KeithWatson on 2007-02-04
Thank you both for the responses.  I guess I am just over thinking it.

---

