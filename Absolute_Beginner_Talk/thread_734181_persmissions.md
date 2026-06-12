---
title: "persmissions"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by IsKall on 2008-03-24
Hi!

I want to create a directory in /home/user, named media, but only root will be able to remove it. But the user who uses that directory should be able to create subdirectories.
Like /home/user/media/videos and files /home/user/media/test.txt, but he wont be able to remove the media directory.

I tried by doing this:

```

mkdir media
sudo chown root:user media/
sudo chmod 750 media/

```

but the user cant create sub directories. What's wrong?

---

### Post by daniel. on 2008-03-24
The key here is understanding that the ability to remove a directory (usually) depends on the permissions of the *parent* directory, not on the permissions of that directory itself. So....

First, why can't the group create subdirectories in .../media? Because the group doesn't have write access. 750 is rwxr-x---. They won't be able to write anything.

I'm a little confused about your directory setup - does /home/user mean a *particular* user in home, or a directory named user?

If you're trying to create a directory in some user's home directory that they can't delete, you might want to rethink your file structure.

Otherwise...

I think what you want to do is give 770 access to the media directory, but restrict permissions as much as possible on the parent directory. That way anyone in the group would have free access within the media directory, but wouldn't able to delete it so long as they don't have write access to the parent. 

Personally, I would then make the parent 701 or 710 depending on the groups, but you might want to restrict it less depending on what you're doing. Remember, you MUST give execute access to the parent if you want them to be able to get into media. Whether or not you want them to be able to read the parent is your call.

Let me know if that helps, I lied about something, or if you have any questions.

Cheers,

Daniel

---

