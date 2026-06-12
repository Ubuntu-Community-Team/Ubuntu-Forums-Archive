---
title: "I screwed up my partitions ..."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Jiran on 2007-05-10
Well now, I'm in a dilly of a pickle. Here's my situation:

I have my HDD partitioned into three chunks (excluding swap): 40GB for Vista, 10GB for Ubuntu, 60GB for /home. When I was playing around in Vista, I noticed that I couldn't see my /home partition, since it was an ext3 drive. So, since Linux can read/write to NTFS, I figured I would format it as such.

So I copied my /home/dylan directory to the Windows partition, for safe keeping. Then I formatted my last partition as NTFS. Now, everything's screwed up. I can't boot into Ubuntu since I need a /home directory, but I can't copy my files back using the failsafe terminal since I need a tool to read/write to an NTFS drive! So, I decided to scrap everything and format it back as an ext3.

Now, I copied everything back, mounted the partition to my /home directory, and ... I get another error. Something about a .dmrc file and 644 permissions. I know this was brought up before in other threads, but their solution didn't work for me. So, I ask you: how can I get my /home directory back? Also, what other way can I have this partition be able to work with both Linux and Windows?

Thanks a lot!

---

### Post by drowner on 2007-05-10
I'm a noob too, but i like trying to answer questions, as it helps me learn ;)

But i *think* the problem is that you probably do not have write access to an ntfs partition, (ubuntu still doesnt do it natively) and by default it has probably mounted this partition as read-only.

How about you show us a 

sudo fdisk -l

which will give us info on your disks.

---

### Post by rich.bradshaw on 2007-05-10
I don't know how to fix, but one of the problems is that NTFS doesn't do permissions in the same way as Linux wants, everything gets owned by root.

---

### Post by Cypher on 2007-05-10
How are you doing all the formatting??

It is always smart to leave the filesystem in the native format of the OS being used. That is, NTFS for Windows and EXT3 for Linux. To get access to the other filesystem, in Linux you'd use "ntfs-3g" and in Windows you'd use [FS Driver]("http://www.fs-driver.org/").

---

### Post by Jiran on 2007-05-10
Yes, I realize now the error of my ways. I will try FS-Driver when I get everything working again. My problem now is that I have an ext3 partition with my /home drive. I mounted it using the failsafe terminal, but when I try to load it I get an error saying that it can't find my $HOME/.dmrc file. What do I do to solve this?

---

### Post by bodhi.zazen on 2007-05-10
> **Jiran said:**
> Well now, I'm in a dilly of a pickle. Here's my situation:

I have my HDD partitioned into three chunks (excluding swap): 40GB for Vista, 10GB for Ubuntu, 60GB for /home. When I was playing around in Vista, I noticed that I couldn't see my /home partition, since it was an ext3 drive. So, since Linux can read/write to NTFS, I figured I would format it as such.

So I copied my /home/dylan directory to the Windows partition, for safe keeping. Then I formatted my last partition as NTFS. Now, everything's screwed up. I can't boot into Ubuntu since I need a /home directory, but I can't copy my files back using the failsafe terminal since I need a tool to read/write to an NTFS drive! So, I decided to scrap everything and format it back as an ext3.

Now, I copied everything back, mounted the partition to my /home directory, and ... I get another error. Something about a .dmrc file and 644 permissions. I know this was brought up before in other threads, but their solution didn't work for me. So, I ask you: how can I get my /home directory back? Also, what other way can I have this partition be able to work with both Linux and Windows?

Thanks a lot!

For .dmrc (you may need to do this with a live CD or boot Ubuntu to failsafe mode):

.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

 As to your larger problem, I advise you use ext3 for you shared partition.

You can access ext3 from windows :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Jiran on 2007-05-10
> **bodhi.zazen said:**
> For .dmrc (you may need to do this with a live CD or boot Ubuntu to failsafe mode):

.drmc file permissions, in a terminal: (use first set)



	OR, if that fails:



 As to your larger problem, I advise you use ext3 for you shared partition.

You can access ext3 from windows :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Thanks very much, I'll try that when I get home. Just wondering, your second suggestion has force-remove commands in it ... what exactly is it doing? You'll have to forgive me if I seem rude, but taking commands from a stranger that tell me to remove something from my computer sets off my warning alarms. :P

---

### Post by bodhi.zazen on 2007-05-10
> **Jiran said:**
> Thanks very much, I'll try that when I get home. Just wondering, your second suggestion has force-remove commands in it ... what exactly is it doing? You'll have to forgive me if I seem rude, but taking commands from a stranger that tell me to remove something from my computer sets off my warning alarms. :P

LOL

No problem, glad you are interested.

Funy how after a while you lean to like the man files. They take a while to get used to though :)

From man rm:

> The command rm deletes each file argument from the system.
     There are a large number of options:

     -f   Forced remove.  Unwritable files are removed without rm
          asking permission.  By default, rm will ask permission
          before removing unwritable files.

     -r   Recusive remove.  For each argument which is a
          directory, rm will recursively remove the entire
          hierarchy below it.  If this was successful, the
          directory itself is removed.

     -i   Interactive remove.  rm will ask permission before
          removing anything.

I included the -i flag for informational purposes.

---

