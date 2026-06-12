---
title: "Writing documents to HDD"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-03
I just finished setting up a tri-boot system.  2 questions really for this post.

1.  While in Ubunto, I can see on my desktop the following:

-Local Disk
-SDA 4
-SDA 5

SDA 4 is a 9 gb fat32 partition I made so that I could send files from xp to ubunto.

SDA 5 is an install of mandrake.  I don't like the fact that I can see this hard drive, because what if I accidently wrote to it?  Does Ubuntu just see it as another place to store data since they are both ext3 ?  

2.  I try to make new documents, but I am unable to move any documents into  any of the folders (from the desktop).  It says I can't because I am not the owner...?  Are the permissions just set too high?  Also, which folder should I store my stuff in.  I see too many folders (DOCS vs Documents & Settings)  If its Docs & settings should I then put it under  All users,  defualt user, local service,  root???  I am the only one that uses this computer. 

Please help me.  I know that I am asking a lot in this one post, but I'm just so excited that I got all 3 OS's running together on my first try.  I tried configuring them with GRUB but got lost, and ended up doing it with lilo.  It was quite the learning experience doing it in lilo from a shell in Mandy.  Thank you very much!

---

### Post by aysiu on 2006-09-03
This should help you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For the Mandrake drive, just remove its entry from your /etc/fstab file. ```
sudo nano -B /etc/fstab
``` Find the line that refers to /dev/sda5 and put a # sign at the beginning of the line. Then save (Control-X, Y, Enter).

---

### Post by macdo on 2006-09-03
You 'live' in your home folder: /home/yourusername. That's the place to keep stuff! A lot of your config files are in there too, but they'll be in hidden folders, so you'll only see them if you want to (press ctrl-H). 
If you don't want to be able to write to the partition where Mandrake is, then simply change the permissions on it. I suggest that you make it read-only except for root, who should be read-write. That way, you'll still be able to put things there if  you need to. Alternatively, you could remove the link from your desktop, for example, or stop the partition from auto-mounting.
HTH

---

### Post by 3rr0r on 2006-09-03
> **macdo said:**
> You 'live' in your home folder: /home/yourusername. That's the place to keep stuff! A lot of your config files are in there too, but they'll be in hidden folders, so you'll only see them if you want to (press ctrl-H). 
If you don't want to be able to write to the partition where Mandrake is, then simply change the permissions on it. I suggest that you make it read-only except for root, who should be read-write. That way, you'll still be able to put things there if  you need to. Alternatively, you could remove the link from your desktop, for example, or stop the partition from auto-mounting.
HTH


How would I go about changing the permissions to read-only, and setting the root (of mandy?) to read-write ?

---

### Post by whizbaby on 2006-09-03
open-terminal
**man chmod**

(I can suggest making a test file (**touch tst**) and experiment a little with that. Permissions are displayed with **ls -l** command)

setting something to rw-mode
**chmod 600 *file_which_belongs_to_me***

if file doesn't belong to you use sudo of course...

---

### Post by macdo on 2006-09-03
In this case, if your Mandrake partition is mounted at /media/sda5:
```
sudo chown -R root:root /media/sda5
sudo chmod -R 644 /media/sda5
```
The first command changes the ownership of the folders, the second modifies the permissions.
Do that in Ubuntu - that's where you don't want to write from!

---

### Post by 3rr0r on 2006-09-03
I typed your commands exactly as put macdo.  Only thing different was after the first command, it prompted me for the password (entering sudo), but that was it.  Now, since I've hidden SDA5 from me, in fstab (used the #), am I still able to write to it?

I imagine I will only be able to do that via terminal since I can't graphically access it right?

---

### Post by whizbaby on 2006-09-03
Sure, with root privileges you will ALWAYS be able to write to a mountable drive. If you don't want to see it, comment it out (aysiu said howto do it) in /etc/fstab and type **mount -a** in terminal (of course terminal. Start liking the idea of having the option to talk to your computer instead of just clicking it)

---

### Post by whizbaby on 2006-09-03
> **whizbaby said:**
> Sure, with root privileges you will ALWAYS be able to write to a mountable drive. If you don't want to see it, comment it out (aysiu said howto do it) in /etc/fstab and type **mount -a** in terminal (of course terminal. Start liking the idea of having the option to talk to your computer instead of just clicking it)
Oh, you did already...
I don't know if there's a non-terminal way to add the drive again, I don't think so (*thats* what you wanted to know, didn't sleep so much)

---

### Post by macdo on 2006-09-03
I'm not sure why you'd want to not have it in the fstab - after all, you can only write to it as root now, so accidents are unlikely...

---

