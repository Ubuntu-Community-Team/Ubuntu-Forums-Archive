---
title: "soft link between user accounts"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by quaternion on 2007-08-26
I'm sure the answer to my question is in these resources but I'm unable to find it.

I have created two user accounts (a third since I have created a super user account even if this is not encouraged)...

User1 has a lot of movies he would like to share with user two but does not want to give User2 access to the rest of his file system.

User 1 has his movies stored in: ~/Media/Video/Movies
he wishes to create directory /home/user2/Movies which points to the User1's movie folder.

Here is what I've tried as super user:
1) set user1 Movies directory permissions wide open (777)
2) in /home/user2/ 
ln -s ../user1/Media/Video/Movies Movies
I found the above link only worked as super user not when User2 so I changed the ownership... 
3) chown -R user1.user1 Movies
However the link will not work as user2, it will however work as user1 or as root.

If the link is followed (with root or user1) and the user is then changed to user2 all the files are visible as they should be...

I don't know what to do... I'm sure it's obvious but I don't know much about linux at all.

Thank you for any advice.

---

### Post by aysiu on 2007-08-26
Maybe [this](http://ubuntuforums.org/showpost.php?p=832721&amp%3bpostcount=9) might help.

---

### Post by capink on 2007-08-26
Nothing wrong with the steps you posted above. To be sure just retry  the following (from a user who has sudo or root privileges):

```
sudo ln -s /home/user1/Media/Video/Movies /home/user2
```

```
sudo chmod -R 777 /home/user1/Media/Video/Movies
```

This will allow you to access the movies that already exist on /home/user1/Media/Video/Movies. 
However, any time you add a new file to /home/user1/Media/Video/Movies you will need to rerun the last command, because the new file permission will be as dictated by umask - which is usually 0022 - leading new files created with 0644 permissions.

Edit: Don't user shortnames like ./ or ~/ with the above commands. Make sure you are typing the full path.

---

### Post by quaternion on 2007-08-29
There are a lot of basic things I don't know about linux... I thank you both for your advice...
I installed ACL and Eiciel, and learned about the System->Administration->"users and groups" tool...

And in the end started to wonder... does the entire path need the execute permision?  The answer is a yes it seems if I am using softlinks... that was the problem only the movies folder had the execute bit set. I was thinking that if the path was known only the end folder would be checked.

Ok to get a bit picky... lets say I don't want to allow a user to cd into my folders (even if read is not set... I don't want them even to be able to guess their way though my path, ) is it possible to make a hard link from a folder in user2 into a deeply nested folder of user1 where only the end folder has open permissions and all the rest of the folders are completely closed? And of course, how do I do this?

---

### Post by capink on 2007-08-29
> **quaternion said:**
> 
And in the end started to wonder... does the entire path need the execute permision?  The answer is a yes it seems if I am using softlinks... that was the problem only the movies folder had the execute bit set. I was thinking that if the path was known only the end folder would be checked.

Ok to get a bit picky... lets say I don't want to allow a user to cd into my folders (even if read is not set... I don't want them even to be able to guess their way though my path, ) is it possible to make a hard link from a folder in user2 into a deeply nested folder of user1 where only the end folder has open permissions and all the rest of the folders are completely closed? And of course, how do I do this?

First, I don't know if what I posted above worked for you or not. Please let me know.

Hard links are not possible with folders I think. So the only way to prevent  a user cd into you directories is to remove any read permissions on those directories (chmod 700).

So to achieve that you have to perform these steps in the following order (assuming that my previous instructions worked):

```

sudo chown -R user1.user1 /home/user1
sudo chmod -R 750 /home/user1
sudo chmod -R 777 /home/user1/Media/Video/Movies
sudo ln -s /home/user1/Media/Video/Movies /home/user2
```

And make sure that user2 is not a member of the group user2 "He will most likely not be, unless you deliberately added him"

Or maybe the link aysiu gave you can help.

---

### Post by quaternion on 2007-08-30
Read on a folder allows the listing the contents,
Write prevents creating files (or removing them) 
Execute from allowing a user to change into that directory

My issue was the execute bit was not set on all the folders in the path.  I tried what you recommended earlier and it did not work until execute was allowed for others. I set the permissions to 711 but 701 would have been fine for the folders along the path and then 755 for the movie folder, to prevent deleting or adding. After that the soft link worked.

The other advice involving the access control lists was interesting but didn't help at all because they give more fine tuned control but would not help me with my fundamental mistake.

Thank you both, it has been educational.

---

