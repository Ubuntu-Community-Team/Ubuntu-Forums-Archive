---
title: "Partiton Access?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by plorman on 2007-12-21
When I installed ubuntu I created a partition to store my music so that every time I reinstall I don't have to back-up 40+ GB of audio files.  I though that ubunu would reconize this partiton as an additional disk automatically like it did with my windows xp partition.  It did not however.  I read this thread 

[http://ubuntuforums.org/showthread.php?t=630885&highlight=partiton+access]("http://ubuntuforums.org/showthread.php?t=630885&highlight=partiton+access")

followed the procedure and was still unable to gain access.  When I enter the first of these codes,

sudo chown -R user:user /storage
sudo chmod -R 755 /storage
Replace user with your username and /storage to the path of your partition. 

"sudo chown -R user:patrick/music" I get this error message....

chown: missing operand after `user:patrick/music'
Try `chown --help' for more information.

Anybody know where I went wrong?

---

### Post by heatpumpcontrol on 2007-12-21
try

sudo chown -hR (NAME) /media/NAME of MEDIA

for example:

sudo chown -hR john /media/music

provided that you have created a directory for the music partition and have named it 'music' without the quotes

---

### Post by blueridgedog on 2007-12-21
user:user would be translated to atrick:atrick.

So, if your partition was to be mounted at /music you would 
sudo chown -R atrick:atrick /music
sudo chmod -R 755 /music

The argument to chown is the USERNAME:GROUPNAME and in most cases they will be the same for the tasks you will undertake, so you would always type your username twice with a : between.

---

### Post by plorman on 2007-12-21
Thank you both for quick replies.  I am a total n00b so I'm probably making a stupid mistake somewhere but I can't seem to get it to work.  
First I tried sudo chown -R patrick : patrick /music, but again I got an error 

chown: missing operand after patrick : patrick/music
Try `chown --help' for more information.

So then I tried sudo chown -hR patrick /media /music, I got back...

sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

Is media the directory name?  I don't think I created a directory so is that the problem?  If so how would I go about doing that?

---

### Post by taurus on 2007-12-21
Do you already have /music?  Also, there shouldn't be any space between the : in the command.

```
sudo chown -R patrick:patrick /music
```

---

### Post by plorman on 2007-12-21
yes I know there shouldn't be any spaces I just put them in so that the P's wouldn't turn into smiles (see my first post).  As for the /music that's the name I gave the partition during instillation. I think the file system is ext3 if that helps any.

---

### Post by taurus on 2007-12-21
You mean /music is on it own partition!  Can you post

```
sudo fdisk -l
df -h
```

---

### Post by plorman on 2007-12-21
yes /music is its own partition.  I just noticed that it shows up under the file systems tab in the system monitor.  

When I enter the codes you gave me this is displayed in the terminal....

patrick@patrick-desktop:~$ sudo fdisk -l
[sudo] password for patrick:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  83  Linux
/dev/sda2             609         730      979965   82  Linux swap / Solaris
/dev/sda3             731       12888    97659135   83  Linux
/dev/sda4           12889       19452    52725330   83  Linux
patrick@patrick-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4.6G  2.4G  2.1G  54% /
varrun                505M   88K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   72K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              92G  337M   87G   1% /home
/dev/sda4              50G  180M   47G   1% /music

---

### Post by taurus on 2007-12-21
What about

```
ls -la /music
```

---

### Post by plorman on 2007-12-21
patrick@patrick-desktop:~$ ls -la /music
total 24
drwxr-xr-x  3 patrick patrick  4096 2007-12-21 19:02 .
drwxr-xr-x 22 root    root     4096 2007-12-21 19:16 ..
drwxr-xr-x  2 patrick patrick 16384 2007-12-21 19:02 lost+found

---

### Post by taurus on 2007-12-21
Well, you should be able to write or save files to /music now.  What happens when you run these commands?

```
cd /music
touch *test* 
ls -la
```
Do you see *test* from the output of the last command with you as the owner?

And if you want to remove _test_, just run

```
rm /music/*test*
```

---

### Post by plorman on 2007-12-22
I think it worked heres what I got back...

patrick@patrick-desktop:~$ cd /music
patrick@patrick-desktop:/music$ touch test 
patrick@patrick-desktop:/music$ 
patrick@patrick-desktop:/music$ touch test 
patrick@patrick-desktop:/music$ ls -la
total 24
drwxr-xr-x  3 patrick patrick  4096 2007-12-22 00:11 .
drwxr-xr-x 22 root    root     4096 2007-12-21 19:16 ..
drwxr-xr-x  2 patrick patrick 16384 2007-12-21 19:02 lost+found
-rw-r--r--  1 patrick patrick     0 2007-12-22 00:11 test
patrick@patrick-desktop:/music$ rm /music/test
patrick@patrick-desktop:/music$ 

now that I can write to it is there a way to create an icon for it in Computer like its a drive?

---

### Post by taurus on 2007-12-22
You mean like an icon on your desktop!  Then you should have mounted it to /media/music in /etc/fstab instead of to /music.

---

### Post by plorman on 2007-12-22
So how would I go about doing that then?  Or am I past the point of no return?  I mean would I need to reinstall and repartition the drive to do that?

---

### Post by NeoLithium on 2007-12-22
If you just want to create an icon to go straight to the music directory, you can right click on the desktop and select Create Launcher.  Select "location" for the type of launcher it is, name it whatever you like, and in the command field, use (Don't forget the /):

/music

Then you can just right click the new icon and select properties if you want to use a different icon image.

---

### Post by plorman on 2007-12-22
Ha ha it works!!!  These web forums are a life saver for noobs like me.  Thanks to everyone for your help!

---

