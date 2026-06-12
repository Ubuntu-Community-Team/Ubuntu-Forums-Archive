---
title: "group permissions to access same path"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-04-20
I have a few users in one group and I want all users of that group to only have /access/to/this/path

Ideally once they login via ssh, they will not see their home dir but instead this predefined path and anything below it.  

Is there a way I can configure the group this way?

---

### Post by rmemm on 2007-04-20
Interesting.  I'm not certain it's a group configuration exactly -- though groups are a tool to help define permissions.  It's more of a user and system configuration.  You can set the home directory of any user to whatever and this can be any directory.  By the same token you can set the shell that each user runs however you want -- or set up the init script process to take them anywhere.

As far as access -- access depends more on the protections you apply to every other file, directory, or file system object in the system.  And also users must pretty much have x access to any command you want them to be able to use and rx access to any script.  Groups help this process of defining permissioins -- but as far as I know Linux permissions are only additive -- meaning you can't use groups to restrict access only add access permissions.

The exceptions to this are "captive" accounts which allow you to create special shells that can only run certain commands.  Other exception is using a chroot jail.  It might be possible (I've never tried this) to create a chroot jail directory tree and then run the users shell using the chroot command to put them into that jail.  I've never tried this -- but one would think it's possible.  

I'm not sure this is what you wanted?

Rob

---

### Post by chymo on 2007-04-20
This will work.  I'm most concerned with the directory the group users see once they log in.  

Is there a command that can configure this path easily for the group that I've created?

---

### Post by rmemm on 2007-04-20
Do you mean ownership and permissioins for the whole tree?

Typically the chown, chgrp, and chmod commands.  Use the "man" command followed by the command your interested it to get information about it.  To change group ownership:

chgrp -R MYGROUP /access/to/this/path

Be careful with the -R option -- it will change ownership of all files and directories below that path and the path it self.  You can do bad things with it -- like changing group ownership of EVERYTHING if your not careful.  Also if you want to change file user ownership or both user and group ownership you can use the "chown" command somewhat similarly.

You'll also need to decide what access permissions this group is to have to each file system object and use the chmod command to set this like you like.  

Note sure -- is this what your asking -- how to change group ownership of a whole tree?

Setting group ownership like this -- allows you to control permissions that members of the group will have on this tree -- be it does not restrict any permissions they might have elsewhere in the file system (such as if they own their home directory, or there are world readable, or writable, or executable files elsewhere in the file system).

Rob

---

