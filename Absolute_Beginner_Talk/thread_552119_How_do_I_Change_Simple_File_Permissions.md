---
title: "How do I Change Simple File Permissions"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by TheDudeAbides on 2007-09-16
Howdy community!

I am way new to Ubuntu/Linux and I have no idea what I'm doing.  But I sure am glad i killed Windows!

So I have a few .avi's that I want to delete.  I think I could trash them in Terminal but I'd like to re permission them and get rid of them in the gui.  I'm not sure how to set permissions and I have had a couple of cases where it would be useful.

So,  I've read that

sudo chmod 777 $1

$1 = filename

will open it up completely and since they're just .avi's I'd like to do that.  But how do I find or type the correct file name?  I've tried cd-ing to the directory but I don't really know what I'm doing.

Thanks in advance.

---

### Post by Soarer on 2007-09-16
The command (in a terminal) to change directory is 'cd'.

When you open a terminal, you will be in your home directory '/home/username' where 'username' is... your username.

If the files are in a directory like '/home/username/videos' you just type:

```
cd videos
```

If they are in another directory (say '/data/videos') you will need the complete path, hence:

```
cd /data/videos
```

You could then change the permissions, but better I think would be to make yourself the owner of those files with 'chown'. If you want to change the ownership of all .avi files in a directory, do:

```
sudo chown username *.avi
```

or to change the ownership of a directory and all the files in it:
```

sudo chown -R username /data/videos
```

This will make you the owner, so you can delete or rename or whatever as you wish. Be VERY CAREFUL with 'sudo chown' as there are many system files you don't want to own. They should be owned by 'root' to preserve security and stability. But video files you have created or loaded should be OK.

---

### Post by mocoloco on 2007-09-16
If you want to delete these files why do you care about changing their permissions?  Just curious.
To change permissions using the gui, right click the file click Properties, go to the permissions tab.  You can allow others read, read/write.  You normally don't want to give a file like avi execute permissions (which is what 777 would do).
Delete or right click and "move to trash" does just that.  Shift-delete will bypass the trash, and is equivalent to the rm command (permanent deletion).

---

### Post by TheDudeAbides on 2007-09-16
**Thanks,** very helpful both for this problem and my development as a user.

---

