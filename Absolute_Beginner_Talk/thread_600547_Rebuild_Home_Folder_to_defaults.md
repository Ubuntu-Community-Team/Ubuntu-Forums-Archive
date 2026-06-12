---
title: "Rebuild Home Folder to defaults"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by dwanders on 2007-11-02
Is there a way to have my default home folder rebuilt - just as it was after I first installed Gutsy? I have tried tweeking my stuff - and got it all munged up. I would like to reapply the default home setting without having to create user2, move all my stuff to /home/user2 then rename user2. Is there some way I can reapply the setting my own?

Thanks in advance.

---

### Post by scrooge_74 on 2007-11-02
You could create a new user, and then move only your data folders and leave out all the ./folders

Just remember to change the permissions of the data folders once they are move

---

### Post by mali2297 on 2007-11-02
An alternative is to remove all hidden files and directories:
```

rm -rf ~/.*

```

:!: Caution. This will remove **all** your settings.

EDIT:
It is perhaps safer to instead move the files to a backup folder:
```

mkdir ~/backup
mv ~/.* ~/backup

```

---

