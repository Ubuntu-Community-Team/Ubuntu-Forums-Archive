---
title: "Partition location/size/useability"
date: 2005-05-30
forum: Absolute Beginner Talk
---

### Post by ckvs on 2005-05-30
hi all,
i am not even a newbie, only *starting* to get ready, so please bear with me...

i would like to install Ubuntu on my box, which presently runs W XP. old but solid machine, 20G, presently set up the following way:
C:/ ~10GB (O/S plus progs), primary, NTFS
E:/ ~5 GB (data),primary, NTFS
unallocated ~4GB
system restore ~1GB, hidden, FAT32

i thought, after reading a good many post in the forum etc., of doing the following:
a) get rid of the superfluous system restore partition,
b) prepare the total of 5GB for U.

BUT: i wonder
a) doesn't the future Linux partition have to be *next* to the C;/ partition?
b) *if* the future Linux partition is *past*  the E:/, would it then not be slow access-wise?
b) will 5GB be enough (for simple general usage, until -hopefully- i discover how things work)?
c) will the totality of the unallocated space (after wiping the system restore part.) be FAT32 or unformatted? and which should it be for installing Ubuntu? 
d) will the E:/ (data) be *useable* in Ubuntu? (ie will it be possible to *write to* that partition? and will, if/when necessary, W XP be able to read accordingly?)

[as an alternative, i could imagine:
1) resizing C:/, down to 7G, ie freeing approximately 3GB...would that be enough for Linux install?
2) if not: 
a) imaging E:/ "over onto" the presently unallocated space [a bit tricky because of size differences]
b) wiping the original E:/, and, if 5G is insufficient for Ubuntu,
c) downsizing C:/ and using the combination of the newly gained free 5GB plus the gained GBs from C:/ to install Ubuntu]

as you can see, *anything* to get Ubuntu to run without having to reinstall W XP!
 
sorry for these truly pedestrian questions, but i want to really be careful in these first steps.

thanks for your understanding and assistance,
ckvs

---

### Post by grim42 on 2005-05-30
> a) doesn't the future Linux partition have to be *next* to the C;/ partition?

b) *if* the future Linux partition is *past* the E:/, would it then not be slow access-wise?

No. Linux doesn't use drive letters such as C: and E:. Performance will be the same no matter where it is installed on your hard drive.

> b) will 5GB be enough (for simple general usage, until -hopefully- i discover how things work)?


Yes. 5GB will be enough to install Ubuntu and then have quite a bit of space to play with.

> c) will the totality of the unallocated space (after wiping the system restore part.) be FAT32 or unformatted? and which should it be for installing Ubuntu?

It will be unallocated if you delete the system restore partition correctly. Ubuntu needs unallocated to install to. **When running the Ubuntu installation, read carefully when it asks where to install to. Don't choose the overwrite everything option.**

> 
d) will the E:/ (data) be *useable* in Ubuntu? (ie will it be possible to *write to* that partition? and will, if/when necessary, W XP be able to read accordingly?)

The E: drive can be made accessible from Ubuntu, but it will be READ-ONLY. Although NTFS write support is available from Linux, it is EXPERIMENTAL and NOT RECOMMENDED. You might corrupt your data by trying to write to NTFS from Linux.

Windows will not be able to access any Linux partitions.

If you need to have read/write access, I suggest keep the FAT32 partition for Windows and Ubuntu to use as "shared space".

---

### Post by ckvs on 2005-05-31
thanks for the reply, grim42.

a few minor clarifications:
> No. Linux doesn't use drive letters such as C: and E:. Performance will be the same no matter where it is installed on your hard drive.
what i meant was: can the Ubuntu partition be *spatially* farther away from (ie NOT next to) C:/??
(from some post i read, this is what i gathered. but if it can indeed be the, say, third partition *spatially* on HDD, then things would be easier in my case because i could simply set it up "at the end" of E:/)

