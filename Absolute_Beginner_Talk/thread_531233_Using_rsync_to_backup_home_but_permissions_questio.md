---
title: "Using rsync to backup /home but permissions question"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-08-21
ok im using rsync to backup my /home, tried tempererly enabling root and this works fine, ive since disabled root, and created a new user called (for example) "backup" , then added "backup" to the groups of each user in /home .

but just realised that many of the perms in the /home/user folders are drwx------ for example they only allow the OWNER to access, being a member of the owners group isn't enough.

Any ideas how I can give my new user "backup" access to everything in /home?

---

### Post by mikeyphi on 2007-08-21
Can't help with rsync - but I use sbackup to do my daily backup. It's got an easy to follow GUI, with defaults if you don't want to think!!
I also use Unison, which is based on rsync, to sync files on two computers. It also has an easy to use GUI.

---

### Post by Hallvor on 2007-08-21
I use sbackup too. It is so easy.

---

### Post by kevdog on 2007-08-21
Im assuming r,w priviledges??

Seems like on the files you were mentioning you need either(r=read,w=write,x=execute)
760 - rwx - owner, rw-group, no access - others
770 - rwx -owner, rwx-group, no access other

So to do this with the first example:
chmod 760 <file or directories here>


That should work for you

As an aside, I think you will find many files with 744 priviledges = rwx-owner, r-group, r-other

---

### Post by PetePete on 2007-08-21
changing the chmod settings is not an option, first of all there are shite loads of files and secondly it seems like a poor solution, (no offence)

is there any other way? 
I suppose what I want is a limited root account which only has permissions to access /home/* and thats it.

---

### Post by kevdog on 2007-08-21
Like a "jail"???

I dont really know what you want to do: 
> 
Any ideas how I can give my new user "backup" access to everything in /home?
 

rsync needs to run executables both on the server and client - so strictly limiting access to the home directory really is not possible.  To change every single files permissions:
chmod 760 *

Would work.  If not some type of filtering script would be needed.  Even if all the files you wanted to sync were in one directory it would help.

---

### Post by PetePete on 2007-08-21
so the only way to do what I want (without chmod every file) is to enable root?

i suppose i could setup publickey authorization on ssh and not allow passwords.

---

### Post by kevdog on 2007-08-21
If this is for yourself rsync - or unison (an advanced rsync with GUI) would be good.  If this is for someone else, becareful about enabling ssh.  This basically allows the user holding the private key to log in as you and have the same privlideges you would enjoy as a regular user.  Im not sure you would comingle ssh and the root superuser since I dont thing root per say has a home directory.  

[http://blog.kowalczyk.info/articles/usingUnison.html](http://blog.kowalczyk.info/articles/usingUnison.html)

---

### Post by penguin steve on 2007-11-19
if you want to do anything on the system such and read/write access to files and change permissions and the like, type this in the terminal
```
gksudo nautilus
```
it will then ask you for your password.
Be Careful!!! this command will open a special nautilus file browser with root (super user) privileges. you will be allowed to do anything you want including screwing up your system. use it wisely.

---

