---
title: "setting permission on remote computer"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-08-21
I guess this is the place to post this. For the last couple of days I have been trying to figure out how to set permissions on the server I have set up. Actually setting permissions on the second hard drive of the remote computer. (It has a larger hard drive) the file is /media/storage/home  My question is how do I set permissions on that computer so I can back up my files to that hard drive. Can anyone tell me how this could be done?
Tim

---

### Post by specker on 2007-08-21
How are you accessing that drive?  NFS, Samba?

---

### Post by schorsch on 2007-08-21
What is the output of
```
mount
ls -ld /media/storage/home
fdisk -l
```
... it is a lowercase "L" after the last command ....

---

### Post by maldojr88 on 2007-08-21
ok....what the first guy asked is a very good question...what type of server did u set up?
if it is samba that u are using to access the computer...to this...
you must edit the /etc/samba/smb.conf file...you have to enable what u want remote users can see...
open the file with nano or watever text editor u have...

then get some empty space (where there are no '#' because what is written after that is a comment and will be omitted by samba)
1. add a tab which looks like this

[share]

what goes inside the share is up to u ...just keep it organized so that when u access the file at a later time you know what it is...

then add the path to the line and save...the portion of the file you must add should look like this:

[shared]
        comment="This is to share my data"
        path=/media/storage/home

then you should be able to accessthe folder that says path...

then once in a different computer type this command:

$sudo smbmount //192.68.152.2 /mnt/whatever

the 192.68.152.2 is the ip of the computer you wanna log into and /mnt/whatever is the location of the computer u are at...where you will mount the drive

NOTE this is only for the samba server....let me know how it goes

---

### Post by SVWander on 2007-08-21
> **schorsch said:**
> What is the output of
```
mount
ls -ld /media/storage/home
fdisk -l
```
... it is a lowercase "L" after the last command ....

