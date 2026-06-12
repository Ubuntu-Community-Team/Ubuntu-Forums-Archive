---
title: "how to access windows network drive?"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-02-13
how can I access my shared windows folders in Ubuntu? I tried browsing my network servers but it wouldnt let me.

---

### Post by PPAAUULL on 2007-02-13
I think you have to set up Samba and then it will work. Mine actually works right out of the box.

---

### Post by syalam on 2007-02-13
Is there a way to do it without Samba?

---

### Post by tronica on 2007-02-13
you need to mount the drive localy, 

> cd /media

> sudo mkdir whatevername

> sudo chmod 777 whatevername/QUOTE]

[QUOTE]sudo mount -t cifs //ipofwindowsmachine/shareofwindowcomp /media/whatevername -o user=usernameofwinodowscomp, pass=passofwindowscomp

and your all done, and by mounting this in /media, it will show up on the desktop

---

### Post by syalam on 2007-02-13
I ust installed GSAMBAD, but I'm not exactly sure how to use it. Do I just give it all my settings and then try and view my windows folder from Network Servers?

---

### Post by balaoko on 2007-02-20
Hi, tronica,

I tried your method but the last step, "mount", failed. It sounds like the usage of mount is not correct. I maned the mount and still get no idea what to do. Is it possible for you to give us any further instructions? Thanks a lot.

> **tronica said:**
> you need to mount the drive localy, 





[QUOTE]sudo chmod 777 whatevername/QUOTE]



and your all done, and by mounting this in /media, it will show up on the desktop

---

### Post by tronica on 2007-02-20
post the error you get

---

### Post by lamalex on 2007-02-20
just install samba. it's easy and powerful.

---

### Post by tronica on 2007-02-20
yes, but mounting localy alows you to be able to stream music and video.

---

### Post by balaoko on 2007-02-20
> **tronica said:**
> post the error you get

Here it is:
two commands were used:
(1)sudo mount -t cifs //domain/computerip/Home /mnt/windrive -o user=xxx, pass=xxx
(2)sudo mount -t cifs //computerip/Home /mnt/win_d -o user=xxx, pass=xxx
reply:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Vivix729 on 2007-02-20
You know, all I had to do to access my Windows shared files was to go Places -> Network Servers, and both PCs in the house with Windows and shared folders were there, and I was able to access the files.  

I did have to use Sambe to have Windows see my Ubuntu data.

---

### Post by balaoko on 2007-02-20
BTW, samba is installed but I still get error message. I have one computer and one server that I have to access.
(1) Starting from Places/Connect to Server..., using "Browse Network", click "Windows Network", then the domain, then the computer, then input domain, userid and password. The shared fold appears, but I cannot make a link. That computer is for me only.
(2) following the same way as (1), but click the server, instead of the computer in the same domain, but an error message pops on: "The folder contents could not be displayed. Sorry, couldn't dispaly all the contents of "Windows network: xxxx"". The server is for a lot of stuffs in my department, and my folder is under the folder Home.

I can not work without accessing those folders. The IT service in my department only support windows system. Please give me some help!

---

### Post by Vivix729 on 2007-02-20
> **balaoko said:**
> BTW, samba is installed but I still get error message. I have one computer and one server that I have to access.
(1) Starting from Places/Connect to Server..., using "Browse Network", click "Windows Network", then the domain, then the computer, then input domain, userid and password. The shared fold appears, but I cannot make a link. That computer is for me only.
(2) following the same way as (1), but click the server, instead of the computer in the same domain, but an error message pops on: "The folder contents could not be displayed. Sorry, couldn't dispaly all the contents of "Windows network: xxxx"". The server is for a lot of stuffs in my department, and my folder is under the folder Home.

I can not work without accessing those folders. The IT service in my department only support windows system. Please give me some help!

Not sure about (1), but for (2), I get that exact same error sometimes, and an empty folder shows up.  Hit F5 to refresh, and it works for me almost ALWAYS.

---

### Post by balaoko on 2007-02-20
Thanks Vivix729. I will try it.

---

### Post by balaoko on 2007-02-20
after F5 several times, it still show the same error message:(

---

### Post by syalam on 2007-02-20
I tried installing GSAMBAD but I still can't access my Windows drive. Can you tell me step by step how to set it up?

---

### Post by balaoko on 2007-02-20
Just found that my computer does not have a static ip. Is it the reason that I can not access the server's folder? my ubuntu version is 6.06.

---

### Post by balaoko on 2007-02-20
It is too wierd. I removed the virtual box and vmware from my windows (I used them to be familar to ubuntu before formally installed it), The action should not affect the ubuntu at all, but the ubuntu showed some problem so I reinstall it. This time the "mount" works! Although I will continue to try to permanently mount it, the success makes me very happy!

Thank you very much for all your helps!

---

