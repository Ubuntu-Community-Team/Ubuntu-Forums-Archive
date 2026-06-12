---
title: "Mouting Network Folder"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-09
i am following ubuntuguide.org:

shoaibi@saber-rider:~$ sudo mount //172.30.10.8/Studentshare /media/shoaibiNetwork/ -o username=bs0426, password=pass132
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
shoaibi@saber-rider:~$ mount -a
mount: only root can do that
shoaibi@saber-rider:~$ sudo mount -a
shoaibi@saber-rider:~$ sudo rm -rf /media/shoaibiNetwork
shoaibi@saber-rider:~$ sudo mkdir /media/Studentshare
shoaibi@saber-rider:~$ sudo mount //172.30.10.8/Studentshare /media/Studentshare -o username=bs0426, password=pass132, dmask=777,fmask=777
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
shoaibi@saber-rider:~$ sudo mount //172.30.10.8/Studentshare /media/Studentshare -o username=bs0426,password=pass132,dmask=777,fmask=777
11443: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
shoaibi@saber-rider:~$ sudo mount //172.30.10.8/Studentshare /media/Studentshare -o username=pieas\bs0426,password=pass132,dmask=777,fmask=777
11452: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
shoaibi@saber-rider:~$ sudo mount //172.30.10.8/Studentshare /media/Studentshare -o username=\\pieas\bs0426,password=pass132,dmask=777,fmask=777
11456: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
shoaibi@saber-rider:~$ sudo mount //172.30.10.8/Studentshare /media/Studentshare -o username=bs0426,password=pass132,dmask=777,fmask=777
11460: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed



I am on PIEAS domain, with username bs0426 and password = pass132, still it doesn't work, any idea?
Ip of the server is correct along with the paths...

---

### Post by shoaibi on 2007-02-09
was the problem statement notclear or nobody ahs any idea about it?

---

### Post by mvaniersel on 2007-02-09
Can you explain what it is exactly that you are trying to achieve?

---

### Post by shoaibi on 2007-02-09
Hmmm just as i suspected, 

Hmmm no problem, here is my poblem:
I am trying to mount a network folder which is located on 172.30.10.8, with the name Studentshare, into /media/Studentshare at the end, under the domain PIEAS, and the login is bs0426, password is pass132, whereas the terminal doesn't allow me to mount it.....

While i wanna ask this as well that why do we need to mount network folders whereas we can still access them directly in network places???

---

### Post by shoaibi on 2007-02-09
still not clear enough?

---

### Post by mvaniersel on 2007-02-09
Yes, it is clearer now. Unfortunately I don't know the answer, I don't know much about network shares.

But be patient, difficult questions may take more than two hours to get an answer. And here is a tip: don't reply to your own question so soon, because some people on the forums look specifically for threads with 0 replies, to look for unanswered questions. If you reply yourself after only two hours, they won't be able to find it.

---

### Post by Jussi01 on 2007-02-09
> **shoaibi said:**
> Hmmm just as i suspected, 

Hmmm no problem, here is my poblem:
I am trying to mount a network folder which is located on 172.30.10.8, with the name Studentshare, into /media/Studentshare at the end, under the domain PIEAS, and the login is bs0426, password is pass132, whereas the terminal doesn't allow me to mount it.....

While i wanna ask this as well that why do we need to mount network folders whereas we can still access them directly in network places???

Ok, im not certain, but i think your command line needs to go:
```

sudo smbmount //172.30.10.8/Studentshare /media/Studentshare -o username=bs0426, password=pass132, uid=1000,mask=000
```

try that and see how you go... let us know if you have success!!


I modelled that on this thread:

