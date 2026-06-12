---
title: "cannot install a .run file"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by byenary on 2008-03-10
Hi All,

Having trouble with this .run file, i have got it installed on other machines before, but for some reason it won't do it now...
Got this file nsm_linux_cli_3_04_03.run wich is a network shutdown module to communicate with ups.
Any idea what would be missing on this system to make it work ? THX

root@server32:/home/byenary# ls -all
total 5704
drwxr-xr-x 2 byenary users    4096 2008-03-10 14:15 .
drwxr-xr-x 4 root  root     4096 2008-03-10 14:12 ..
-rw------- 1 byenary users     121 2008-03-10 14:15 .bash_history
-rw-r--r-- 1 byenary users     220 2008-03-10 14:12 .bash_logout
-rw-r--r-- 1 byenary users    2298 2008-03-10 14:12 .bashrc
-rwxr-xr-x 1 root  root  5803952 2008-03-10 14:13 nsm_linux_cli_3_04_03.run
-rw-r--r-- 1 byenary users     566 2008-03-10 14:12 .profile
root@server32:/home/byenary# chmod 777 nsm_linux_cli_3_04_03.run
root@server32:/home/byenary# ./nsm_linux_cli_3_04_03.run
-bash: ./nsm_linux_cli_3_04_03.run: No such file or directory
root@server32:/home/byenary# sh nsm_linux_cli_3_04_03.run
nsm_linux_cli_3_04_03.run: 1: Syntax error: "(" unexpected
root@server32:/home/byenary#

---

