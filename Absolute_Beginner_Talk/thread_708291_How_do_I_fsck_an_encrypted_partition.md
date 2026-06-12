---
title: "How do I fsck an encrypted partition?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Golem XIV on 2008-02-26
I have Gutsy installed on my laptop with a small /boot partition and the remainder of the disk as an encrypted LVM volume.

I had a small problem recently with the system not coming out of suspend correctly (wouldn't take any keyboard input) and I was forced to turn it off.

Apparently by turning it off I damaged something and now I have problems with DNS resolution.  I am fixing the problem, but I still want to run fsck to see what is the extent of the damage.  I'm a complete newb WRT fsck; I see I have to umount the volume before running fsck, but if I umount the root volume, how will I run fsck (or anything else, for that matter)?

I guess I could try with the Live CD but I'm not sure if it will recognize and check correctly an encrypted volume.

Any ideas?

---

### Post by airbornemist6 on 2008-02-26
I don't think your problem lies with your filesystems. I think that your video driver broke your mDNS config file. 

```
 sudo gedit /etc/nsswitch.conf
```
You should see a line like this:
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

For the sake of troubleshooting go ahead and change it to:

hosts: files dns mdns4

If that doesn't work then search the forums for suspend bugs.

---

### Post by beatryder on 2008-02-26
> **Golem XIV said:**
> I have Gutsy installed on my laptop with a small /boot partition and the remainder of the disk as an encrypted LVM volume.

I had a small problem recently with the system not coming out of suspend correctly (wouldn't take any keyboard input) and I was forced to turn it off.

Apparently by turning it off I damaged something and now I have problems with DNS resolution.  I am fixing the problem, but I still want to run fsck to see what is the extent of the damage.  I'm a complete newb WRT fsck; I see I have to umount the volume before running fsck, but if I umount the root volume, how will I run fsck (or anything else, for that matter)?

I guess I could try with the Live CD but I'm not sure if it will recognize and check correctly an encrypted volume.

Any ideas?

**[SIZE="3"]IF YOU HAVE ANY QUESTIONS ASK HERE FIRST!! I have worked with encrypted HDD's before but not LVM these steps may not work for you[/SIZE]**


To answer your question do the following:
```

$ sudo passwd root # to set a root password this is required.

```

Now log out of your user account ans switch to a terminal via CTRL+ALT+F1

log in as root using the password you just set. DO NOT USE SUDO SU!! This will be apparent why in a second.

Now you have to determine the device. So say for example we are working with the /home mount point

```

# mount | grep /home
/dev/sda4 on /home type ext3 (rw) #< yours will be different than mine but the first part is what you need.
# fsck /dev/sda4 
# mount /dev/sda4

```


If that worked then you should reboot at this point and you should be okay.

---

### Post by az on 2008-02-26
There is no need to set a root password.  You should unmount the partition before you fsck it.

---

### Post by beatryder on 2008-02-26
> **az said:**
> There is no need to set a root password.  You should unmount the partition before you fsck it.

How then would you unmount /home if that is the partition?

If you are logged in as user in the home directory, you cannot unmount a partition that is the cwd, as umount will complain that the partition is in use.

---

### Post by philinux on 2008-02-26
Using the live cd seems a good idea. :)

---

### Post by beatryder on 2008-02-26
> **philinux said:**
> Using the live cd seems a good idea. :)

That is a fantastic idea. One might also consider using the "Recovery Mode" option from the grub menu?

The reason I hadn't suggested either of those methods was simply that since his machine was already up and running, the encrypted partition would already be "opened" thus he could fsck the filesystem easily.

Now if / is the partition that is encrypted, then the liveCD or recovery mode is the way to go.

---

### Post by Golem XIV on 2008-02-26
Thanks, people, I'll try these solution(s) as soon as I get home...

---

### Post by bodhi.zazen on 2008-03-16
In case this is still questioned.

1. Boot the Ubuntu Desktop CD.

2. Install  lvm2 and cryptsetup

```
sudo apt-get install lvm2 cryptsetup
```

3. load the cyrptsetup module :

```
sudo modprobe dm-crypt
```

4. Decrypt your file system

```
sudo cryptsetup luksOpen /dev/hda5 crypt1
```

5. Get the live CD to recognize (activate) your LVM :

```
sudo vgscan --mknodes
sudo vgchange -ay
```

6. Run fsck

```
fsck /dev/mapper/<root>
```

Where <root> = your root partition (It will be the name of your LVM volume - root)

If you do not know the name, use tab completion ...

---