[http://ubuntuforums.org/showthread.php?t=280473&highlight=samba+etc%2Ffstab](http://ubuntuforums.org/showthread.php?t=280473&highlight=samba+etc%2Ffstab)

---

### Post by shoaibi on 2007-02-10
using the command you provided gives this:

4850: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

and by the why do we need to mount?

---

### Post by shoaibi on 2007-02-10
Here is what i get by following your thread:

```

shoaibi@saber-rider:~$ sudo apt-get install smbfs smbclient
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbfs is already the newest version.
smbclient is already the newest version.
The following packages were automatically installed and are no longer required:
  libgsf-gnome-1-114
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 141 not upgraded.
shoaibi@saber-rider:~$ smbclient -L 172.30.10.8 -U%
Domain=[PIEAS] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 172.30.10.8 failed (Called name not present)
session request to 172 failed (Called name not present)
Domain=[PIEAS] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]

        Server               Comment
        ---------            -------
        ABID                 
        AHMED                Ahmad
        AMJADFAROOQ          
        B-5B7794E34D7C4      
        BOOKS                
        CAE-LAB              
        CISD                 
        DATASERVER           
        DATASTORAGE          
        DELL                 
        DELL2                
        DR-SHAHID            laser
        EXCHANGE             
        FIAZ                 
        GFV-06237D505F5      PC-I
        GLOBEL               
        IMRANKARORI          
        INPC-048             
        INPC-057             
        LAB1                 
        LASER                
        LASERPC              laser1
        LIBRARY2             
        MATERIALS1           
        MEMSPC-09            memspc-09
        MOHSIN               
        MP0607               
        N1PC---038           
        N1PC-00              
        N1PC-00083           
        N1PC-0079            
        N1PC-025             
        N1PC-033             
        N1PC-037             
        N1PC-039             
        N1PC-041             
        N1PC-042             
        N1PC-043             
        N1PC-044             
        N1PC-046             
        N1PC-047             
        N1PC-050             
        N1PC-052             
        N1PC-054             
        N1PC-055             
        N1PC-059             
        N1PC-060             
        N1PC-061             
        N1PC-062             
        N1PC-065             
        N1PC-068             
        N1PC-069             
        N1PC-071             
        N1PC-072             
        N1PC-081             
        N1PC-085             
        N1PC-086             
        N1PC-087             
        N1PC-153             
        N1PC-88              
        N1PC034              
        N1PC067              
        N2T5B7               
        NEW                  
        NIPC-051             
        OPERATORPC           
        PIEAS-1195FORKM      
        PIEAS-B47F069A4      
        PIEAS-CCPC-001       
        PIEAS-D616           
        PROF                 Moinca
        SHAKERA              
        TEST48               
        TRAVELLER            
        UETIAN               cooljatt
        WSUS                 
        WXPMACHINE           
        YAQOOB               
        YSF                  

        Workgroup            Master
        ---------            -------
        HOME                 ADEEL
        MSHOME               BUNTY
        NOGROUP              TGFDWUH6856JH6R
        PIEAS                DELL
        PIEAS.EDU.PK         N4PC-025
        SMD                  KHALIQ
        WG                   WS
        WORKGROUP            ACER-AC84C68AD2
shoaibi@saber-rider:~$ sudo smbmount //172.30.10.8/Studentshare /mdeia/Studentshare/ -o username=bs0426,password=pass132,uid=1000,mask=000
Could not resolve mount point /mdeia/Studentshare/
shoaibi@saber-rider:~$ sudo smbmount //172.30.10.8/Studentshare /media/Studentshare/ -o username=bs0426,password=pass132,uid=1000,mask=000
5043: protocol negotiation failed
SMB connection failed
shoaibi@saber-rider:~$ sudo smbmount //172.30.10.8/DATASERVER/Studentshare /media/Studentshare/ -o username=bs0426,password=pass132,uid=1000,mask=000
5073: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed
shoaibi@saber-rider:~$ sudo smbmount //DATASERVER/Studentshare /media/Studentshare/ -o username=bs0426,password=pass132,uid=1000,mask=000
5077: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

So any idea?

---

### Post by e-rebus on 2007-02-10
Maybe you need to specify the domain, PIEAS in your case. I am using a command like this to mount my university shares:
```

mount -t smbfs -o uid=1000,gid=1000,credentials=/path/to/credentials/file,workgroup=DOMAIN,dmask=777,fmask=777 //path/to/share /path/to/mount/point
```

You have to have smbfs installed for this to work.

---

### Post by shoaibi on 2007-02-10
sorry couln't understand your command, please can you use a simple one like above?

---

### Post by e-rebus on 2007-02-10
> **shoaibi said:**
> sorry couln't understand your command, please can you use a simple one like above?

```
sudo mount -t smbfs -o uid=1000,gid=1000,username=bs0426,password=pass132,workgroup=PIEAS,dmask=777,fmask=777 //172.30.10.8/Studentshare /media/Studentshare/
```

Is this better?

---

### Post by shoaibi on 2007-02-10
Results:
```

shoaibi@saber-rider:~$ sudo mount -t smbfs -o uid=1000,gid=1000,username=bs0426,password=pass132,workgroup=PIEAS,dmask=777,fmask=777 //172.30.10.8/Studentshare /media/Studentshare/
7764: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed


```
Thanks

by the by typing:
```

smb://172.30.10.8/Studentshare

```
in Run i can easily access it, means the destination exist, and also tell me why do i need mounting it?

---

### Post by mr.v. on 2007-02-10
try this:
```
mount -t smbfs //172.30.10.8/Studentshare /media/Studentshare -o rw,username=PIEAS\\bs0426,password=pass132
```

The problem is that the username specified must be qualified by the domain name under which the user account is present unless you've got a SAMBA capable PAM. In your example you used tried username=\\pieas\bs0426 which isn't the correct form. The correct form for a windows username is DOMAIN\user  BUT since you're using a UNIX shell \ is a special character that requires you to escape it with, you guessed it, another \. Therefore at the terminal to pass a program "DOMAIN\user" you actually need to type "DOMAIN\\user"

also it ain't a great idea to give out IP addresses, usernames AND passwords on a public forum...it would generally be acceptable to write //MYSERVER/MYSHARE -o username=MYDOMAIN\\MYUSER,password=MYPASS

---

### Post by shoaibi on 2007-02-10
Results: ;)
```

shoaibi@saber-rider:~$ sudo mount -t smbfs //172.30.10.8/Studentshare /media/Studentshare -o rw,username=PIEAS\\bs0426,password=pass132
Password:
9041: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

---

### Post by shoaibi on 2007-02-11
Problem still UnResolved!

---

### Post by shoaibi on 2007-02-11
First post 2 Days ago, Last post 8 hours ago,
Need immediate assistance, please please please :( :(

---

### Post by shoaibi on 2007-02-22
not solved as of yet......

---

### Post by mr.v. on 2007-02-22
The above commands work for people. My commands work for my username/password combination on my SMB server.

There are a number of things that can give you that issue.

1) your username or password is incorrect or you've erred in its case sensitivity. Perhaps theres a capital letter somewhere?

2) the domain that stores your username/password is different than the domain you're trying to login to. Here's an example. Your username/password is on the MYDOMAIN domain. The PIEAS domain you're trying to login to has a trust with the MYDOMAIN. So you'd actually need to login to do a
```
-o username=MYDOMAIN\\myusername,password=mypass
``` to login to the server in PIEAS. Check with your network administrator as to what domain your username is under

3) the IP address the server is incorrect. Are you absolutely sure that the server share Studentshare is at the ip: 172.30.10.8 ?  What is the NETBIOS name of the server? Why don't you use that (the NETBIOS name) instead of the IP address? That way you're sure even if the ip is wrong the name should be right

4) The sharename is wrong. Are you absolutely sure that Stuentshare isn't StudentShare or studentshare or studentShare or Student-Share or student-share (etc etc etc).

The generic command to mount an SMB share is
```
sudo mount -t smbfs  //SERVERNAME/SHARENAME /directory/to/mount/share/in -o username=DOMAINNAME\\USERNAME,password=PASSWORD
```
now you have to figure out what SERVERNAME is what the SHARENAME is. You have to figure out what DOMAINNAME your USERNAME is under and ensure you've got the right case for those. Make sure you're tying your password in correctly too.

when you get all that straight, it'll work for you.

Another thing to browse the sharelist to ensure you're trying to mount a share that exists do ```
smbclient -L //SERVERNAME --user=DOMAIN\\USERNAME
``` then enter password. I noticed you tried to browse the server in question and were unable because you got an access denied. If the above including your usename and password doesn't allow you to browse, you've got an issue with your username/password or perhaps are listing the wrong DOMAIN. If you do get a browse list, then your usename/password/DOMAIN are likely correct and see that the sharename is listed.

keep at it. Good luck.

---

