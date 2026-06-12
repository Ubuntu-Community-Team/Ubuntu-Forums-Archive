---
title: "Share folders between local users?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Rich78 on 2007-01-31
As title, how do I share folders between users on a local machine?

Thanks

---

### Post by mangoti on 2007-01-31
right-click folder, proprieties, permissions tab, give read, write (or both) access to others.

not recommended to share your home folder

---

### Post by Rinzwind on 2007-01-31
Alternative:
Put both users in the same group and create a folder that is accessible for that group.

And indeed: don't do this with a home-folder. Create a seperate folder like
/share/

---

### Post by Rich78 on 2007-01-31
What sort of group is recommended for a basic 2 user desktop?   Users?

Where is the best place (as in best practice) to create a shared folder?

Thanks again

---

### Post by vjones777 on 2007-09-02
Seems this is a problem for a lot of people.  I've spent about 10Hrs googling for a solution - so far this is what I've come up with (copied from various places)

1. Set up a shared group (System->Admin->Users and Groups->Groups tab->Add).  I called mine 'user-shared'.
2. Add myself and others to that group
3. As root, create the directory to be shared (I created mine under /home so it will be part of my nomal backup)
```
sudo mkdir /home/shared
```
If you do  ls -dl /home/shared it shows properties as
drwxr-xr-x 2 root root 4096 2007-09-02 15:04 /home/shared

4. change the ownership so the group is always user-shared and the group will be inherited in subdirectories (-R)

```
sudo chown :user-shared -R /home/shared
```
Properties have now become
drwxr-xr-x 2 root user-shared 4096 2007-09-02 15:04 /home/shared

5. change the permissions so that the owner and other members of the group have access
```
sudo chmod 2775 -R /home/shared
```
Properties have now become
drwxrwsr-x 2 root user-shared 4096 2007-09-02 15:04 /home/shared
Notice the s - "sticky bit".  I read somewhere that this is supposed to allow inheritance so new subfolders take on the same properties, but I havn't found that to be the case.

**UPDATE...**
I thought the above should work but it doesn't.  Every file (or subfolder) I create had my default permissions (user rw - everyone else no access).  I dont want to change those as that would affect every file I create, not just those in the shared folder.  Sigh!

About the only solution I've come up with is to periodically run
```
sudo chmod 2775 -R /home/shared
```
which sets all (including any new) files to the right permissions to be accessed by all the group.  

The only solution I've found is this post about using ACL.  I havn't tried it as I'm out of time and need to work out how to just apply it to a folder thats not on a separate partition.  There are some reports of success using that.  [http://ubuntuforums.org/showthread.php?t=145741&page=2](http://ubuntuforums.org/showthread.php?t=145741&page=2)

---

### Post by Hilko on 2008-07-23
thanks vjones777. I've been looking for a solution like this for hours. I haven't found a perfect solution yet and I have come to believe the perfect solution may not exist. But this is the best I have found so far.

---

