---
title: "Partitioning Ubuntu on 80Gb and 250Gb hard drive..."
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by phucough on 2006-12-13
Hi there, I have 80Gb and 250GB hard drives, on the 80Gb one I intend to have 20Gb for XP, the rest for Ubuntu. Also, the 250Gb drive I want to use for Ubuntu.

I've heard that if you have that much room it's a good idea to create separate partitions for a number of the Ubuntu folders - /home, /usr and what have you. Can anybody recommend how many partitions I should create, and how big they should be?

Thanks in advance.

---

### Post by bodhi.zazen on 2006-12-13
> **phucough said:**
> Hi there, I have 80Gb and 250GB hard drives, on the 80Gb one I intend to have 20Gb for XP, the rest for Ubuntu. Also, the 250Gb drive I want to use for Ubuntu.

I've heard that if you have that much room it's a good idea to create separate partitions for a number of the Ubuntu folders - /home, /usr and what have you. Can anybody recommend how many partitions I should create, and how big they should be?

Thanks in advance.

You will get a variety of opinions here.

My 2c: I would make 2 partitions, 15 Gb each.

Go ahead and install Ubuntu into the first. Get it set up and updated just the way you like. Then copy it (using gparted) to the second partition as back up.

I would give the rest of the space either for data, which you can share with windows, or additional 5-15 Gb partitions for testing of other versions of Linux...... 

Additional options may include /home and /boot partitions.

If yo do not know what /tmp and /var partitions are you likely can put them in your root partition :)

---

### Post by housam on 2006-12-13
You can also read [this link ]("http://community.linux.com/howtos/Partition/index.shtml")as a guide

---

### Post by moshuptrail on 2006-12-13
Generally people recommend 3 partitions for Ubuntu.  /, /home, and swap.
By putting /home separately, if you need to re-install, in theory you shouldn't have to mess with your own files.  /usr is "unix system resources", not a short form of "user".  So there's no value in placing it elsewhere.

I can't imaging a Ubuntu install that needs more than 10Gb for / and it doesn't do much good to have a swap larger than 2x system memory.

So if you devote the entire 250G to /home, that leaves you with 60G on the first drive after XP of which you won't need more than about 15G.  That still leaves 45G.  I might create a filesystem called /pictures or /music or whatever you need space for.

Does anyone need more than 10G for /?  Like if you install large games.

---

### Post by moshuptrail on 2006-12-13
Here's a variation on bodhi.zazen's idea:

Create a fat32 partition on the 80G drive and share it with XP.
Both Ubuntu and XP will be able to write to it.  Then do the following in XP:

1. Log in to your user account
2. Right click on My Documents, select Properties
3. Re-define the location of My Documents to go into the shared partition.
4. When you save, XP will ask if you want to move all your files.  Say yes.
5. It will move your entire My Documents to the shared partition (which will be a new drive letter in XP)

Now you don't have to worry about saving files on the tiny 20G XP partition.

---

### Post by bodhi.zazen on 2006-12-13
> **moshuptrail said:**
> Does anyone need more than 10G for /?  Like if you install large games.

I can get / as small as 2.5 Gb, but I usually go with Gb on the low end, but as you know it depends on how much additional software you install. I have one package that will eat > 1 Gb (It is a program written for windows running on wine and it is a hog :) No Linux option :( ).

---

### Post by phucough on 2006-12-13
Thanks all for your help. I think moshuptrail's first idea is best - the 20Gb for XP should be adequate. How would I go about creating a /pictures or /music directory?

And if /home was on the 250Gb hard drive, would XP be able to see it?

---

### Post by say592 on 2006-12-13
I am a little new, but I think that you should go 20gb for XP (that was good) maybe the rest for linux, and then you format teh 250gb in fat32 so it can be used on both!

---

### Post by phucough on 2006-12-14
> **say592 said:**
> I am a little new, but I think that you should go 20gb for XP (that was good) maybe the rest for linux, and then you format teh 250gb in fat32 so it can be used on both!

So the 250Gb wouldn't be used as /home or anything, just a blank formatted partition? Is that how that'd be done?

---

### Post by bodhi.zazen on 2006-12-14
Yep. format to FAT, mount somewhere like say /media/data

You can make links in /home:

```
mkdir /media/data/music
ln -s /media/data/music ~/music
```
For example will give you a folder (directory) in your home directory "music". The data is on the FAT partition and can be shared with windows....

Likewise for documents, pictures, what have you ....

HTH

---