> Yes. 5GB will be enough to install Ubuntu and then have quite a bit of space to play with.
could you please tell me what the (reasonable) *minimum* should be?

> The E: drive can be made accessible from Ubuntu, but it will be READ-ONLY. ..Windows will not be able to access any Linux partitions...If you need to have read/write access, I suggest keep the FAT32 partition for Windows and Ubuntu to use as "shared space".
let me get this straight: if i reformat my (presently E:/, NTFS) data partition to FAT32, then both WXP and Ubuntu will be capable of read/write? is there any "counterindication" to do this? 

thanks so much for your help!
ckvs

---

### Post by grim42 on 2005-05-31
[QUOTE=ckvs]
what i meant was: can the Ubuntu partition be *spatially* farther away from (ie NOT next to) C:/??
(from some post i read, this is what i gathered. but if it can indeed be the, say, third partition *spatially* on HDD, then things would be easier in my case because i could simply set it up "at the end" of E:/)[/QUOTE]

I really don't see any reason for it not to be the 3rd partition. I've never seen anything about where a partition is spatially on a hard drive. You don't have a link to that post handy do you?

The only thing I can think of would be related to the placement of /boot which can affect older versions LILO/GRUB if after cylinder 1024. (which only makes a difference if it's the 1st partition, but you shouldn't have a problem here)


> could you please tell me what the (reasonable) *minimum* should be?

I'm not 100% sure what the *minimum* required is, but I wouldn't recommend less than 3 GB. I think the install of Ubuntu uses just under 2GB and you'll need free space to work with, temp space for programs, swap space, etc.

> let me get this straight: if i reformat my (presently E:/, NTFS) data partition to FAT32, then both WXP and Ubuntu will be capable of read/write? is there any "counterindication" to do this?
ckvs

Linux can safely read and write to FAT32 partitions but not NTFS. So yes, if you reformat your E: drive, both systems will be able to use it.

The only "downsides" of doing this would be from a Windows perspective in that the added features of NTFS would not be available -- not really a problem if you're just using it to store some data on.

---

### Post by phen on 2005-05-31
[QUOTE=grim42]I really don't see any reason for it not to be the 3rd partition. I've never seen anything about where a partition is spatially on a hard drive. You don't have a link to that post handy do you?

The only thing I can think of would be related to the placement of /boot which can affect older versions LILO/GRUB if after cylinder 1024. (which only makes a difference if it's the 1st partition, but you shouldn't have a problem here)




I'm not 100% sure what the *minimum* required is, but I wouldn't recommend less than 3 GB. I think the install of Ubuntu uses just under 2GB and you'll need free space to work with, temp space for programs, swap space, etc.



Linux can safely read and write to FAT32 partitions but not NTFS. So yes, if you reformat your E: drive, both systems will be able to use it.

The only "downsides" of doing this would be from a Windows perspective in that the added features of NTFS would not be available -- not really a problem if you're just using it to store some data on.[/QUOTE]
 Hello!

I ve been using ubuntu as my only os for three months now. i am using 9.8 GB of my HD, whereby 6.5 GB are used to store data (my home dir). this makes a total of 3.3 GB for programs, games and a lot of wierd stuff i have installed :-) (several kernel images, programs i never use etc...)

so my suggestion:

if you reformat E: as FAT32, and use this as the primary storage device for data, you can start with 3 or even 2.5 GB.

But: keep in mind that you need a swap partition (twice the size of your ram is recommended) and keep in mind, that you want to play with ubuntu, and thats easier (especially in the beginning, if you have some hd space to play with.) example: until i found out which media player best suits my needs, i used about 4.

and a last note: the last partition (cylinder-wise) is on the outer side of the physical disk of a harddisk. this fact as an impact on the access time, but i think it can be considered negligible.

cheers,

kai

---

### Post by ckvs on 2005-06-13
thanks for all your help!!!
i'm getting closer to take the "plunge".
cheerio,
ckvs

---

