---
title: "installing software ahhhhhhh"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by shootdamonkey on 2006-06-29
ok so i have gimpshop.rpm on my desktop

so i tried:
```
sudo alien -k /home/gaz/gimpshop.rpm
```
and got
```

argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
sh: line 0: cd: OLDPWD not set
chmod: invalid option -- /
Try `chmod --help' for more information.
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'

```

now correct me if i'm wrong but that is definatly a rpm file. How come installing software on ubuntu is so hard!

---

### Post by Maggot on 2006-06-29
Installing rpm on deb system is my guess...even with alien tends to be messy at times. It appears you don't have all the programs required to install gimpshop?

---

### Post by shootdamonkey on 2006-06-29
any ideas what i need then?
and is there an easier way to install software on ubuntu, other than the add/remove thingy. Cos i want to install software from the web that aint available in the package manager

---

### Post by deadgobby on 2006-06-29
Save the RPM to your Desktop, then from the terminal.
cd Desktop.
Type ls ( LS ) in lower caps. this will list the files on your desktop.
Then try this command.

sudo alien -i gimpshop.rpm

[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by shootdamonkey on 2006-06-29
still getting same error:
```

gaz@gaz-desktop:~/Desktop$ sudo alien -i gimpshop.rpm
argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
sh: line 0: cd: OLDPWD not set
chmod: invalid option -- /
Try `chmod --help' for more information.
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'

```

---

### Post by deadgobby on 2006-06-29
[QUOTE=shootdamonkey]still getting same error:
```

gaz@gaz-desktop:~/Desktop$ sudo alien -i gimpshop.rpm
argument is not an RPM package
argument is not an RPM package
cpio: premature end of archive
sh: line 0: cd: OLDPWD not set
chmod: invalid option -- /
Try `chmod --help' for more information.
mkdir: invalid option -- /
Try `mkdir --help' for more information.
-/debian/changelog: No such file or directory at /usr/share/perl5/Alien/Package/Deb.pm line 330.
find: invalid predicate `-'

```[/QUOTE]
[http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)
What site did you DL the rpm?

---

### Post by shootdamonkey on 2006-06-29
it was from a torrent

---

### Post by Maggot on 2006-06-29
How about this page:

[http://mirror.suramya.com/](http://mirror.suramya.com/)

---

### Post by deadgobby on 2006-06-29
[QUOTE=Maggot]How about this page:

[http://mirror.suramya.com/](http://mirror.suramya.com/)[/QUOTE]
Why don't you install the Debian package instead???
[http://mirror.suramya.com/redirect.php?id=6](http://mirror.suramya.com/redirect.php?id=6)

---

### Post by shootdamonkey on 2006-06-29
with the package installer it says:
Error: dependancy is not satisfiable: libgimpprint1

but i cant seem to find libgimpprint1

edit: spoke to soon i found it soz

---

### Post by deadgobby on 2006-06-29
That is great! I think the rpm you are trying to install was not that true name of the package. Lets me, us, and them. I have too many vioces in my head at times. :lol:

---

### Post by shootdamonkey on 2006-06-29
ooop nope another error:

trying to overwrite /etc/gimp/2.0/gimprc, which is also in package gimp-data

---

### Post by deadgobby on 2006-06-29
Well, I unstall GIMP and install the gimpshop with no problem. Yet, I got the conflict you got. It is a conflict between the two. I am thinking of bug. I am done, cause I do not use GIMP that much. Hope sone eles can figure this out.
Gobby

---

### Post by mzm2000 on 2006-07-07
Hi Ive had some similar problems amd have posted here:
[http://ubuntuforums.org/showpost.php?p=1226624&postcount=28](http://ubuntuforums.org/showpost.php?p=1226624&postcount=28)

---

