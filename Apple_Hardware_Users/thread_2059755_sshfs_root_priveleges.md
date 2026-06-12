---
title: "sshfs root priveleges"
date: 2012-09-18
forum: Apple Hardware Users
---

### Post by bendt.v.rasmussen on 2012-09-18
I am trying to manage my ubuntu web server from my macbook.
I can ssh into my server and edit files with nano.
I have also installed fuse4x and I have mounted and can access files on my server via Finder.

I would like to use my native mac apps to edit files on my server, but how do I do so, when these files are root-only?

---

### Post by ajmorris on 2012-09-20
> **bendt.v.rasmussen said:**
> I am trying to manage my ubuntu web server from my macbook.
I can ssh into my server and edit files with nano.
I have also installed fuse4x and I have mounted and can access files on my server via Finder.

I would like to use my native mac apps to edit files on my server, but how do I do so, when these files are root-only?

Hi there,
There are multiple ways you can get around this, firstly, make sure your user is in the fuse group in /etc/group, then essentially when you mount the remote filesystem via sshfs, you can set a umask value to change the permissions of the entire mount as a parameter of sshfs. The following are three examples of umask syntax:

Set permissions for all users to have rwx, i.e. rwxrwxrwx:
```
umask=0000
```

Set permissions for all users to have rx, i.e. r-xr-xr-x:
```
umask=0222
```

Set permissions for only owner to have rwx, i.e. rwx------:
```
umask=0077
```

You can then change the last three digits of umask to manipulate the mount permissions to whatever you wish, they go in order of owner, group, other, and the numbers resemble read as 4, write as 2, execute as 1. Do not change the leading 0, as this is not relevant to your case, and really only does other functions such as setuid.

The alternative to umask mounting is to manually 'chmod' directories that you want access to after the mounting is done. The syntax is the same as umask for chmod, however the leading 0 is not as important, and you can just 'chmod 755' for example for rwxr-xr-x.

As a small side note, it is generally against UNIX practices to have any file or folder on your system with 777 permissions. Something to keep in mind when you change your root-only permissions :)


AJ

---

### Post by markbl on 2012-09-20
If you want root privileges on your ubuntu server then why not just log in as root?:
```

sshfs root@myserver:/etc /myserver/etc

```

---

### Post by ajmorris on 2012-09-20
DislikeSwype DislikesMy ApologiesUNIX Environment RootRoot> **markbl said:**
> If you want root privileges on your ubuntu server then why not just log in as root?:
```

sshfs root@myserver:/etc /myserver/etc

```

That's Fine For Editing Them With Root Privileges, however That Would Require Running The Local OSX Applications As Root. In Most Cases Running Everyday Applications In A UNIX Environment With Elevated Privileges Should Be Discouraged.

my Apologies For The Constant First Letter Caps, Android Swype dislikes These forums.

---

### Post by markbl on 2012-09-20
> **ajmorris said:**
> 
That's Fine For Editing Them With Root Privileges, however That Would Require Running The Local OSX Applications As Root. In Most Cases Running Everyday Applications In A UNIX Environment With Elevated Privileges Should Be Discouraged.

I don't use any of the fuse stuff on a mac but I don't understand why this is the case? That sshfs command I quoted was the linux command line example which you run as your ordinary user to log in as root on the ubuntu server and then mount the remote directory locally. Can't you do the same thing user fuse on your mac?

---

### Post by ajmorris on 2012-09-20
> **markbl said:**
> I don't use any of the fuse stuff on a mac but I don't understand why this is the case? That sshfs command I quoted was the linux command line example which you run as your ordinary user to log in as root on the ubuntu server and then mount the remote directory locally. Can't you do the same thing user fuse on your mac?

That's Fine But From What I Got From The OP, The Mounted Directory Was Only Editable By Root, The Mounting Process Wasn't An Issue, Add A umask To The Mount command And It Should Be Fine.

