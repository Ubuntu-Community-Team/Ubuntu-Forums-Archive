---
title: "just wanting verification before i hit format"
date: 2011-09-15
forum: Any Other OS
---

### Post by 3lud13 on 2011-09-15
partition 1; extended 64gb
partition 2; linux swap 4gb
partition 3; ext4 / 50gb main install 
partition 4; ext4 10gb if i wanna try a different distro later
partition 5; ntfs 30gb for windows when its required
partition 6; ext4 /home 1.27tb want all my files to go here 
just wanting to check that correct

[http://i1208.photobucket.com/albums/cc377/3lud13/Screenshot.png](http://i1208.photobucket.com/albums/cc377/3lud13/Screenshot.png)

---

### Post by varunendra on 2011-09-16
> **3lud13 said:**
> partition 1; extended 64gb
partition 2; linux swap 4gb
partition 3; ext4 / 50gb main install 
partition 4; ext4 10gb if i wanna try a different distro later
partition 5; ntfs 30gb for windows when its required
partition 6; ext4 /home 1.27tb want all my files to go here 
just wanting to check that correct

[http://i1208.photobucket.com/albums/cc377/3lud13/Screenshot.png](http://i1208.photobucket.com/albums/cc377/3lud13/Screenshot.png)
Umm.. have never seen an extended partition in the beginning. Although not sure if this may cause problems in booting, why don't you make it the standard way? That is, 1 to 3 primary partitions in the beginning, then the extended one in the last.

Besides, usually a 2GB swap is more than sufficient (regardless of the amount of RAM) if you are not going to use hibernation or "suspend to RAM".

Also, some of us (including much experienced oldfred) prefer a separate 'data' partition instead of a common '/home'. We have our own reasons which we think are more common. We prefer to keep our user-data in that 'data' partition, and keep separate '/home' for each installation to avoid possible configuration conflicts between the different installations. Amount-wise the plan seems to be okay.

So my choice would be - 

[LIST=1]
[*]**40 GB** NTFS (primary - as win7/vista prefer primary partitions for themselves AFAIK)
[*]**40 GB** ext4
[*]**rest** - extended
[*]**2 GB** swap (extended)
[*]two equal data partitions in the rest of the 'extended' partition. NTFS if the system has win installed, ext4 if it is 'Linux-only'.
[/LIST]

---

### Post by Dangertux on 2011-09-16
Yay Mint! :-) I love that distro, though don't use it anymore.

But yeah, your partitions will boot. The scheme is not "standard" however, the extended partition won't contain a bootable flag anyway so it won't effect the bootloader.

The only thing if you're separating out your home that 50gb / partition will probably last you a long time. The Mint initial install is only like 6 GB or something like that.

I'd say go ahead and pull the plug :-)

---

### Post by pqwoerituytrueiwoq on 2011-09-16
i see nothing wrong with that
if you have a lot of ram (like my desktop) and don't think you will ever use swap put / at the front

separate /home is a good thing (some prefer to use a /data instead to keep there app settings separate from there data files)

---

### Post by varunendra on 2011-09-16
Here's the quote by oldfred that I mentioned in my previous post:
> **oldfred said:**
> ....
....
I do not believe in sharing /home either. Some do it and if the verisons  are all the same it will mostly work. If upgrading from one version to  another it is fine for the new verision will update settings. But if you  have systems using different versions of software you may get  conflicts. My /home is only about 1GB of mostly hidden folders &  settings as all my data is in a /data partition (including firefox &  thunderbird profiles and some other (normally) hidden data folders). 

I do believe in creating a /data partition and moving all your data  folders to that partition if you have multiple systems. Then you have no  conflicts and can easily mount your data in each system. I use linking  after mounting it.

But having a separate, shared /home does have its advantages. It really depends upon the way you are going to use it and the OSes involved.


**_PS_:**
> **Dangertux said:**
> ..The only thing if you're separating out your home that 50gb / partition  will probably last you a long time. The Mint initial install is only  like 6 GB or something like that..I think that's a very good point.

---

### Post by 3lud13 on 2011-09-16
I've always put my extended partitions at the front and never had any issues with it thats relatively the same format i have used on and off in the past though never worried about the /home directry.

The reason I have chosen 50gb for my main install is I am thinking I might try virtualbox and then maybe wont need the windows partition at all.

Have opted for 4gb of swap in means of kind of future proofing it as Im planning a new laptop soon but currently my laptop only has 2gb ram is this gonna cause issues currently or not.

And lastly I should change the /home partition to /data is that correct.

---

### Post by mue.de on 2011-09-16
I've choosen 16GB for '/' but now it's to less, my 65GB for /home are nearly used up cause virtualbox stores its images by default at the /home-Partition

---

### Post by varunendra on 2011-09-16
> **3lud13 said:**
> The reason I have chosen 50gb for my main install is I am thinking I might try virtualbox and then maybe wont need the windows partition at all.
 The default location for VMs (which are treated as user-data) is user's home directory. Besides, you can always choose where to put a VM and can even move it later.

> **3lud13 said:**
> 
Have opted for 4gb of swap in means of kind of future proofing it as Im planning a new laptop soon but currently my laptop only has 2gb ram is this gonna cause issues currently or not. IMHO, 2GB RAM is more than sufficient for most of the tasks you can do in Ubuntu. Together with 2 GB swap, you should never go out of memory for whatever you do (except if you plan to dedicate more than 1 GB RAM to your running VMs, or open a couple of hundred browser tabs simultaneously ;)). You can even use hibernation with an equal amount of RAM, which currently is 2GB. In fact, if you have 4GB or more RAM, you can completely do away with swap (not an official statement, just some user-experience).

> **3lud13 said:**
> 
And lastly I should change the /home partition to /data is that correct.
That completely depends upon what OSes you are going to use. For most, the separate /home is good. I just think (personally) that a separate /data is better. For you, if you have no immediate clear plans about OSes to be used, it should not be an issue. But leaving everything at default, and making the /data partition place for user-data definitely seems to me a better approach.

---

### Post by Perfect Storm on 2011-09-16
Moved to Other OS/Distro talk.

---

