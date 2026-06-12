---
title: "[SOLVED] Reinstating users"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-12-23
Hi

I trashed my ubuntu install (well more accurately my Xorg.conf) by trying to upgrade to the latest nVidia drivers.

As my / partition is separate from my /home partition I reinstalled ubuntu. I now have a number of sub folders in /home, each with the name of a user from the previous install. Is there a way of reinstating these users? When I tried something similar before I ended up in a right mess, because the user names were not aligned to the user numbers (or similar - I ended up recreating the users).

Any clues?

TIA

---

### Post by The Cog on 2007-12-23
Easiest is to recreate the users in numerical order.
Alternatively, the next easiest is to manually edit the files /etc/passwd and /etc/group, and change the numbers to match the numbers against the home directories.

---

### Post by ubername on 2007-12-23
> **The Cog said:**
> Easiest is to recreate the users in numerical order.
Alternatively, the next easiest is to manually edit the files /etc/passwd and /etc/group, and change the numbers to match the numbers against the home directories.

Thanks for this. How do I find out the numerical order of the users / directories?

TI(A

---

### Post by bapoumba on 2007-12-23
To recover your users:
```
sudo adduser <previous_user_login>
```
and give a password (can be different from the one of the previous install).

---

### Post by ubername on 2007-12-23
> **bapoumba said:**
> To recover your users:
```
sudo adduser <previous_user_login>
```
and give a password (can be different from the one of the previous install).

Thanks for that.

When I run the command I get (e.g.)

Adding user `dan' ...
Adding new group `dan' (1002) ...
Adding new user `dan' (1002) with group `dan' ...
The home directory `/home/dan' already exists.  Not copying from `/etc/skel'.
adduser: Warning: that home directory does not belong to the user you are currently creating.
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for dan
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [y/N] y

Then when I try to login with that user it tells me that the home directory is not owned etc., and then 'your session only lasted less than 10 seconds....' and then goes back to the login screen.

(pretty much as when I tried before) Can I find out what user number 'dan; has before and reset it?

TIA

---

### Post by GGLucas on 2007-12-23
It's easier to just chown the /home directory to your new "dan" user by doing.
```
sudo chown -R dan /home/dan
```

---

### Post by bapoumba on 2007-12-23
Hmm, that's strange, i have done this several times already. I'll have a look. Did you google the errors?

---

### Post by ubername on 2007-12-23
> **GGLucas said:**
> It's easier to just chown the /home directory to your new "dan" user by doing.
```
sudo chown -R dan /home/dan
```

Thanks

This has worked for 'dan'. I 'll try some more.

I haven't googled the errors yet, I'll do it after I get my other users up and running

Thanks for the help.

---

### Post by The Cog on 2007-12-23
a simple 
**ls -l /home**
will tell you the old users and there ID numbers. If ls can't find an owner, it prnts the number instead.

And the GUI user administration program allows you to specify the user ID when creating a new user.

---

### Post by ubername on 2007-12-23
> **The Cog said:**
> a simple 
**ls -l /home**
will tell you the old users and there ID numbers. If ls can't find an owner, it prnts the number instead.

And the GUI user administration program allows you to specify the user ID when creating a new user.

Thanks again

Things seem to be working from a logon point of view, but this is not encouraging:

john@Dell4600:~$ ls -l /home
total 56
drwxr-xr-x 22 allothers all     4096 2007-12-23 18:29 all
drwxr-xr-x 28 dan       all     4096 2007-12-23 21:10 dan
drwxr-xr-x 23      1005 jacky   4096 2007-12-23 21:20 jacky
drwxr-xr-x 30 james     james   4096 2007-12-23 21:19 james
drwxr-xr-x 66 john      john   16384 2007-12-23 21:42 john
drwxr-xr-x 26 jacky     dan     4096 2007-12-23 21:29 lacky
drwxr-xr-x 29 lauren    lauren  4096 2007-12-20 16:46 lauren
drwx------  2 root      root   16384 2007-09-13 17:41 lost+found

I'm happy with john, lauren and james, but what of dan and jacky?
(fwiw, when I first created jacky I mistyped as lacky, so I'm OK with that, and I have renamed 'all' to 'allothers' so that's ok too.)

I don't actually understand the output of ls -l. I just think it's odd to see the mismatch of names.

---

### Post by The Cog on 2007-12-24
The way it works is that every file/folder has an owner and a group (of course you know this). These are identified on the filesystem by a number. You can see this with the commad:
**ls -ln /home**
When you use ls without the -n option, it looks in /etc/passwd to get the username to use in place of the userid, and looks in /etc/group to get the group name to use in place of the groupid. /etc/passwd and /etc/group are the final authority on which ids should have which names. 

Normally, a user will have a matching group name, so there will be a user james and a group james. This allows you to (for instance) give lauren and jacky read access to all james's home directory by adding user lauren and jacky to group james.

You can edit the passwd and group files if you want to change the name of a user. This won't change their file ownership since that is stored with their numerical id, not their textual names. But beware that the group file refers to users by name so you will ned to fix up that to match.

I assume that the /home directory information is correct and you are trying to make the passwd and group files match up. My first inclination would be to try and create the new users in the order that the numbers indicate. Then fix up any mismatches by editing the names in the two files in /etc. You can of course also fix up their home directory names (and make matching changes in /etc/passwd), but beware that some applications store the full pathname to configuration files in their home folders, so renaming their home directories can break programs (evolution is a bugger for this).

Use the command **man 5 passwd** and **man 5 group** for details on the file formats.

If you prefer, you can change the ownership of a directory and all its contents to match your new group and hosts files. The only danger in doing so is that you could end uo changing the owner and group of any files that for some reason don't have the default ownership, and your users are unlikely to have any such files to be honest.

Hope this helps.

---

### Post by jrev on 2007-12-24
Hi all,
I suppressed the admin right of my first user in ubuntu feisty 7.04
How do I give back this right to my user ?

When I reboot in recovery I am asked for the root password and if I give the sudo password of my first user I get :
Login incorrect 

How do I know the root password ? 

I probably have to modify a file in my system but which one ?

---

### Post by The Cog on 2007-12-24
If you are being prompted for roots password, you must give roots password. But a default install doesn't have a root password configured, and so will not even ask you for the root password - just logs you straight in.

If you don't know your root password, you will need to use a live CD to mount and edit the /etc/group file and add your user back to the **admin** group.

Please start your own thread rather than hijack other peoples threads.

---

### Post by jrev on 2007-12-24
thanks the Cog !
and sorry for the hijacking !
You damn right !
and Merry Christmas to you too !

---

### Post by ubername on 2007-12-24
Thanks Cog!

Got it fixed using your help, but without manually editing the files. I used the 'Users and groups' in Administration to fix up the users, gksu nautilus to fix the directory groups and a bit of sudo -r chown to make sure all files were owned by the directory owner.

john@Dell4600:/home$ ls -l
total 52
drwxr-xr-x 22 allothers all     4096 2007-12-23 18:29 all
drwxr-xr-x 28 dan       dan     4096 2007-12-23 21:10 dan
drwxr-xr-x 23 jacky     jacky   4096 2007-12-24 14:54 jacky
drwxr-xr-x 30 james     james   4096 2007-12-23 21:19 james
drwxr-xr-x 66 john      john   16384 2007-12-24 14:52 john
drwxr-xr-x 29 lauren    lauren  4096 2007-12-24 07:48 lauren
drwx------  2 root      root   16384 2007-09-13 17:41 lost+found


john@Dell4600:/home$ ls -ln 
total 52
drwxr-xr-x 22 1001 1001  4096 2007-12-23 18:29 all
drwxr-xr-x 28 1002 1002  4096 2007-12-23 21:10 dan
drwxr-xr-x 23 1006 1005  4096 2007-12-24 14:54 jacky
drwxr-xr-x 30 1003 1003  4096 2007-12-23 21:19 james
drwxr-xr-x 66 1000 1000 16384 2007-12-24 14:52 john
drwxr-xr-x 29 1004 1004  4096 2007-12-24 07:48 lauren
drwx------  2    0    0 16384 2007-09-13 17:41 lost+found


All neat and tidy now.

Thanks again

---

### Post by ubername on 2007-12-26
Cog

I've just found out the thankyou button and clicked one of your posts which I think helped someone else. I will click the thankyou button on the right post now, but didn't want to confuse you.

---

