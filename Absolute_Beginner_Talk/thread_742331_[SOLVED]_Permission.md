---
title: "[SOLVED] Permission"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-04-01
I have a partition where I created to store my music, but not when I try to transfer files into the folder mounted on my desktop it say "You do not have permissions to write to this folder." How do I fix this??

---

### Post by StOoZ on 2008-04-01
use the :
> sudo
command prefixing the command you are using.
for example:
> sudo cp ~/c.mp3 /var/

---

### Post by forrestcupp on 2008-04-01
How many accounts do you have set up?  Are you using an account that was created to not have any administration rights?

---

### Post by sirisaac87 on 2008-04-01
I only have my own account so I guess I am the administrator unless I have to give myself those privileges...but there is only one account.

---

### Post by Xiong Chiamiov on 2008-04-01
Can you take a look at that folder on your desktop and tell us what the permissions are?  (Should be in the properties somewhere, not sure quite how gnome works)

---

### Post by sirisaac87 on 2008-04-01
Owner: root
Folder access: Create and delete files

Group: root
Folder access: access files

Others:
Folder access: access files

**all of these options are greyed out so I cant change them

***I attached a screenshot so maybe you can see what im looking at

---

### Post by forrestcupp on 2008-04-01
You're trying to copy the files somewhere on your root partition.  If you look on the left side of Nautilus, you will see your user name, sirisaac.  Click that to get to your home folder.  You just need to make a new folder in there to copy your files to.  You have all the permissions you need for any folder that is within /home.

---

### Post by sirisaac87 on 2008-04-01
This drive was not partitioned as the root folder, so your saying I cant put things in this partition?  Im sorry im new to this I dont really understand what your saying

---

### Post by t0p on 2008-04-01
> **sirisaac87 said:**
> This drive was not partitioned as the root folder, so your saying I cant put things in this partition?  Im sorry im new to this I dont really understand what your saying

Because the folder is owned by root, you'll need to be root to put things in it.  It would be easier to make a new folder *in your home directory*, so it will have read and write permissions for your user name.

---

### Post by sirisaac87 on 2008-04-01
ok is there a way to change that from root?? Cuz i partitioned that drive for 30gb because i needed it for my music

---

### Post by halitech on 2008-04-01
You should be able to edit fstab to give yourself read/write permissions

---

### Post by diegog on 2008-04-01
I am trying to extract files to /usr/local/src and I get a message about not having rights to write to the specified folder.
Needless to say I am new to linux.
The file is on the desktop.
I tried sudo and also sudo -i and still get this message.
Thanxs

---

### Post by halitech on 2008-04-01
from a terminal 

```
sudo nautilus
```

should allow you to copy files anywhere with nautilus although be forewarned, that opens it with you having root permissions and any mistakes could be fatal.

---

### Post by forrestcupp on 2008-04-01
> **sirisaac87 said:**
> This drive was not partitioned as the root folder, so your saying I cant put things in this partition?  Im sorry im new to this I dont really understand what your saying

Well, in your screen shot the window is blocking your drives, so I want to know which partition you are wanting to use.  Are you totally sure it's not your root drive?

I'm going to tell you something to try, but **you need to be very careful**.  Open a terminal and type
```
gksu nautilus
```
That will open your file browser with super user privileges.  Navigate to that partition/drive and right click it to see if you can change permissions now.  Don't get crazy and go changing a lot of permissions because you could get yourself in trouble.  But if it is just an empty partition that you made for that purpose, it might work.

---

### Post by halitech on 2008-04-01
forrestcupp - thanks for correcting me, forgot about the gksu to run gui apps from the terminal (bloody windows computeers at work)

---

### Post by t0p on 2008-04-01
Just out of interest: what, if anything, is the difference between **gksu** and **gksudo**.  As far as I can tell they do the same thing (let you run a GUI program as super-user); but I figure there must be *some* difference, right?  Right?

---

### Post by forrestcupp on 2008-04-01
> **halitech said:**
> forrestcupp - thanks for correcting me, forgot about the gksu to run gui apps from the terminal (bloody windows computeers at work)
Sorry.  I didn't realize that we posted the same thing and you beat me to it.  Great minds think alike, huh?

> **t0p said:**
> Just out of interest: what, if anything, is the difference between **gksu** and **gksudo**.  As far as I can tell they do the same thing (let you run a GUI program as super-user); but I figure there must be *some* difference, right?  Right?
Some people claim that if you run Nautilus and other programs with sudo instead of gksu, you can totally screw up your root permissions.  So I guess in this case, it's definitely wise for the OP to use **gksu**.  Also if you use gksu, you can close the terminal and it won't close the GUI program, unlike if you use sudo.

