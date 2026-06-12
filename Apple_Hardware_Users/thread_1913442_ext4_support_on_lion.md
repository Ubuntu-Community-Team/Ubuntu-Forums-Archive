---
title: "ext4 support on lion?"
date: 2012-01-22
forum: Apple Hardware Users
---

### Post by 300Z on 2012-01-22
Is there any way to access files from a hdd formated to ext4 on osx lion?

I need to transfer some files from my laptop running ubuntu to my imac, problem is both of my external hdd are formated to ext4 and I don't have enough room to move everything to one drive and reformat the other to xfs+.

I've searched for any ways I could do this but no luck.
I setup up a virtual box on the imac and installed lubuntu on it to have access to ext4 drives but I'm having trouble installing the guest additions to be able to move the files from the virtualbox to lion. :(

I even tried booting a live cd and moving the files over but it won't let me as it will only read the imac hdd but will not write.

---

### Post by sudodus on 2012-01-22
I think of two ways to go:

1. Install the SSH server ***sshd*** in your Ubuntu computer and then run an SFTP client from the imac via your LAN

2. Make a boot CD or USB drive with Ubuntu for the architecture of your imac and run a live session. Then you can access your ext4 drive and probably also the internal drive in the imac.

---

### Post by pindar on 2012-01-22
[ext2fuse]("http://sourceforge.net/projects/fuse-ext2/") has been pretty reliable for me. It gives you read access to ext2/3/4 under OS X.

HTH

---

### Post by 300Z on 2012-01-22
> **sudodus said:**
> I think of two ways to go:

1. Install the SSH server ***sshd*** in your Ubuntu computer and then run an SFTP client from the imac via your LAN

2. Make a boot CD or USB drive with Ubuntu for the architecture of your imac and run a live session. 1. Then you can access your ext4 drive and probably also the internal drive in the imac.
Installed SSH server on ubuntu, getting ready to install filezilla but I'm gonna have to read up on how to setup and use that.

2. I did try booting an ubuntu live cd and I'm able to access the mac hdd but it won't let copy/write the files to the mac hdd. :(

---

### Post by 300Z on 2012-01-22
> **pindar said:**
> [ext2fuse]("http://sourceforge.net/projects/fuse-ext2/") has been pretty reliable for me. It gives you read access to ext2/3/4 under OS X.

HTH

I installed ext2fuse and mac-fuse (dependency) but when I plug the external hdd in it wont mount it, when I go to disk utility to try to mount it nothing happens. What am I doing wrong?

---

### Post by sudodus on 2012-01-23
> **300Z said:**
> Installed SSH server on ubuntu, getting ready to install filezilla but I'm gonna have to read up on how to setup and use that.

2. I did try booting an ubuntu live cd and I'm able to access the mac hdd but it won't let copy/write the files to the mac hdd. :(
I suggest you continue along the SSH-SFTP track :-)

---

### Post by 300Z on 2012-01-23
I installed both programs but I don't have the first clue how setup it up and use it... :( Guess I'll have a lot to read.

---

### Post by jujulian1987 on 2012-03-29
I wrote this guide.

[http://diesistmein.name/?p=30](http://diesistmein.name/?p=30)

 It's based on mac-fuse and a new project called ext4fuse. It's read only till now but perhaps this will change in the future.
Ext2fuse is not compatible with lion right now.

With best regards,
Julian

---

### Post by 300Z on 2012-03-29
> **jujulian1987 said:**
> I wrote this guide.

[http://diesistmein.name/?p=30](http://diesistmein.name/?p=30)

 It's based on mac-fuse and a new project called ext4fuse. It's read only till now but perhaps this will change in the future.
Ext2fuse is not compatible with lion right now.

With best regards,
Julian

I just tried this but got "bash: git: command not found" when I tried to enter "git clone https://github.com/gerard/ext4fuse.git" from terminal. :(

---

