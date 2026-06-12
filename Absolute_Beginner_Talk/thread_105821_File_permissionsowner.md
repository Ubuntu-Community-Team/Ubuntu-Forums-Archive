---
title: "File permissions/owner"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by ggraham68 on 2005-12-19
I know this is stupid...

I just loaded Breezy and I created a "MyDocs" folder on my desktop and used Nautilus to copy some files from a CD to there.  When I got to looking at their ownership it showed that the owner was root and now it won't let me delete them (says I don't have permission).  I wasn't logged in as root when I copied them there - what's up with that?

Also, what about getting my USB harddrive setup (point me somewhere to read)?

---

### Post by earobinson on 2005-12-19
USB harddrive should be plug and play in my expirence.

as for the cd was it burned on linux, Im pretty sure I read something about burning files to a cd and maintaining ownership.

---

### Post by Mustard on 2005-12-19
Try this in terminal, substituting your username in the appropriate places...

```
sudo chown username.username ~/Desktop/MyDocs/*
```

That is basically saying, as a superuser (sudo), change ownership (chown) to username (substituting your username) for all the files in the directory /Desktop/MyDocs/.

The terminal is found in your Applications>>Accessories menu.  The password it asks for, when you do a sudo command, is your user password.

---

### Post by frodon on 2005-12-19
You have to keep in mind that : 
1- NTFS and FAT32 don't support ownership and unix rights. However you're able to set a owner when you use the mount command.
2- To access a partition (FAT32 or NTFS) as a simple user you have to set a good umask when you use the mount command.
3- If you have a ext3 or reseirfs partition all you have to do is to set the good rights, owners (and groups). In this case the command given by Mustard is really usefull.

---

### Post by kont.raen on 2005-12-19
[QUOTE=Mustard]Try this in terminal, substituting your username in the appropriate places...

```
sudo chown username.username ~/Desktop/MyDocs/*
```
...
[/QUOTE]

Hmmm - I think there is a typo in your command, for I only know the ":" to be the correct separator between user and group. Therefore the command should imho look like this :

```
sudo chown username:username ~/Desktop/MyDocs/*
```

---

### Post by Mustard on 2005-12-19
kont.raen, both are correct.

As usual there is more than one way to skin a cat, in linux. :D

See below from man chown.

[quote=from the chown manual]If only a user name (or numeric user ID) is given, that user is made the owner of each given  file,  and the files&#8217; group is not changed.  If the user name is followed by a colon **or dot** and a group name (or numeric group ID), with no  spaces between them, the group ownership of the files is changed as well.[/quote]

I didn't know you could use the colon, myself.  I hadn't read the manual.  I've just seen it done before using the dot. ;)

---

### Post by bszmyd on 2005-12-19
Colon is the only way to go ;)

---

### Post by ggraham68 on 2005-12-19
[QUOTE=earobinson]USB harddrive should be plug and play in my expirence.

as for the cd was it burned on linux, Im pretty sure I read something about burning files to a cd and maintaining ownership.[/QUOTE]
Ok, sorry for not being more specific...

This was a CD I created from an XP box - I just wanted to copy my docs over!

---

### Post by bb002 on 2005-12-19
**Mustard**'s command will still work. His command is affecting the files in ~/Desktop/MyDocs. it doesn't matter where they came from.

Also I'd like to update **Mustard**'s command to```
sudo chown  -R username.username ~/Desktop/MyDocs/*
```
The "-R" options causes chown to also scan through subfolders of ~/Desktop/MyDocs/.

---

### Post by ggraham68 on 2005-12-19
[QUOTE=bb002]**Mustard**'s command will still work. His command is affecting the files in ~/Desktop/MyDocs. it doesn't matter where they came from.

Also I'd like to update **Mustard**'s command to```
sudo chown  -R username.username ~/Desktop/MyDocs/*
```
The "-R" options causes chown to also scan through subfolders of ~/Desktop/MyDocs/.[/QUOTE]
I did the "sudo chown..." thing and it worked.  But I still get this message when I try to delete files and directories under the MyDocs folder - "/home/ggra...sofInc.pdf" cannot be deleted because you do not have permissions to modify its parent folder.  When I go to the Properties on the MyDocs folder, I've got rwx.

---

### Post by bb002 on 2005-12-19
oops. Forgot that anything that comes off a cd is read-only. run this to fix that:
```
chmod -R u+rw ~/Desktop/MyDocs/*
```
This is similar to the chown command. This command gives you read/write rights to everything in ~/Desktop/MyDocs.
That should take care of your problem.

[edit]
Noticed a mistake in my chmod command. Didn't put a slash between the tilde and Desktop....

---

### Post by ggraham68 on 2005-12-19
[QUOTE=bb002]oops. Forgot that anything that comes off a cd is read-only. run this to fix that:
```
chmod -R u+rw ~Desktop/MyDocs/*
```
This is similar to the chown command. This command gives you read/write rights to everything in ~/Desktop/MyDocs.
That should take care of your problem.[/QUOTE]
Good deal!  That did it.  So I have to do that every time I copy something from a CD to my hard drive (both the chown and the chmod)?

---

### Post by bb002 on 2005-12-19
You have to do the chmod command everytime but you have to do the equivilant in windows, too. As for the chown command, I've copied files off of several cds just now and mine have never been owned by root but all have been read-only.

If your files continue to come off the cd owned by root. You will have to do both commands:
```

sudo chown  -R username.username ~/Desktop/MyDocs/*
chmod -R u+rw ~/Desktop/MyDocs/*

```

---

