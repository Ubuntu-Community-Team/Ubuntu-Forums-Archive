---
title: "Fiesty Fawn Lost in The Wilderness"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by A Zen Roshi on 2007-08-01
OK - the quick and drity of it is:

When i try to log in i get the following:

/home/username does not appear to exist do you want to log in with the root directory as your home directory?  It is unlikely anything will work unless you use a failsafe session.

I change the session to failsafe - enter my username and password - then i get a message:

User's $Home/.dmrc file is being ignored.  This revents default session and language from being saved.  File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users.

I press OK and then i get the following message:

GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact System Adminstrator.

:))

I have logged in - i have relaxed permissions to 2, i have deleted my /home/username, i have created a new root user, i have chmod 755 /home/newusername.  :))

I can't seem to Create a New ADMIN USER - Root User and just log in at the next reboot.  Hope the terminology is correct?

Must I reinstall?

Must I give up? :)) LOL [j/k]

NO, I must have your help.  

thanky

---

### Post by Rocket2DMn on 2007-08-01
It sounds like the problem is that your home folder doesn't have the correct permissions on it.  Since you can't login with that username, you need to login as root and do the following
```
chown -R username /home/username
chmod 700 /home/username
chmod 644 /home/username/.dmrc
```
You may have to add your username back to the sudoers so you can use the "sudo" command.  I don't know how to do that off that top of my head, but I'll look it up.

---

