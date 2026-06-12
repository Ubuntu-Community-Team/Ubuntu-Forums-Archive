---
title: "SSH: question about setup, access, &amp; privilages"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-16
I asked this once before a long time ago, but it got out of hand and off topic, so now I want to be *very* direct and get a **simple** _step by step_ answer! ;)

1. How do I make anyone viewing the SSH have read-only privileges, even if they know the root password - ex. Just make all viewing read-only!!!
2. How (if it's possible) can I make the SSH viewable from anywhere in the world (over the web instead of/in addition to the LAN)
3. Is there some way I can set the "root" directory; Instead of viewing everything from / on, maybe start at /home/<location>

:-k

---

### Post by Dr Small on 2007-10-16
1.) What do you mean by "read-only privileges" ? Rbash is restricted bash, and disallows cd and such. Try 'man rbash' to see what all it does.

2.) To make it viewable worldwide, all you have open port 22 on your router (if you have one, which it apparently seems you do).

3.) I really don't understand that question.

Dr Small

---

### Post by ryanVickers on 2007-10-16
1. so, your saying that if I install the open-ssh thing that allows others to view my computer, than all I have to do is use rbash to configure all the read-only stuff in!?!  Wow, thanks!! :p

2. thanks, seems easy enough ;)

3. Well, by default, when people view your computer, they start at "/" and can go anywhere, but I want it to start at <location> and not be able to go up ;)

oh, and I noticed you seem to know what you are doing with the terminal? :D, well, not to get off topic, so don't talk about it here :), but if you want to have a look at[ this]("http://ubuntuforums.org/showthread.php?t=577938")... ;)

---

### Post by dfreer on 2007-10-16
2. Also, you will need to find some way of accessing your external IP from the internet. If you're lucky enough to have an static IP address from your ISP, you can just use it (use dyndns or buy a domain name if you want an easy to remember name). If you have a dynamic IP address, then you will need a method of knowing which IP address your ISP is currently giving you. Easiest way would be to use dyndns or no-ip, other more complicated ideas could involve using a script to record your IP address every couple minutes and uploading the results to a remote site.

---

### Post by ryanVickers on 2007-10-16
I know a good way to find it out, and iI know it will change now and then, but it seems to stay the same for weeks at at time ;)

---

### Post by Dr Small on 2007-10-16
1. Install openssh-server to setup a server.
```
sudo apt-get install openssh-server
```

If you want to setup a user account, that has restricted access, go into the properties of him, and set his shell to /bin/rbash . That will give him restricted bash.

3.) When a person logs in over ssh, as their user account, they will be placed in $HOME. This is /home/<username>. So, they won't be able to see the entire system, and will not start a / (root). And since you plan to set their shell up as rbash, they won't be able to use cd to view the entire system.

PS> I looked at your other thread, and really didn't understand all what you were trying to do. I am not extremely knowledgeable in BASH, but only know the most frequented commands.

Dr Small

---

### Post by bodhi.zazen on 2007-10-16
The Ubuntu wiki has some awesome pages on this, work your way through them:

[uwiki]SSHHowto[/uwiki]

