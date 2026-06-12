---
title: "Would like to share a directory between my two computers"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Rinnan on 2006-06-01
I'm not really a newbie in Linux in general, but I guess I am in Linux file sharing,  and any file sharing in fact other than FTP, and this is probably an easy question, so I'll put it here.

I've got two Dapper computers, one is an x86 and the other is a PPC.  The PPC is a laptop (iBook G3) and talks to the network through a wireless router.  The desktop hooks to the same router through an ethernet cable.  Networking works well in general on both computers.  The router is where the computers get their IP addresses from, since those IP addresses are like: 192.168.0.x.  They each have a different "x" of course.  The router then talks to the cable modem and gets a unique IP for itself that looks more like an ordinary IP, and somehow magically hooks both computers to the internet.

What I want is to see a drive, or directory, or something pop up on the desktops of both machines.  The contents of the directory should be stored on the desktop system (the x86), since it's on all the time and hooked to the internet.  I want the same directory to pop up on the laptop's desktop as well, and anything changed in it  by either computer should be reflected by the other.  Both computers run only Dapper, with no other OS's on them, so I don't need any help in getting any other OS's to read/write the same directory.

How?
:confused:

---

### Post by dbd on 2006-06-01
Ubuntu or Kubuntu?

In Kubuntu I think it is as easy as right clicking a folder, properties, the "share" tab and then going to "configure file sharing" from there. Not sure about Ubuntu, maybe that is simmilar?

---

### Post by graigsmith on 2006-06-01
SSH works well. get the ssh client and server.  it's easy.

---

### Post by Nequeo on 2006-06-01
Best way to share between two Linux/Unix systems is to use NFS. You say you're not a newbie to Linux in general, so I'll give you a link to some not very newbie-ish instructions:

[https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo](https://wiki.ubuntu.com/SettingUpNFSHowTo?action=show&redirect=NFSServerHowTo)

If you get into trouble with those, post the error message and circumstances up here and we can get more specific. 

Cheers,

---

### Post by dvarsam on 2006-06-01
[QUOTE=graigsmith]SSH works well. get the ssh client and server.  it's easy.[/QUOTE]

If you are running SSH in Dapper, SSH client & Server is already installed on BOTH (your Ubuntu) Machines!!!

1. Right-click on your Top Panel

2. Select "Add to Panel..."

3. Under "Utilities", select "Connect to Server"

4. Click on the Button named "Add"

5. Click on the Button named "Close"

6. Click on the Button named "Connect to a Remote Server" on your Top Panel

7. Under "Service Type" select "SSH"

8. Under "Server", type the "Destination IP" (e.g. 192.168.1.5)

9. Under "User Name", type the User Name of the "Destination's PC"

10. Under "Name to User for Connection", give any name you would like.

11. Click on the Button named "Connect"

12. You will be asked for the "Password" of the "Destination's PC"

Congratulations, you are ALL Set!!!

Good Luck!

---

### Post by phetre on 2006-06-02
[QUOTE=dvarsam]If you are running SSH in Dapper, SSH client & Server is already installed on BOTH (your Ubuntu) Machines!!!

[...Bunch of steps...]
Congratulations, you are ALL Set!!!

Good Luck![/QUOTE]

Thanks so much for the advice, dvarsam!  I'm in the same boat as the OP (except that my laptop isn't PPC).  When I follow your steps and double-click on the desktop icon for the share, I get this error dialog:
```
Couldn't display "ssh://myusername@192.168.0.9".
The attempt to log in failed.
```
I had already successfully set up an SSH share folder for my university-provided webspace, so I don't think the problem's on my client computer.  Might the server require access through a particular port?  Or some sort of configuration?

Many thanks,
Peter

---