### Post by phucough on 2006-12-14
> **bodhi.zazen said:**
> Yep. format to FAT, mount somewhere like say /media/data

You can make links in /home:

```
mkdir /media/data/music
ln -s /media/data/music ~/music
```
For example will give you a folder (directory) in your home directory "music". The data is on the FAT partition and can be shared with windows....

Likewise for documents, pictures, what have you ....

HTH

Sounds good, I'll give it a try in a day or two (don't feel like backing up, installing and configuring everything just yet!)

---

### Post by dross on 2006-12-14
Quick question: if the /home is fat32, can the / and /swap be ext3?  Or perhaps a better way to ask the question...if /home is fat32 (so it can be shared with XP), does anyone have suggestion on what /swap and / should be??

---

### Post by housam on 2006-12-14
> **dross said:**
> Quick question: if the /home is fat32, can the / and /swap be ext3?  Or perhaps a better way to ask the question...if /home is fat32 (so it can be shared with XP), does anyone have suggestion on what /swap and / should be??

swap partition is a swap type. you choose this type (swap)during the partitioning process.

---

### Post by dross on 2006-12-14
Thanks, I didn't realize that swap was a file system type, just thought it referred to what the partition did (e.g. analagous to /home).  So would this configuration make sense?:

/  file system type:  ext3
/home  file system type:  fat32
/swap  file system type: swap


Also, my windows laptop already has 3 partitions that Dell created...the main xp partition (70+ GB), a partition with a restore os (that is about 4 GB), and another partition that is not even a GB...anyone care to hazard a guess what that 3rd partition is for??  From [this thread]("http://ubuntuforums.org/showthread.php?t=112073"), it sounds like it wouldn't be a swap partition for Windows...

---

### Post by gurgle on 2006-12-14
> **phucough said:**
> Thanks all for your help. I think moshuptrail's first idea is best - the 20Gb for XP should be adequate. How would I go about creating a /pictures or /music directory?

And if /home was on the 250Gb hard drive, would XP be able to see it?

xp can read ext3 drives:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

just be careful, of course.

---

### Post by housam on 2006-12-14
> **dross said:**
> Thanks, I didn't realize that swap was a file system type, just thought it referred to what the partition did (e.g. analagous to /home).  So would this configuration make sense?:

/  file system type:  ext3
/home  file system type:  fat32
/swap  file system type: swap


Also, my windows laptop already has 3 partitions that Dell created...the main xp partition (70+ GB), a partition with a restore os (that is about 4 GB), and another partition that is not even a GB...anyone care to hazard a guess what that 3rd partition is for??  From [this thread]("http://ubuntuforums.org/showthread.php?t=112073"), it sounds like it wouldn't be a swap partition for Windows...


I think this 3rd partition is for Dell utilities & diagnostics (check [this thread]("http://www.ubuntuforums.org/showthread.php?t=313899&page=4"))

For partitions config. ,it is ok . the 1st one normally named ( / ) for root.

---

### Post by phucough on 2006-12-14
> **dross said:**
> Also, my windows laptop already has 3 partitions that Dell created...the main xp partition (70+ GB), a partition with a restore os (that is about 4 GB), and another partition that is not even a GB...anyone care to hazard a guess what that 3rd partition is for??  From [this thread]("http://ubuntuforums.org/showthread.php?t=112073"), it sounds like it wouldn't be a swap partition for Windows...

I think installations of XP create another really small partition, for boot maybe? My computer's always had one, and I've done a few clean installs of XP before. I think it's only 8Mb or something, though.

---

### Post by dross on 2006-12-14
Yeah, not concerned about the size of the 3rd partitioned, just concerned that it takes up a primary partition...those 3 windows partitions are all primaries...that leaves me only 1 to install Ubuntu...can I install it with only 1?  housam, I read the thread you suggested...where someone suggested moving the small windows utility partition to the main windows partition...I'd prefer not to do that (because I don't know how)..so if there is a way to install Ubuntu /, /home, and /swap on an extended partition, I'd probably prefer to do that...

---

### Post by housam on 2006-12-14
Of course you can. using Gparted live CD to create an extended partition which can be parted to many logical partitions.

---

### Post by dross on 2006-12-14
Hmm, and Windows and Ubuntu will be able to share virtual /home partition (assuming I make it a Fat32)???

---

### Post by housam on 2006-12-15
> **dross said:**
> Hmm, and Windows and Ubuntu will be able to share virtual /home partition (assuming I make it a Fat32)???

Correct. FAT32 is suitable for both OS to be shared.

---

