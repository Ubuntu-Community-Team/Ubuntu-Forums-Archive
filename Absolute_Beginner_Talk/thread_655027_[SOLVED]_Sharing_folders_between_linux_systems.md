---
title: "[SOLVED] Sharing folders between linux systems"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-12-31
Hi

I have what seems like a straightforward requirement, but I am struggling to find the answer, possibly because other people have more complex setups / requirements.

I have two computers, both running Gutsy (although one is dual boot Vista and the other is dual boot XP). Both boxes and OS's have multiple users (i.e. all my family members) with identical login names on each machine / OS.

For now, all I want to do is create a folder on one machine (e.g. 'work') which I (and only I) can access as read / write from both machines. I specifically don't want any windows access for now, in order to understand how the linux setup works before complicating the issue. ( so far I have had success with sharing folders between everyone both with samba and linux - it is the restriction to a single user  or controlling the user access that I have problems with)

I just want to be able to store info in one machine and access it from the other ( and vice versa) without sharing it with everyone on either machine. A simple step-by-step HOWTO would be welcome.

So I might want to create a spreadsheet in a folder on box a and access/edit it on box b, or create it on box b (in the folder on box a) and access/edit it on box a, without any other of the users on box a or box b seeing the file.

TIA

---

### Post by blueridgedog on 2007-12-31
If you create your folder called /work, then assign ownership to you, lets call you JOE for today:

sudo chown joe:joe /work

Then set the permissions of work so that only you can access it:

chmod 700 /work

Then you can create a samba share for work with something like:

[WORK]
path = /work
read only = no
browseable = yes
write list = joe
valid users = joe

---

### Post by Paqman on 2007-12-31
Well, basically what you want to do is set the permissions of that folder so that only you can access it. So give yourself read/write/execute and everybody else gets nowt. Then you want to mount that folder as a share on the other machine.

To set permissions you can use the chmod command. For example:
```

chmod -R 700 /pathto/woo

```
Sets read/write/execute permission for the owner of the directory woo, and all files/folders within it. All others are denied access