### Post by buried on 2008-03-10
hmmm... first, right click and give full permissions to it (execute permissions) then run this is terminal: /home/byenary/nsm_linux_cli_3_04_03.run and see if it executes if not, it might just be the package itself (maybe it's corrupted) so try re-downloading it.

---

### Post by handydan918 on 2008-03-10
Very strange. Wonder if this is an issue of root vs. sudo? Yeah, I know, it should work. Have you tried running the file with sudo?

---

### Post by byenary on 2008-03-10
Hi,

maybe this a problem on a whole other level, sudo does not seem to work for some reason, it tried it with sudo with a user (byenary) instead of root. Got the message that is was not a sudoer so i added byenary to the admin group.
He does allow me to sudo but does not execute my commands, does not react to my shutdown command or nothing... ???
More ideas ?

byenary@server32:~$ sudo ./nsm_linux_cli_3_04_03.run
byenary@server32:~$ sudo shutdown -h now
byenary@server32:~$

---

### Post by byenary on 2008-03-10
sudo thing seemes solved but stil same problem :

byenary@server32:/$ sudo /home/byenary/nsm_linux_cli_3_04_03.run
sudo: unable to execute /home/byenary/nsm_linux_cli_3_04_03.run: No such file or directory

---

### Post by defmomo on 2008-03-10
Why don't you try this :
```
 sudo sh nsm_linux_cli_3_04_03.run
```

---

### Post by byenary on 2008-03-10
byenary@server32:/$  sudo sh /home/byenary/nsm_linux_cli_3_04_03.run
/home/byenary/nsm_linux_cli_3_04_03.run: 1: Syntax error: "(" unexpected

---

### Post by forrestcupp on 2008-03-10
Well, it says No such file or directory.  Are you absolutely sure you're in the right directory and that you're typing the file name exactly right?  Change to that directory and type ls to make sure the file is really there and exactly what the name of the file is.

If you were in the wrong place or had the wrong file name, you may need to do a chmod +x on the file again to make it executable.

---

### Post by byenary on 2008-03-10
Absloutly sure, i am in the directory and used TAB to autocomplete  the file...
It is a 64bit system but I installed the same file on another 64bit system so that should not be the problem...


byenary@server32:~$ ls -all
total 5708
drwxr-xr-x 3 byenary users    4096 2008-03-10 17:54 .
drwxr-xr-x 4 root  root     4096 2008-03-10 14:12 ..
-rw------- 1 byenary users    1078 2008-03-10 17:15 .bash_history
-rw-r--r-- 1 byenary users     220 2008-03-10 14:12 .bash_logout
-rw-r--r-- 1 byenary users    2298 2008-03-10 14:12 .bashrc
-rw-r--r-- 1 root  root  5803952 2008-03-10 17:52 nsm_linux_cli_3_04_03.run
-rw-r--r-- 1 byenary users     566 2008-03-10 14:12 .profile
drwx------ 2 byenary users    4096 2008-03-10 17:08 .ssh
-rw-r--r-- 1 byenary users       0 2008-03-10 17:20 .sudo_as_admin_successful
byenary@server32:~$ chmod 777 nsm_linux_cli_3_04_03.run
chmod: changing permissions of `nsm_linux_cli_3_04_03.run': Operation not permitted
byenary@server32:~$ sudo chmod 777 nsm_linux_cli_3_04_03.run
byenary@server32:~$ ls -all
total 5708
drwxr-xr-x 3 byenary users    4096 2008-03-10 17:54 .
drwxr-xr-x 4 root  root     4096 2008-03-10 14:12 ..
-rw------- 1 byenary users    1078 2008-03-10 17:15 .bash_history
-rw-r--r-- 1 byenary users     220 2008-03-10 14:12 .bash_logout
-rw-r--r-- 1 byenary users    2298 2008-03-10 14:12 .bashrc
-rwxrwxrwx 1 root  root  5803952 2008-03-10 17:52 nsm_linux_cli_3_04_03.run
-rw-r--r-- 1 byenary users     566 2008-03-10 14:12 .profile
drwx------ 2 byenary users    4096 2008-03-10 17:08 .ssh
-rw-r--r-- 1 byenary users       0 2008-03-10 17:20 .sudo_as_admin_successful
byenary@server32:~$ sudo ./nsm_linux_cli_3_04_03.run
sudo: unable to execute ./nsm_linux_cli_3_04_03.run: No such file or directory
byenary@server32:~$

---

### Post by bodhi.zazen on 2008-03-10
Is your /home on a separate partition ? If so, is it mounted noexec (what is the line for /home in /etc/fstab)?

---

### Post by byenary on 2008-03-10
No it is not, this is becomming a real riddle....

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             224G  1.8G  211G   1% /
varrun               1007M  168K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   76K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
/dev/mapper/VG_Raid5_WavData-LV_WavData
                      4.7T  1.3T  3.2T  29% /mnt/WavData

---

### Post by bodhi.zazen on 2008-03-10
Looking over your post I think I see the problem. The file is owned by root.

```
cd /home/byenary/

sudo chmod a+x /home/byenary/nsm_linux_cli_3_04_03.run
sudo ./nsm_linux_cli_3_04_03.run
```

---

### Post by handydan918 on 2008-03-10
> **bodhi.zazen said:**
> Looking over your post I think I see the problem. The file is owned by root.

```
cd /home/byenary/

sudo chmod a+x /home/byenary/nsm_linux_cli_3_04_03.run
sudo ./nsm_linux_cli_3_04_03.run
```
Well, I hope your answer helps the OP, but I don't get it. He already did
```
root@server32:/home/byenary# chmod 777 nsm_linux_cli_3_04_03.run
```
so how is that any different? 
I would think that if you chmod a file to 777, then it wouldn't matter much who owned it, root or not.
Am I missing something?

:confused:

---

### Post by icechen1 on 2008-03-10
You might have to switch from dash to bash.
Do > sudo dpkg-reconfigure dash and try it again

---

### Post by byenary on 2008-03-10
Indeed, the riddle continues, already thx for the efforts,

byenary@wavstordjm:~$ sudo chmod a+x /home/byenary/nsm_linux_cli_3_04_03.run 
[sudo] password for byenary:
byenary@wavstordjm:~$ sudo chmod a+x /home/byenary/nsm_linux_cli_3_04_03.run 
byenary@wavstordjm:~$ sudo ./nsm_linux_cli_3_04_03.run 
sudo: unable to execute ./nsm_linux_cli_3_04_03.run: No such file or directory
byenary@wavstordjm:~$

---

### Post by icechen1 on 2008-03-10
Do you misspelled the file name?try to use a wildcard like:
sudo ./ns*

---

### Post by byenary on 2008-03-10
Nope, i always use TAB to autocomplete

---

### Post by forrestcupp on 2008-03-10
Have you tried running it without sudo?  And have you tried redownloading the file in case the script is corrupted?

---

### Post by byenary on 2008-03-10
yes redownloaded it, also made a copy from another server where it is already installed, and yes also tried to just run it as root or as byenary without sudo...

---

### Post by bodhi.zazen on 2008-03-10
> **handydan918 said:**
> Well, I hope your answer helps the OP, but I don't get it. He already did
```
root@server32:/home/byenary# chmod 777 nsm_linux_cli_3_04_03.run
```
so how is that any different? 
I would think that if you chmod a file to 777, then it wouldn't matter much who owned it, root or not.
Am I missing something?

:confused:

I do not know, but s/h posted this :

```
-rw-r--r-- 1 root root 5803952 2008-03-10 17:52 nsm_linux_cli_3_04_03.run
```

Actually though it should work with

sudo sh ./nsmnsm_linux_cli_3_04_03.run

without making it executable.

Try :

```
sudo -i

sh /home/byenary/nsm_linux_cli_3_04_03.run
```

If that fails, post the output of :

ls -l /home/byenary | grep nsm_linux_cli_3_04_03.run


My only other thought would be the partition is mounted noexec.

---

### Post by byenary on 2008-03-10
root@server32:~# cd /home/byenary
root@server32:/home/byenary# su byenary
byenary@server32:~$ sudo sh ./nsm_linux_cli_3_04_03.run 
./nsm_linux_cli_3_04_03.run: 1: Syntax error: "(" unexpected
byenary@server32:~$ sudo -i
root@server32:~# sh /home/byenary/nsm_linux_cli_3_04_03.run 
/home/byenary/nsm_linux_cli_3_04_03.run: 1: Syntax error: "(" unexpected
root@server32:~# ls -l /home/byenary/nsm_linux_cli_3_04_03.run 
-rwxrwxrwx 1 byenary root 5803952 2008-03-10 17:52 /home/byenary/nsm_linux_cli_3_04_03.run


root@server32:~# cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c101cef-b313-44ed-8509-bbfcfe87f3f5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=82a17b49-53db-4d10-b645-231718a87c9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# LVM
/dev/VG_Raid5_WavData/LV_WavData        /mnt/WavData    ext2    defaults        0       1


root@server32:~#

---

### Post by bodhi.zazen on 2008-03-10
OK, now your script is running, but there is a syntax error :

> /home/byenary/nsm_linux_cli_3_04_03.run: 1: Syntax error: "(" unexpected

At this point we need to either :

1. Post a bug report to the maintainer of that *.run (This is my advice).

2. Read any README or other documentation you can find.

3. Inspect the code and see if we can determine (and correct) the syntax error (May be difficult if you do not know how to code).

---

### Post by byenary on 2008-03-10
Thanx for your help, but it is a rather strange thing though, the same file works on an other machine wich is pretty much identical, and works with using just ./
AND, it is binary file so there is not much of code to inspect, still think there is something else going on, maybe i should reinstall the sever, I never had troubles, but this time a collegue of mine installed it but i can not figure out what is wrong with this, i also tried an other bin file and does start installing...
So it is still a riddle to me...

---

### Post by bodhi.zazen on 2008-03-10
You could try checking the integrity of the file with say md5sum (just to make sure the download was not corrupt).

Hard to know how a re-install would help without knowing the problem.

---

### Post by byenary on 2008-03-11
Checked it, that was not the problem either :(

---

### Post by byenary on 2008-03-20
Solution is found, 
When using the command head to view the filestart, there is /ib/ld-linux.so
But het 32bit version of the file need is not present.
Installing getlibs is the trick.
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb) 
Thx for all tips evb

---

