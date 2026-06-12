---
title: "Slave HDD Manipulation in Ubuntu?"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by AeroCross on 2007-10-31
Hello all. I'm very VERY new to Ubuntu and Linux in general, and I have lots of questions. I can work out some, but this is specially hard for me to figure out...

I used (in my now-over Windows XP days) 2 HDD, a 40GB Primary Hard Drive, with Windows XP SP2, and a Slave HDD, a 80GB Disk, with ONLY Files, no OS, Both NTFS. When I installed Ubuntu 7.04 on my Primary HDD (40GB) everything went "fine" (I had lots of troubles but I finally made it, and now I'm writing this thread on my new OS n.n). When I logged into my Account, I found out that I have "hdb1" in my Desktop. That's good, I can access my old files from my Ubuntu, but there's a problem... I can't write, edit, move, delete, or anything in that drive (The Slave, the 80GB one). I want to use that HDD as a Storage Drive, cuz If for any reason I have to reinstall Linux and because of that, Partition and Format, I don't wanna lose any data I start to make in Ubuntu. I need help with this... Is it possible to enable the manipulation of that drive under Ubuntu? (Like in Windows? Like, treating the Slave Drive like a Huge 80GB Folder and nothing else?)

Thanks in advance, and I'm sorry if this took so long.

---

### Post by JairunCaloth on 2007-10-31
Hey there Aero, no need to fret, your existing NTFS drive can continue it's duties as it did under windows. My first question is what version of ubuntu are you running. Secondly does it give you a permission error when you try to change the files under the drive. If that's the case, you simply need to change them to allow you access to the drive. 

It could be that you don't have the proper NTFS support installed. Unfortunately  I don't have much recent experience with NTFS support so maybe some searching around for Linux NTFS support could help you find what you need.

Personally I would backup everything to DVD and format the partition with a linux file system and then put the stuff back on it.

---

### Post by AeroCross on 2007-10-31
I'm running Ubuntu 7.04 Feisty, and I think it was a permission error. Cuz when I click properties, it said "Owner: Root" and I couldn't access Root.

I found out that entering:

```
sudo nautilus /media/hdb1
```
(Of course, substituting the "hdb1" for the Drive/Folder you want to access as root)

Enables the Root GUI for editing. I also installed the NTFS-3G package and it seems it did something, I really can't tell if it actually DID something, but it's there.

And well, I would have backed-up in a DVD... But it's 63GB of Data... and... I don't have a DVD-RW Drive (Insane, right?) to burn, so I NEEDED another way =P

Thanks for the advice. The Idea came into my mind when you told me the Permission thing n.n

---

