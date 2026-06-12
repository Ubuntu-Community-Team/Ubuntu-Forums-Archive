---
title: "Backup over LAN for a noob"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by morticiaskeeper on 2007-10-17
Hi All

I moved from XP to Gutsy last weekend, but can't complete the transfer until I sort out document backups.  Tearing out my hair has left me bald:)

I would like to automatically backup my documents to a disk on a NASLite server on my home LAN.   I would also like to backup the same files to a FAT32 drive on the pc.

Being brought up on DOS, I'm at a loss with the Linux way of addressing, hence this post.

The address I want to backup to is "192.168.1.101/disk-3/ubuntu/backup".

What would be the best app to use for this?

How do I do it?

I've tried Home User Backup, but don't seem to be getting anywhere, although I have no problems accessing files on the server.

TIA

Paul

---

### Post by Ek0nomik on 2007-10-17
Anytime I need to back something up, I transfer all my files via SSH to my backup computer.

---

### Post by maybeway36 on 2007-10-17
What kind of file-sharing is it? Does it use SMB?
If it does, then you might need to install Konqueror because Nautilus is really bad at SMB shares.

---

### Post by llamakc on 2007-10-17
Since you want to automate the backup, you can mount that SMB share at boot.

I backup to a 500G Buffalo NAS, and have this in my /etc/fstab:

```

//192.168.X.XXX/share   /media/Buffalo  smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0       0

```

Which mounts it at boot (or after you tailor the line to your liking run "sudo mount -a"). The uid used is my current Ubuntu user's uid. It also mounts the share at /media/Buffalo, which is where I copy stuff I need backed up.

Next, sbackup provides all of the functionality you need, and is in the repos. Either that or you could learn about creating a script that does precisely what you want. HTH.

---

### Post by reckless2k2 on 2007-10-17
500GB NAS...i'm jealous. I only have a 250GB linkstation. geez i've gotta get something bigger. haha

---

### Post by morticiaskeeper on 2007-10-17
Thanks for all the replies.

I'm such a noob with this, but I'm pretty sure it's SMB.

The address I go to when exploring the directory is: *smb://192.168.1.101/Disk-3/ubuntu/backup*  I presume this is SMB:confused:

As for a NAS box, I bought NASLite+ and installed it on a very old pc that I rescued from a skip.  Total cost = £15!

---

### Post by morticiaskeeper on 2007-10-17
I've just tried editing the etc/fstab   but it won't let me save the file, saying I do not have permission.   

Sbackup says the same.

---

### Post by llamakc on 2007-10-17
That's because you are attempting to edit system files as a user. You need to invoke "sudo".

Here's a page that explains it:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

After reading that you'll realize that you want to run:

```

sudo gedit /etc/fstab

```

I STRONGLY recommend you back up the current /etc/fstab FIRST.

```

sudo cp /etc/fstab /etc/fstab-backup

```

After you have successfully edited /etc/fstab with sudo, you can mount it.

---

### Post by disasm on 2007-10-17
After you get it mounted:

rsync -a /path/to/source /path/to/dest will work.

If you want it to remove from the backup files that have been deleted change it to:
rsync -a --delete /path/to/source /path/to/dest

Choose which one you want, and put it in a crontab like so:

crontab -e

put this in file to backup midnight daily:
0 0 * * *      rsync -a --delete /path/to/source /path/to/dest

Sam

---

### Post by morticiaskeeper on 2007-10-17
I've worked out how to edit the fstab file using sudo gedit and have added the following: **//192.168.1.101/disk-3/ubuntu/backup  smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0       0**  

The file has been saved and I have rebooted the pc.

I then went back into sbackup as this seems to be the app to do what I want.  I selected the files to backup. Under the **Destination** tab, I've selected **Use a remote directory (SSH or FTP)**.  In the path box I've typed **smb://192.168.1.101/disk-3/ubuntu/backup**.

After running the test, the error message reads:  **The selected destination is not writtable with current permissions. The backups can not be written there.**

I've got the feeling I'm getting close #-o

---

### Post by llamakc on 2007-10-17
Your fstab line doesn't have WHERE you mounted it to. Copy and paste that line precisely as you currently have it.

---

### Post by morticiaskeeper on 2007-10-17
Pasted from fstab:

//192.168.1.101/disk-3/ubuntu/backup  smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0       0

Paul

---

### Post by timcredible on 2007-10-17
once you have it mounted, i would suggest using grsync ( a gui frontend for rsync) since it's a little easier imho than command line.  grsync is in synaptic.

---

### Post by llamakc on 2007-10-17
> **morticiaskeeper said:**
> Pasted from fstab:

//192.168.1.101/disk-3/ubuntu/backup  /NAME/OF/MOUNT/POINT smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0       0

Paul

Where I wrote /NAME/OF/MOUNT/POINT you need to establish WHERE you want the share to mount to. What this means is when you issue the "ls" command or view directories in Nautilus, you'll see the directory and its contents listed (after it's mounted).

For example, I used /media/Buffalo

You can use whatever you want. Here's how I solved it:

```

//192.168.1.106/share   /media/Buffalo  smbfs   guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0       0

```

```

ken@llamakc 01:49:01:~$ cd /media
ken@llamakc 01:50:36:/media$ ls -l
total 16
drwxr-xr-x 1 ken  root 4096 2007-10-15 11:47 Buffalo
lrwxrwxrwx 1 root root    6 2007-04-18 19:50 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-04-18 19:50 cdrom0
drwxr-xr-x 7 root root 4096 2007-03-06 17:42 hdc1
drwxr-xr-x 4 root root 4096 2007-06-13 18:37 hdc2

```