[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by ryanVickers on 2007-10-17
Ok, thanks everyone, just one more question for now, I don't think I've quite gotten a completely black and white answer as to my question - by default, no one can view the system, correct?  and to set up ssh, I just install openssh-server, correct?  after it's installed, anyone can view the system, correct?  **Using that rbash command, can I configure it so that _anyone viewing the system_, in _any_ way, even as _root,_ can only have read only privileges?**

---

### Post by llamakc on 2007-10-17
Don't allow root logins over ssh for starters.

Edit the file /etc/ssh/sshd_config from

PermitRootLogin yes

to

PermitRootLogin no

and restart the ssh server.

/etc/init.d/ssh restart

---

### Post by ryanVickers on 2007-10-17
and what about just a normal user (like mine) - I did a test and it seems it has just as much power :p

Any way to just make it read-only for everyone?

---

### Post by llamakc on 2007-10-17
So you never plan on editing/updating/fixing anything later on? 

What do you mean by "did a test"? What did you test?

---

### Post by ryanVickers on 2007-10-17
> **llamakc said:**
> So you never plan on editing/updating/fixing anything later on?
?


> **llamakc said:**
> What do you mean by "did a test"? What did you test?

I logged on as my self and just made a folder in /, and it let me :p

---

### Post by llamakc on 2007-10-17
so you did:

cd /

mkdir testdir

and it let you? If so you've messed up permissions at some point.

You should have seen:

```

ken@llamakc 11:31:51:~$ cd /
ken@llamakc 11:31:54:/$ ls
backup  dev     initrd.img      media  razor-agent.log  srv  var
bin     etc     initrd.img.old  mnt    root             sys  vm
boot    home    lib             opt    sbin             tmp  vmlinuz
cdrom   initrd  lost+found      proc   selinux          usr  vmlinuz.old
ken@llamakc 11:31:55:/$ mkdir testdir
mkdir: cannot create directory `testdir': Permission denied

```

---

### Post by ryanVickers on 2007-10-17
no, I was viewing / and i right-clicked and went "create folder" :p

---

### Post by llamakc on 2007-10-17
> **ryanVickers said:**
> no, I was viewing / and i right-clicked and went "create folder" :p

Are you using Gnome or KDE? Have you already set-up a launcher for something akin to "gksudo nautilus", or something that grants sudo rights? 

Are you logging into the system as root?

---

### Post by ryanVickers on 2007-10-17
I'm using Gnome and I was logged in as my regular old self, not root, but I can do root things when logged on to the SSH.  I *want* _everyone, regaurdless of DE, or terminal, even if root,_ to have **read-only access!!! ](*,)**

It shouldn't be this hard...  Doesn't someone have a little tool for configuring it!?!

---

### Post by llamakc on 2007-10-17
> **ryanVickers said:**
> I'm using Gnome and I was logged in as my regular old self, not root, but I can do root things when logged on to the SSH.  I *want* _everyone, regaurdless of DE, or terminal, even if root,_ to have **read-only access!!! ](*,)**

It shouldn't be this hard...  Doesn't someone have a little tool for configuring it!?!

Have you ever edited your /etc/sudoers file? Why not just create and use a livecd instead?

---

### Post by llamakc on 2007-10-17
> **ryanVickers said:**
> I'm using Gnome and I was logged in as my regular old self, not root, but I can do root things when logged on to the SSH.  I *want* _everyone, regaurdless of DE, or terminal, even if root,_ to have **read-only access!!! ](*,)**

It shouldn't be this hard...  Doesn't someone have a little tool for configuring it!?!

I'm confused. You said earlier that you created a directory in / with Nautilus, correct? And did this as your regular user. Next you mentioned that when ssh'd in you can create directories in / as your regular user also. Is it both? 

What are the permissions of /

```

ls -l /

```Here's mine:

```

ken@llamakc 11:54:05:/$ ls -l
total 124
drwxr-xr-x   3 root root  4096 2007-10-08 18:57 backup
drwxr-xr-x   2 root root  4096 2007-10-09 21:20 bin
drwxr-xr-x   3 root root  4096 2007-10-15 09:43 boot
lrwxrwxrwx   1 root root    11 2007-04-18 19:50 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13760 2007-10-16 07:20 dev
drwxr-xr-x 165 root root 12288 2007-10-16 19:20 etc
drwxr-xr-x  15 root root  4096 2007-09-30 19:51 home
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 initrd
lrwxrwxrwx   1 root root    33 2007-10-10 15:05 initrd.img -> boot/initrd.img-2.6.22-14-generic
lrwxrwxrwx   1 root root    33 2007-10-08 23:04 initrd.img.old -> boot/initrd.img-2.6.22-13-generic
drwxr-xr-x  17 root root 12288 2007-10-15 09:40 lib
drwx------   2 root root 16384 2007-04-18 19:49 lost+found
drwxr-xr-x   6 root root  4096 2007-10-15 11:47 media
drwxr-xr-x   2 root root  4096 2007-04-12 04:11 mnt
drwxr-xr-x   6 root root  4096 2007-10-13 08:10 opt
dr-xr-xr-x 153 root root     0 2007-10-15 11:44 proc
-rw-r--r--   1 root root 11507 2007-10-15 11:47 razor-agent.log
drwxr-xr-x  30 root root  4096 2007-10-08 23:35 root
drwxr-xr-x   2 root root  4096 2007-10-16 17:34 sbin
drwxr-xr-x   2 root root  4096 2006-11-15 20:44 selinux
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 srv
drwxr-xr-x  12 root root     0 2007-10-15 11:44 sys
drwxrwxrwt  19 root root 12288 2007-10-16 23:26 tmp
drwxr-xr-x  12 root root  4096 2007-06-22 13:54 usr
drwxr-xr-x  17 root root  4096 2007-04-18 20:15 var
drwxrwxrwt   4 root root  4096 2007-05-26 06:13 vm
lrwxrwxrwx   1 root root    30 2007-10-10 15:05 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
lrwxrwxrwx   1 root root    30 2007-10-08 23:04 vmlinuz.old -> boot/vmlinuz-2.6.22-13-generic

```

---

### Post by dfreer on 2007-10-17
> **ryanVickers said:**
> I'm using Gnome and I was logged in as my regular old self, not root, but I can do root things when logged on to the SSH.  I *want* _everyone, regaurdless of DE, or terminal, even if root,_ to have **read-only access!!! ](*,)**

It shouldn't be this hard...  Doesn't someone have a little tool for configuring it!?!

I don't think it's a standard feature, because what's the point of using SSH if you can't modify any files? So the answer may very well be, there is no way to do this. Whatever reason you want users to be able to log in via SSH yet be able to read only, can probably be accomplished by some other tool. That being said, I don't see why you couldn't create a regular user with no home directory and no sudo powers. As long as you don't leave folders writable to the world, this user would not be able to write anything anywhere.

---

### Post by bodhi.zazen on 2007-10-17
> **ryanVickers said:**
> I'm using Gnome and I was logged in as my regular old self, not root, but I can do root things when logged on to the SSH.  I *want* _everyone, regaurdless of DE, or terminal, even if root,_ to have **read-only access!!! ](*,)**

It shouldn't be this hard...  Doesn't someone have a little tool for configuring it!?!

I do not think ssh is the tool you are looking for. If you could give us some general ideas of what you want.

You might for example want to look into restricted shells or mounting a nfs share read only. Are you looking to give access to your whole system / or are you looking to give access to data ?

---

### Post by ryanVickers on 2007-10-17
well, I would like something basically like a samba share (but it will only be used for other Linux computers - I just use samba 'cause it's easier ;)), but I want to be able to access it from any where in the world, and make it read-only no matter what!!! ;)

---

### Post by ryanVickers on 2007-10-17
> **llamakc said:**
> Have you ever edited your /etc/sudoers file? Why not just create and use a livecd instead?

> **llamakc said:**
> I'm confused. You said earlier that you created a directory in / with Nautilus, correct? And did this as your regular user. Next you mentioned that when ssh'd in you can create directories in / as your regular user also. Is it both? 

What are the permissions of /

```

ls -l /

```Here's mine:

```

ken@llamakc 11:54:05:/$ ls -l
total 124
drwxr-xr-x   3 root root  4096 2007-10-08 18:57 backup
drwxr-xr-x   2 root root  4096 2007-10-09 21:20 bin
drwxr-xr-x   3 root root  4096 2007-10-15 09:43 boot
lrwxrwxrwx   1 root root    11 2007-04-18 19:50 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13760 2007-10-16 07:20 dev
drwxr-xr-x 165 root root 12288 2007-10-16 19:20 etc
drwxr-xr-x  15 root root  4096 2007-09-30 19:51 home
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 initrd
lrwxrwxrwx   1 root root    33 2007-10-10 15:05 initrd.img -> boot/initrd.img-2.6.22-14-generic
lrwxrwxrwx   1 root root    33 2007-10-08 23:04 initrd.img.old -> boot/initrd.img-2.6.22-13-generic
drwxr-xr-x  17 root root 12288 2007-10-15 09:40 lib
drwx------   2 root root 16384 2007-04-18 19:49 lost+found
drwxr-xr-x   6 root root  4096 2007-10-15 11:47 media
drwxr-xr-x   2 root root  4096 2007-04-12 04:11 mnt
drwxr-xr-x   6 root root  4096 2007-10-13 08:10 opt
dr-xr-xr-x 153 root root     0 2007-10-15 11:44 proc
-rw-r--r--   1 root root 11507 2007-10-15 11:47 razor-agent.log
drwxr-xr-x  30 root root  4096 2007-10-08 23:35 root
drwxr-xr-x   2 root root  4096 2007-10-16 17:34 sbin
drwxr-xr-x   2 root root  4096 2006-11-15 20:44 selinux
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 srv
drwxr-xr-x  12 root root     0 2007-10-15 11:44 sys
drwxrwxrwt  19 root root 12288 2007-10-16 23:26 tmp
drwxr-xr-x  12 root root  4096 2007-06-22 13:54 usr
drwxr-xr-x  17 root root  4096 2007-04-18 20:15 var
drwxrwxrwt   4 root root  4096 2007-05-26 06:13 vm
lrwxrwxrwx   1 root root    30 2007-10-10 15:05 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
lrwxrwxrwx   1 root root    30 2007-10-08 23:04 vmlinuz.old -> boot/vmlinuz-2.6.22-13-generic

```

As to everything regarding permissions, I'm quite sure I haven't changed anything ;)

---

### Post by llamakc on 2007-10-17
> **ryanVickers said:**
> As to everything regarding permissions, I'm quite sure I haven't changed anything ;)

Yet you claim you can create a new directory in / by both ssh'ing in as USER and by opening Nautilus and creating a directory. Permissions control access to doing that.

Again, would you please list the permissions of / and the contents of /etc/sudoers?

---

### Post by ryanVickers on 2007-10-17
well, actually, perhaps something is up - I just opened regular old nautilus, no root, no SSH, and was able to make a directory at /.  However, any of the sub-folders are definitely locked :p

---

### Post by bodhi.zazen on 2007-10-17
> **ryanVickers said:**
> well, I would like something basically like a samba share (but it will only be used for other Linux computers - I just use samba 'cause it's easier ;)), but I want to be able to access it from any where in the world, and make it read-only no matter what!!! ;)

You could consider making a directory to store your data as ro (ownership of directory and files = root.root and permissions of 744 [or 444 if you prefer] ).

Mount is over sshfs : 

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)
	[http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/](http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/)

On windows use putty or winscp

---

