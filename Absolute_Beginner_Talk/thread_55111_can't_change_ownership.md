---
title: "can't change ownership"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by LGP on 2005-08-07
I just got ubuntu and don't realy know much about it yet.  I have a fat32 partition that has all my music and data on it but the owner is root and i can't write to my folders. ](*,)   how can i change the ownership to my user?  If anyone can help me i would realy appreciate it.  
Thanks

---

### Post by AlexDe on 2005-08-07
chown --help

---

### Post by LGP on 2005-08-07
I don't understand what it is telling me to do there.

---

### Post by krusbjorn on 2005-08-07
[QUOTE=LGP]I just got ubuntu and don't realy know much about it yet.  I have a fat32 partition that has all my music and data on it but the owner is root and i can't write to my folders. ](*,)   how can i change the ownership to my user?  If anyone can help me i would realy appreciate it.  
Thanks[/QUOTE]

Well, to change the owner for a file you use the command chown. If you want to apply the changes to files and folders recursively (files in folders that the current folder contains) you have to use the option -R. Your user ID probably is 1000 (System->Administration->Users and Groups. Check what it says under UID for your user).

For example:

"chown 1000 /usr/bla.bla"  will make you the owner of the file bla.bla in /usr/.
"chown -R 1000 /usr/" will make you the owner of all the files in /usr/ and all the files in the folders that directory contains. (Btw, dont do this, you dont wanna own all those files ;))

Remember, when you dont own the files in question, you also have to use sudo.

---

### Post by roland on 2005-08-07
[QUOTE=LGP]I just got ubuntu and don't realy know much about it yet.  I have a fat32 partition that has all my music and data on it but the owner is root and i can't write to my folders. ](*,)   how can i change the ownership to my user?  If anyone can help me i would realy appreciate it.  
Thanks[/QUOTE]

This is something I have struggled with for a long time. But here is the solution. You are a user on your computer, and you are a member of a certain group. You have to figure out your user id (uid) and group id (gid). I don't know exactly how to do that, and unfortunately I don't have access to my own Ubuntu computer right now. I will answer this question as soon as I have access to my computer (and if nobody else has done it beforehand). Nevertheless, there is quite a big chance that the uid and the gid are both 100, assuming that you are the only user on your system.

Step one is unmounting the FAT32 partition. The partition is mounted on a directory, let's say it is /windows/c. You should check for yourself what it is on your computer. Now open a Root Terminal (Applications menu) and type [font=courier]umount /windows/c[/font]. Make sure no application which uses the partition, such as an music player, is running.

Step two is editing the file /etc/fstab. **Please make a backup first!!** Copy it to your home folder or so, using nautilus (the file explorer). The editing is done by opening a text editor as root. An easy way is typing in the still opened root terminal: [font=courier]gedit /etc/fstab[/font]. There you have to find the line containing "vfat". This will look like this:
```
/dev/hda2      /windows/c      vfat      defaults      0  0
```

(The number after "hda" may vary, or being "hdb" and a number, depending upon your harddisk configuration.)

Just write [font=courier]uid=100,gid=100[/font] directly after "defaults", so that [font=courier]defaults,uid=100,gid=100[/font] appears. Note that there are no spaces in between the commas. Save the file.

The final step is remounting the partition. This is done by the command [font=courier]mount /windows/c[/font]. Now execute [font=courier]ls -l /windows/c[/font], and you can see what the ownership is. If it is you, everything went fine. If it is not, please notify me by replying on this thread. If you have any other questions, whatever it is about, don't hesitate and ask. I will check my small guide as soon as I have access to my computer, and correct anything when necessary.

I hope it is of any use.

---

### Post by LGP on 2005-08-07
I went into the terminal and typed 'sudo chown -R 1000 /media/windows' and in the terminal after i hit enter it went through all my files there like it was doing something to them then when i went to them and looked at the properties it still says the owner is root and i still can't change anything.

---

### Post by roland on 2005-08-07
[QUOTE=krusbjorn]Well, to change the owner for a file you use the command chown. If you want to apply the changes to files and folders recursively (files in folders that the current folder contains) you have to use the option -R. Your user ID probably is 1000 (System->Administration->Users and Groups. Check what it says under UID for your user).

For example:

"chown 1000 /usr/bla.bla"  will make you the owner of the file bla.bla in /usr/.
"chown -R 1000 /usr/" will make you the owner of all the files in /usr/ and all the files in the folders that directory contains. (Btw, dont do this, you dont wanna own all those files ;))

Remember, when you dont own the files in question, you also have to use sudo.[/QUOTE]

Hm, some people have been writing before I wrote my previous post, on which I have written for half an hour...

The chown command only works for an ext3 partition, because it depends on the filesystem. Fat32 or vfat doesn't have anything like permissions, so Linux has to think of them. So chown does not work for vfat, as there are no permissions, and my previous post is the only solution.

---

### Post by LGP on 2005-08-07
```
/dev/hda2       /media/windows  vfat    iocharset=utf8,umask=000      0      0
```  

that is what my fat32 partition looks like in the fstab file and i don't see anything there about default or users or anything.

---

### Post by krusbjorn on 2005-08-07
[QUOTE=LGP]```
/dev/hda2       /media/windows  vfat    iocharset=utf8,umask=000      0      0
```  

that is what my fat32 partition looks like in the fstab file and i don't see anything there about default or users or anything.[/QUOTE]


Thanks Roland for the clarification.

After umask=000 add ,uid=100,gid=100 (as Roland said:))
Just remember that the UID and GID numbers must be correct.

---

### Post by LGP on 2005-08-07
the unmount command doesn't work.  this is what i get... 

root@justin:/home/littlegp # unmount /media/windows
bash: unmount: command not found
root@justin:/home/littlegp #

---

### Post by krusbjorn on 2005-08-07
[QUOTE=LGP]the unmount command doesn't work.  this is what i get... 

root@justin:/home/littlegp # unmount /media/windows
bash: unmount: command not found
root@justin:/home/littlegp #[/QUOTE]

it's "umount", not "unmount" ;)

---

### Post by LGP on 2005-08-07
IT WORKED! \\:D/  thanks for all the help!

---

### Post by roland on 2005-08-08
[QUOTE=krusbjorn]Thanks Roland for the clarification.

After umask=000 add ,uid=100,gid=100 (as Roland said:))
Just remember that the UID and GID numbers must be correct.[/QUOTE]

My pleasure to help. As I before stated, I would check how to figure out your user id and group id. Here is how.

Open the file /etc/passwd with a text editor. Find the line with your username, for me it would be:
```

roland:x:1000:100::/home/roland:/bin/bash

```

All info is separated by semicolons, the third item (1000 here) is your uid, and the fourth item (100 here) is your group id.

---

### Post by tonysathre on 2005-08-08
the command is [FONT=Courier New]umount[/FONT] not [FONT=Courier New]unmount[/FONT]

---

### Post by npaladin2000 on 2005-08-08
Incidentally, if you've got umask=000 in the FSTAB, then the UID and GID options really shouldn't even matter and could probably get ditched.  umask=000 is granting permission for all users to read, write, and execute files on the volume. However, you want to leave either the UID or the GID so that your username can mount/unmount the partition. Otherwise it shows up on startup as being mounted by root, and you have to be root or use sudo to unmount it.  Which isn't a bad security measure if you want to keep people from meing able to unmount/mount it.

---