### Post by Rinnan on 2006-06-02
Thanks guys.  SSH worked fine.  I'm going to switch to NFS a little later to make it more permanent but for now will use SSH because it's easy.  I found out that Dapper has a nice little GUI (System -> Administration -> Shared Folders) that appears to make this easy, but even after I set everthing up with NFS I can't find the drive/folder!  So, I open the above, click "Add", select my home dir as path, and NFS.  It installs NFS for me since I hadn't already and I add the other computer as an "allowed host".  And I do the same for the other side.  However, when it's all said and done (and even rebooted) I don't see any change anywhere, neither "Places -> Computer" nor "Places -> Network Server" show anything.  I guess I'll have to do the long way as Nequeo suggested.

Ubuntu (not Kubuntu) by the way.

---

### Post by dvarsam on 2006-06-04
Dear "Rinnan",

> I found out that Dapper has a nice little GUI (System -> Administration -> Shared Folders) that appears to make this easy, but even after I set everthing up with NFS I can't find the drive/folder!

I know!!!

I have experienced the _SAME_, when I tried to "Share a Folder in Two Networked Desktops/Clients" (no Server involved).

Both of the Clients were Ubuntu v6.06 Dapper Final Release!!!

> So, I open the above, click "Add", select my home dir as path & NFS.
It installs NFS for me (since I hadn't already) & I add the other computer as an "allowed host".
And I do the same for the other side...
However, when it's all said & done (& even rebooted) I don't see any change anywhere...
Neither "Places -> Computer" nor "Places -> Network Server" show anything.

...And the funny thing, is that user "tom56" said that it SO _easy_ to do...

> Originally Posted by user "tom56":

All you need to do is right click the folder you want to share and click "Share folder", it's fairly self-explanatory from there.

My Response to the guy's suggestion, was the following:

> Ok, I tried what you said:

1. Right-click in a folder & select "Share Folder".

2. I select: Install NFS (since I am trying to share a folder in 2 Ubuntu v6.06 Linux Client Machines)

Note: Next, I also install NFS on the other Ubuntu v6.06 Client machine!

3. I select "Share with NFS"

4. I click on the Button named "Add Host"

5. Under "Allowed Hosts", I select "Specify IP Address"

6. Under "IP Address", I type "192.168.1.3"

7. I click on "Read Only" text box & click on button named "OK".

8. I switch on the Other Networked Ubuntu PC & from Menu I select "Places/Network Servers"...

So, where is my Shared Folder & why can't I see it/access it?

Thanks.

Unfortunately, I got NO response from that user!

So, "Rinnan", I did exactly as you did, only followed a different approach...

However, the Result was the _same_: NO SHARED FOLDER!!!

[quote=Rinnan]I guess I'll have to do the long way as Nequeo suggested.[/quote]

To be honest, I do NOT like the way "Nequeo" suggested!

Because:

1. lt includes a Server!

2. It is very-very complicated!

3. It icludes too many steps!

Either a simple Step-by-Step approach has to be given, or the programmers _fix_ the code involved, so that Networking 2 "Client" PCs (without an ntermediate Server), is possible!

To be honest, they need to do both of the above!

Thanks.

P.S.> If anybody knows how we can manage to "Share" a Folder in an easy (step-by-step) procedure, please tell us how! (no mounting of shared folders please...)

---

### Post by RudolfMDLT on 2006-06-04
Hi there!

I know NFS is the way to go when you network Linux to Linux, but Samba proved extremely easy to use. Give it a try if you wish. Please read some of these how to's or threads:

[http://www.ubuntuguide.org/#networking](http://www.ubuntuguide.org/#networking)
[http://librenix.com/?inode=390](http://librenix.com/?inode=390)
[http://www.linuxforums.org/forum/linux-networking/58070-nfs-problems.html](http://www.linuxforums.org/forum/linux-networking/58070-nfs-problems.html)

Sorry this post is a bit grey and rushed but I've got to run! :)

---

### Post by tkjacobsen on 2006-06-05
In order to share folders using nfs you should just go to system -> administration -> Shared folders. Then check nfs shares.. 
On a fresh dapper-install following packages should get installed:
libevent
libnfsidmap
nfs-common
nfs-kernel-server
portmap

just follow then instructions and chooce which folder to share and specify which options to user..

Afterwards check that the share is written correct to /etc/exports (the nfs-kernel-server) configuration file. And afterwards start / restart the nfs-kernel-server:
```
sudo /etc/init.d/nfs-kernel-server restart
```
And your selected folders are shared..

THE PROBLEM with nfs shares is that they does NOT show up anywhere.. Not even under Places ->Network Servers on the clients. They have to be mountet manually. (or written into fstab) from a client with access using:
```
sudo mount -t nfs hostname:/shared/folder /mount/point/on/client
```


An example can be found in the ubuntu help: system -> help -> System Documentation -> ubuntu server guide -> networking -> network file system (nfs)    (topic 4.6)

---

### Post by RudolfMDLT on 2006-06-05
I was going to follow up on my post on Samba and get you guys to try it but honestly it seems that <i>tkjacobsen</i> has solved the problem. 

Good luck and I hope that you guys get sorted!

---

### Post by dvarsam on 2006-06-07
Dear "tkjacobsen",

I followed your guide below:

> To share folders using NFS:

1. From the Menu, select "System\Administration\Shared Folders".
2. Click on the button named "Add"
3. Under "Share with:", select "NFS"
4. Click on the button named "Add host"
5. Under "Allowed hosts:", select "Specify IP Address"
6. Under "IP address", I type "192.168.1.2" (destination PC's IP)
7. Click on the button named "OK"
8.  Click on the button named "OK"
9. Install on _Both_ Dapper CLIENT PCs, the packages:
a. libevent
b. libnfsidmap
c. nfs-common
d. nfs-kernel-server
e. portmap
10. Perform a "cat /etc/exports" (on the source PC), to check that the share is written correct (to the "nfs-kernel-server" configuration file).
11. Perform a "sudo /etc/init.d/nfs-kernel-server restart" (on the source PC), to restart the "nfs-kernel-server".
12. Your selected folders are NOW shared (from the source PC)!!!

Note:
THE PROBLEM with NFS shares is that they does NOT show up anywhere...
Not even under "Places\Network Servers" on the Clients.
They have to be mounted manually (or written into fstab), from a Client (destination PC), with access using:
```
sudo mount -t nfs hostname:/shared/folder /mount/point/on/client
```


To "mount" the shared folder, I typed (on the Destination PC):

```
sudo mount -t nfs dimitris-desktop:/home/dimitris/Desktop/Shared /mnt/shared
```

And get the following error:

> mount: can't get address for dimitris-desktop

The file I want to share on the Source PC is called "Share"

And I want it to show on the Destination PC in the "/mnt/share" folder.

Any idea what I am doing wrong?

Thanks.

P.S.> I also checked on the URLs you suggested, but the Examples in there did NOT help...

---

### Post by tkjacobsen on 2006-06-07
To use the hostname it has to be in /etc/hosts else you should use the servers ip address

---

### Post by Iowan on 2006-06-07
[QUOTE=dvarsam]
mount: can't get address for dimitris-desktop  [/QUOTE] Looks like your DNS/DHCP isn't mapping hostnames to ip addresses... try the mount with the ip address - if that works, you have a new problem to solve.

---

### Post by dvarsam on 2006-06-07
[QUOTE=Iowan]Looks like your DNS/DHCP isn't mapping hostnames to ip addresses... try the mount with the ip address - if that works, you have a new problem to solve.[/QUOTE]

Thanks for your Reply!

I tried using the following:

```
mount -t nfs 192.168.1.4:/home/dimitris/Desktop/Shared /mnt/shared
```

And it worked!

Could somebody tell me what LINE I need to type to the "fstab" file to make this a permanent mount - with a password being asked every time I try to connect?

Thanks.

---

### Post by phetre on 2006-06-07
[QUOTE=phetre]Thanks so much for the advice, dvarsam!  I'm in the same boat as the OP (except that my laptop isn't PPC).  When I follow your steps and double-click on the desktop icon for the share, I get this error dialog:
```
Couldn't display "ssh://myusername@192.168.0.9".
The attempt to log in failed.
```[/QUOTE]
Okay, I solved my problem.  In case anyone else has the same experience, it was extremely simple to resolve:
[LIST=1]
[*]I needed the openssh-server package on the host machine (already had -client)
[*]I'm behind a router, so I had to forward port 22 to my machine.
[/LIST]
Now it works like a charm!

---

### Post by dvarsam on 2006-06-07
> I tried using the following:

```
mount -t nfs 192.168.1.4:/home/dimitris/Desktop/Shared /mnt/shared
```

And it worked!

I tried to add the following line to the "fstab" file:

> /192.168.1.4/home/dimitris/Desktop/Shared  /mnt/shared  ext3  username=dimitris,password=tony,dmask=777,fmask=777

But I get the following error:

> mount: special device /192.168.1.4/home/dimitris/Desktop/Shared does not exist

Could somebody tell me what LINE I need to type to the "fstab" file to make this a permanent mount - hopefully with a password being asked every time I try to connect?

Thanks.

---

### Post by rccharles on 2006-06-07
Quote:
/192.168.1.4/home/dimitris/Desktop/Shared /mnt/shared ext3 username=dimitris,password=tony,dmask=777,fmask=77 7

But I get the following error:

Quote:
mount: special device /192.168.1.4/home/dimitris/Desktop/Shared does not exist

You need to use a filesystem type of nfs.  I'd try - all on one line - :

/192.168.1.4/home/dimitris/Desktop/Shared /mnt/shared nfs username=dimitris,password=tony

Sometimes these mask are reversed:
dmask=000,fmask=000

I'd leave them at first and see if things worked.  You left out the masks on the working mount command so you shouldn't need them in fstab.  ( The fstab file contains mount commands in a slightly different format. )

the command: 

sudo mount -a 

will mount the unmounted filesystems in fstab.

Or you can just re-boot.


You can use the command:

sudo showmount -e 192.168.1.4

to see what mounts have been exported by 192.168.1.4

Robert :-\"

---

### Post by rccharles on 2006-06-07
Oh, the fstab file contians two more columns of data.  I added 0 0.  Don't know if you must have them or not.


/192.168.1.4/home/dimitris/Desktop/Shared /mnt/shared nfs username=dimitris,password=tony  0 0

Robert

---

### Post by dvarsam on 2006-06-08
Dear "rccharles",

As I said before, I wanted to make the "mount" _permanent_! (I do NOT like to perform manual mounts/umounts).

So, I tried to add the LINE you suggested inside the "fstab" file (to achieve this permanent mount - with a password being asked every time I try to connect...):

> /192.168.1.3/home/dimitris/Desktop/Shared  /mnt/shared  nfs  username=dimitris,password=tony,dmask=777,fmask=777  0  0

But I get the following error:

> mount: directory to mount not in host:dir format

The above is a different error than before!

I then followed your suggestion:

> Sometimes these mask are reversed:
dmask=000,fmask=000

...only to get the _same_ results!!!
I then tried your next suggestion:

> I would leave them at first & see if things worked.
You left out the masks on the working mount command so you should NOT need them in "fstab".
(The "fstab" file contains mount commands in a slightly different format)
So, I used:

> /192.168.1.3/home/dimitris/Desktop/Shared  /mnt/shared  nfs  username=dimitris,password=tony  0  0

...without the "dmask=000,fmask=000" part...

...only to get the _same_ results:

> mount: directory to mount not in host:dir format


I then tried:

> root@dimitris-desktop:/etc# showmount -e 192.168.1.3
Export list for 192.168.1.3:
/home/dimitris/Desktop/Shared 192.168.1.2

To see the mounts exported...

What am I doing wrong?

Thanks.

P.S.1> Sorry man, but the way NFS Shares work, STINK!!!
            It is very very PRIMITIVE!!!

P.S.2> Why do the Ubuntu Programmers make our lives miserable...?
            Couldn't they automate this man...?

P.S,3> And my IPs change every time I boot man...
            Why can't the Ubuntu programmers make this thing automated...

P.S.4> And I do NOT know yet, how to SET it work with "Fixed" IPs...
            Whenever I attempted to change this in the past, my Internet Connection would go OFF (no Internet!)

---

### Post by tkjacobsen on 2006-06-08
you have to write it as host:dir.. You forget the ":", try this:

192.168.1.3:/home/dimitris/Desktop/Shared /mnt/shared nfs username=dimitris,password=tony 0 0

---

### Post by carlosqueso on 2006-06-08
> P.S.1> Sorry man, but the way NFS Shares work, STINK!!!
            It is very very PRIMITIVE!!!

P.S.2> Why do the Ubuntu Programmers make our lives miserable...?
            Couldn't they automate this man...?

P.S,3> And my IPs change every time I boot man...
            Why can't the Ubuntu programmers make this thing automated...

P.S.4> And I do NOT know yet, how to SET it work with "Fixed" IPs...
            Whenever I attempted to change this in the past, my Internet Connection would go OFF (no Internet!)


1. I dunno...once you learn how they work, NFS shares are pretty cool, fully integrating into the filesystem of your client computer.

2.  NFS isn't made by Ubuntu, it's a seperate sourceforge project.  They probably haven't automated because it is, unless you know what you're doing, or are behind a router with a good security setup, very insecure.

4.  It's probably easier to get your router to assign fixed IP's to you network cards.  All you should have to do is go to your router's control panel and change the DHCP settings to assign a certain IP to a certain card.  I can't tell you more without knowing more about your router, but it's pretty easy on my D-Link one.

---

### Post by dvarsam on 2006-06-08
Dear "tkjacobsen",

Thank you for your reply!

I tried using:

> /192.168.1.3:/home/dimitris/Desktop/Shared /mnt/shared nfs username=dimitris,password=tony 0 0

And got:

> mount: can't get address for /192.168.1.3

I then decided to remove the "/" from "/192.168.1.3...".

So, I typed:

> 192.168.1.3:/home/dimitris/Desktop/Shared /mnt/shared nfs username=dimitris,password=tony 0 0

And got:

> Bad nfs mount parameter: username

What is wrong with my "username"?

Thanks.

---

### Post by rccharles on 2006-06-08
> 192.168.1.3:/home/dimitris/Desktop/Shared /mnt/shared nfs username=dimitris,password=tony 0 0

Why don't you try this:

192.168.1.3:/home/dimitris/Desktop/Shared /mnt/shared nfs rw 0 0

I am not sure the username and password parameters are valid.

Robert

---

### Post by dvarsam on 2006-06-08
Dear "rccharles",

> Try this:

192.168.1.3:/home/dimitris/Desktop/Shared /mnt/shared nfs rw 0 0

IT WORKED MAN, IT FINALLY WORKED!!!

Thank you!!!

> I am not sure the username and password parameters are valid.

However:
I do NOT know why it worked...?

So, basically NFS works _without_ the need of "username" & "password"?

Is such an approach considered safe?

Any ideas?

---

### Post by rccharles on 2006-06-09
[QUOTE=dvarsam]

However:
I do NOT know why it worked...?

So, basically NFS works _without_ the need of "username" & "password"?

Is such an approach considered safe?

Any ideas?[/QUOTE]

You can think that NFS uses your logon id and password.

NFS is integrated into Unix/Linux.  
1) The exporting system indicates which machines may access the shared folder.
2) NFS uses the standard Unix/Linux permissions to access the folder.  NFS assumes all users and groups are defined the same way on the server machine and the client machines.  In Unix/Linux userids and groups are mapped to numbers.  The mapping of the numbers must have the same meaning across all the machines.

Since you probably defined only one user both systems, both users got the same user number and group number.

There is a way for the server to map unknown client users and groups to a common user.

One way to see the user and group numbers is to list a file in your home directory.

cd 
ls -l
ls -n

ls -l will give you the names and ls -n will give you the numbers. (ls -nl on some systems )

To see the complete list of users and groups
cat /etc/passwd
cat /etc/groups

You might find this interesting and dangerous:
sudo bash

when done: 
exit

This puts you in the root account for multiple commands.

Robert
;)

---

### Post by dvarsam on 2006-06-09
Dear "rccharles",

Thanks for your reply!

> You can think that NFS uses your logon id & password.

Ok, this seems logical.

> Since you probably defined only one user both systems, both users got the same user number and group number.

Ok, this is correct!

I have created _only_ one user per machine!

On both of the machines I have (by using an "ls -n"):

User   Id: 1000
Group Id: 1000

And I also have (by using an "ls -l"):

PC1 - > User name: dimitris
PC1 - > Group name: dimitris

PC2 - > User name: elena
PC2 - > Group name: elena

> NFS uses the standard Unix/Linux permissions to access the folder.
NFS assumes all users & groups are defined the same way on the server machine & the client machines.
In Unix/Linux userids & groups are mapped to numbers.
The mapping of the numbers must have the same meaning across all the machines.

Ok:
User Ids & groups are mapped to numbers...
And ...all users & groups are defined the same way on all the machines...

So, you mean that:

1. A Client userid=1000 can _only_ connect to a Server userid=1000?

And

2. A Client userid=1001 can _only_ connect to a Server userid=1001?

And

3. A Client userid=1001 can _NOT_ connect to a Server userid=1000?

And

4. A Client userid=1000 can _NOT_ connect to a Server userid=1001?

So, basically if I have 2 users defined on a Client:

a. User1 with userid1=1000, and
b. User2 with userid2=1001,

User2 (with userid2=1001), can _NOT_ connect to a Server userid=1000, because the numbers do NOT match? 

And to (basically) manage to connect user2 (on the Client side) to the Server, I _must_ create a 2nd user on the Server side, so that the numbers match?:confused: 

There _must_ be some way to make possible to connect a Client userid=1001 to a Server userid=1000...:( 

Please tell me there is, otherwise I will go nutts...](*,) 

> There is a way for the server to map unknown client users & groups to a common user.

And what way/method would that be?

Thanks.

P.S.> Sorry man, but I am kind of confused...

---

### Post by u.b.u.n.t.u on 2006-06-09
Hi,

I want ubuntu box 1 to have full access to ubuntu box 2.

I have installed NFS on both, via

System>Administration>Shared Folders

box 1 = client (computer in control)
box 2 = server (computer serving data)

On the server I added "Allowed host" IP address of the client box.

On the client I entered, where the IP is of the server box:
sudo mount -t nfs 1.2.3.4:/home/name /mnt/hda

I get an error message

"sudo mount -t nfs 1.2.3.4:/home/name /mnt/hda"

I want to have complete access to that computer, both HDDs.

Thanks.

---

### Post by rccharles on 2006-06-10
[QUOTE=dvarsam]

And what way/method would that be?

[/QUOTE]

It's something called squashing...

"To squash every remote user, including root, use the all_squash option. To specify the user and group IDs to use with remote users from a particular host, use the anonuid and anongid options, respectively. In this case, a special user account can be created for remote NFS users to share and specify (anonuid=<uid-value>,anongid=<gid-value>), where <uid-value> is the userid number and <gid-value> is the group ID number."

Stolen from:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-nfs-server-config.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-nfs-server-config.html)

see also the online version of the manual pages:
[http://www.die.net/doc/linux/man/man5/exports.5.html](http://www.die.net/doc/linux/man/man5/exports.5.html)

in your server /etc/exports 
examples:
/home/joe       pc001(rw,all_squash,anonuid=150,anongid=100)
/pub            (ro,insecure,all_squash)

and the linux command:
man exports

Once you get NFS working, it is easy. Until then, it is hard.
Robert
!:o

---

### Post by rccharles on 2006-06-10
[QUOTE=u.b.u.n.t.u]
sudo mount -t nfs 1.2.3.4:/home/name /mnt/hda

I get an error message

Thanks.[/QUOTE]

We need to know the error message.

User the command:
sudo showmount -e 1.2.3.4

to see if your export worked.

Post a copy of /etc/exports

You might get more results if you started a new thread.

Robert

---

