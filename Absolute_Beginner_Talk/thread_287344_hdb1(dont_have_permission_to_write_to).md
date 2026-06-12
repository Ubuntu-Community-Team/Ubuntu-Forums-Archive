---
title: "hdb1(dont have permission to write to)"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-28
hi all i was trying to send an archive to hdb1 but i dont have write permission ,
 how do i solve this .
 i have ubuntu 6.06 on hda1 200 gig, and ubuntu 6.06 on hdb1 80 gig hdb1 was set up for all my doc storage but it seems to have been hijacked.
 so i would like to know how to get my permissions back so i can easily send files to hdb1 for storage.
  thank you:twisted:

---

### Post by highneko on 2006-10-28
What format? ntfs?

Try:
df -T | grep hda1

When doing that command I get:
highneko@ubuntu:~$ df -T | grep hda1
/dev/hda1     ntfs   102398276  21765860  80632416  22% /windows
highneko@ubuntu:~$

---

### Post by tk92 on 2006-10-28
chmod to 777?

---

### Post by highneko on 2006-10-28
> **tk92 said:**
> chmod to 777?
That would make all files -rwxrwxrwx
i don't think it's a good idea.

I think ntfs is a more likely problem. File ownership it could be too.

---

### Post by Arby on 2006-10-28
I may have missed the point here but what about

```
sudo cp /path/to/my/file /path/where/I/want/to/send/my/file
``` Using sudo should give you write permission to anywhere.

---

### Post by highneko on 2006-10-28
> **Arby said:**
> I may have missed the point here but what about

```
sudo cp /path/to/my/file /path/where/I/want/to/send/my/file
``` Using sudo should give you write permission to anywhere.

Cp would work, but cd would be easier to test for a ownership problem.

---

### Post by STREETURCHINE on 2006-10-28
sorry i can not understand the command ,how do i write it up i want to send archives i have on my desktop on hda1 to hdb1 in lost+found
 i tried a couple of times but my commands not found.
 can i not just configure them to work together so i can just send files across for storage instead of the sudo command all the time.
 i have ubuntu on both drives i thought they would just work as one(wrong)

---

### Post by STREETURCHINE on 2006-10-28
nfts i'am not sure whatever ubuntu writes in because that is all that is on both hard drives

---

### Post by highneko on 2006-10-28
That lost+found is owned by root I believe. I don't really understand your problem. Try the command I gave you in your gnome-terminal, or whatever terminal you use.

Are sudo commands working for you? Can you list the folder and file you are trying to send to and from using the "ls -l" for your list command and paste the output here.

if you don't give us some more detailed information using the commands, it might not be possible to help. The commands are 100% safe to use.

commands:
ls -l example.txt; ls -l folder
df -hT | grep hda1

---

### Post by STREETURCHINE on 2006-10-28
rex@Linux:~$ ls -l
total 12676
drwxr-xr-x 2 rex  rex     4096 2006-10-28 08:56 archive
-rw-r--r-- 1 rex  rex    44355 2006-10-24 18:32 article.pl apt-get check if wall paper dont load
-rw------- 1 rex  rex       91 2006-10-23 14:48 autologin.c.save
drwxr-xr-x 2 rex  rex     4096 2006-10-29 05:23 Canon-BJC-50-bjc600_files
-rw-r--r-- 1 rex  rex    92940 2006-10-29 05:23 Canon-BJC-50-bjc600.ppd
-rw-r--r-- 1 rex  rex    93154 2006-10-29 05:25 Canon-MultiPASS_C2500
drwxr-xr-x 2 rex  rex     4096 2006-10-29 05:25 Canon-MultiPASS_C2500_files
drwxr-xr-x 3 rex  rex     4096 2006-10-29 06:32 Desktop
lrwxrwxrwx 1 rex  rex       26 2006-10-18 13:07 Examples -> /usr/share/example-content
drwxr-xr-x 2 rex  rex     4096 2006-10-22 10:34 home_files
-rw-r--r-- 1 rex  rex        0 2006-10-27 07:55 hsqlprefs.dat
drwxr-xr-x 2 rex  rex     4096 2006-10-26 13:43 Incomplete
-rw-r--r-- 1 root root   33686 2006-08-06 04:29 jriddell.key
-rwxr--r-- 1 rex  rex     1730 2006-10-24 09:58 key.gpg.asc
-rwxr--r-- 1 rex  rex     1730 2006-10-24 09:58 key.gpg.asc.1
-rwxr--r-- 1 rex  rex     1730 2006-10-24 09:58 key.gpg.asc.2
-rw-r--r-- 1 rex  rex     1730 2006-10-26 12:38 key.gpg.asc.3
-rwxr--r-- 1 rex  rex      348 2006-10-24 16:21 public keys
-rw-r--r-- 1 root root    1787 2006-08-06 04:36 quinn1.key
-rw-r--r-- 1 root root    1690 2006-08-06 04:37 quinn2.key
drwxr-xr-x 2 rex  rex     4096 2006-10-26 08:18 Shared
drwxr-xr-x 2 rex  rex     4096 2006-10-29 05:31 stp-canon-cp100.5.0_files
-rw-r--r-- 1 rex  rex    92940 2006-10-29 05:31 stp-canon-cp100.5.0.ppd
drwxr-xr-x 2 rex  rex     4096 2006-10-29 05:34 stp-canon-cp220.5.0_files
-rw-r--r-- 1 rex  rex    92940 2006-10-29 05:34 stp-canon-cp220.5.0.ppd
drwxr-xr-x 2 rex  rex     4096 2006-10-26 11:44 vmware
-rw-r--r-- 1 root root 5665020 2006-10-25 17:55 w32codecs_20060611-0.0_i386.deb
-rw-r--r-- 1 root root 2969388 2006-10-25 17:57 w32codecs_20060611-0.0_i386.deb.1
-rw-r--r-- 1 root root 3389981 2006-10-25 18:00 w32codecs_20060611-0.0_i386.deb.2
-rw-r--r-- 1 root root  376232 2006-10-25 18:00 w32codecs_20060611-0.0_i386.deb.3
rex@Linux:~$ df -hT | grep hda1
/dev/hda1     ext2    181G  3.2G  169G   2% /
rex@Linux:~$ __________________


 i know the commands are safe it is that i am a noobie to the computer world and not proficient with them,i need to see them as i should write them.  as for more information i a trying to send from hda1 to hdb1 two seperate hard drives,i want to configure them so i dont have to use the sudo command all the time to send files across ,that is what i put it for   

