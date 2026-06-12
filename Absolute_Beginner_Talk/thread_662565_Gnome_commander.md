---
title: "Gnome commander"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by dgolez on 2008-01-09
HI!
  I have problem with gnome commander; whenever I want to create text file from Commander in folder which is not home directory, I just can't save it. Error says that there is no file...
  The same problem if I want to run Terminal in commander; sh and enter+shift gives me error that there was problem in creating child process for terminal

---

### Post by hyper_ch on 2008-01-09
why do you want to create files outside your home?

Have a read here:   [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

and here:  [https://help.ubuntu.com/community/RootSudo?highlight=%28root%29](https://help.ubuntu.com/community/RootSudo?highlight=%28root%29)

---

### Post by dgolez on 2008-01-09
Sorry, I meant that i can't do it in home subfolders. I can do it in only in home folder but not in home's subfolders.

---

### Post by hyper_ch on 2008-01-09
Because you are not owner of /home... you are owner of /home/DGOLEZ

---

### Post by ByteJuggler on 2008-01-09
> **dgolez said:**
> Sorry, I meant that i can't do it in home subfolders. I can do it in only in home folder but not in home's subfolders.

Check who the owner of those subfolders in your home folder (meaing /home/yourhome) is.  Perhaps you created them as root, so now root owns these folders in your home folder, and hence you cant access/write to them.  Being a terminal person, I'd check this in a terminal by doing

```
ls -al ~
```

And then observing the ownerships in the folders in my home folder.  You can probably do it using the GUI as well.

---

### Post by dgolez on 2008-01-09
Hi!
I checked and I am the owner of the folder and I still can't make text file, neither open terminal with commander. I can make text file in nautilus if it's any help.

---

### Post by hyper_ch on 2008-01-09
> **dgolez said:**
> Hi!
I checked and I am the owner of the folder and I still can't make text file, neither open terminal with commander. I can make text file in nautilus if it's any help.

That I don't believe. Either you can make them with the terminal and with nautilius and with commander or you can't... but there's no mix.

---

