---
title: "/home and /music on same partition"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-05-15
I want to put my /home and another folder called /music on a seperate partition

but all the guides i've seen have only had /home on its own partition.

Would it cause problems to have other folders in that partition, for example when mounting the partition to /home (on hda1) 

eg in fstab
/dev/hda5 /home ext3 nodev,nosuid 0 2

i presume this would mount the whole partition to /home, is it possible to mount just /dev/hda5/home to /home ?

---

### Post by Bachstelze on 2007-05-15
Follow the guide for /home and then you can do

```
sudo mv /music /home
```

It will give you /home/music. you cannot have /home and /music on the same partition it it's not your / partition.

---

### Post by chamberlain2006 on 2007-05-15
If I understand correctly, you have a specific partition for /music?  This would mean that your partition would have to be mounted in /music.  So your fstab entry would look something like this: 

```
/dev/sdb1 /music etc.. etc..
```

---

### Post by Happy_Man on 2007-05-15
Uh, so what you want to do is to transfer your /home to a different partition than the one it's already on, while keeping all your files and stuff? Easy. Go to [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) for a complete tutorial.

---

### Post by PetePete on 2007-05-15
i wanted /music and /home on the same partition..... 

friggit.. i'll whack sort it so /home/music

thought i might have to do that, thanks anyways

---

