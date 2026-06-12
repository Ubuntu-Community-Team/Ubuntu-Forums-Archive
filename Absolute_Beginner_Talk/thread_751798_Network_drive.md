---
title: "Network drive"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by onana on 2008-04-10
Here's my problem:

I have an iomega home network hard drive. I can't see it in the network. It does have it's own IP address. I can access the configuration utility by opening my browser but I can't see or mount the drive.

I don't know how to change my network name (I assume it's workgroup by default)

I also have an XP system that has a shared folder with read and write permissions to the network.

---

### Post by PointyWombat on 2008-04-11
Based on what I've seen in the past, a lot of home network  drives requires Windows drivers in order to work. It may not be not a true NAS device. What model is it?

---

### Post by hyper_ch on 2008-04-11
Do you have samba installed?

---

### Post by njparton on 2008-04-11
If you're connected to it over ethernet and not a USB connection then drivers shouldn't be necessary.
 
Do you have ntfs-3g installed and operating?

---

### Post by PointyWombat on 2008-04-11
> **njparton said:**
> If you're connected to it over ethernet and not a USB connection then drivers shouldn't be necessary.


You would think that, but there are some so-called network drives available that don't work with linux because they rely on an intermediate windows driver. The question is, is this one of those?

oana, you could install nfs-common then query if see if it's exporting anything via NFS.

```
sudo apt-get install nfs-common
```

then

```
showmount -e <ip of your device> 
```


There may be other ways, but this is what I know of.

---

### Post by onana on 2008-04-11
the model is an iomega Home Network Hard Drive

I just tried the showmount command and nothing happened

it came with an install disk, so would you need to run that in wine?



[EDIT]

I just tried to run the install disk with it in wine and it gave me the error "no network"

---

### Post by onana on 2008-04-11
> **hyper_ch said:**
> Do you have samba installed?

Yes samba is installed but all the explanations I've read to set it up are way beyond me so I know nothing about configuring it

---

### Post by PointyWombat on 2008-04-11
When you log into the network driver interface, you should be able to setup some shares. You'll probably need to specify which hosts can either see the share in either a read only or read write mode. once you specify a share, you should be able to mount that share from your ubuntu box.

---

### Post by onana on 2008-04-12
> **PointyWombat said:**
> When you log into the network driver interface, you should be able to setup some shares. You'll probably need to specify which hosts can either see the share in either a read only or read write mode. once you specify a share, you should be able to mount that share from your ubuntu box.

I dont understand what you mean. I have very limited experience with ubuntu and have even less experience with network drives. 

The cd says to use it in every computer that is going to access the drive. I've done that and have no idea what to do from there.

---

### Post by onana on 2008-04-13
Ok it took a few days but I have been able to see the drive in wine but it won't let me mount it. I get the error "no network"

How do you mount a drive on it's own IP address

---

### Post by njparton on 2008-04-14
Scroll to the bottom of this current thread:
 
[http://ubuntuforums.org/showthread.php?t=752149](http://ubuntuforums.org/showthread.php?t=752149)

---

### Post by onana on 2008-04-18
ok, I followed all of the links and I still don't get a listing of the files on the external drive or I get an error that I can only mount if logged in as root.

I am a complete beginner and all of the instructions has gotten very confusing and now I'm lost as to what to do

---

### Post by redbob on 2008-04-19
If you wan to mount a network folder on a local folder, it necessary to sudo it. Type > mount --help to take an idea about mounting shared folders.

---