rex@Linux:~$ df -hT | grep hdb1
/dev/hdb1     ext3     76G  129M   72G   1% /media/hdb1
rex@Linux:~$

---

### Post by highneko on 2006-10-28
See how it says root twice? The first root means user, and the second means group. If you're trying to move those files, as a user, you'll have to make them have the ownership of a user.

To do this; Make sure you're in the folder you want to move your files from. Change the ownership of the file, or all files with the command chown. Type "man chown" for more information.

If you don't know about wildcards(*), I suggest maby not using the command I'll post now. Maby trying the second command on a test file would be best.

man chown
chown rex:rex *
#or
chown rex:rex example.txt

---

### Post by STREETURCHINE on 2006-10-28
all i am trying to do is get root permision to write to my second hard driveso i can just send them there ,i dont want to have to use the sudo command every time i want to send files to storage,i hope this makes it clearer

---

### Post by highneko on 2006-10-28
Ok, I think I'm starting to understand.

hda1 / is the folder you want to move a file to?

Maby pasting "df -h" and posting what you want to go where.
Try "ls -l folder; ls -l folder" on the mounted folders, and paste the results.

---

### Post by STREETURCHINE on 2006-10-28
sorry i have no idea as it was loaded at the shop when the second hard drive was installed ,how do i find out what file it was mounted on

 no i am trying to move a file from hda1 to hdb1 but i dont have write perrmission to hdb1

 i need to change permissions on hdb1 to get write permissions

rex@Linux:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1             181G  3.2G  169G   2% /
varrun                506M  156K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  120K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1              76G  129M   72G   1% /media/hdb1
rex@Linux:~$



 it looks like it is mounted on media ,so if i can somehow change that file to give me write permissions we should be ok is that correct?

 yep i saw that and was giving it a go it did nothing so i tried a reboot
 after i typed it in terminal i t just dropped down one line and this appeared > 

 have not set up any im services yet ,do that later

rex@Linux:~$ chown rex:rex /media/hdb1; chmod 755 /media/hdb1; ls -l /media/hdb1chown: changing ownership of `/media/hdb1': Operation not permitted
chmod: changing permissions of `/media/hdb1': Operation not permitted
total 48
drwxr-xr-x 2 root root 49152 2006-10-18 13:02 lost+found
rex@Linux:~$
 that is the read out ?
 yahoo that fixed it ,thank you for your patience and help much appreciated
\\:D/

---

### Post by highneko on 2006-10-28
Glad you got it fixed. It's best to take things step by step, and not random commands + wildcards. Learning all about what you're doing. I once chmod 777 my whole /data directory recursively, over 10,000 files. I did some learning, and managed to fix it, but I wouldn't want anyone else to go through the same thing.

Do lots of manual reading with;
man command
E.g;
man ls

---

