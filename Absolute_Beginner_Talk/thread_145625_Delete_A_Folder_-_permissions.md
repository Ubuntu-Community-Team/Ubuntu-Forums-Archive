---
title: "Delete A Folder - permissions"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-16
I have a folder in my wastebasket.

The permissions of each file are set to 555 (-r-xr-xr-x)

It won't let me delete the folder as I don't have permission.

I assume all the files need to be 777?

How do I use chmod on an entire folder? I found reference to og=rw but that hasn't done it.

---

### Post by 5-HT on 2006-03-16
You were close.
'og=rw' sets read/write permissions for users in your group and users not in your group.
Problem is that you no longer have such permissions...

Easiest thing to do would be to just use 'sudo' to remove the directory.

```
 sudo rm -r <path_to_directory> 
``` 

If you wanted to change permissions though, you could always try this*:

*I don't know if you are the owner of the directory. 
If you are, you don't need to use 'sudo' in the next command.
I put it in there as it will cover all cases.

```
sudo chmod -R u+rw <path_to_directory> 
``` 
The 'R' is for recursive, and the 'u+rw' will give your user read/write
 permissions.

After the permissions are set you can then delete the directory.

As an aside, 555 permissions should be enough to let you delete the files. 
I'm guessing you tried that chmod, and as a result removed permissions for your user.

HTH

---

### Post by _simon_ on 2006-03-16
thank you :)

---