To mount a folder as a share you'll need to edit the file system table on the machine where you want to mount it. Linux systems talk to each other using NFS.
[HowTo mount NFS shares](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by HermanAB on 2007-12-31
Note that nowadays, everything is easier with NFS.  Only use Samba when you really, absolutely have to and you'll save yourself a lot of hair.  Compared to NFS, Samba is bloated, complicated, slow and full of bugs...

Cheers,

Herman

---

### Post by sdowney717 on 2007-12-31
i samba across to both windows xp and other ubuntu boxes from my ubuntu box.
even wirelessly.
just seems to work without grief yet.

right click share the folder

I tried NFS and I got permission errors so I just use what worked.

---

### Post by toupeiro on 2007-12-31
Hello ubername,

I'm going to share with you one of the easiest ways to do this, bypassing all the NFS stuff it would normally require as well as samba:  You can always lay samba over the top of this at a later time.

> sudo apt-get install sshfs

now, create a directory you want to be able to access the remote system from:  

this can be an empty directory in your home directory if you wish, or you can use sudo to create it somewhere else in your system

e.g. sudo mkdir /mnt/remote

now, we are going to make you the owner of the directory with full read write access, and no access for anybody else:
> sudo chown $USER:$USER /mnt/remote ; sudo chmod 770 /mnt/remote 

then type shfsmount username@hostcomputer:/path/to/wanted/folder /mnt/remote



If you want this to take place on a system boot:

> sudo gedit /etc/fstab 

username:password@hostcomputer:/path/to/wanted/folder /directory_to_mount_in shfs defaults 0 0


the username and password would be the username and password for /your/ account on the other system.

---

### Post by ubername on 2007-12-31
> **toupeiro said:**
> Hello ubername,

I'm going to share with you one of the easiest ways to do this, bypassing all the NFS stuff it would normally require as well as samba:  You can always lay samba over the top of this at a later time.



now, create a directory you want to be able to access the remote system from:  

this can be an empty directory in your home directory if you wish, or you can use sudo to create it somewhere else in your system

e.g. sudo mkdir /mnt/remote

now, we are going to make you the owner of the directory with full read write access, and no access for anybody else:


then type shfsmount username@hostcomputer:/path/to/wanted/folder /mnt/remote



If you want this to take place on a system boot:



username:password@hostcomputer:/path/to/wanted/folder /directory_to_mount_in shfs defaults 0 0


the username and password would be the username and password for /your/ account on the other system.

Sorry, v dumb here. I get confused about which commands I run on each computer.

I have two boxes

DellE520
Dell4600

I would like the files to be on DellE520


I have a user called john on both boxes (so a /home/john folder on both boxes). I would like to have a folder on DellE520 called /home/john/work which I can access from Dell4600.


I can create that and make it only accessible to john on the E520, but I can't seem to share it only with john on the Dell4600

If you can help that would be great

---

### Post by The Cog on 2008-01-01
Yet another way:

If you install openssh-server on the machine serving files, you can then gain access to all your files from your client nautilus by entering an address like this into the address bar:
ssh://1.2.3.4
Now you can drag/drop files much like an FTP client. The remote machine is not fully mounted onto your filesystem to make the files look local though. If you don't need a full mount, this is easiest in my opinion.

---

### Post by ubername on 2008-01-01
OK here's a short spec of what I would like, which probably demonstrates my complete lack of the philosophy behind linux security:

Go to somewhere like synaptics and install my wished for package: network-share-manager. System automatically detects if any sharing / network components (samba / NFS / sshfs shfs-utils etc.) are required and advises installation of these.

successful install results in an option under System>Administration called 'Network Share manager'

Click on that.

Asked for sudo password for current computer.

Screen shows 'Computers on your network' 

click on a computer

asked for sudo password on that computer

Displays browsable / drill-able list of drive(s) contents on that computer

click on required  drive or folder or file

screen comes up asking

'which computers/users should share this?'

Displays list of computers again

ctrl-click on each computer which you would like to share with

screen comes up with list of users (on each computer) arranged by each selected computer.

default for each user is 'no access'

Check box options available for each user to read or read/write or execute the chosen drive or folder or file.

Click 'OK'

Job done

Now the chosen users have the chosen access to the chosen files  or folders or drives on the chosen computers.

Should be easy. I just need to learn linux, samba, nfs, the linux security model, a programming language, how to package things, how to add them to repositories and I'm done.

Unless someone can help?

TIA
(and please don't take me too seriously: I would love this but am trying to say I realise it is no small task)

---

### Post by ubername on 2008-01-01
> **The Cog said:**
> Yet another way:

If you install openssh-server on the machine serving files, you can then gain access to all your files from your client nautilus by entering an address like this into the address bar:
ssh://1.2.3.4
Now you can drag/drop files much like an FTP client. The remote machine is not fully mounted onto your filesystem to make the files look local though. If you don't need a full mount, this is easiest in my opinion.

Thanks cog

I installed openssh-server on the box with the files on it I want.

I than went to the other box and typed ssh://1.2.3.4 (where 1.2.3.4 is the IP address of the other machine, I presume)

I got (see thunbnail: I don't know how to put it in stream, as it were)


Also I don't see how this method restricts the access to specified users.

But thanks for the help.

---

### Post by toupeiro on 2008-01-01
> **ubername said:**
> Thanks cog

I installed openssh-server on the box with the files on it I want.

I than went to the other box and typed ssh://1.2.3.4 (where 1.2.3.4 is the IP address of the other machine, I presume)

I got (see thunbnail: I don't know how to put it in stream, as it were)


Also I don't see how this method restricts the access to specified users.

But thanks for the help.

It really doesn't...  You are just doing an ssh connection using this method.

That is why I suggested a mount, because with a mount, you have to mount the directory on the other computer to a directory on the computer you are using.  This gives you the ability to set the permissions on the directory on your computer to allow and restrict certain people or groups of people.

Sorry, I forgot about the fact that ubuntu does not have ssh-server installed by default.  but now that you have it installed, my method should work.


> shfsmount john@DellE520:/home/john/work /mnt/remote 

if you can't get name resolution, use the IP address of DellE520.  to find out your IP address, open a terminal on DellE520 and type: ifconfig

This will show you all of your network adapters and their information.  Your network adapter is most likely eth0 or eth1.  You are looking for a field called inet_addr:xxx.xxx.xxx.xxx where x = numbers that make up your IP address

so to use an IP address instead of a name, it would be:

> shfsmount [email]john@xxx.xxx.xxx.xxx[/email]:/home/john/work /mnt/remote 

hope this helps

---

### Post by g2g591 on 2008-01-01
you can share folders really incredibly easy in KDE, incase any Kubuntu users are reading this, system settings -> shareing , install nfs-kernel-server on both machines first though

---

### Post by The Cog on 2008-01-01
Nah, you type the address into nautilus, not firefox. See attached picture

---

### Post by toupeiro on 2008-01-01
> **g2g591 said:**
> you can share folders really incredibly easy in KDE, incase any Kubuntu users are reading this, system settings -> shareing , install nfs-kernel-server on both machines first though

the problem with using pure NFS without having a domain where you can use a netgroups file is that you can't get granular with the users.  You have to allow hosts.  My method let you apply user and group permissions to a mounted folder.

---

### Post by toupeiro on 2008-01-01
> **g2g591 said:**
> you can share folders really incredibly easy in KDE, incase any Kubuntu users are reading this, system settings -> shareing , install nfs-kernel-server on both machines first though

the problem with using pure NFS without having a domain where you can use a netgroups file or just an SSH **connection** without a **mountpoint** is that you can't get granular with the users access.  with NFS and no netgroups, you are allowing all users on that host to connect to your NFS share, depending on your assumptions of the UIDnumber and GID number of accounts on both computers.  My method with sshmounting lets you apply user and group permissions to a mounted folder.  So, by doing a chmod 770 on the directory, and with both UID and GID being his, nobody, even with ssh, can see the directory unless they have the power to become root.


You can do the same NFS sharing thing incredibly easy in Ubuntu by going to sytem -- administration -- shared folders, but it would not give him the access control he is asking for.

:edit: sorry for the dual post :-(

---

### Post by ubername on 2008-01-01
> **toupeiro said:**
> the problem with using pure NFS without having a domain where you can use a netgroups file or just an SSH **connection** without a **mountpoint** is that you can't get granular with the users access.  with NFS and no netgroups, you are allowing all users on that host to connect to your NFS share, depending on your assumptions of the UIDnumber and GID number of accounts on both computers.  My method with sshmounting lets you apply user and group permissions to a mounted folder.  So, by doing a chmod 770 on the directory, and with both UID and GID being his, nobody, even with ssh, can see the directory unless they have the power to become root.


You can do the same NFS sharing thing incredibly easy in Ubuntu by going to sytem -- administration -- shared folders, but it would not give him the access control he is asking for.

:edit: sorry for the dual post :-(

Thanks for the help Toupeiro

I got quite excited until I got:

sudo shfsmount john@192.168.2.5:/home/john/DellE520 /mnt/remote
john@192.168.2.5's password: 
shfsmount: shfs filesystem not supported by the kernel

That took me down a bit. I googled and it seems as if shfsmount doesn't work on gutsy. I followed some steps here [http://www.debian-administration.org/articles/30](http://www.debian-administration.org/articles/30) 

so I did:

sudo module-assistant build shfs 

and got a load of error messages about things being deprecated.

such as 

In file included from /usr/src/modules/shfs/Linux-2.6/dcache.c:24:         &#9646; 
 &#9474; /usr/src/modules/shfs/Linux-2.6/shfs_fs.h:76: warning: ‘kmem_cache_t’ is   &#9618; 
 &#9474; deprecated                                                                 &#9618; 
 &#9474; /usr/src/modules/shfs/Linux-2.6/shfs_fs.h:77: warning: ‘kmem_cache_t’ is   &#9618; 
 &#9474; deprecated                                                                 &#9618; 
 &#9474; /usr/src/modules/shfs/Linux-2.6/shfs_fs.h:78: warning: ‘kmem_cache_t’ is   &#9618; 
 &#9474; deprecated               

and then


 make[2]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'               &#9618; 
 &#9474; make[1]: *** [binary-modules] Error 2                                      &#9618; 
 &#9474; make[1]: Leaving directory `/usr/src/modules/shfs'                         &#9646; 
 &#9474; make: *** [kdist_build] Error 2    

I hope to solve things but it won't be tonight. Thanks for all your help. I have to go to work tomorrow so it may be some time before I get back. Cheers,

---

### Post by ubername on 2008-01-03
> **Paqman said:**
> Well, basically what you want to do is set the permissions of that folder so that only you can access it. So give yourself read/write/execute and everybody else gets nowt. Then you want to mount that folder as a share on the other machine.

To set permissions you can use the chmod command. For example:
```

chmod -R 700 /pathto/woo

```
Sets read/write/execute permission for the owner of the directory woo, and all files/folders within it. All others are denied access

To mount a folder as a share you'll need to edit the file system table on the machine where you want to mount it. Linux systems talk to each other using NFS.
[HowTo mount NFS shares](http://ubuntuforums.org/showthread.php?t=249889)

Hi

Thanks for this.

Tried it part of the way, but then realized it wasn't going to give me control over which users on the client machine could access the folder, unless I've missed something)

My need is really simple:

I have a folder called e.g. work on one computer (box_a) which only one user on that computer (stan_a) can access r/w

I would like another user (stan_b) on a different computer (box_b) to also have r/w  access to it.

Have I missed something really simple? It seems to me that my need is one of the simplest. I can't believe I have to get into compiling stuff, editing config files etc just to do that.

(But I will if I have to)

---

### Post by ubername on 2008-01-04
Sorry to 'fluff' (as I think posting unnecessarily is called) , but would love to see some more help.

---

### Post by stump138 on 2008-01-04
You can go an alternate route, but it may simply be too much work for the small size of your network. If you are looking for a fairly well documented alternative, you can try autofs and ldap.  It will allow you to control users and groups, as well as authenticate and login to a centeralized server. 

This can be a great deal of work, as you'd have to setup NFS, openldap, autofs, then configure PAM and gnome/kde for ldap login.  This would give you a measure of access control w/o using netgroups.  It will allow for roaming desktops, and automounts of your network shares with access control.

---

### Post by ubername on 2008-01-04
> **stump138 said:**
> You can go an alternate route, but it may simply be too much work for the small size of your network. If you are looking for a fairly well documented alternative, you can try autofs and ldap.  It will allow you to control users and groups, as well as authenticate and login to a centeralized server. 

This can be a great deal of work, as you'd have to setup NFS, openldap, autofs, then configure PAM and gnome/kde for ldap login.  This would give you a measure of access control w/o using netgroups.  It will allow for roaming desktops, and automounts of your network shares with access control.

Thanks for this.

Can the centralised server be one of my current client machines? (you can see how little I know about *nix). 

I'm sure it is overkill. Am I really asking too much of the current security model to let a single user on a number of machines on a network have exclusive access to a folder?

P.S. this is not an attempt to surreptitiously criticise *nix, I just don't know. It seems a straightforward requiement to me.

---

### Post by stump138 on 2008-01-04
The answer to your first question is, yes, it can be done:)  That said, It is overkill for the amount of people you want to give access.

You can share a folder very easily with NFS.  You don't need all of the fluff and you can automount it if you wanted to go that far.  Since this seems to be a home network, simply setup NFS-kernel-server on the machine that hosts the shared folder.

You have to be sudo on the computers to nfs mount if you aren't using ldap/autofs/fstab mounting.  so if you are the only person on your network with sudo priviledges, then it really isn't a problem at all:)

There is a great NFS how-to [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

---

### Post by ubername on 2008-01-04
> **stump138 said:**
> The answer to your first question is, yes, it can be done:)  That said, It is overkill for the amount of people you want to give access.

You can share a folder very easily with NFS.  You don't need all of the fluff and you can automount it if you wanted to go that far.  Since this seems to be a home network, simply setup NFS-kernel-server on the machine that hosts the shared folder.

You have to be sudo on the computers to nfs mount if you aren't using ldap/autofs/fstab mounting.  so if you are the only person on your network with sudo priviledges, then it really isn't a problem at all:)

There is a great NFS how-to [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

Thanks, I'm tantalizingly close...

You are quite right, it is a home network, with usually two computers on it (barely deserves the name 'network')!

AFAIK I am the only user on either machine with sudo rights.

Followed the HOWTO on the server box (where the files are) then ran this on the box I want to access the files from:

john@Dell4600:~$ sudo mount 192.168.2.5:/home/john/DellE520 /home/john/DellE520
mount.nfs: 192.168.2.5:/home/john/DellE520 failed, reason given by server: Permission denied


Help?

---

### Post by ubername on 2008-01-04
> **ubername said:**
> Thanks, I'm tantalizingly close...

You are quite right, it is a home network, with usually two computers on it (barely deserves the name 'network')!

AFAIK I am the only user on either machine with sudo rights.

Followed the HOWTO on the server box (where the files are) then ran this on the box I want to access the files from:

john@Dell4600:~$ sudo mount 192.168.2.5:/home/john/DellE520 /home/john/DellE520
mount.nfs: 192.168.2.5:/home/john/DellE520 failed, reason given by server: Permission denied


Help?


Hooray 'tis done!

I haven't done a full test yet to ensure other users can't access the share, but since it asks me for a password (twice!?) I'm happy enough. I used various posts to get here, so thanks to all, but stump138 seemed to get me over the final hurdle (f only I'd read the NFS howto properly).

I ended up using that and the 'connect to server..' option under 'places'.

Now when I boot I have the share in my 'places' menu and when I click on it I am asked for my password, then again asked for my password. This could be because I haven't got it set up right, or because it needs the p/w  for sudo on this machine then the p/w for the user/folder on the 'server' machine. should be easy to test, but I am very happy at the moment!

Thanks all.

---

### Post by stump138 on 2008-01-04
big grats on the success:)  Sorry to get back late as I was out after work for a bit:)  Then connect to server function works just fine.  I generally use automounts or the terminal for NFS mounts, so I'm not familiar with the GUI aspects(I'll have to look at it :) ) to see why you are prompted for so many passwords.

If you were having problems using a command line, it is most commonly do to differing uid's between your accounts on each computer.  You can get your uid number under the user and group tabs and going through your user account properties.

---

