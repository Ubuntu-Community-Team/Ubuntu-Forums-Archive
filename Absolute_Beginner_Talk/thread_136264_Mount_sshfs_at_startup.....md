---
title: "Mount sshfs at startup...."
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2006-02-25
sudo mount -a
```

mount: wrong fs type, bad option, bad superblock on sshfs#todd@desk:/mnt/H/Music/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

fstab:
```

sshfs#todd@desk:/mnt/H/Music/   /home/todd/Music/       fuse     defaults       0       0

```

After it fails in startup, i run the following and it works fine
```

sshfs desk:/mnt/H/Music /home/todd/Music/

```

Any ideas why it fails on boot?

---

### Post by nikopol on 2006-02-25
Try removing the trailing / from the 
/mnt/H/Music/   /home/todd/Music/  in fstab

Also make sure you hit a return at the end of that line in fstab file (i.e. there is a blank final line in the file).

Then try to remount it by doing
```

sudo umount /home/todd/Music
sudo mount /home/todd/Music

```

---

### Post by Todd_Z on 2006-02-25
same error

```

sshfs#todd@desk:/mnt/H/Music    /home/todd/Music        fuse       defaults        0       0
(blank line)

```

---

### Post by nikopol on 2006-02-25
Mmmm not sure - it all looks correct to me.

---

### Post by hizaguchi on 2006-03-06
I'm having the same problem.  From my internet surfage, its looking like you need sshfs version 2.4 to get support for mounting from fstab.

```
sshfs -V
```
Tells me I have version 1.1.  Maybe an updated version will fix the problem.

---

### Post by hizaguchi on 2006-03-06
Ok, I can't get fstab to like the sshfs line, so instead I've written some simple little bash scripts to mount my ftp locations with just a click.  Now maybe if I could figure out how to use a public key I could get rid of those annoying password prompts and add my scripts to my startup apps.

---

### Post by chantra on 2006-04-27
Hi,

check out my tutorial on how to use [sshfs, fuse and fstab]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab").
The reason it didn't work was that mont.sshfs was not present.
hope this helps,

---

### Post by lx73 on 2006-04-28
Chantra,

thank you SO much for providing the updated version of fuse-utils, containing mount.fuse. It works, but there are 2 problems associated with it:

1. Anything else but "defaults" in /etc/fstab seems to fail (like user,noauto)
2. The sshfs mount points are not shown in the "computer" location of nautilus, presumably due to the # in the line

Any ideas on how to get around these?

---

### Post by chantra on 2006-05-02
> 1. Anything else but "defaults" in /etc/fstab seems to fail (like user,noauto)
Yep, I found the same. Maybe the mount.fuse can be rearranged in order to accept different arguments.
> 2. The sshfs mount points are not shown in the "computer" location of nautilus, presumably due to the # in the line
Maybe the best is to tell this to the fuse developper on [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/) . This guys might be able to take this into account for their next release.

---

### Post by jis on 2006-10-31
> **chantra said:**
> Hi,

check out my tutorial on how to use [sshfs, fuse and fstab]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-from-etc-fstab").
The reason it didn't work was that mont.sshfs was not present.
hope this helps,

The link does not work.

---

### Post by chantra on 2006-11-05
hi jis,
sorry , I changed my site from wordpress to drupal, as a result some links did not work anymore :s
Here is the new link: [sshfs, fuse and fstab]("http://www.debuntu.org/2006/04/27/39-mounting-a-fuse-filesystem-form-etcfstab")
Hope it works now :)

---

### Post by SuperMike on 2006-12-01
So, connecting two Ubuntu systems, the /etc/fstab would look sort of like this:

```
sshfs#my-remote-user@my-remote-host:/ /mnt/remote fuse defaults 0 0
```

But how do I supply the password automatically?

---

### Post by chantra on 2006-12-01
Hi SuperMike,

So far
```
sshfs#my-remote-user@my-remote-host:/home/my-remote-user /my-local-filesystem/remotefs fuse user,noauto 0 0
```
allow you to inform fstab not to mount your remote filesystem at boot time, but still easily mount your remote filesystem when needed with:
```
mount /my-local-filesystem/remotefs
```
But, I believe, you could use rsa or dsa key authentification.
During boot, the filesystem should be mounted by root so you should make the remote host accept key authentification for root.

---

### Post by chantra on 2006-12-01
Forgot to mention.....
This might not be neither secure nor convenient as the mounted filesystem will be owned by root

---

### Post by SuperMike on 2006-12-01
Oh, I get it. Thanks.

---

### Post by leetcharmer on 2008-03-24
```
sshfs#root@192.168.100.15:/vmfs/volumes/storage1 /mnt/15 fuse user 0 0
sshfs#root@192.168.100.17:/vmfs/volumes/47b18307-b1268944-6f9d-001d0932cccb /mnt/17 fuse user 0 0
sshfs#root@192.168.100.20:/vmfs/volumes/storage1 /mnt/20 fuse user 0 0
```

This isn't mounting automatically at bootup.  I have to do mount /mnt/15 && mount /mnt/17 && mount /mnt/20 in order for it to mount (I don't need passwords because of ssh keys).  Any ideas how to get it to mount automatically?

---