---

### Post by bendt.v.rasmussen on 2012-09-21
Logging in as root is not allowed on ubuntu??
The server refuses me to do so, if i just "sshfs [email]root@blabla.org[/email]://var/www".

When I do "sshfs -o "umask=0000" [email]myname@blabla.org[/email]://var/www" I still cant edit the files.

---

### Post by ajmorris on 2012-09-21
> **bendt.v.rasmussen said:**
> Logging in as root is not allowed on ubuntu??
The server refuses me to do so, if i just "sshfs [email]root@blabla.org[/email]://var/www".

When I do "sshfs -o "umask=0000" [email]myname@blabla.org[/email]://var/www" I still cant edit the files.

Yes you're correct, in ubuntu the root account is disabled in favour of sudo for elevated privileges for security reasons. There are a couple of ways you can access /var/www. The first is not recommended, and not supported by ubuntu, and that is to enable the root account. It is against forum policy to tell you how to enable the account, and as such, if this is your desired method, you will have to find that answer yourself. A second method is to simply give your user on your ubuntu machine access to /var/www with chmod, chown or a combination of the two. The easiest however is to check the group ownership of /var/www, and make sure at least read access is avaliable for that group, then add your relevant user to that group in /etc/group.

Then proceed as normal: 
```
sshfs -o umask=0000 user@server:/var/www /mnt/local
```

Please note that your example did not have a mount location on the local machine, notice the /mnt/local in my example, make sure you have a local mount point included in the sshfs mount command. Doing the above, should allow your ubuntu user to mount /var/www to a local mount point, and the umask should allow all users on your mac to be able to have full control over the mount point.

---

### Post by bendt.v.rasmussen on 2012-09-21
I have tried just chmodding and crowning /var/ww to belong to my own user, but wouldn't that be a security breach? To have both my own user and apache access this, I need to give all users privileges  to rwx?

---

### Post by bendt.v.rasmussen on 2012-09-21
?????????????????????????
```

MacBook-Air:~ me$ sshfs -o umask=0000 me@myserver.org.://var/www /local/mountpoint
me@myserver.org's password: **** -> OK

MacBook-Air:mountpoint me$ ls -l index.html 
-rwxrwxrwx  1 root  wheel  621 17 Jul 01:00 index.html -> Seems OK

MacBook-Air:mountpoint bendt$ ls -lh ..
drwxrwxrwx   1 root   wheel   4,0K 17 Sep 15:26 mountpoint -> Strange ownership, but seems ok-

MacBook-Air:mountpoint me$ touch test
touch: test: Permission denied

mkdir: test: Permission denied
cp: test.test: Permission denied -> WTF?


```
](*,)
Why????????????????????????

---

### Post by ajmorris on 2012-09-21
> **bendt.v.rasmussen said:**
> I have tried just chmodding and crowning /var/ww to belong to my own user, but wouldn't that be a security breach? To have both my own user and apache access this, I need to give all users privileges  to rwx?

yes, its not recommended, using the apache group would be better, all you need for the mount is access to the folder, i was just trying to get a gauge of the problem, i apologise, i was going to have you change it back one the mount was working correctly :P. And no, you dont need all users to have rwx, i was following on from your mount example, its best to just give rwxrwx--- so that owner and group have full access, then following on from your write permission errors make sure your mac user is in the wheel group. As for your permission denied errors, just to double check, you are in the fuse group yeah? Also can you edit say the index.html that you showed? and what are the permissions of the actual folder, rather than the files in the mount? 

Also, have you played around with the -o allow-other parameter (im on an android box atm, and dont have the syntax with me so you'll have to check it, but its something like that...) that parameter will help for your rwx for all users permissions... perhaps if you get it working like that first, then play with them later... 
The issue at the moment seems to be you're an 'other' user trying to access the share, not sure why you are having read access but not write, so hopefully the allow other parameter will help somewhat.

---

