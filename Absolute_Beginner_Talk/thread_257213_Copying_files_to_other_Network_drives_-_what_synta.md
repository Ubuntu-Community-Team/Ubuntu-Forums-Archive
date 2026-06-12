---
title: "Copying files to other Network drives - what syntax do I use?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-14
I want to copy some files from a Ubuntu Server 6.06 to a client computer and I do not know how to nominate the client computer's drive or directory's name.

I can see the client drive on the server using Gnome, but when I use the cp command to copy I get the following:

root@Server1:/etc/Stuff# cp *.* /jj6400/SharedDocs/
cp: target `/jj6400/SharedDocs/' is not a directory: No such file or directory

Please let me know how to nominate the client drive's name.

Thanks

---

### Post by kidders on 2006-09-14
Hi there,

What filesharing protocol are you using? For most of them, you have to mount the remote directory first!

---

### Post by Iowan on 2006-09-14
root@Server1:/etc/Stuff# cp *.* [COLOR="Red"]//[/COLOR]jj6400/SharedDocs/
*Might* be as simple as the extra slash... no guarantees though. (Depends on the protocol...)

---

### Post by Calculator on 2006-09-14
Thanks 

It is a Ethernet network using TCP.  I have mounted the server and alas the double dashes does not resolve the issue.

For protocol is there anything else that I should look at that would help?

:)

---

### Post by bodhi.zazen on 2006-09-14
Correct me if I am wrong, but it looks as if the directory on your client does not exist. try:

mkdir /jj6400/SharedDocs/

Or perhaps you need a full path like /home/jj6400/SharedDocs/ ?

---

### Post by Calculator on 2006-09-14
Thanks Bodhi

The /jj6400/SharedDocs/ is a networked drive that is mounted.  

This is the drive directory path that I am trying to copy files into - but alas, it does not seem to be recognised.

Any ideas on how to copy files to a networked drive?

---

### Post by kidders on 2006-09-15
Hi again,

Let's go from the beginning. Say you have a directory called "/home/calculator/shared" on one PC that you want to access from a second PC, and copy stuff into. The first thing the others and I are wondering is *how* you're sharing the directory.

> It is a Ethernet network using TCP.

Far too low-level! We were hoping for something like samba/nfs/scp/atalk/etc. Say, for instance, you're using NFS. Since you've already mounted the share, you'll have maybe typed something like:

```
sudo mount -o uid=1000,gid=1000 pc1:/home/calculator/shared /mnt/shared
```

In that case, all you'd need to do is maybe **cp -R stuff/* /mnt/shared** and you'd be done.

Find out where *your* fileshare is mounted by typing **mount** and looking for a line that looks right.

This may be a stupid question, but which computer is the "/jj6400/SharedDocs/" directory on? You see, if your PC says it doesn't exist, then it really doesn't! (ie it's not some kind of glitch.)

---

### Post by Calculator on 2006-09-16
Thanks Kidders 

I have set Samba and I have a Windows Network also setup.

I can see the other computers when I use Gnome in Ubuntu 6.06 and, in particular, with Samba I can place files into the file **share folder** that I setup.

The problem is that I need to be moving files using the command line since I have administrator rights to move files using CLI. 

Primarily I am trying to setup OpenVPN and have to move certificates across to the client computer (which is the JJ6400 computer).

On typing in **mount** I get teh following:
/dev/sda3 on / type ext3 (rw,errors=remount-ro,usrquota,grpquota)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
capifs on /dev/capi type capifs (rw,mode=0666)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=michael)
/dev/sda1 on /media/scsidisk type ext3 (rw,nosuid,nodev)

Here I don't see the jj6400 computer so it must not be mounted as you alerted me to (which raises the question of if I can see it in Gnome according to the above, this does not mean that the drive is mounted?)

To quote you:
[I]Say, for instance, you're using NFS. Since you've already mounted the share, you'll have maybe typed something like:

Code:

sudo mount -o uid=1000,gid=1000 pc1:/home/calculator/shared /mnt/shared

[B]Please let me know what the uid and the gid are?
Can I use these same commands with Ssamba?[/B]

In that case, all you'd need to do is maybe cp -R stuff/* /mnt/shared and you'd be done.

Find out where your fileshare is mounted by typing mount and looking for a line that looks right.
**Alas, there did not appear to be a line that looked right as shown above?**
[/I]

Thanks Kidders for your guidence - hopefully I will get there soon.

---

### Post by Calculator on 2006-09-17
Hi Kidders 

Thanks for your help - I am still having trouble as follows (I've tried various manifestation of your suggestions):

root@Server1:/home/michael# sudo mount -o uid=1000,gid=1000 pc1:/home/michael/samba /mnt/shared
mount: can't get address for pc1
root@Server1:/home/michael# sudo mount -o uid=1000,gid=1000 pc1:/home/michael/shared /mnt/shared
mount: can't get address for pc1
root@Server1:/home/michael# mount -o uid=1000,gid=1000 pc1:/home/michael/shared /mnt/shared
mount: can't get address for pc1
root@Server1:/home/michael# mount -o uid=1000,gid=1000 pc1:/home/michael/samba /mnt/samba
mount: can't get address for pc1
root@Server1:/home/michael#

What is "pcl"?

Thanks again for your help.

---

### Post by kidders on 2006-09-17
Hi again,

> **Calculator said:**
> Thanks Kidders 
[B]Please let me know what the uid and the gid are?
Can I use these same commands with Ssamba?[/B]

Take a look at the man page for "mount". It's quite long-winded, but it (somewhat) explains all possible mount options for you. "uid" = "user id" and "gid" = "group id".

Since you're using samba (ie Windoze filesharing) to share your stuff, my NFS-related comments are inapplicable.

> 
What is "pc1"?


"pc1" is the name of the computer you are trying to connect to, using the mount command you typed. It does not appear to exist.

At any rate, NFS filesharing (just like Samba) won't work out of the box for you ... it needs to be configured first. This is a security issue ... Linux systems don't tend to allow any kind of funny business to go on without permission!

_**How to do what you want to do:**_

Firstly, you seem to have already noticed that graphical environments like KDE and Gnome have pretty-looking filesharing interfaces that hide all the technical garbage going on underneath. These often work without actually mounting any fileshares on your system.

If you want to be able to access a fileshare using the CLI *and* your graphical environment, you need to make sure it's been mounted. For samba, you can do this with **sudo mount -t smbfs //server/sharename**. This has the following effect:

[LIST]
[*]The share must not require any authentication
[*]The mounted share may require root privileges to access
[/LIST]

You can use various mount options to control these (and other) details of how your share is mounted. The man page for "mount" lists all samba-specific mount options for you.

The next thing that might be of interest is having shares mount automagically for you. You could, for example, arrange to have a commonly-used share mounted inside your own home directory every time your system boots. You could then completely ignore the fact that the files stored in it aren't, in reality, on your own PC, and treat them as if they were. To copy stuff to and from the share, you would simply navigate to the appropriate location within your home directory. This would work both from the command line *and* Gnome/KDE.

Doing this requires the addition of a line to your /etc/fstab.

> The problem is that I need to be moving files using the command line since I have administrator rights to move files using CLI.

If you don't feel you should have to be root to copy certain stuff, this can be changed. If you like, post some more detail, and I can advise you :-)

I hope this helps!

---

### Post by cinderella on 2006-09-18
Hi Kidders!!!

U seem pretty clued up with NFS. So here is a question for u since I am just learing linux and Ubunutu.... I'm try to  install nfs-kernel-server package but realised it had some depencies such as nfs-common. So then I tried to install NFS common but it gave me this error:
Conflicts with the installed package 'nfs-common'. Bear in mind that my synaptic package manager is not working properly due to the following errors hence I am installing these packages by downloading them and then clicking on the install button. These are the errors I get from my synaptic package manager when I click on the [COLOR="Lime"]RELOAD[/COLOR] button:

[COLOR="Red"]http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[/COLOR]



Anyway i went to the synaptic manager just to check if there was another nfs-common installed and it so happened that it was installed however the version that I downloaded is the same as the version that is in the package  manager but the one I downloaded is 312Kb and the one in the package manager is 319Kb. Can u shed any light on this problem!!!!

---

### Post by Najand on 2006-09-18
For setting up your proxy server:
CLICK:
System -> Prefrences -> Network Proxy and enter your proxy information there.

---

### Post by kidders on 2006-09-18
How very odd! Something's gone all pear-shaped on you :-( My first steps would be to remove any existing NFS-related stuff and update my package database, before trying again.

By the way, HTTP error 407 means a web proxy is sitting between you and the internet that requires you to authenticate, before it will let you do anything.

---

