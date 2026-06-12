---
title: "folder permissions"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by serosis on 2006-12-06
How would I go about changing permissions of an entire folder and its contents?

I've been working with sourcecode between my winxp and ubuntu and I found out that ubuntu hates to give me or the root permission to edit anything that I copy over from my NTFS drives, nor does it let me compile.

---

### Post by agustin.g on 2006-12-06
```
sudo chown (your username) (folder or file)
```
for all the content of one folder i'm not too sure though.

---

### Post by serosis on 2006-12-06
well i'm talking EVERYTHING thats inside the destination folder, the folder itself, files inside the folder, and subfolders.

if this command can do that then i'm ok

---

### Post by mitch.c on 2006-12-06
> **agustin.g said:**
> ```
sudo chown (your username) (folder or file)
```
for all the content of one folder i'm not too sure though.
Ummm... actually, I think he wants to change permissions. That would be (change 755 as appropriate):
```
$ chmod -R 755 /path/to/folder
```
The -R option is required to propegate down through the files and other folders contained therein.

chown changes ownership. You would also need the -R option for the same reason.

---

### Post by GuitarFingers on 2006-12-06
> **serosis said:**
> How would I go about changing permissions of an entire folder and its contents?

I've been working with sourcecode between my winxp and ubuntu and I found out that ubuntu hates to give me or the root permission to edit anything that I copy over from my NTFS drives, nor does it let me compile.

To change the permissions of all the files in a particular folder:

sudo chmod -R username.username /path/to/folder

-R = Recursive, to all files and folders below the selected one
username.username = changes the owner and the group (ie owner.group)

You can't modify the files because they're not yours to modify OR they are set to read only. To change the permissions you do this:

sudo chmod -R u+rw /path/to/folder

-R = Recursive
u+rw = User add Read Write

The options here are u = user g=group and o=other. r = Read w=Write and x=Execute + = add permission - = take it away

So if you wanted to give read write and exectute permissions to the user and the group for a particular file this command will do it:

sudo chmod ug+rwx /path/to/file

Equally to stop any else from seeing the file or having anything to do with it:
sudo chmod o-rwx /path/to/file

Note that sudo is only required if you don't already own the file. 

Hope that helps

---

### Post by agustin.g on 2006-12-06
(question answered, this post can be deleted, i just haven't figured out how to...)

---

### Post by serosis on 2006-12-06
cool, Thanks guys

---

