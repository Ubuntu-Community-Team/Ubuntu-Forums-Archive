---
title: "Lost my hostname, made a new one and now stucked..."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Vesukka on 2007-08-01
Hello!

Somehow (I really have no idea how it happended!) I had lost my hostname in Ubuntu Feisty. As soon I noticed it I made a new one, rebooted and noticed that I couldn't get to 'Users & groups' anymore. Ubuntu logs in as root and I have to change it somehow. What can I do?

---

### Post by bodhi.zazen on 2007-08-01
LOL

Lost your host name ? That sounds might odd ... What were you doing and what file were you editing ? Did you save a backup ?

Open a terminal

Enter this command to see your current hostname :
```
hostname
```

To change you hostname,
```
sudo hostname <new_naem>
```

where <new_naem> is your new host name.

IMO best reboot at that point ...

FYI you hostname is in BOTH Change both /etc/hosts and /etc/hostname

---

### Post by Vesukka on 2007-08-01
I really didn't do anything. It was just gone when I turned my computer on. I have made a new hostname already, now it's okay. But Ubuntu starts as 'root' and I can't access to 'Users & groups' as root. And with my own username Users & group doesn't even works.

---

### Post by lambros on 2007-08-01
> **Vesukka said:**
> Hello!

Somehow (I really have no idea how it happended!) I had lost my hostname in Ubuntu Feisty. As soon I noticed it I made a new one, rebooted and noticed that I couldn't get to 'Users & groups' anymore. Ubuntu logs in as root and I have to change it somehow. What can I do?

I've seen these symptoms come up a few times now.  This kind of thing can happen when, for whatever reason, the /home filesystem fails to mount.

Did you get some error-messages about failing to find /home/yourusername, and logging in as /root instead?

Try using the 'ls' command to find out if your /home and /home/yourusername folders exist.

You might need to run 'fsck' on whatever drive holds your /home directory.  Or maybe you have a loose physical connection on your hard drive?

Some more details would be helpful.  Are you running a dual-boot?  Have you set up your /home on a separate drive or partition?  Are you sure you did nothing unusual to trigger this?  Did you install any kind of drive-management software in Windows, for example?

[Edit] Another thought occurred to me: did you edit your /etc/fstab file by any chance?  I can see how a bad edit of this file might cause these symptoms.

Lambros

---

### Post by Vesukka on 2007-08-01
All the folders of mine seems to be ok, same as all other files... I have single-boot system and not much extras installed yet. It started suddenly, I haven't do anything abnormal or got any error messages.

Now I  succeed in getting to Users & groups as 'root'. I think that's it... There is no users or groups and I can't made any! Think it's time to reinstall...?

EDIT: And I don't touch anything which I don't know about.

---

### Post by lambros on 2007-08-02
> **Vesukka said:**
> All the folders of mine seems to be ok, same as all other files... I have single-boot system and not much extras installed yet. It started suddenly, I haven't do anything abnormal or got any error messages.

Now I  succeed in getting to Users & groups as 'root'. I think that's it... There is no users or groups and I can't made any! Think it's time to reinstall...?

EDIT: And I don't touch anything which I don't know about.

This is very strange.  Your hostname is stored in the file /etc/hostname .  Your user account information is stored in the file /etc/passwd .  Your user groups are stored in the file /etc/groups .  And you say all of these went missing?  Do you spot the common connection with these files?  :)

I'm beginning to wonder if the filesystem with the /etc folder got corrupted somehow?  Unless anyone has any better suggestions, I'm going to go out on a limb here, and suggest you're better off doing a full reinstall?  It might be worth having a look at some of these files, especially /etc/passwd .  For comparison, mine looks like this:

```
ll@lambros-home:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
postfix:x:100:103::/var/spool/postfix:/bin/false
syslog:x:105:105::/home/syslog:/bin/false
klog:x:106:106::/home/klog:/bin/false
ll:x:1000:1000:Lambros Lambrou,,,:/home/ll:/bin/bash
messagebus:x:101:110::/var/run/dbus:/bin/false
... lots more snipped ...

```

Lambros

---

### Post by Raineer on 2007-08-02
If you have a seperate /home partition you can reinstall without much worry at all.  If not then if you choose to reinstall you can partition differently :)

I don't have any input on the hostname issue, never seen that one

---

### Post by Vesukka on 2007-08-03
> **lambros said:**
> 
I'm beginning to wonder if the filesystem with the /etc folder got corrupted somehow?  Unless anyone has any better suggestions, I'm going to go out on a limb here, and suggest you're better off doing a full reinstall?

It came to my mind at the very beginning. But it really SEEMS that everything in etc is ok, files and folders... Fortunately I haven't got much to lose because Ubuntu was installed just few weeks ago, and most of my important files lies on the other disk. And of course I can copy files to another place if it's necessary. Just hate to install again all plugins etc.

Thank all of you for help!

---

