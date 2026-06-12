---
title: "Restoring clonezilla image"
date: 2013-02-01
forum: Any Other OS
---

### Post by vicke4 on 2013-02-01
Hi all I've created a clonezilla image from 4 ntfs partitions all of that were 50Gb in size.Later i deleted those 4 partitions to create one bulk partition of size 200Gb.I did that job well using gparted.After i tried to restore that image in that 200Gb ntfs partition.but i can't do that.It returned with some errors.I'm sure image is good.I checked that image after creating.So,there's no problem with image.

how to restore that image in that 200Gb partition?
I need help to accomplish this task successfully.
Thanks in advance..

---

### Post by orb9220 on 2013-02-02
> i deleted those 4 partitions to create one bulk partition of size 200Gb.

Might be the problem delete or keep the 200gb partition and clonezilla will ignore anyways. It will restore the the 4 partitions to that drive no matter how it is configured. As it overwrites whatever is there.

What you are trying to do is merge 4 partitions into a larger one. And if my understanding is right it cannot be done as that is not how mirroring partitions work. They are a byte-by-byte exact copies including the critical partition table layout for files inside. And their is no magic merge for restoring partitions.

You would need to manually copy contents from all 4 partition contents to one partition and then you can backup a single partition.

Maybe someone with Magic JuJu skills and Linux skills can share another way to do it.

You'll have to copy the files from one partition to the other and delete the empty one, then resize the remaining ones; there's no such thing as "merging" partitions in the sense you're probably thinking of.
.

---

### Post by mips on 2013-02-02
Delete the 200GB partition and let clonezilla do it's job. It does not allow you to merge partitions. That you would have to do manually. You can restore the first partition if it contains the OS, resize it, mount the other images and simply copy the data across. If they are all data partitions then just mount them and copy the data to your new 200GB partition.

---

### Post by speartip on 2013-02-02
Are you restoring like for like?
For eg. Are you restoring sda1 to an sda1 partition or have your partition numbers changed now you have changed your hard drives table?
If your partition numbers have changed, you need to change the partition number of the clonezilla image that you are restoring, to match the partition number on your hard drive, that you want to restore it to.

---

### Post by vicke4 on 2013-02-02
> **orb9220 said:**
> Might be the problem delete or keep the 200gb partition and clonezilla will ignore anyways. It will restore the the 4 partitions to that drive no matter how it is configured. As it overwrites whatever is there.

So should i delete the 200Gb partition and leave the vacant space unallocated and let clonezilla to restore the image in the unallocated space?

---

### Post by vicke4 on 2013-02-02
> **mips said:**
> Delete the 200GB partition and let clonezilla do it's job. It does not allow you to merge partitions. That you would have to do manually. You can restore the first partition if it contains the OS, resize it, mount the other images and simply copy the data across. If they are all data partitions then just mount them and copy the data to your new 200GB partition.

Yes,they are only data partitions.i need this solution only how to mount that image and restore back the data?

> **speartip said:**
> Are you restoring like for like?
For eg. Are you restoring sda1 to an sda1 partition or have your partition numbers changed now you have changed your hard drives table?
If your partition numbers have changed, you need to change the partition number of the clonezilla image that you are restoring, to match the partition number on your hard drive, that you want to restore it to.

Yes,the partition numbers have changed.how to change the partition number in the image?

---

### Post by speartip on 2013-02-02
>  Yes,the partition numbers have changed.how to change the partition number in the image?

Go into the folder were the image is, there will be about 15 files.
At least 2 of them will be numbered, ie sda5.
Right click the files & rename them.
Keep the name exactly the same, just change the partition number so it corresponds to the one you are restoring to.
You should then be able to restore the image.

---

### Post by vicke4 on 2013-02-02
> **speartip said:**
> Go into the folder were the image is, there will be about 15 files.
At least 2 of them will be numbered, ie sda5.
Right click the files & rename them.
Keep the name exactly the same, just change the partition number so it corresponds to the one you are restoring to.
You should then be able to restore the image.

It's a combination of 4 partitions image i.e sda3,sda4,sda5,sda6
and my new partition is sda8 renaming all of the above to sda8 will work? 
I don't want to destroy my backup.please be sure.

---

### Post by speartip on 2013-02-03
No...
If you have made one image from 4 partitions, then you need to ensure you have 4 partitions of at least equal size on your hard drive, to restore back to, & each partition needs to be named the same, as the ones you're restoring to.

---

### Post by mips on 2013-02-03
> **vicke4 said:**
> Yes,they are only data partitions.i need this solution only how to mount that image and restore back the data?


What filesystem did you use for those partitions? ntfs, fat32, ext3 etc?

Can you post a list of the image file names here you created with clonezilla?

