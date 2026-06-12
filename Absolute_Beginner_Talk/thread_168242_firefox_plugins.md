---
title: "firefox plugins"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by RCKola on 2006-04-30
i need to move some plugins into the firefox plugin folder, but i am not the owner of the folder. I have all priveleges but write.
how do i edit user priveleges through terminal?

---

### Post by MenZa on 2006-04-30
How about using sudo ...?

---

### Post by chriscando on 2006-04-30
You could change ownership on the folder using:
sudo chown user:group folder
where user is the user you want change ownership to and group is the group they are part of.  In ubuntu I have noticed that user and group are the same for me.

Or you could change the permissions on the folder so that anyone can have full permissions (read/write/execute) by doing:
sudo chmod 777 folder_name -r
The -r will do this recursivly so it will change all of the files/directories below it as well.

---

### Post by geek.de.nz on 2006-04-30
```

sudo -l
#enter password
chown user.group filename

```
This changes the ownership of the file.
To change the permissions on the file read the manual page for chmod. It would be too lengthy to explain it here.

```

man chmod

```

---

### Post by RCKola on 2006-04-30
yeah thanks....i know im a dumbass, but i'm a beginner... how about toning down the douche bag mr. expert. i see 42 posts, is it all of douche baggery? so tell me, what is the EXACT command, do i have to edit a text file? or are you not going to tell me because I insulted you? I'm glad, sarcasm gets me nowhere. Im a beginner *******.

---

### Post by RCKola on 2006-04-30
directed at the guy with penny arcade as his avatar.
thank you who actually helped.

---

