---
title: "Move /usr/bin to another drive"
date: 2008-01-27
forum: Apple Intel Users
---

### Post by wbetters on 2008-01-27
OK, I am not a complete newbie to Ubuntu or Linux, but I am nervous about doing what this post is in reference to.

I have Ubuntu 7.10 Gutsy running in a VM on my MacBook with vmware-tools installed.  Works flawlessly!  I have all the updates and upgrades installed via apt.  I originally only setup the virtual hd for 10 gig.  Once I installed everything I liked I was running out of space.  So, I opened the settings in VM Fusion 1.1 and added a 30 gig virtual scsi.  Then used gparted to create an extended logical partition (/media/linuxstore).  I edited the fstab to mount the logical on boot. No problem...  Now I have an additional 30 gig available to this linux system.  However, now I want to move the entire /usr to the new drive...  I have read a few posts about doing it, but I am still pretty nervous about it because I am afraid all my links and desktop menus in (e, kde, and gnome) will be broken,

Can someone please tell me the best way to do this?  Please be explicit...  Your help is greatly appreciated...  If all else fails I will just recreate the VM with larger initial max HD, however it will take forever to re-set this vm backup.

---

### Post by incubus on 2008-01-27
wbetters,

That's understandable, I would be very worried myself.  But are you sure you need to do this?  Can't you move and mount the home directory in the other drive, for example?  Also, google around and you'll see some discussion on how to resize a vmware virtual disk.

incubus

EDITED: I deleted my instructions, because they could cause harm to an installation.  Moving /usr/bin is a very involved process.  Read wbetters' post.

---

### Post by wbetters on 2008-01-27
Thanks incubus...

I found an explanation on how to expand my virtual disk using a command line tool in VM Fusion.  I am doing it right now...  My only question is whether or not Ubuntu Linux will see the entire size of the partition or just what was originally created at install.   I think I will have to use gparted and expand the logical partition if gparted lets you do that.  I appreciate your help and if all else fails I will try your method of binding after copy.

---

### Post by wbetters on 2008-01-28
OK, here is an update for those that are watching this post...

I was not able to increase the partition with gparted.  I was able to increase the size of the virtual disk with vmware fusions command line tool.  It leaves unparitioned space on the disk.  Once Ubuntu or any linux distro has been installed (especially if you let it do it automatically with the install partitioner) it creates a swap partition right after the system partition.  This would require partition rearrangement.

Does anyone know of a tool in either MAC or linux to rearrange linux partitions?

Also, I did what incubus suggested with editing the fstab and binding after I copied /usr/bin.  Be very CAREFUL if you do this, especially after copying /usr/bin.  It is a good thing I copied my VM before I did this.  I screwed-up the first time.  Sudo fails to work on reboot....  Before you reboot you must manually reset the owner and permissions of to sudo and the new /usr/bin.  Even if you ls- l the new sudo it looks ok, but IT IS NOT!  Search for other posts on the settings and commands. I forgot them already.  You also have to recreate one of the link files in the directory because it WILL NOT copy.

I was not able to figure out how to boot back into my Live CD of Ubuntu.  If I could have doen this then I could have reapired the fstab temporarily to sudo again and edit teh settings on my new .usr/bin and sudo.  All of this is because there really isn't a root in ubuntu.  I WANT to be able to SU damnit!  Does anyone know how to boot into the LIVE CD after you have installed a VM?

Hope this posting helps someone else.  Thanks again to incubus!

---

### Post by cyberdork33 on 2008-01-28
> **wbetters said:**
> Does anyone know of a tool in either MAC or linux to rearrange linux partitions?

> **wbetters said:**
> Does anyone know how to boot into the LIVE CD after you have installed a VM? I think the issue is that you are trying to rearrange the partitions from the running partition. You cannot do this. You need to boot from a live cd and make changes. (you cannot resize a mounted partition).

I ran into the boot a cd after an OS installed issue just awhile back, I didn't find a solution... Instead, I pulled the virtual disk file and made a backup (just incase), then created a VM in Q.app (using the VMWare disk image), which you can force to boot from CD, made the changes I wanted to the system, then put the virtual disk image back where it goes, and restarted VMWare.

---

### Post by incubus on 2008-01-29
wbetters,

Hmm, very good point, I hadn't thought about those issues.  If you don't mind, I will erase my post, before somebody else runs into those problems.  Copying /usr/bin would really involve a lot of expert work (it can be done, but is it worth it).

Regarding partitioning, my reaction is exactly what cyber said: the partition can't be mounted.  Now here's where you get the advantage of a virtual machine, it's pretty easy to load something else, like booting from a disk, without having to reboot your actual machine.

incubus

---

### Post by incubus on 2008-01-29
wbetters,

I'm thinking, what if you backup everything into a tar file, and restore the whole thing into the new virtual disk?  In theory, a linux installation really is just copying, but as you mentioned, with proper permissions and links.

Something in these lines:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I think I've seen another tutorial on the ubuntu wiki, but I can't find it now.  This is not moving /usr/bin, but it could solve your problem, I believe.

incubus

---

### Post by incubus on 2008-01-29
Along the same lines, but without having to compress/decompress (tar and gzip):
[http://www.linux.com/base/ldp/howto/Hard-Disk-Upgrade/index.html](http://www.linux.com/base/ldp/howto/Hard-Disk-Upgrade/index.html)

incubus

---

### Post by cyberdork33 on 2008-01-29
> **incubus said:**
> wbetters,

I'm thinking, what if you backup everything into a tar file, and restore the whole thing into the new virtual disk?  In theory, a linux installation really is just copying, but as you mentioned, with proper permissions and links.

Something in these lines:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

I think I've seen another tutorial on the ubuntu wiki, but I can't find it now.  This is not moving /usr/bin, but it could solve your problem, I believe.

incubusIn fact, this would be exactly how a gentoo system is installed.

---

### Post by wbetters on 2008-01-29
Thanks for the help guys...  I think I am going to try the moving thing...  I have it working fine now after copying /usr/bin.  It wasn't that involved, but it does take some knowledge and tweaking.  I understand why you removed your post incubus.

Thanks for the suggestions and help.

---

