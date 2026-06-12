---
title: "A Question of Permissions..."
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Hopkins on 2007-03-01
I have what I think is a rather simple problem, but after a few hours of fiddling and reading about Linux file permissions I have yet to come up with a solution.  The problem:

I'm running an Ubuntu server with vsftpd as an ftp server.  Instead of allowing anonymous logins, I have created a single user whose password I give to any of my friends who may want to access my ftp server.  This user is chrooted to its home directory.  All sub-directories, with the exception of an "incoming" directory, are set to be read only to this user.

I have set up a second user, this time known only to me, who can log into the ftp server and upload content into the home folder of the public user.  My problem is that I cannot work out a way to set up the users/groups/permissions so that content uploaded via the private user is immediatelly accessible (as read only) to the public user.  I always have to chmod the files after uploading.

[I have been trying out the "Set Group ID" [chmod g+s] property on this page]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html"), and I've made sure that there is a group shared by both the private and public users, but to no avail!  Is what I'm trying to do fundimentally wrong in Linux, or have I just not fully understood the way that file permissions work?

Many thanks in advance.

---

### Post by Lanky Juggler on 2007-03-02
Okay, the following is more from what I know and doing some theoretical fooling around in menus than actually going through with it, so give it all a read-through before following the steps.

1. Create a group with only the public user in it.

2. With your private account (or with SU, then chmod the owner to be the private), Create 2 Directories in the public account (maybe put both in a folder like "home/server" or something)
  - For the incoming directory, make it attached to the group you created, and give both the Owner (your private account) and the group (with only the public account) -rw permissions

  - Make the outgoing directory once again attached to the group you created.  Give the Owner (your private account) -rw permissions while only giving the group (the public account) -r permissions.

Unless I'm missing some details, that should work.  Come to think of it, you might be able to avoid making that group with only the public account, and just replacing the group permissions with the "other" designation.

I was particularly lazy (and not as familiar with chmod as perhaps you are) and was able to do all of the above by simply right clicking on the folders and hitting properties.

Good luck!

---

### Post by Amenemhet on 2007-03-03
Hehe, yes lazy! You really should only need to change permissions for others ie: chmod o+rw
This gives others the read and write permissions, and they can play a bit but as you will be the owner still,(and the group owner too, by default) they shouldn't be able to delete things.
Hope that helps :)

---

### Post by Hopkins on 2007-03-08
Thanks for your replies!  Sorry that it took me a while to action them and get back to you.

It seems that I had done what you suggested already.  The problem, it turns out, was an "unmask" setting in vsftpd that denied any uploaded files permissions to anyone other than the user that uploaded the file.  (Specifically, it was doing an unmask=077 by default.)  With that changed, all is well!  Thanks again.

---