### Post by Rocket2DMn on 2007-08-01
To give a user sudo privileges: [https://help.ubuntu.com/community/RootSudo#head-3f8a7e5ae5fe6b048ffecef0bf38c811eede7aec](https://help.ubuntu.com/community/RootSudo#head-3f8a7e5ae5fe6b048ffecef0bf38c811eede7aec)
While logged in as root (since you can't sudo yet)
```
adduser username admin
```

PS: If you are unable to login as root, you will need to boot from the LiveCD to perform these tasks

---

### Post by A Zen Roshi on 2007-08-01
Thank you for your interest in my problem.  I did as above with the following error messages upon reboot / login:

etc/gdm/Presession/Default . . .
mkdtemp:Private Socket dir: Permission Denied

then:

Could not open or create file "(null)" this indicates that there may be a problem with your configuration [ya think?] as many programs will need to create files in your home directory.

The error was "failed to create file /tmp/gconf-test-locking-file DTVOVT: Permission Denied" (errno=2)

If anyone can foul things up -it's me.  I should work in q/c for software developers. lol :)

I'm having so much fun - I should be paying entertainment tax. :)

thanky

---

### Post by Rocket2DMn on 2007-08-01
OK, so you tried logging in using "root" as the username and your regular password, and it didn't let you in.

Try booting from the LiveCD and performing the commands I listed.  If it tells you the /home/username directory isn't there, create it.  We will use sudo since we are running from the LiveCD
```
sudo chown -R username /home/username
[I][sudo mkdir /home/username
sudo chown -R username /home/username][/I]
sudo chmod 700 /home/username
sudo chmod 644 /home/username/.dmrc
sudo adduser username admin
```

If this doesn't work, you might need to just create a completely new username while running from the LiveCD, then give that user sudo privileges with the last command.
Here is how you can add a new user: [https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by asmoore82 on 2007-08-01
how did this problem start??

did you just install ubuntu?

---

### Post by A Zen Roshi on 2007-08-01
Ubuntu 7.04 was installed 07/2007 - The problem began after installing a windows 2000 program allowing me to assign a logical drive letter to my linux partitions - i could view, copy, move files (.jpg mostly) to my windows folders.  I logged into Ubuntu and was bombarded with error messages.  Ubuntu is on a partition along with windows 2000.  The Grub loader allows me to boot to ubuntu, recovery, windows 2000 or windows 2000 recovery console.

Doctor? Shouldn't I be the one on the couch?

thanky

---

### Post by Rocket2DMn on 2007-08-01
You mean they are on different partitions that reside on the same physical hard drive.
It's possible that this program has somehow corrupted the ext3 partition that Ubuntu lives on.  What program was this?
If this turns out to be the case and my above suggestions don't work, a reinstallation may be in order.  It could be possible for you to recover some data from your Ubuntu partition using that windows 2000 program.

---

### Post by A Zen Roshi on 2007-08-01
Alas, no live cd.  That is a different story.  I am downloading it.  It should be ready in about 18 hrs. 34 mins.

I have added different user names, deleted old user names, deleted user folders, given new users admin privs., changed the group, chmod 700 /home/user, etc.

I remain optimistic. :)

___________
Nothing is impossible as long as somebody else does it. [giggle]

---

### Post by A Zen Roshi on 2007-08-01
Correctamundo:

I have a 180 GB HD with 5 partitions - not equally spaced.

1. windows 2000 with room for the OS and a few applications
2. room for downloads, pictures, music, etc.
3. swap
4. Ubuntu 7.04 Fiesty Fawn
5. Storage space for fiesty fawn (music, pictures, downloads, etc.)

The program installed on Window$ 2000 is Ext2 1.10 for Windows 2000
This program allows windows to assign logical drive letters to the Linux partitions [ in my case X,Y,Z].

:) All I did was copy some pictures from the Ubuntu partition to the windows partition (for honest and for true).

As far as recovering data on the Ubuntu Partition - there is no data of any significance on that partition.  

_____________________
The TRUTH?  The truth is a filthy as a pack of lies. - Elizabeht Taylor "Cat on a Hot Tin Roof".

---

### Post by Rocket2DMn on 2007-08-01
I use this program on my WinXP partition, but I'm in XP so little, I haven't had any problems, but I hear it can screw up the Ubuntu partition since we use ext3 and this is designed to mount as ext2.
Since you don't have any important data on the Ubuntu partition, I think you should do this:
-Once the LiveCD is downloaded, try my advice. Fiddle around a little bit, search more forums if needed, or ask.  If you can't get it to work:
-use the LiveCD to reinstall Ubuntu on the current partition.  You should be able to keep your data partition for Feisty and just overwrite your 4th partition with the Ubuntu installation.

---

### Post by A Zen Roshi on 2007-08-01
Thank you.  I'm really trying to understand this all myself.  Should I uninstall the Windows 2000 program?  I kind of already know the answer to that.  If I figure it out -  I PROMISE to tell you how.  Thank you for your help, your interest, and you quotes. My next post will be tomorrow, after the download and ISO of Ubuntu 7.04.  Have a great day.  Hope to type to you later.

__________________
The impossible often has a kind of integrity which the merely improbable lacks. 
- Douglas Adams

---

### Post by A Zen Roshi on 2007-08-01
Thank you Rocket2dmn for all the help.

Thank you asmoore82 for your response.

This is what i did:

 called a guy down the street - he came by with the live cd and i reinstalled Ubuntu 7.04.

Lesson Learned:  

1.  WIndows and Ubuntu are not best of friends.

2.  It did not take as long as i thought to reinstall everything.

3.  It takes much longer to fix something one knows nothing about.

4.  Realization of the VASTNESS of Linux.

5.  Read, read, read, read, read.

Thanks Guys  -  hope to type to you all sooner than later.

[email]azenroshi@yahoo.com[/email]

---

### Post by calinb on 2007-08-04
> **A Zen Roshi said:**
> 
 called a guy down the street - he came by with the live cd and i reinstalled Ubuntu 7.04.

[email]azenroshi@yahoo.com[/email]

I don't think that was necessary.  I guess I saw this thread a couple of days too late. :(

Both /home and /home/<username> should have permissions set to  drwxr-xr-x 

You probably missed /home

as root:

chmod 755 /home
chmod 755 /home/<username>  (substitute the correct username for <username>

Or perhaps your partition was full.  Check with the df command.

---

### Post by southernman on 2007-08-04
I have had this happen before... more than once. Not sure what caused it yet, but rebooting the machine a few times got it back in order. Luckily for me, looks like.

Good luck getting that deer roped up! ;)

---

### Post by bodhi.zazen on 2007-08-04
> **calinb said:**
> I don't think that was necessary.  I guess I saw this thread a couple of days too late. :(

Both /home and /home/<username> should have permissions set to  drwxr-xr-x 

You probably missed /home

as root:

chmod 755 /home
chmod 755 /home/<username>  (substitute the correct username for <username>

Or perhaps your partition was full.  Check with the df command.

That is not true.

You can have permissions of 700 on $HOME (Private home)

The problem is either with permissions on ~/.dmrc or with GDM

[http://ubuntuforums.org/showthread.php?t=489171](http://ubuntuforums.org/showthread.php?t=489171)

---