Edit:
Now I see that you weren't asking about the difference between gksu and sudo.  So the only difference I know between **gksu** and **gksudo** is that it takes two less letters to type gksu.

---

### Post by bodhi.zazen on 2008-04-01
> **t0p said:**
> Just out of interest: what, if anything, is the difference between **gksu** and **gksudo**.  As far as I can tell they do the same thing (let you run a GUI program as super-user); but I figure there must be *some* difference, right?  Right?

They are the same thing, gksudo is a link to gksu

> ls -l  /usr/bin | grep gksu 

-rwxr-xr-x 1 root   root      23080 2007-09-16 08:42 gksu
lrwxrwxrwx 1 root   root          4 2007-09-16 08:42 gksudo -> gksu

The issues with config files are reviewed here :

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

@ forrestcupp :

You can use disown , nohup, dtach, or sub shells ( ) to keep applications running once you close the terminal.

This thread has a nice review : [http://ubuntuforums.org/showthread.php?p=3208362](http://ubuntuforums.org/showthread.php?p=3208362)

---

### Post by Tatty on 2008-04-01
If all you are doing with that partition is storing music on it then perhaps you could just chown the mount point of your music partition to give yourself ownership... ([http://ubuntuforums.org/showthread.php?t=697118]("http://ubuntuforums.org/showthread.php?t=697118")) If so all you would need to do is find your mount point (i assume it will be /media/Music, but check first) then do this:

```
sudo chown -R USERNAME:GROUP /media/Music
```

**_BUT_** im not sure if that might cause bad things to happen, so i would wait before you do that to see if anyone more knowledgeable replies to shoot it down. ;)

---

### Post by Mildredd on 2008-04-01
> **sirisaac87 said:**
> ok is there a way to change that from root?? Cuz i partitioned that drive for 30gb because i needed it for my music

I have the same problem. I partitioned part of my HD to store documents separately and I don't have permissions on anything in there.

---

### Post by bodhi.zazen on 2008-04-01
If you added a partition , post install, you need to edit fstab.

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by sirisaac87 on 2008-04-01
i put the "gksu nautilus" command in but I could not find the partition that I needed to change permissions on anywhere.  Is there something im doing wrong or is there another solution to fix this problem?

---

### Post by bodhi.zazen on 2008-04-01
> **sirisaac87 said:**
> i put the "gksu nautilus" command in but I could not find the partition that I needed to change permissions on anywhere.  Is there something im doing wrong or is there another solution to fix this problem?

The "fix" is to add a line to fstab, see the link I gave.

If you need help, post the output of 

```
sudo fdisk -l
```

Identify both the partition you are wanting to add and the mount point you are using. The "default" is to mount in /media, but you can use /mnt or any location you like.

---

### Post by sirisaac87 on 2008-04-01
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d3c4d3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         622     4996183+  83  Linux
/dev/sda2             623         746      996030   82  Linux swap / Solaris
/dev/sda3             747        9461    70003237+  83  Linux
/dev/sda4            9462       14593    41222790   83  Linux
sirisaac@bossman07:~$ 


*sda4 is the partition and /media is the mount point

---

### Post by bodhi.zazen on 2008-04-01
OK, you should not use /media, use a directory in media, I will use sda4, you can change the name to what you will.

```
sudo mkdir /media/sda4
sudo umount /dev/sda4
```

The edit fstab

```
gksu gedit /etc/fstab
```

Add this line :

> /dev/sda4 /media/sda4 auto defaults 0 2

Save and exit gedit.

Then 

```
mount /media/sda4
```

We can check permissions with ```
ls -l /media
```

---

### Post by sirisaac87 on 2008-04-01
When i tried this command "mount /media/sda4" this is the message that I got "mount: only root can mount /dev/sda4 on /media/sda4" I dont know if I did something wrong but I followed the exact directions you gave me

---

### Post by bodhi.zazen on 2008-04-01
Try ```
sudo mount /media/sda4
```

Then please post the output of :

```
ls -l /media | grep sda4
```

---

### Post by sirisaac87 on 2008-04-01
drwxr-xr-x 3 root root 4096 2008-03-31 21:31 sda4

That is what came up when I put that command in

---

### Post by bodhi.zazen on 2008-04-01
What is your user name ? Substitute your user (login) name for "user" in the following commands

```
sudo chown -R user.user /media/sda4
sudo chmod 770 /media/sda4
```

That should now work, try it with :

```
umount /media/sda4
mount /media/sda4
```

If you still get an error re: Only root can mount ....

edit fstab again and change "defaults" to user (this time do NOT substitute your user name for user)

---

### Post by sirisaac87 on 2008-04-01
It worked...Thanks I really appreciate it...

---

