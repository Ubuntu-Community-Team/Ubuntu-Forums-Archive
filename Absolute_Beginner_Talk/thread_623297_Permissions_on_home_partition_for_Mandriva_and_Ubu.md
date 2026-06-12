---
title: "Permissions on home partition for Mandriva and Ubuntu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by mike sumner on 2007-11-25
Hi Guys, I am attempting to make serious use of ubuntu for the first time and am struggling with this permission thing.  I have mandriva in another partition and a home partition with music, documents, pictures etc.  Although Ubuntu mounts the drive (partition) at startup, I cant access anything because I dont have permission. I have been looking through the hepl files all evening and I cant find anything about hoe to make a drive available to me!  That's why I came here and spotted your thread. 

I tried to change permissions for the drive and failed as all the options were greyed out,  and the same goes for my music directory.

So how do I get permission to read/write to what is effectively my data drive?
Thanks, Mike

---

### Post by aysiu on 2007-11-25
I wouldn't share a /home partition between two separate distros.

---

### Post by mike sumner on 2007-11-25
OK ive heard that before, but I should surely be able to access my data?

---

### Post by bluepowder7 on 2007-11-25
ya, you should.  first, i'd try to make a separate partition to house shared documents / files, and move your stuff out of /home and into there.

then, you can use aysiu's psychocats instructions to set permissions for ubuntu to access that new partition.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by mike sumner on 2007-11-25
OK, thanks to you both.  When I was dual booting with windoze, that was my setup, with a fat32 partition accessible to all OS's.  Now I have dumped windoze, I have no use for fat32, so I went for the mandriva + separate home partition, which I am mostly happy with.  

I have not seen an explanation why a linux home partition should not be accessed by another distro.  This setup would be particularly useful during the process of evaluating another distro, as I am doing now. 

So I guess I will maybe go back to  the "data drive" setup, but if anyone could explain why this is the best way, I would appreciate it.
Cheers, mike

---

### Post by bluepowder7 on 2007-11-25
there's a ton of config files (hidden) in /home, so you might not want ubuntu to mess around with your mandriva configurations, and you might want them to be completely separate and distinct.

my /home is small, and i don't manually store anything there.  if the OS decides to write stuff there, that's OK with me, but all my downloads, work documents, and tunes are on a separate /media/storage partition.

---

### Post by mike sumner on 2007-11-25
> **bluepowder7 said:**
> there's a ton of config files (hidden) in /home, so you might not want ubuntu to mess around with your mandriva configurations, and you might want them to be completely separate and distinct.

my /home is small, and i don't manually store anything there.  if the OS decides to write stuff there, that's OK with me, but all my downloads, work documents, and tunes are on a separate /media/storage partition.

Thanks bluepowder7, OK I seee now.   That is how I used to work, and it looks like it's the best way if you are dual booting I guess.

---

### Post by mike sumner on 2007-11-27
> **bluepowder7 said:**
> ya, you should.  first, i'd try to make a separate partition to house shared documents / files, and move your stuff out of /home and into there.

then, you can use aysiu's psychocats instructions to set permissions for ubuntu to access that new partition.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

Hi Guys, afraid I am struggling with psycocats instructions. Its not that I dont like using the terminal, but that I don't like blindly following instructions with no indications as to what exactly I am doing. I would feel more comfortable using a gui mainly because I can visualise and understand what is happening, because I am navigating around the file system, so I would actually learn something.  Copying a load of lines of text into the terminal teaches me nothing, especially if I dont know what the various commands like cp and -R do . This is the "tutorial":

So now I'll create a mount point for that partition:
sudo mkdir /storage

Then I'll edit my /etc/fstab file:
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab

Once in there, I should add in this line:
/dev/hda5 /storage ext3 defaults 0 0

Then I can save (Control-X), confirm (Y), and exit (Enter).

Since we've made changes to the /etc/fstab file, we need to have Ubuntu acknowledge those changes:
sudo mount -a

Now I need to give it the proper permissions. Let's just assume, for this example, that my username is marie.
sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

Now the partition is mounted in the /storage folder and is ready for use! 



OK, so if someone could tell me in plain language what the above actually does, I would be a lot happier.
I can see that I have to backup fstab in case I make a cock-up,  and add a line then save fstab but what does the rest of it mean?

All I want to do is have my data partition (sda9) mounted during boot so that I can access and do what I like with its contents. Can't be that difficult can it? I can navigate through the file system and edit files, but I would like to know what I am doing for future reference. 

I hope someone can help me out here with an explanation of what is required and why.  I have spent hours trying to find this out from the wiki and forum etc.

Cheers, Mike

---