tim@ubuntu:~$ mount
/dev/hda1 on / type ext3 (rw,noatime,usrquota,grpquota,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdb1 on /media/storage type ext3 (rw)

ls -d /media/storage/home
drwxrwxr-x 7 root users 4096 2007-08-20 11:35 /media/storage/home

fdisk -l
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         978     7855753+  83  Linux
/dev/hda2             979        1027      393592+   5  Extended
/dev/hda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/hdb: 46.1 GB, 46103371776 bytes
255 heads, 63 sectors/track, 5605 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5488    44082328+  83  Linux
/dev/hdb2            5489        5605      939802+   5  Extended
/dev/hdb5            5489        5605      939771   82  Linux swap / Solari

Is how they are set up now. I tried for days to get hda1 set up as a server for days and finally gave up on it. This smaller hard drive worked except for not being able to access the larger hard drive.

tim

---

### Post by SVWander on 2007-08-21
> **specker said:**
> How are you accessing that drive?  NFS, Samba?

I am using samba and openssh.

---

### Post by SVWander on 2007-08-21
> **maldojr88 said:**
> ok....what the first guy asked is a very good question...what type of server did u set up?
if it is samba that u are using to access the computer...to this...
you must edit the /etc/samba/smb.conf file...you have to enable what u want remote users can 
[share]

what goes inside the share is up to u ...just keep it organized so that when u access the file at a later time you know what it is...

then add the path to the line and save...the portion of the file you must add should look like this:

[shared]
        comment="This is to share my data"
        path=/media/storage/home


$sudo smbmount //192.68.152.2 /mnt/whatever

the 192.68.152.2 is the ip of the computer you wanna log into and /mnt/whatever is the location of the computer u are at...where you will mount the drive

NOTE this is only for the samba server....let me know how it goes

I have edited /etc/samba/smb.conf . . . and restarted the network so many times I think I could do it in my sleep. LOL I have been trying hard but getting nowhere. When I enter the command smbmount I get a command not found. I have done a little searching on the web for smbmount but my eyes are getting blurry. 

Tim

---

### Post by schorsch on 2007-08-21
You have already installed the package smbfs:
```
apt-get install smbfs
```

---

### Post by maldojr88 on 2007-08-21
yehhh....
aparently u just need to install the smbmount 
do what the person above states...
if that works then great
if it doesnt try:

sudo apt-get install smbclient

DONT GIVE UP
together we'll make it work...and trust me dogs...when u have problems with ****..thats when ur gonna learn...i had so many problems with samba i can write a book about it...

---

### Post by SVWander on 2007-08-22
> **maldojr88 said:**
> yehhh....
aparently u just need to install the smbmount 
do what the person above states...
if that works then great
if it doesnt try:

sudo apt-get install smbclient

DONT GIVE UP
together we'll make it work...and trust me dogs...when u have problems with ****..thats when ur gonna learn...i had so many problems with samba i can write a book about it...

Well, I am moving forward . . . all ahead SLOW . . . and I don't plan on giving up. Now I am getting this message:

laptop:~/.ssh$ sudo smbmount //192.168.1.4 6media/storage/home
Password:
Could not resolve mount point /media/storage/home

I am not sure what that means. The drive is already mounted on the server. I will keep at it!

Tim

---

### Post by schorsch on 2007-08-22
> **SVWander said:**
> Well, I am moving forward . . . all ahead SLOW . . . and I don't plan on giving up. Now I am getting this message:

laptop:~/.ssh$ sudo smbmount //192.168.1.4 6media/storage/home
Password:
Could not resolve mount point /media/storage/home

I am not sure what that means. The drive is already mounted on the server. I will keep at it!

Tim
Well, you are working on a laptop, right? And the IP of your samba server is 192.168.1.4, right? Then you should try to use the name of the share, not the mountpoint on the samba server. The name of the share is given in /etc/samba/smb.conf in brackets like these [ ].
So if your share is called "shared" as mentioned above and links to /media/storage/home (all on the server!) the command on your laptop should look like:
```
sudo smbmount //192.168.1.4/shared /where_to_mount
```
where "where_to_mount" is the mountpoint on your laptop.

---

### Post by maldojr88 on 2007-08-23
this guy brings up an important point: 
lemme break it down to you...
ok you got the remote computer...and the host computer...the remote is the one that you are using ...and the host is the one where the files are in.....so ur trying to access the files on the host system from you remote computer...(remote doesnt have to be a laptop it can just be over the network...)

so on the host computer...(where the files are in) you must have the permisions set...which i think u do

ok so in the host computer u have to do the samba stuff..this being the editing of the /etc/samba/smb.conf....where i told u to add a tag [shared] and on the line that says path you must add :
[COLOR="Red"]path=/media/storage/home[/COLOR]

ok and save ....NOTE this is all on the host computer...ur just setting it up to allow a conection....


Ok now on ur remote computer...which is the one your conecting from ....you need to mount the drive from the other computer....

DONT get scared with the word mount...it just means make it part of your computer...
so when you type in the command

[COLOR="Red"]sudo smbmount //192.168.1.4/shared /where_to_mount[/COLOR]


your just mounting (making it part of your computer) the drive that is in the host computer...and its able to do so thru the server samba....

so when ur gonna run the command it should look like this:

[COLOR="Red"]sudo smbmount //192.168.1.4/media/storage/home /where_to_mount[/COLOR]

now the where to mount...this is the path of the remote computer that you will go to in order to access the files...for instance if i mounted the drive in /etc/junk i would go to the /etc/junk       in the REMOTE computer

and be able to access the file or files... one recomendation is to use the folder /mnt
go in there and create a folder to use...lets say i called the foder 'finally"

your final command would look like this....


**[COLOR="Red"]sudo smbmount //192.168.1.4/media/storage/home /mnt/finally[/COLOR]**

then you would go to /mnt/finally and be able to access the files...(note ther is a space between home and /mnt

you might not even need the /media/storage/home on the comand...so if it doesnt work try it without it
 
good luck...keep me posted on how it went

---

### Post by schorsch on 2007-08-23
> **maldojr88 said:**
> 

your final command would look like this....


**[COLOR="Red"]sudo smbmount //192.168.1.4/media/storage/home /mnt/finally[/COLOR]**

then you would go to /mnt/finally and be able to access the files...(note ther is a space between home and /mnt

you might not even need the /media/storage/home on the comand...so if it doesnt work try it without it
 
good luck...keep me posted on how it went

Correct me if I am wrong but I am pretty sure you have to use the name of the share that you typed in smb.conf on the host and not the mount point of the shared device on the host. So the command should look like:
```
sudo smbmount //192.168.1.4/shared /mnt/finally
```
You can try both commands as it won't hurt :-)
Right at the moment I cannot test it as there is no windows machine availabe despite of having several machines running ..... :)

---

### Post by maldojr88 on 2007-08-25
well it depends from where u wanna access the files...
if you on a windows computer and wanna access the files from linux...meaning that the windows is the remote and linux the host:

then all u have to do is go to start, run (on the windows pc)
then in the prompt u type in :
[B][COLOR="RoyalBlue"]
//192.168.1.4/shared[/COLOR][/B]

thats all it takes.......but this assumes that "shared" was the tag that you created in the smb.conf file...in other words

shared must be in brackets... so if u look in the smb.conf file u see 

[shared]

and then all the stuff that u already did...this is the syntax to do it. Again this is accessing the files that are on linux from a windows computer....

if it is backward (Linux machine accessing windows files) then it is a little bit different and i appoligize for not making it clear the distinction between the two senarios


The first thing that you must do on the windows computer is give access to the folder that you want to see...so u must share the folder....meaning remote users can view the files...in windows you right click the folder or drive...and hit "sharing and security"
and then select the box that says share over the network....

lets say i shared the 'c' drive on the windows computer...now from the linux computer

you type the following command...

**[COLOR="Red"]sudo smbmount//192.168.1.4/c /mnt/finally[/COLOR]**

and again the same rule applies..with the /mnt/finally thats the place where u will go to access the files of the windows pc...


I appoligize for not making it clear the distinction... try that and let me know


**ohhhhh one very important note...make sure the folders on the windows pc have no spaces in the name...because linux doesnt really like spaces so you would have to use a differente syntax...so to simplify ur life just dont have spaces**

---

### Post by schorsch on 2007-08-25
Thanks for clearing this!
I read the whole thread again and at them moment I am a little bit confused ....
I guess the machine on which the files are physically attached to is a linux computer, right? I guess this as you mentioned that you edited "/etc/samba/smb.conf" and this file is not windows like. Then we will call it the "host". 
The other machine which wants to mount the shared filesystem ("remote" or "client" called) is it al linux or windows machine? Again I guess linux as you mentioned that you want to mount it via "smbmount" command. Can you please clear this before we investigate further?

---

### Post by maldojr88 on 2007-08-28
ok this is how it goes....
[COLOR="Blue"]1.host computer[/COLOR]
[COLOR="Red"]2.remote[/COLOR]

[COLOR="Blue"]1.host computer is the mac daddy computer cuz it acutually has all the data that u want to back up...this computer must have permisions enabled in order to be able to access the files that are on this computer....from another computer
so this is the main computer that has the files and now u wanna access this host computer from some other computer....
[/COLOR]
[COLOR="Red"]2.that other computer is the remote computer....meaning from this computer you will access the files that are on the host computer...
[/COLOR]

In more simple terms computer [COLOR="Blue"]A [/COLOR]is the [COLOR="Blue"]host[/COLOR]. [COLOR="Red"]B[/COLOR] is the [COLOR="Red"]remote[/COLOR].. So from [COLOR="Red"]B[/COLOR] you are able to see the files on [COLOR="Blue"]A[/COLOR]


now ....heres where the thing has its litttle twist....if either of the computers is runinng windows then you must use Samba. samba is a server that allows networking between linux and windows. 

The cool thing is that samba only needs to be installed on the computer that is running linux period. So regardless of which computer has linux (A or B) (remote or host) only this one needs samba installed and the smb.conf file edited.

Ok one other thing....im here talking about computer A and [COLOR="Red"]B[/COLOR] ....just to make it clear...
[COLOR="Blue"]A[/COLOR] can see [COLOR="Red"]B[/COLOR]'s files and[COLOR="Red"] B[/COLOR] can see [COLOR="Blue"]A[/COLOR]'s files...
thats the power of samba....


So in conclusion....the linux computer is wat must have samba installed and running..
and teh file configured (smb.conf) ...the permisions must also be enabled on each of the computers and the comands to view the files are on my last post

because it depends on how ur connecting...either from the windows pc to the linux or from the linux to the windows. See which of these applies to you and do as it says in my last post

hope this helps

---

