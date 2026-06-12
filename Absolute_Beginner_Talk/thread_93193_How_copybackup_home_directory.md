---
title: "How copy/backup home directory?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by buzst on 2005-11-21
I'm trying to copy my home directory (using gnome) to my account on my server machine (which has the same name and is a member of the same group), many of the user and systems files  don't copy (no error message) for what i suspect are permission problems. I don't want to change permissions on the system files so i'm thinking that I should create an archive of the directory and copy it to the server.

Is this the best way or is there a better way? If I create the achive in gnome will the system files that are being used go into the archive or do I need to become root and create the archive from the command line?

Thanks for the help

---

### Post by Kvark on 2005-11-21
Did you remember to copy all the hidden files too? (Select "Show hidden files" in the View menu to see them.)

---

### Post by buzst on 2005-11-21
I did remember the hidden files but again most of the will not copy due to what I think are permission issues....

---

### Post by dubz on 2005-11-21
the best way to backup would be using tar.
In the console type 
tar cf dubzs_home.tar  /home/dubz >> In my case.

you might have to pass -R to make it act recursively.

to extract 
tar xf <new_dir_name>.tar 


hope this helped.

thanks.

---

### Post by buzst on 2005-11-21
I killed tar after it spent 4 hours and never finished a 12 gig home directory archive. I thought I need to be root to archive home so I exited gnome and did sudo -s to become root prior to making the archive. I'm thinking though that sudo -s does not make me root, but instead gives me root access, though I am still in my home directory and this may be the problem. any thoughts or suggestion?

---

### Post by dubz on 2005-11-22
you can always do it graphically using file-roller.It is a very good app.

---

### Post by schdefan on 2005-11-22
Hi!
I use rsync to clone an entire partition to another harddisk. An ubuntu 5.10 installation with almost 2GB of disk space took me 10 minutes to copy.

So to coy your home directory to your server you can mount the server partition via NFS to your machine and then use ```
#rsync -avxP /home/you /mnt/nfs/newhome
```

Depending on the amount of data on the source partition, this could take hours. But the "P" option makes rsync verbosely show the overall progress of the operation, so that you aren't troubled by uncertain wonders.

For installation NFS read [here]("https://www.ubuntulinux.org/support/documentation/faq/nfs-server")
and in the forum there are some posts about nfs issue 
[http://ubuntuforums.org/showthread.php?t=88378&highlight=nfs]("http://ubuntuforums.org/showthread.php?t=88378&highlight=nfs")

Maybe it seems a little bit complecated but it is a very fast way. 

schdefan

---

### Post by buzst on 2005-11-22
Hi,
Thanks for the reply. I tryed rsync (using samba not nfs) and while it transfered user data just fine the transfer errored on many system and application files. I'm assuming that is because they were in use. I'm thinking the only way to do the copy is to set up a root user account, but ubuntu suggests that we not do this,  ...so any more suggestions?  Please....

---

### Post by seatea on 2005-11-22
There is a lengthy  discussion of backuppc in  the  *Debian Gnu/Linux 3.1 Bible* that might be what you are looking  for. I suspect that there  are online  references to backuppc use as well. I find  the man pages can be  a little cryptic to use as the sole  source, but they will have information on its use as well.

---

### Post by schdefan on 2005-11-23
Boot from a live CD and mount the 2 partition. The files of your home partition are not in use then.

---

### Post by Original Brownster on 2005-11-23
[QUOTE=buzst]I'm trying to copy my home directory (using gnome) to my account on my server machine (which has the same name and is a member of the same group), many of the user and systems files  don't copy (no error message) for what i suspect are permission problems. I don't want to change permissions on the system files so i'm thinking that I should create an archive of the directory and copy it to the server.

Is this the best way or is there a better way? If I create the achive in gnome will the system files that are being used go into the archive or do I need to become root and create the archive from the command line?

Thanks for the help[/QUOTE]

Hi,
I'm assuming your server is linux, one thing to remember when copying files from one *nix machine to another is that although the username maybe the same, the actual system id for that user will be different in most cases. 
This is because user accounts are created with an auto incrementing id number at the time created. This might not be your problem but I suspect it maybe. you can check this by looking at the /etc/passwd file and finding the numeric id after your name and comparing to the server.

HTH

---

### Post by dixonstalbert on 2005-11-23
[QUOTE=buzst]I killed tar after it spent 4 hours and never finished a 12 gig home directory archive. /QUOTE]

hello

I am wondering if your tar file was trying to back itself up?

You can create a tar file inside your home directory (you have write permissions in your home  dir so you do not have to go root or change dir permissions), but you must explicitly exclude the tar file you are creating like this:

~> tar cvpzf  todayshomebackup.tgz --exclude=/home/{whateverisyourusername}/todayshomebackup.tgz /home/{whateverisyourusername}/

note that the exclude statement has to come before the source or include list. also note tar will copy hidden files and subdirectory by default. (sorry I dont know how to make code appear in separate window, there should be a space between ...tgz and /home...) 

I backup my home file regularly this way, even with firefox and nautilus running at the same time so I dont think tar is bothered with what is open or not. 
If you do it this way then you could copy the compressed file across your network and not the whole 12 gig. -hope this helps

---

### Post by jfryman on 2005-11-23
[QUOTE=dubz]the best way to backup would be using tar.
In the console type 
tar cf dubzs_home.tar  /home/dubz >> In my case.

you might have to pass -R to make it act recursively.

to extract 
tar xf <new_dir_name>.tar 


hope this helped.

thanks.[/QUOTE]

This is probably one of the better ways to backup your home directory. From there, you can set up with your server automated transfers using SSH and trusted keys. Just a thought.

In addition, when doing a tar backup, it's also good to add the following flags : p & (z/j)

-p will preserve the original file permissions
-z will compress using gzip (medium cpu usage, but less space)
-j will compress using bzip2 (lots of cpu, even less space)
-v verbose output (optional)

So, a full backup would look something like this:
```

[<user>]$ tar c(z/j)vf <name_of_archive>.tar.(gz/bz2) /home/<username>

```
and an extract would be
```

[<user>]$ tar x(z/j)vf <name_of_archive>.tar.(gz/bz2) 

```

Hope that helps!

-James

---

### Post by d1337 on 2005-11-23
Methink James' process should work quite well.

I have done quite a few backups as well as restores and have always referred to  [this wiki]("https://wiki.ubuntu.com/BackupYourSystem") entry.  I am an ubernoobie and don't always understand each option etc from Linux In A Nutshell, but have been rather successful with the directions provided in the preceeding link.

But, again, jfryman's method should work just as well.  Most command line methods are quite similar, mostly just different in their explanation.

---

### Post by buzst on 2005-11-24
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by buzst on 2005-11-24
thank you for the advice i'll try again. never did think about the home directory trying to back itself up.....

Buzst

---