### Post by bodhi.zazen on 2007-11-27
> **mike sumner said:**
> Hi Guys, afraid I am struggling with psycocats instructions. Its not that I dont like using the terminal, but that I don't like blindly following instructions with no indications as to what exactly I am doing. I would feel more comfortable using a gui mainly because I can visualise and understand what is happening, because I am navigating around the file system, so I would actually learn something.  Copying a load of lines of text into the terminal teaches me nothing, especially if I dont know what the various commands like cp and -R do . This is the "tutorial":

You might want to see this link : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

> So now I'll create a mount point for that partition:
sudo mkdir /storage

hard drives are devices and /dev/hda5 is the raw hard drive. The operating system needs to prepair the drive for use, AKA mount the partition. The mount point is where is is mounted.

> Then I'll edit my /etc/fstab file:
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab

Once in there, I should add in this line:
/dev/hda5 /storage ext3 defaults 0 0

/etc/fstab is the configuration file for mounting. Take a peek at the link I gave you.

If a partition is not listed in fstab, you can always manually mount it as root.

make a mount point and mount with :

```
mount /dev/hda5 /storage
```

FYI the "traditional" location to mount would be /media/storage or /mnt/storage, but /storage is fine.

> Then I can save (Control-X), confirm (Y), and exit (Enter).

nano is a editor and those are the commands to close and save your changes. If you prefer you can use gedit: ```
gksu gedit /etc/fstab
```

> Since we've made changes to the /etc/fstab file, we need to have Ubuntu acknowledge those changes:
sudo mount -a

yes, mount -a mounts all  partitions in fstab.

You could also just

```
mount /storage
```

> Now I need to give it the proper permissions. Let's just assume, for this example, that my username is marie.
sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage

permissions determine who may access a file or directory. Setting permissions depends on file type (ie FAT/NTFS is different for linux native file systems). See the link I gave you.

Her is one on permissions : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

> Now the partition is mounted in the /storage folder and is ready for use! 

\o/

---

### Post by bodhi.zazen on 2007-11-27
> **mike sumner said:**
> Hi Guys, I am attempting to make serious use of ubuntu for the first time and am struggling with this permission thing.  I have mandriva in another partition and a home partition with music, documents, pictures etc.  Although Ubuntu mounts the drive (partition) at startup, I cant access anything because I dont have permission. I have been looking through the hepl files all evening and I cant find anything about hoe to make a drive available to me!  That's why I came here and spotted your thread. 

I tried to change permissions for the drive and failed as all the options were greyed out,  and the same goes for my music directory.

So how do I get permission to read/write to what is effectively my data drive?
Thanks, Mike

Well, this is the problem you run into with sharing /home across distro's :(

My guess is that the uid is different. The first user on Debian systems is usually 1000. The first user on rpm systems is 500

so although you know your user by your log-in name, the system used uid #

Worse, sometimes when you try to change permissions you will get an "unknown user" error.

to check just do ls -l

You should see 

user:group <file>

If you have this type of problem you will stat to see numbers rather then users

500:500 <file>

The best solution, IMO, is a /data partition, but you can still have problems with permissions.

The solution I use is to have the permissions of the /data be root:users with permissions of 770.

This seems to work well across distros fairly well, but will not work for /home.

FYI you run across this all the time if you chroot (usually for development).

---

### Post by mike sumner on 2007-11-27
thanks for your help bodhi.zazen, I am just digesting all the info. 
Mike

---

### Post by mike sumner on 2007-11-28
Thanks bodhi.zazen, I now have my data drive fully accessible.  Havent rebooted yet so not sure if the permission will still be there after a reboot. Also need to figure how to have it mount during boot. Can I drop a mount line in somewhere?  I seem to remember doing that when I was using Puppy, but I cant remember what the file was, and ubuntu probably has a different system anyway.

Thanks again, Mike

---

### Post by bodhi.zazen on 2007-11-28
To have your hard drive / partition automatically mount at boot, all you need to add is add a line in /etc/fstab.

If you use "auto" in the options column it will auto mount.

---

### Post by mike sumner on 2007-11-28
That's working fine now thanks.
I am now trying to put a symlink to it on the desktop, but everything I try comes to nought, cos of bloody permissions again.  I seem to be able to create a folder on the desktop which   gives me the option to link but even using gksudo to look at the storage directory, I can't seem to create a symlink to the desktop. It seems that everything that I want to do is thwarted by ubuntu for no good reason that I can see.  This is going to take some getting used to!
Hints would be greatly appreciated......
Cheers, Mike

---

### Post by cherry316316 on 2007-11-28
I had similar problem with windows partition
I changed the line in fstab from

/dev/sda6    /media/e     vfat     defaults,utf8,umask=007,gid=46     0     0


to

/dev/sda6  /media/e  vfat   auto,rw,users,uid=1000,gid=1000,utf8,umask=000,exec,sync    0    0


now, its working fine :)

---

### Post by mike sumner on 2007-11-28
My data drive is ext3. How would that affect things?

---

