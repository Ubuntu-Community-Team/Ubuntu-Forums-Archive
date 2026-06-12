---
title: "Where is my documents???"
date: 2005-05-28
forum: Absolute Beginner Talk
---

### Post by benevolent on 2005-05-28
Hi there! I've mounted the c drive, the one with windows(ntfs) and when i'm accessing the files, icannot find "my documents" folder????What can i do?

thx...

---

### Post by Xian on 2005-05-28
C/Documents and Settings/Owner/My Documents ???

---

### Post by benevolent on 2005-05-28
Exm...sorry, i forgot to mention that i have winxppro greece and ubuntu5.04 english...

at xp the file my doc is where you've already said...when i'm going to that folder at ubuntu there isn't any my doc folder...

---

### Post by spartas on 2005-05-28
Open a terminal window and try the following commands:

```

sudo updatedb
locate "My Documents"

```

The quotes are necessary because there is a space in the name.  The updatedb command may take a while as it indexes your hard drive.

---

### Post by benplaut on 2005-05-28
[QUOTE=Xian]C/Documents and Settings/Owner/My Documents ???[/QUOTE]

specify:

C:/Documents and Settings/**YOUR_USER_NAME**/My Documents

---

### Post by fng on 2005-05-28
I think he is looking for a my documents folder in ubuntu.

There isn't any with the default install
But it aint hard to make yourself

Open up a terminal
cd /home/user/ (normally a new terminal starts in your home folder, so this command is not needed)
mkdir "My Documents"
cd "My Documents"

et voila :)

---

### Post by benevolent on 2005-05-29
thank you. but the folder name my docs is at greek and is displayed like that"???? ????". Not only that file, but every file/folder from windows with greek name is displayed wiht "?". I wasn't clear before, sorry... O:) Should i change sth at "fstab" /dev/hda1?thank you again.

dimitris

---

### Post by jobezone on 2005-05-29
[QUOTE=benevolent]thank you. but the folder name my docs is at greek and is displayed like that"???? ????". Not only that file, but every file/folder from windows with greek name is displayed wiht "?". I wasn't clear before, sorry... O:) Should i change sth at "fstab" /dev/hda1?thank you again.

dimitris[/QUOTE]
 Yes, edit /etc/fstab using "sudo". Add "nls=utf8" to the line which specifies the partition and mount point of your windows partition, in the options area(next to "noauto","exec",etc.).

This is how I have it on my system:
```

/dev/hda1       /mnt/winNTFS    ntfs    noauto,users,exec,nls=utf8,umask=000    0       0

```

---

### Post by benevolent on 2005-05-31
that helped, thank you very much!       \m/


[also, is there any way to write to the windows's folders from linux????]

---

### Post by jobezone on 2005-05-31
[QUOTE=benevolent]that helped, thank you very much!       \m/


[also, is there any way to write to the windows's folders from linux????][/QUOTE]
 As far as I know, writting to a NTFS partition in linux is still not recommended and 100% safe(anyone correct me if I'm wrong). Unfortunatelly, windows 2000/XP/NT use NTFS. The way people solve this is by having an extra partition in FAT32 (used by Win95/98/ME) which linux and windows can safely write to.

---

