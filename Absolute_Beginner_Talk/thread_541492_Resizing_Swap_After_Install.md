---
title: "Resizing Swap After Install"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-09-02
so ive been using ubuntu for a while now but ive made my swap partition too small. i have 1 GB of RAM and i only made it about 256MB. So how can i resize my swap partition again? if i do will all the files be okay or do i pretty much have to reformat?

---

### Post by jordanmthomas on 2007-09-02
You can resize it using gparted.
Install gparted:
```
sudo apt-get install gparted
```
and run it.  Before you resize a swap partition, you have to turn it off (right click on it in gparted and go to swapoff...it's the easiest way to explain here)


Now, you'll be left with space after the swap partition, so **you may want to do this instead**:
1.  Reboot with a LiveCD
2.  Run gparted and remove your swap partition (remember if it was encased in a extended partition or not...Ubuntu likes to put swap partitions inside a extended partition for whatever reason)
3.  Resize your main ext3 partition and give it a little more space, saving enough on the end for your swap.
4.  Make a new swap of your desired size (including a extended partition if you had one before)

---

### Post by logos34 on 2007-09-02
It should be too difficult, unless it's inside an extended partition.

Post a screenshot of Gparted:

**gksudo gparted**

---

### Post by amneziac on 2007-09-02
now i have a problem, i unmounted my ext3 but now i cant format it back to ext3 :confused:

---

### Post by amneziac on 2007-09-02
i just want everything back to the way it was, resizing it is no big deal but now ubuntu wont load, im on the livecd right now

---

### Post by jordanmthomas on 2007-09-02
Did you delete your ext3 partition?
What happens when you try to boot Ubuntu?

---

### Post by amneziac on 2007-09-02
no its still there but i cant format it it back to ext3 because u have to unmount it to resize it but wont format back again it says the mount point is media/disk but it should be my root it should only be a '/'

---

### Post by jordanmthomas on 2007-09-02
It is probably mounted automatically by the liveCD.  Just because it is the root in one system doesn't mean it's mounted at / in another...know what I mean?
```
sudo umount /media/disk
```
Then run gparted and you should be able to resize it.

**edit** I'm a little confused at your situation, so forgive me if I didn't make sense.  Perhaps you could attach a screenshot of gparted?

---

### Post by amneziac on 2007-09-02
Ok, i am trying to get everything back to the way it was, i unmounted my ext3 partition but i decided to do all of this later, but when i want to format it back i get this error. When i try to load ubuntu in the Dualboot screen, when its loading, it stops and i get an error. So i want to just get my ext3 partition back to the way it was with all my files on it

[[IMG]http://img462.imageshack.us/img462/3793/screenshotvi3.png[/IMG]](http://imageshack.us)

---

### Post by amneziac on 2007-09-02
the mount point on my ext3 isnt root anymore its under /media/disk-3 so how can i mount it back as root and pretend this whole thing never happened

---

### Post by jordanmthomas on 2007-09-02
You shouldn't have formatted your ext3 partition, just resized.  
I'm afraid that you lost all your data.  You could look into recovery software, but if the stuff on there wasn't too important you'd be best off just deleting the linux partitions (NOT YOUR WINDOWS ONE) and reinstalling.

Also, the way your partitions were laid out I'm not sure if you could have reclaimed the space you would have gained by shrinking your swap except by making a new (small...like 500MB) partition.

---

### Post by jordanmthomas on 2007-09-02
You can try remounting and seeing if there's anything left on it, but your screenshot makes it look as if it is empty.

If you can mount it and your data is still there (unlikely), edit the /etc/fstab in it and make sure everything looks right.

On the liveCD the mount point of your ext3 won't be / and isn't supposed to be.

---

### Post by amneziac on 2007-09-02
thats not what i did though, i went to my ext3 partition and i had to unmount it inorder to resize it, but i decided not to do anything so i closed it and i right clicked on ext3 and it said Format to> so i just went to that and clicked ext3

---

### Post by amneziac on 2007-09-02
my ubuntu partition is showing on my desktop and it has all my files and stuff, so i doubt i corrupted it

---

### Post by jordanmthomas on 2007-09-02
Right, when you went to format to > ext3, it formatted (and removed your stuff)

If you never clicked apply after the format to > ext3, then you are fine, and there's no reason your grub shouldn't work.

Can you mount /dev/hda8?

**edit** looks like you're still safe since you didn't actually DO the format.

From your Ubuntu partition, can you post the /etc/fstab?

---

### Post by asmoore82 on 2007-09-02
](*,)[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0):-k

---

