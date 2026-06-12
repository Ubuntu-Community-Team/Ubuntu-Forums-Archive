---
title: "Mount a network drive?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Bwangster12 on 2007-12-13
I searched for this topic, but couldn't really find anything to help me...

I am a new user to Xubuntu and am finding it relatively easy to work through.

My main Windows XP computer has an external harddrive that I have shared for my gf to use wirelessely from her computer downstairs.  I understand the process of sharing the drive and then accessing the drive on a Windows computer...

But how can I access that shared harddrive using my Xubuntu laptop?  Is there a relatively easy way to kind of locate the network drive and have it show up on my desktop as if it were a harddrive on the laptop?

---

### Post by niteshifter on 2007-12-13
Hi

These programs should work: smbclient and smbfs. First install them:
```
apt-get install smbclient
apt-get install smbfs

```

Next, provide a place for the share to mount:
```
cd /mnt
sudo mkdir nas

```
Mount the share. In the code window below replace
MACHINE_NAME with the name of the computer that has the share (the Win computer's name)
SHARE_NAME with the name of the share on the above machine (the folder on the Win computer)
USERNAME with the username associated with the share
PASSWORD with the password for the share
XU_NAME with your user name in Xubuntu 
XU_GROUP with the group name the above user belongs to in Xubuntu
```
sudo smbmount //MACHINE_NAME/SHARE_NAME /mnt/nas -o username=USERNAME,password=PASSWORD,uid=XU_NAME,gid=XU_GROUP

```
Example - The Win machine's name is WINDOWS01, it has a folder on it's root named MyShares and john is user on this machine, his password is abcd. The Xubuntu user is jane:
```
sudo smbmount //WINDOWS01/MyShares /mnt/nas -o username=john,password=abcd,uid=jane,gid=jane

```

To unmount the share:
```
sudo smbumount /mnt/nas
```


Option #2
I mention this for completeness. Some folks use Xubuntu because they like it. others because of limited RAM. If you have sufficient resources to run the full Ubuntu you can install it - this will get you GNOME which can access Windows shares.

However ... I use Ubuntu w/ GNOME and I still prefer to access Windows shares using smbclient and smbfs for some things. Some of my existing maintenance scripts just didn't like smb:// URIs.

---

### Post by Bob Howland on 2008-01-01
Why isn't there a simple graphical front end that guides beginners through this? Sorry, but this technique just doesn't pass the "Grandmother test".

---