To get my 'username' of "ken" listed as owner of Buffalo, I ran:

```

cd media

sudo chown ken:root Buffalo

```

HTH

---

### Post by morticiaskeeper on 2007-10-17
Told you I didn't have a clue!!!!

So if I change the line to:

**//192.168.1.101/disk-3/ubuntu/backup /home/servbac smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,uni code 0 0**

It will mount the network folder to the **servbac** directory in **home** ?

Still liking Ubuntu, just getting a bit confused :-)

---

### Post by Tom Mann on 2007-10-17
> **morticiaskeeper said:**
> Told you I didn't have a clue!!!!

So if I change the line to:

**//192.168.1.101/disk-3/ubuntu/backup /home/servbac smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,uni code 0 0**

It will mount the network folder to the **servbac** directory in **home** ?

Still liking Ubuntu, just getting a bit confused :-)

You're nearly there...

Not to steal llamakc's thunder (sorry) - just run the following:

```

cd /media
sudo chown /media/servbac $USERNAME:root

```

if that doesn't work do the above with 'users' (less secure) instead of root.

For understanding's sake, I'm pointing the current directory to where all your external media is held in Linux, then changing the ownership of servbac to $USERNAME user, and the root group, so no other users can access the box.

Hint: go into a console and type ```
echo $USERNAME
```

---

### Post by llamakc on 2007-10-17
That's a great point, Tom. I'm going to modify my setup that way also. Thanks.

---

### Post by morticiaskeeper on 2007-10-17
So, I've changed the fstab to include:

**//192.168.1.101/disk-3/ubuntu/backup /home/paul/servbac smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,uni code 0 0**

Then I enter the terminal and do this:

paul@paul-desktop:~$ **cd /media**
paul@paul-desktop:/media$ **sudo chown /media/servbac $paul:root**

And get this:

chown:** `/media/servbac': invalid user**


The hairs getting thinner!!  (and the IQ)

---

### Post by Dr Small on 2007-10-17
Remove the dollar sign from $paul

---

### Post by morticiaskeeper on 2007-10-17
Tried that!!

paul@paul-desktop:~$ cd /media
paul@paul-desktop:/media$ sudo chown /media/servbac $paul:root
chown: `/media/servbac': invalid user



Looking around the file explorer, I noticed a directory called **smb:**  In that is a sequence of directories that lead to where I want.  Have I already found what I'm looking for?

If so, how come sbackup still claims I don't have permissions?

Paul

---

### Post by morticiaskeeper on 2007-10-17
Carrying on with my experiements, i did a backup through Sbackup to smb:192.168.1.101/disk-3/ubuntu/backup.

I checked the archive went to the directory.

I then used an XP laptop to check the server, but the file wasnt there.  I put a test file into the directory using the XP pc.  Looking from the smb: directory path, it wasn't there, but the archive was.

Navigating from the desktop link to the server, I could see the XP test file.

This leads me to think that the destination I navigated to via the smb: route is not the server!

I think an early night is on the cards](*,)

---

### Post by morticiaskeeper on 2007-10-18
A bit more research shows that my server is NFS/HTTP/FTP enabled - [http://www.serverelements.com/naslite-plus.php]("http://www.serverelements.com/naslite-plus.php")

I presume that the fstab edits I did yesterday are wrong as I thought it was a samba server.

If I can't get backups working directly to the server, is there a way I can set a timed task to copy the contents of a directory to the server?

Off to the library tomorrow to find a linux book!!!

---

### Post by civic_si on 2007-10-18
> **disasm said:**
> After you get it mounted:

rsync -a /path/to/source /path/to/dest will work.

If you want it to remove from the backup files that have been deleted change it to:
rsync -a --delete /path/to/source /path/to/dest

Choose which one you want, and put it in a crontab like so:

crontab -e

put this in file to backup midnight daily:
0 0 * * *      rsync -a --delete /path/to/source /path/to/dest

Sam

I also use rsync to back up works well. good luck

---

### Post by disasm on 2007-10-18
> **morticiaskeeper said:**
> A bit more research shows that my server is NFS/HTTP/FTP enabled - [http://www.serverelements.com/naslite-plus.php]("http://www.serverelements.com/naslite-plus.php")

I presume that the fstab edits I did yesterday are wrong as I thought it was a samba server.

If I can't get backups working directly to the server, is there a way I can set a timed task to copy the contents of a directory to the server?

Off to the library tomorrow to find a linux book!!!

apt-get install nfs-common

this will work in fstab:

servername:/serverpath                /path/to/mount            nfs             rw,udp                0            0

---

### Post by morticiaskeeper on 2007-10-25
After various tries, I phoned a mate who attempted to talk me through things, but even he gave up in the end!!

I then tried KBackup and directed it to the server via FTP and every works fine.   The only problem is that it isn't automatic, I have to iniate things.

So I tried SBackup again, copying the url that I know works, and it doesn't!!

So I run KBackup every morning just before I head to work.

Thanks for all your help guys, although we didn't have success, I've learnt a bit about Linux.

---

### Post by Tom Mann on 2007-11-02
> **morticiaskeeper said:**
> Tried that!!

paul@paul-desktop:~$ cd /media
paul@paul-desktop:/media$ sudo chown /media/servbac $paul:root
chown: `/media/servbac': invalid user



Looking around the file explorer, I noticed a directory called **smb:**  In that is a sequence of directories that lead to where I want.  Have I already found what I'm looking for?

If so, how come sbackup still claims I don't have permissions?

Paul

Sorry about the long delay, You've put in $paul. It should be $USERNAME
Don't substitute your username in :)

---

