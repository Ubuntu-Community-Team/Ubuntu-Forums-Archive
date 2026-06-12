---
title: "Moving a linux-swap partition..."
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by pommattski on 2006-03-13
Hi all, 

I think I know how I'm ging to do this, but I guess I'm after clarification...

I'm currently dualbooting Ubuntu and WinXP, both on 1 (IDE 80GB) hard drive.
I've now added a second drive (SATA 300GB) to use mainly for media storage.  
I gather that I'd benefit from having the linux-swap partition as the first partition of this drive.
So (using Gparted on a Kubuntu Live CD - which I found very easy to use) I've created a 1.5GB linux-swap partition at the start of the new drive.

So...  When I next boot into Ubuntu, should I just edit the drive allocated to linux-swap in /etc/fstab??...  Can I then just restart then delete the original swap partition from the 1st drive?...  Is there anything else I should know?

Cheers, 
Matt.

---

### Post by mlind on 2006-03-13
I suggest you have grub backup on floppy or Ubuntu's cd somewhere in case
grub gets confused about parititions if you modifly existing partition table.

If you've already done it, then no problem. Changing swap to other patition should
work just as you described, correcting /etc/fstab entry.

---

### Post by pommattski on 2006-03-13
Thanks for that, mlind.

Yes, I do have an Ubuntu CD around... hope I won't need it though!
I'll let you know how I go.
Cheers. Matt.

---

### Post by pommattski on 2006-03-14
Just a quick update to say - Yes that worked, no problems.

Now I've done that, I have another query...
I'd like to move my main Ubuntu partion, which is currently on a primary, onto a logical drive on an extended partition.
Can I (simply!- or is that the wrong word) copy everything from one partition to another, and edit the grub configuration to point to the new partition?... and if so what would be the best way for me to copy it?... Or is there more to it?

Cheers. Matt.

---

### Post by pommattski on 2006-03-14
hmmm... No. I can see that that won't work - As grub is in the Ubuntu Partition I want to move, isn't it?
How can I do this, please?

---

### Post by mlind on 2006-03-14
I don't know if parted (GParted, kpartEd) supports copying partition data,
but you can achieve this by booting from Ubuntu's cd. Not mounting your
root partition before moving the data is safer.

Boot from cd to rescue terminal, then create termporary mount points for
new and old partition in to /mnt for example, copy data and modify grub
accordingly. You (may) need to run *grub-install* or *update-grub* script,
if you change the location of the boot partition.

first hit it found from google [http://lug.mtu.edu/lists/lug-l-0302/msg00051.html](http://lug.mtu.edu/lists/lug-l-0302/msg00051.html)
describes this, but it's not very detailed.

You must use copy command that will preserve file&folder permissions
and avoid following symbolic links.

command 
```

cp -pidRv /mnt/old_drive/* /mnt/new_drive/.

```

could work, but I haven't tested it myself. I bet there's more detailed guide
on this floating around somewhere..

when you're on rescue terminal, *sudo fdisk -l* will show you available partitions.

---

### Post by Irony on 2006-03-14
First you mount the partitions in folders. For example;

[PHP]sudo mkdir /mnt/hda5
sudo mkdir /mnt/hda8[/PHP]

Thus if I have Ubuntu in hda5 I can then copy it into hda8;

[PHP]sudo rsync -aS /mnt/hda5/. /mnt/hda8/.[/PHP]

Note the dots. To carry out this I would do it from another partition. In my case I booted into my Zenwalk partition and went to root (su) and performed the instruction. You could also do it from a live cd.

I then used the Ubuntu install cd to change grub from pointing to hda5 to hda8, so that it looks for /boot/grub/menu.lst in hda8 - to do this boot from the Ubuntu install cd and type rescue at the boot prompt, then go to the new mount point *dev/disc/disc0/part8*.

You'll need to check you */etc/fstab* file in the new partition.

---

### Post by pommattski on 2006-03-16
hmmm... Thanks guys.
I seem to be having some problems though.

Using a Kubuntu live CD, I've temporarily mounted the old and new partitions - easy.  I've then used the rsync command (above), but get some errors...
> rsync: recv_generator: mkdir "/mnt/new/./var/tmp/kdecache-root" failed: No such file or directory (2)
rsync: stat "/mnt/new/./var/tmp/kdecache-root" failed: No such file or directory (2)

sent 2198534455 bytes  received 1968254 bytes  5708178.23 bytes/sec
total size is 2197257297  speedup is 1.00
rsync error: some files could not be transferred (code 23) at main.c(791)
... well, lots actually: there were pages of "no such file or directory" errors...

I was thinking I'd try the cp command above, but as I understand it, it doesn't report errors, does it?... so I wouldn't actually know if there was a probelm or not.

... not sure where to go from here!? Any ideas?

Cheers, Matt.

EDIT:  Whoops, didn't sudo!!... Think I'll try again!

---

### Post by Irony on 2006-03-16
Note once you've;

[PHP]sudo mkdir /mnt/hda5
sudo mkdir /mnt/hda8 [/PHP]

You then need to mount them;

[PHP]sudo mount /dev/hda5 /mnt/hda5
sudo mount /dev/hda8 /mnt/hda8[/PHP]

Then;

[PHP]sudo rsync -aS /mnt/hda5/. /mnt/hda8/. [/PHP]

Don't forget the dots.

You can then point grub to the new */boot/grub/menu.lst* in hda8 by using the install disc in rescue mode. What I would do first though is add an entry in your */boot/grub/menu.lst* in hda5 first just to see if the new hda8 Ubuntu will boot up. Something like this;

[PHP]title		Breezy 5.10, hda5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Breezy 5.10 copy, hda8
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot[/PHP]

You'll have to look a your menu.lst to see the exact wording.

---

