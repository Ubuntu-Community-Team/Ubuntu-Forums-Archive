---
title: "crossover cable networking???"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-09-28
I have a Ubuntu Box and a Kubuntu laptop!!! both have ethernet cards. I also have a crossover cable.... how to i connect the 2 just to share and transfer files!
need a step by step process as i am know "NOTHING" in networking stuff! 
searched for the threads...but did not find any tutorial or discussion on the same [may be i am not searching right!!!] please help!

---

### Post by Shin_Gouki2501 on 2007-09-28
in short:
assgin private IP adress from same subnet like:
192.168.2.1 -> PC 1
192.168.2.2 -> PC 2
then hmm in windows i would use share Folder with Linux u could try Samba.
Install samba ( apt-get...)
create user for samba u need CLi command for that.

then need to configure Fodlers within samba ( thats grapfical in ubuntu)

then it should work ;)

---

### Post by badguyanil on 2007-09-28
is there anything which actually has a more explained stuff..may be a few screenshots!!! Know nothig of samba :(

---

### Post by anaconda on 2007-09-28
Samba is the Windows networking. Why would you use samba to connect 2 LINUX machines?? Yeah. it works, and if you have even one windows machine then samba propably is the best choise, but..

---

### Post by badguyanil on 2007-09-28
well what but!!! i just want to transfer files...samba or any other software... and BTW both have ubuntu (1 with ubuntu and the other kubuntu).. so any non-samba :confused: way will also do!

---

### Post by ukripper on 2007-09-28
i use SSH - [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by hyper_ch on 2007-09-28
I'd also go for SSH

---

### Post by ukripper on 2007-09-28
More info on SSH - [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s03.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s03.html)

---

### Post by anaconda on 2007-09-28
Hi.. didn't have time to write this to my previous post:
I use SSH and SSHFS. SSH is just a terminal connection to your other machine. With SSHFS you can mount any folder from the other machine to the other. (without needing to share it in the other machine.)

Advantages of sshfs are that it is easy, encrypted and you can also connect safely to your home machine from anywhere!

The (only) disatvantage is that because it is encrypted it is slower(and safer) than the alternatives (eg. nfs or samba)  So if you want to copy a 10GB file then it just takes longer..

Some links:
NFS:
[http://en.wikipedia.org/wiki/Network_File_System_(protocol](http://en.wikipedia.org/wiki/Network_File_System_(protocol))
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

SSH:
[http://element14.wordpress.com/2006/12/18/how-to-install-and-use-ssh-server-on-ubuntu-610/](http://element14.wordpress.com/2006/12/18/how-to-install-and-use-ssh-server-on-ubuntu-610/)

SSHFS:
[http://en.wikipedia.org/wiki/SSHFS](http://en.wikipedia.org/wiki/SSHFS)
[http://www.linuxjournal.com/article/8904](http://www.linuxjournal.com/article/8904)
[http://ubuntuforums.org/showthread.php?t=275856&highlight=sshfs](http://ubuntuforums.org/showthread.php?t=275856&highlight=sshfs)

---

### Post by Shin_Gouki2501 on 2007-09-28
I think this is a very good example of how to NOT solve a problem. ok SSH is fine but does these tons of "very usefull" Information interested our badguyanil 
?
I think not he has two pcs  and want a fast solution and not read tons of stuff which might be interesting but not relevant...

I mean he uses a CROSSOVER cable how save has the conenction to be?

IMO badguyanil  u could also install a FTP Server but SSH with some similiar  GUi like WinSCP in Dwindows in should make the deal.

---

### Post by kvonb on 2007-09-28
The problem is that Ubuntu doesn't come with file sharing built in and you are going to have to download a small (3.3 megs) file in order to do this!

If one of the computers can access the internet you are in luck.

1. Simply click on Places->Home Folder from the menu to start the file browser (Nautilus), then right click on the folder you wish to share and select "Share Folder".  Note that you can only share a folder that is inside your home folder though, ie one you own!

2. Enter your normal/login password, then select "Install Windows Network Support (SMB) from the list, don't bother with "Unix NFS" as it is too complicated and is not really that useful!

It will then install the stuff you need, you will then have to do the same thing with the other machine.

If you can't get the Interent on the other machine, than you can transfer the installed file to the other machine using a USB type storage device such as an ipod/mp3 player/USB key etc' or a writeable CD.

To transfer the file:

On the first machine, (the one you just installed file sharing on at step 1. above) the file you need is in **/var/cache/apt/archives**, and is called: **samba_3.0.24-2ubuntu1.2_i386.deb** (assuming you are using Ubuntu 7.04 Feisty).

Run an admin enabled file browser.  Press **<alt><f2>** and type **gksu nautilus** in the box, and enter your password. Now browse to */var/cache/apt/archives* and copy **samba_3.0.24-2ubuntu1.2_i386.deb**, browse to your media device by clicking on the UP button several times and look in /media, it will be in there, as in /media/ipod or whatever, and paste it.

Eject the media device and plug it into the second machine, it will appear as a device on your desktop.

Open the device, browse to where you saved the file then simply open it (double click).  Select install from the window that opens.

Once installed, follow step 1 again on this computer to share the folder.

Plug your crossover cable in, wait a few seconds, then click on menu->Places->Network and you should now see the other computer.

---

### Post by anaconda on 2007-09-28
> **Shin_Gouki2501 said:**
> 
I mean he uses a CROSSOVER cable how save has the conenction to be?
.

Heh.. that is true.  Sounds pretty secure now that I finally got that point. But anyway ssh is probably the easiest to get going. and then sshfs on top of that.

But no point in sacrifising speed for "security" when using a direct line.

Whatever is the easiest.

---

### Post by ukripper on 2007-09-28
> **Shin_Gouki2501 said:**
> I think this is a very good example of how to NOT solve a problem. ok SSH is fine but does these tons of "very usefull" Information interested our badguyanil 
?
I think not he has two pcs  and want a fast solution and not read tons of stuff which might be interesting but not relevant...

I mean he uses a CROSSOVER cable how save has the conenction to be?

IMO badguyanil  u could also install a FTP Server but SSH with some similiar  GUi like WinSCP in Dwindows in should make the deal.

You got valid point. I have only suggested him the solution which i am using and that is  SSH. I could have mentioned NFS but keeping security in my mind i cant think of anything better.

---

### Post by hyper_ch on 2007-09-28
SSH is just quick and plain simple to setup... that's why I like it also... in Linux I have Konqueror availble that serves me as graphical interface... on windows I have WinSCP which is also free...

As said, it's quick and simple to setup and it just works.

---

### Post by badguyanil on 2007-09-28
Well ya i think i needed to specify somethings a lil more clearly! Thaks for all your help...will try out a few things and trouble you guys again with some weired questions... anyways...

Security is not imp coz both the systems are..well my own and i just need a solution which does not make me use a 2gb thumb drive to transfer files between 2 pc's ...i guess you get the picture...

just waiting for the office hours to be over to use all the information given by u guys, and get going with the 2 machines :)

---

### Post by badguyanil on 2007-09-28
> **kvonb said:**
> 
Once installed, follow step 1 again on this computer to share the folder.

Plug your crossover cable in, wait a few seconds, then click on menu->Places->Network and you should now see the other computer.

and there is no need of any ipconfigs and all!!!! if just this will do then...oh life is so easy ;)

---

### Post by sgtbob on 2007-10-02
I realize this is an older posting, but would someone explain/describe what is meant by 'a crossover cable'?  I'm trying to do the exact same thing that badguyanil was trying to do, connect two home PC's together, but no one explained what the crossover feature was. Probably simple, but to a 'noob' it isn't.

Would appreciate a reply on this.

Bob:confused:

---

### Post by ukripper on 2007-10-02
Crossover cable is different from straight cable( which is used generally by routers, hubs and switches very common/general networking). Crossover directly connects two machines together without the need of any router/hub/switch but will only connect two machine at one time. 
For technical wiki - [http://en.wikipedia.org/wiki/Crossover_cable](http://en.wikipedia.org/wiki/Crossover_cable)

---

### Post by badguyanil on 2007-10-02
i did the walktrhu as given on the below page

[http://ubuntuforums.org/showthread.php?t=561921](http://ubuntuforums.org/showthread.php?t=561921)

got everything right and could view the shared folder from the KUBUNTU machine. But am not able to create and file or folder in the same and gives me a error. Can anyone tell me if i missed something.

---

