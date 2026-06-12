---
title: "Replicating Triple Boot System"
date: 2009-02-18
forum: Apple Hardware Users
---

### Post by anthonious on 2009-02-18
Hi,

I'm getting put on a project to clone several MacPro machines with:
Leopard/Vista/Ubuntu and want to know the best/quickest way to
replicate all the partitions.

I'm looking at possibly using NetRestore to do the Mac and PC partitions, but was wondering the best way to replicate the Ubuntu
partition on each machine?  Is Winclone a possibility as a call after running NetRestore?  Using dd to make an image and then restore?

Also, I saw that it is better to use NTFS so access to the PC partition is read-only from the Mac side.  Just wanted to verify
that. 

Any insight from your past experience is much appreciated.

Thanks,
Anthony

---

### Post by cyberdork33 on 2009-02-18
> **anthonious said:**
> Also, I saw that it is better to use NTFS so access to the PC partition is read-only from the Mac side.  Just wanted to verify
that. 
I don't think that is correct.

---

### Post by buntuLo on 2009-02-18
> **anthonious said:**
> Hi, I'm getting put on a project to clone several MacPro machines with: Leopard/Vista/Ubuntu and want to know the best/quickest way to replicate all the partitions.
I'm looking at possibly using NetRestore to do the Mac and PC partitions, but was wondering the best way to replicate the Ubuntu
partition on each machine?  Is Winclone a possibility as a call after running NetRestore? Using dd to make an image and then restore?
hi Anthony, i'm used to back up linux and win$ partitions -and more often the entire disk- running dd from a livecd, simple and effective. i didn't backup yet my new macos/ubuntu dualboot, hence i'm not really sure about the results on the hfs+ partition, but there shouldn't be problems for the efi-fat and mbr.. if i were you i'd give it a try on the entire disk and before any other more complicated software, as your application doesn't really require compression for the image. i will try it myself as i get some space on an external drive, but if you precede me, please write back about it!
greetings, Lo.

---

### Post by cyberdork33 on 2009-02-18
> **buntuLo said:**
> hi Anthony, i'm used to back up linux and win$ partitions -and more often the entire disk- running dd from a livecd, simple and effective. i didn't backup yet my new macos/ubuntu dualboot, hence i'm not really sure about the results on the hfs+ partition, but there shouldn't be problems for the efi-fat and mbr.. if i were you i'd give it a try on the entire disk and before any other more complicated software, as your application doesn't really require compression for the image. i will try it myself as i get some space on an external drive, but if you precede me, please write back about it!
greetings, Lo.
used properly, dd should be able to clone a drive byte for byte, and in that case, it wouldn't matter what filesystems are on the drive at all.

---

### Post by flaggh on 2009-02-18
I have used dd_rescue to copy multiple partitions all with different filesystems from one hard drive to another.  After it was finished cloning the drive, my macbook booted up as if the original hard drive was still in it.  Might require you to fix your fstab though, I'm not sure if the UUID changes.

dd_rescue is a simple to use script that uses dd but decides for itself what byte sizes to use and which direction to start copying from rather than relying on user parameters.  Its really designed to copy the data as quickly as possible from a failing hard drive, but just as effective for a good hard drive.  Just boot up the liveCD and:
```
sudo apt-get install ddrescue
```
then I believe its:
```
dd_rescue *infile* *outfile*
```

---

### Post by cyberdork33 on 2009-02-18
> **flaggh said:**
> dd_rescue is a simple to use script that uses dd but decides for itself what byte sizes to use and which direction to start copying from rather than relying on user parameters.  Its really designed to copy the data as quickly as possible from a failing hard drive, but just as effective for a good hard drive.  Just boot up the liveCD and:
```
sudo apt-get install ddrescue
```then I believe its:
```
dd_rescue *infile* *outfile*
```
sounds like a good route to try.

---

