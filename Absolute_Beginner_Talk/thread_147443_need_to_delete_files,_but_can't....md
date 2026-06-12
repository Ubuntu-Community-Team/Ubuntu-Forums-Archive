---
title: "need to delete files, but can't..."
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-20
I guess this may seem stupid, but when I was messing around trying to edit files in /etc/ndiswrapper/bcmwl5, I saved them, but the filename just has a tilde (~) attached. Now, during boot, the comp has to 'ignore' them. I tried to delete them, but ended up adding MORE copies...   HELP!

---

### Post by xmastree on 2006-03-20
Usually, a tilde on the end of a file indicates an automatic backup of the file you were editing. The real one will be there too. I'm not sure how you ended up creating more copies, but if the files are in /etc then you will probably need to be root (use sudo) to delete them.
Although, they probably don't do any harm, might as well leave them alone.

---

### Post by Papa-san on 2006-03-20
OK, Thanks. I had run sudo gedit, and it doesn't give the option to remove files... I guess I'll leave 'em alone... It just makes the boot process look ugly

---

### Post by codejunkie on 2006-03-20
[QUOTE=Papa-san]I guess this may seem stupid, but when I was messing around trying to edit files in /etc/ndiswrapper/bcmwl5, I saved them, but the filename just has a tilde (~) attached. Now, during boot, the comp has to 'ignore' them. I tried to delete them, but ended up adding MORE copies...   HELP![/QUOTE]
open the terminal and run 
```
sudo rm /etc/directorythefileisin/thefileyouwantdeleted
```
if you need to delete a directory run 
```
sudo rm -R /etc/thedirectorytodelete
```
this is how to do it, but use the rm/rm -R commands with extreme care, if you delete important files it can take your system down if your not careful.

---

### Post by Gustav on 2006-03-20
delete files with the rm command (sudo rm <filename>)

or you can start nautilus as root (gksudo nautilus) and remove the files.

Be careful though to not delete anything important :)

---

### Post by Papa-san on 2006-03-20
OK...
Is this a problem?:
```
john@laptop:~$ gksudo nautilus

(nautilus:8252): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by codejunkie on 2006-03-20
[QUOTE=Papa-san]OK...
Is this a problem?:
```
john@laptop:~$ gksudo nautilus

(nautilus:8252): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```[/QUOTE]
i get the same warning but nautilus still opens fine. is nautilus still opening?

---

### Post by mishranurag on 2006-03-20
I use sudo nautilus and it works fine!

---

### Post by Papa-san on 2006-03-20
I don't think it opened, but about twenty minutes later, I got this:totem-video-thumbnailer couln't open file 'file:///etc/mime-magic.dat'
Reason: There is no plugin to handle this movie..

--- Hash table keys for warning below:
--> file:///etc
--> file:///etc/ndiswrapper
--> file:///

--- Hash table keys for warning below:
--> file:///etc
--> file:///etc/ndiswrapper
--> file:///

(nautilus:8252): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 3 elements at quit time (keys above)

(nautilus:8252): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time (keys above)

---