[http://ubuntuforums.org/showthread.php?t=872832](http://ubuntuforums.org/showthread.php?t=872832)
[http://geek.soosoo.at/linux/clonezilla/how-to-restore-and-mount-a-clonezilla-image-with-partclone/](http://geek.soosoo.at/linux/clonezilla/how-to-restore-and-mount-a-clonezilla-image-with-partclone/)
[http://www.robholland.com/?p=2604](http://www.robholland.com/?p=2604)
[http://blog.thewulph.com/?p=232](http://blog.thewulph.com/?p=232)
[https://www.linux.com/community/forums/ubuntu/ubuntu-mount-clonezilla-image/9760](https://www.linux.com/community/forums/ubuntu/ubuntu-mount-clonezilla-image/9760)

---

### Post by vicke4 on 2013-02-03
> **mips said:**
> What filesystem did you use for those partitions? ntfs, fat32, ext3 etc?


All of those partitions filesystem is ntfs.

> 
Can you post a list of the image file names here you created with clonezilla?

[U]

[/U]

---

### Post by mips on 2013-02-03
See the links I provided above.

---

### Post by vicke4 on 2013-02-03
I find all of those ways are complicated.can i restore that image as such?i mean can i rebuild that 4 partitions with data that i deleted to create one large partition using that image?

---

### Post by orb9220 on 2013-02-04
> **vicke4 said:**
> I find all of those ways are complicated.can i restore that image as such?i mean can i rebuild that 4 partitions with data that i deleted to create one large partition using that image?

No that's what we been trying to explain to you. You need to restore the 4 partitions than back up all the data to some other means like external usb drive. Then create one big partition and move the data there.

You cannot extract or merge 4 separate partitions into one.
.

---

### Post by vicke4 on 2013-02-04
> **orb9220 said:**
> No that's what we been trying to explain to you. You need to restore the 4 partitions than back up all the data to some other means like external usb drive. Then create one big partition and move the data there.

You cannot extract or merge 4 separate partitions into one.
.

If my guess is correct i should delete that 200Gb partition and left that space unallocated correct?
then using clonezilla live i should make use of the unallocated space to restore that 4 partitions.is it possible to do?

---

### Post by sudodus on 2013-02-04
> **vicke4 said:**
> If my guess is correct i should delete that 200Gb partition and left that space unallocated correct?
then using clonezilla live i should make use of the unallocated space to restore that 4 partitions.is it possible to do?

I know, that if you made an image of the whole disk, you can restore it to an empty disk. I have done that with Clonezilla.

But I don't know what would happen, if you made an image of the individual partitions (not the whole disk). You can try to restore to an empty disk. If it does not work, you need to create four partitions of at least the same size (bigger works too, but not smaller). And they should have the same partition numbers (like /dev/sdb1 ...) as in the Clonezilla image, otherwise you must edit a file or some files or file names in the Clonezilla image, as described by Speartip in post #7.

---

### Post by orb9220 on 2013-02-04
> **vicke4 said:**
> If my guess is correct i should delete that 200Gb partition and left that space unallocated correct?
then using clonezilla live i should make use of the unallocated space to restore that 4 partitions.is it possible to do?

Yep and once the 4 partitions are restored then you can deal with moving the data/files whatever to another larger partition or HD and then you can backup that one partition.
.

---

### Post by mips on 2013-02-04
> **vicke4 said:**
> I find all of those ways are complicated.can i restore that image as such?

i mean can i rebuild that 4 partitions with data that i deleted to create one large partition using that image?

It's a few commands you have to run, surely it's not that hard?

No.

---

### Post by vicke4 on 2013-02-04
> **mips said:**
> It's a few commands you have to run, surely it's not that hard?

No.

[http://www.robholland.com/?p=2604](http://www.robholland.com/?p=2604)

I tried to follow the above link.But unfortunately it is difficult to follow for me.can you explain it step by step?

step 1: Prepare a large disk in Linux

should i create a large ext3 partition in my harddisk?

---

### Post by mips on 2013-02-04
> **vicke4 said:**
> 
step 1: Prepare a large disk in Linux

should i create a large ext3 partition in my harddisk?

Yes, it just means a large enough partition to store the image files when you convert them from a bunch of small split ones to big single ones you can mount..

---

### Post by vicke4 on 2013-02-04
Now i am doing this using live cd and my image is in an external harddisk.I entered the following code in terminal.

```
file /media/FreeAgent GoFlex Drive/sajith/2013-02-01-20-imgBACKUPs/sda5.ntfs-ptcl-img.gz.aa

```

and the output is

```
/media/FreeAgent:                                                ERROR: cannot open `/media/FreeAgent' (No such file or directory)
GoFlex:                                                         ERROR: cannot open `GoFlex' (No such file or directory)
Drive/sajith/2013-02-01-20-imgBACKUPs/sda5.ntfs-ptcl-img.gz.aa: ERROR:  cannot open  `Drive/sajith/2013-02-01-20-imgBACKUPs/sda5.ntfs-ptcl-img.gz.aa' (No  such file or directory)


```

what to do next?

---

### Post by mips on 2013-02-04
> **vicke4 said:**
> Now i am doing this using live cd and my image is in an external harddisk.I entered the following code in terminal.

```
file /media/FreeAgent GoFlex Drive/sajith/2013-02-01-20-imgBACKUPs/sda5.ntfs-ptcl-img.gz.aa

```

and the output is

```
/media/FreeAgent:                                                ERROR: cannot open `/media/FreeAgent' (No such file or directory)
GoFlex:                                                         ERROR: cannot open `GoFlex' (No such file or directory)
Drive/sajith/2013-02-01-20-imgBACKUPs/sda5.ntfs-ptcl-img.gz.aa: ERROR:  cannot open  `Drive/sajith/2013-02-01-20-imgBACKUPs/sda5.ntfs-ptcl-img.gz.aa' (No  such file or directory)


```

what to do next?

You have spaces in your path, you can use quotation " marks for that.

---

### Post by vicke4 on 2013-02-05
Mips,I am superconfused.I created a 200GB ext4 partition and gave label as "CCC".Then i put that image in that partition and renamed it as "image" inside the folder there are so many files(please refer the attachment).I entered the following code.

```
"file /media/CCC/image/sda5.ntfs-ptcl-img.gz.aa"
```

I don't know which file to select first so i selected "sda5.ntfs-ptcl-img.gz.aa"

and i get the following:

```
bash: file /media/CCC/image/sda5.ntfs-ptcl-img.gz.aa: No such file or directory

```

So,please simplify each steps using code tags for my sake.As i am a beginner in entering codes it is so difficult for me.

---

### Post by speartip on 2013-02-05
Vicke4.
It may be worth starting again here.
The Partitions you cloned were on sda3,4,5,6, right?
How big were they in GBs, & was anything on sda 1 or 2?
Also what is the full capacity of your hard disc?

---

### Post by vicke4 on 2013-02-05
> **speartip said:**
> Vicke4.
It may be worth starting again here.
The Partitions you cloned were on sda3,4,5,6, right?
How big were they in GBs, & was anything on sda 1 or 2?
Also what is the full capacity of your hard disc?

Full capacity of the harddisk is 300Gb.
while i made image from four partitions they were as follows:
sda5,sda6,sda7,sda9.
before cloning each was 50Gb in size.
and each of that containing 10-30Gb data.


@mips i think every code should be entered in clonezilla live.

---

### Post by speartip on 2013-02-05
ok..
What was on sda8?

---

### Post by vicke4 on 2013-02-05
It was Linux swap.

---

### Post by speartip on 2013-02-05
What exactly was on the partitions you Cloned? Windows, Ubuntu or what?
And do you still have partitions on the drive you are keeping? If so what are their sda numbers, or are you wiping the full disc?

---

### Post by vicke4 on 2013-02-05
> **speartip said:**
> What exactly was on the partitions you Cloned? Windows, Ubuntu or what?
And do you still have partitions on the drive you are keeping? If so what are their sda numbers, or are you wiping the full disc?

All of that partitions cloned has data like images,pdfs,videos.all are ntfs partitions.

yes there are still partitions in that drive they are:
sda5-linux swap
sda6-linux partition 
sda7-linux partition

---

### Post by vicke4 on 2013-02-05
My system is dual booted with Ubuntu & windows7.
sda1-system reserved
sda2-windows7
sda3-extended partition

---

### Post by speartip on 2013-02-05
Ok.. Quite a mess.
This is what I would do personally. No guarantees this will work but it can be reversed.

1st Using gparted create 4 x 50 gig NTFS partitions in the space you have.

2nd Check the sda no.s of the partitions created, if they are different to the ones in your thumbnails, you will need to change the partition nos on your clone to match.
eg. If it creates sda1,2,3,4, then change all the sda5s to sda1, sda6s to sda2 etc etc..
ps. make sure the rest of the named files stays exactly the same, its only the number you are changing.

3rd You should now be in a position to restore your cloned image back.

4th Assuming all goes well, if you want to do what you are trying to do, it would be easier to backup/copy all the data you want to save from all 4 partitions to an external drive, rather than clone the drive. Then you can simply delete the partitions, make one big partition and copy all the data back.

Hope this works & helps.

---

### Post by speartip on 2013-02-05
Actually it may help if you 1st post a picture of your partition table as it looks now.

---

### Post by vicke4 on 2013-02-05
We can't change the partition name.
Eg:changing the name of sda8 to sda5 is possible.but quite difficult :(

---

### Post by speartip on 2013-02-05
> **vicke4 said:**
> We can't change the partition name.
Eg:changing the name of sda8 to sda5 is possible.but quite difficult :(

What do you mean?
It's simply a case of right clicking on the file, rename, & change the number to whatever it needs to be.

Could you post a picture of the partition table on your hard drive.

---

