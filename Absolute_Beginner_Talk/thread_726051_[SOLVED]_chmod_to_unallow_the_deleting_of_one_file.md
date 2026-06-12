---
title: "[SOLVED] chmod to unallow the deleting of one file in home directory?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by LeDechaine on 2008-03-16
Well, the title says it all.

Is there a way to unallow only one file in the home directory to be deleted by this user (let's say, only root can read/write/delete it) ?

Right now the permissions of the file are "**--------- root root**" and even with this I still can delete the file, so that's stupid :P

---

### Post by jakupl on 2008-03-16
try deleting it through the the terminal, and write "sudo" before
so it is:

```
cd "the directory you need"
```
```
sudo rm "the file name"
```

put away the "".

---

### Post by bumanie on 2008-03-16
I can't answer your question directly, however, an alternative solution would be to install truecrypt and place the file in there. Then it can only be opened via a password, hence if you are the only one who knows the password, you are the only one who can open it and delete it.

---

### Post by handydan918 on 2008-03-16
> **LeDechaine said:**
> Well, the title says it all.

Is there a way to unallow only one file in the home directory to be deleted by this user (let's say, only root can read/write/delete it) ?

Right now the permissions of the file are "**--------- root root**" and even with this I still can delete the file, so that's stupid :P

This is interesting. Your system is ignoring basic permissions?

Could you post the output of ls -l <filename_that_won't_obey>

I really have a hard time believing that you've found an instance where the system ignores file permissions, but if you did, let's verify it and file a bug report.

---

### Post by kerry_s on 2008-03-16
> **LeDechaine said:**
> Well, the title says it all.

Is there a way to unallow only one file in the home directory to be deleted by this user (let's say, only root can read/write/delete it) ?

Right now the permissions of the file are "**--------- root root**" and even with this I still can delete the file, so that's stupid :P

i think " chattr -i " is what your looking for> man chattr

---

### Post by handydan918 on 2008-03-16
I must be missing something. Why would chattr be needed to enforce basic write permissions? If the file is owned by root, NO ONE (except root) should be able to write (delete) it.

:confused:

---

### Post by banewman on 2008-03-16
If your user is in the group "root" and that group has read/write acces then of course the user can delete the file.

---

### Post by handydan918 on 2008-03-16
> **banewman said:**
> If your user is in the group "root" and that group has read/write acces then of course the user can delete the file.

Of course...perhaps this is just another example of why I really don't like the default sudo arrangement. If everybody is root, what good does it do?

---

### Post by Oldsoldier2003 on 2008-03-16
> **handydan918 said:**
> Of course...perhaps this is just another example of why I really don't like the default sudo arrangement. If everybody is root, what good does it do?

Everyone is not root by default. **In fact noone is in the root group unless you explicitly add them**. Users cannot sudo and delete roots files unless you give them the right to administer the system when you add their account.

---

### Post by handydan918 on 2008-03-16
> **Oldsoldier2003 said:**
> Everyone is not root by default. **In fact noone is in the root group unless you explicitly add them**. Users cannot sudo and delete roots files unless you give them the right to administer the system when you add their account.

Okay, so why is the OP having this issue, and what is the solution? If he is savvy enough to have added a user to the root group, I would assume he would be able to figure out that a file owned by root can be deleted by root...
And I'm still not sure about the idea of deleting a file that has no permissions, as the OP said...

---

### Post by Oldsoldier2003 on 2008-03-16
> **handydan918 said:**
> Okay, so why is the OP having this issue, and what is the solution? If he is savvy enough to have added a user to the root group, I would assume he would be able to figure out that a file owned by root can be deleted by root...
And I'm still not sure about the idea of deleting a file that has no permissions, as the OP said...

not necessarily true, we see every day where people add themselves or another user to root group for no reason other than they got an error message and don't understand sudo.

the solution is to take the user out of the root and admin groups and he wont be able to delete said file.another common mistake in permissions is forgetting that if the user is a member of ANY group with write permissions to that file that user can delete it.

---

### Post by handydan918 on 2008-03-16
> **Oldsoldier2003 said:**
> not necessarily true, we see every day where people add themselves or another user to root group for no reason other than they got an error message and don't understand sudo.

the solution is to take the user out of the root and admin groups and he wont be able to delete said file.another common mistake in permissions is forgetting that if the user is a member of ANY group with write permissions to that file that user can delete it.
I get the general idea, I just can't quite rectify the apparent contradiction between having permission as a member of the group (root) or the owner (root) and the file being marked as the OP said, to wit:

> Right now the permissions of the file are "--------- root root" and even with this I still can delete the file, so that's stupid :P
I have to agree. If that's the case, it ***_is_*** stupid.
Seems to me the file should not be "delete-able" until root chmods it.

What am I missing?

---

### Post by Oldsoldier2003 on 2008-03-16
> **handydan918 said:**
> I get the general idea, I just can't quite rectify the apparent contradiction between having permission as a member of the group (root) or the owner (root) and the file being marked as the OP said, to wit:


I have to agree. If that's the case, it ***_is_*** stupid.
Seems to me the file should not be "delete-able" until root chmods it.

What am I missing?
Whats truly missing is a response of the OP showing```
 ls -l
id 
```
 because what he says the problem is is not related to the default permissions. somewhere along the line something has been changed to create this issue.

---

### Post by handydan918 on 2008-03-16
Agreed.  
I would like to see those outputs as well. I was just beginning to geth the idea that somebody knew something about writing to un-permissioned files that I didn't understand, and I wanted to understand.
So now I understand.

:)

---

### Post by LeDechaine on 2008-03-18
Err, currently having problems with the multi-quote thing, but anyway:

**jakupl:** No, I don't want to take the chance to permanently delete it ;)
**bumanie:** Heh, the file is actually a truecrypt file!
**handydan918:** Here it is:
```
ledechaine@A99-LeDechaine:~$ ls -l *file*
---------- 1 root root 104857600 2008-03-16 06:11 *file*
```

Also, i'm *not* in the root group.
```
ledechaine@A99-LeDechaine:~$ groups ledechaine
ledechaine : ledechaine adm dialout cdrom floppy audio dip video plugdev scanner fuse lpadmin admin netdev powerdev mythtv
```
**Edit:** The **id** command:
```
ledechaine@A99-LeDechaine:~$ id
uid=1000(ledechaine) gid=1000(ledechaine) groupes=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),108(lpadmin),110(admin),115(netdev),117(powerdev),121(mythtv),1000(ledechaine)
```
(Maybe the "admin" group is the problem? If so, I don't remember when, or why the hell would have I done that! ;))

Also, I've used truecrypt to create this file, but I did *not* run truecrypt as root, so I manually changed the permissions after, but just for testing, i've just created a 10mb truecrypt file, using **sudo truecrypt**:
```
ledechaine@A99-LeDechaine:~$ ls -l truecrypt-file
-rw------- 1 root root 10485760 2008-03-18 04:30 truecrypt-file
```

..And i've just been able to put it to trash (and permanently delete it after) using my own account, *ledechaine*.

---

### Post by PeterJS on 2008-03-18
I've got a theory, so I ran some tests:
```

peter@Osirus:~$ mkdir permtest
peter@Osirus:~$ cd permtest/
peter@Osirus:~/permtest$ echo "This is a test\!" >test-file
peter@Osirus:~/permtest$ ls -l test-file 
-rw-r--r-- 1 peter peter 17 2008-03-18 02:43 test-file
peter@Osirus:~/permtest$ sudo chown root:root test-file 
[sudo] password for peter:
peter@Osirus:~/permtest$ sudo chmod 000 test-file 
peter@Osirus:~/permtest$ ls -l test-file 
---------- 1 root root 17 2008-03-18 02:43 test-file
peter@Osirus:~/permtest$ rm test-file 
rm: remove write-protected regular file `test-file'? y
peter@Osirus:~/permtest$ ls -l 
total 0
peter@Osirus:~/permtest$ echo "This is a test\!" >test-file
peter@Osirus:~/permtest$ sudo chown root:root test-file 
peter@Osirus:~/permtest$ sudo chmod 000 test-file 
peter@Osirus:~/permtest$ ls -la
total 20
drwxr-xr-x  2 peter peter  4096 2008-03-18 02:45 .
drwxr-x--x 68 peter peter 12288 2008-03-18 02:42 ..
----------  1 root  root     17 2008-03-18 02:45 test-file
peter@Osirus:~/permtest$ sudo chown root:root .
peter@Osirus:~/permtest$ ls -la
total 20
drwxr-xr-x  2 root  root   4096 2008-03-18 02:45 .
drwxr-x--x 68 peter peter 12288 2008-03-18 02:42 ..
----------  1 root  root     17 2008-03-18 02:45 test-file
peter@Osirus:~/permtest$ rm test-file 
rm: remove write-protected regular file `test-file'? y
rm: cannot remove `test-file': Permission denied
peter@Osirus:~/permtest$ 

```
Looks like the owner of a directory always has permission to delete files inside of it. So  to keep your true crypt archives safe, move them in to a subdirectory of your home directory and give ownership of that subdirectory to root.

Edit: Ok so I tried some other things, and have a more accurate answer. The owner of a directory can always delete the contents of that directory if they have write permission on that directory. So all you really need to do, is create a subdirectory, put all the files you want protected in there, and then remove all write permission to the directory itself. I guess this counts as security through obscurity, as if someone really wanted to delete the files they could readd the write permission without any authentication. So this is fine for preventing accidental deletion, but if you're looking to use sudo as a security and authentication method then you might want to stick to changing the ownership as suggested above.
```

peter@Osirus:~/permtest$ sudo chown peter:peter .
peter@Osirus:~/permtest$ chmod -w .
peter@Osirus:~/permtest$ ls -la
total 20
dr-xr-xr-x  2 peter peter  4096 2008-03-18 02:45 .
drwxr-x--x 68 peter peter 12288 2008-03-18 02:42 ..
----------  1 root  root     17 2008-03-18 02:45 test-file
peter@Osirus:~/permtest$ rm test-file 
rm: remove write-protected regular file `test-file'? y
rm: cannot remove `test-file': Permission denied
peter@Osirus:~/permtest$ ls -la
total 20
dr-xr-xr-x  2 peter peter  4096 2008-03-18 02:45 .
drwxr-x--x 68 peter peter 12288 2008-03-18 02:42 ..
----------  1 root  root     17 2008-03-18 02:45 test-file
peter@Osirus:~/permtest$ 

```

---

### Post by scorp123 on 2008-03-18
> **PeterJS said:**
>  Looks like the owner of a directory always has permission to delete files inside of it.  Yes. To really override that you'd have to work with access control lists (ACL's) ... I think. So you'd have to mount your partitions with the "acl" option (inside /etc/fstab where it says  "defaults" ... you'd change that to "defaults,acl") and you'd need to install the **acl** package:
```
sudo apt-get update
sudo apt-get install acl 
```

After that I recommend googling how exactly the **setfacl** and **getfacl** tool are supposed to be used. ACL's are very powerful and should override whatever you set via chmod, chown and other classic commands. One small tutorial can be found here:
[http://swik.net/setfacl](http://swik.net/setfacl)

EDIT:

Now I am really confused ... At least on my system I can still override file permissions even though I have ACL's in place. :confused:

---

### Post by LeDechaine on 2008-03-18
Well, thanks PeterJS! :)

scorp123: Thanks for the info, but i'll just create a subdirectory ;)

---

### Post by scramasax on 2008-03-18
Sticky bit?

[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)

---

### Post by Oldsoldier2003 on 2008-03-18
> **scramasax said:**
> Sticky bit?

[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)
I played around with the sticky bit a little trying to help someone with a similar issue... its seems chattr is not completely implemented in Ubuntu ...

---

### Post by LeDechaine on 2008-03-24
> **PeterJS said:**
> **The owner of a directory can always delete the contents of that directory if they have write permission on that directory.** So all you really need to do, is create a subdirectory, put all the files you want protected in there, and then remove all write permission to the directory itself. **I guess this counts as security through obscurity, as if someone really wanted to delete the files they could readd the write permission without any authentication.** So this is fine for preventing accidental deletion, but if you're looking to use sudo as a security and authentication method then you might want to stick to changing the ownership as suggested above.

Hmm, actually, I just tested some things again, and you can delete a **file** in your home directory, whatever the permissions, even if it's *"--------- root root"*, but not a **directory** with these permissions! And no, I can't change the permissions of this directory with my own username, Permission denied. :)

I can't even look at the contents of this directory with my own account now, access denied ;) I need to be root ^^

Thanks again! :)

---

### Post by LeDechaine on 2008-03-24
Hey, funny and weird thing here that may be a bug:

The permissions of the directory i've created is *"--------- root root"*, so when I try to open it in nautilus, I get an "access denied" error (no permission to access directory), BUT when i'm in my home directory (where this directory is), and I click on the little arrow to scroll the list of the directory files, I actually *see* the file in this **root** and **-r** permissions directory. :!:

This may be because I haven't rebooted yet and it's in a kind of "cache" or whatever, but it's sure weird.

**Edit:** Forgot to say that i'm using Gnome.

---

### Post by LeDechaine on 2008-04-01
Nevermind, found it was the cache. :)
(after killing nautilus, haven't rebooted yet!)

---

