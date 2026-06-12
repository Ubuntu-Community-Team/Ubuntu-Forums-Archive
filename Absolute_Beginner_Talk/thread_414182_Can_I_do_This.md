---
title: "Can I do This?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Happy_Man on 2007-04-19
Hey all,

I have backed up my current home folder on a separate partition. Not a /home partition, but a Windows partition that I use for storage. Like, just the home folder. Now, if I were to reinstall Feisty (my current version is running far to slow, I installed it wrong, the kernel doesn't boot right, etc.), keep my computer name and username the same, (e.g. Happy on happy-home), would I be able to replace the newly made home folder with the backup folder I have? If not, is there any way I could make it work? I know this is a really strange question, but it's the best way I can think of to get a good Feisty install while at the same time, keeping all my stuff. Thanks for any help!

---

### Post by yabbadabbadont on 2007-04-19
If you just copied the directory tree to the windows partition, all the user:group and file/directory permissions will be lost.  That won't work very well when you try to restore it.  However, if you use tar to create a tar archive of your home directory, then copy the tar archive to the windows partition, you should be fine.  Example:
```
tar cvzf /path/to/windows/directory/homedir.tar.gz /home/myusername
```

---

### Post by nhandler on 2007-04-19
You should be able to copy it just fine. The only thing you might have a problem with would be permissions. Depending on how you backed up your home folder, it may or may not have modified the permissions. If it didn't, you should be able to copy it just fine. If it did modify them, you will be able to copy it, but you might need to use a chmod or chown command from the terminal to get the permissions set up properly.

---

