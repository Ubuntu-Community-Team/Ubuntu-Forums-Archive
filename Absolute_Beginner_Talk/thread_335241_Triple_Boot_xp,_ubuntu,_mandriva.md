---
title: "Triple Boot xp, ubuntu, mandriva"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2007-01-10
Hi, I am currently running windows xp and ubuntu on the same hard drive. I want to add mandriva to my hard drive and am wondering how best to partition it. Currently I have my hdd set up like this:

| XP | ext3 - shared files and /home for ubuntu | ubuntu | swap |

I want to cut down on my shared partition to add in mandriva and use the shared partition for all three systems:

| XP | shared files and /home for ubuntu | possibly /home for mandriva? | mandriva | ubuntu | swap|

Now, would I need to add a new swap partition too or can I use/do I even need to use the swap partition already in place for mandriva?

Does anyone see a problem with the configuration I am thinking about?

And, since mandriva uses LILO (I think), is there anything special I have to do when I go about installing the OS?

---

### Post by tchoklat on 2007-01-10
not sure as to whether this will help you, refer to my earlier post on adding Ubuntu and Sabayon to one HDD and the set up of the boot

---

### Post by tomcat1965 on 2007-01-10
Mandriva 2007 gives a choice of Lilo or Grub,so you haven't any problems there,stick with Grub.:)

---

### Post by r4ik on 2007-01-10
Not to well known and based on Mandriva with extra's is "Cherbourg" it is a live cd with install option.

[http://distrowatch.com/?newsid=03856#0](http://distrowatch.com/?newsid=03856#0)

Give it a try.

---

### Post by herrma29 on 2007-01-10
I checked out cherbourg, and the website recommended using the mandriva live cd for the install, so I'm thinking I'll probably just stick with mandriva.

I was reading through previous threads and I found a suggestion to use a seperate partition for the grub loader so when I do updates on any of the OS's, I don't have to go through and redo GRUB, don't know if that is exactly what it said, but I think it is pretty close.

Would this be a smart move? And how would I go about doing it?

Any suggestions as to changes I should make to the partition configuration I am planning on?

---

### Post by louieb on 2007-01-10
> **herrma29 said:**
>  Currently I have my hdd set up like this:
| XP | ext3 - shared files and /home for ubuntu | ubuntu | swap |
I want to cut down on my shared partition to add in mandriva and use the shared partition for all three systems:
| XP | shared files and /home for ubuntu | possibly /home for mandriva? | mandriva | ubuntu | swap|
Are you planning to wipe the disk and reinstall everything? The reason I ask is there is a limit of 4 primary partitions on a hard drive. If you need more that 4 partitions then you will need to make one of the primary partitions an extended partition and add logical partitions inside of it. I don't trust GParted to create new partitions in the middle of a hard drive and preserve the data.
You might want to check PClinuxOS and its partitioner (diskdruid it think is the name). I've seen it do some non-standard partitioning that no other partitioner can do. I don't trust it either.
My P3 use to boot a half dozen type of Linux before I turned it into a web and file server. It only had 1 swap partition that was shared by all the Linux distros. And one distros grub was use to select which one to boot.
What you want to do can be done. The easy route is plan your partitions. Plan how to configure grub (there is are two ways that I can think of).  Partition the disk for all operating systems. Install operating systems.  Configure the boot loader. 
If your really into computers and Linux its lots of fun.:D

---

### Post by herrma29 on 2007-01-12
I would rather not wipe my hdd clean, I've been through that too much recently and have finally got things configured to where I like them.  I suppose it wouldn't be too bad to delete ubuntu.

So, would you recommend deleting all but my ntfs partition, creating a swap partition at the end of the drive, and an extended partition in between, then creating logical partitions for my linux OS's so it would look like this:

| NTFS | Beginning of Extended partition - Ubuntu | /Home Ubuntu | Mandriva | /home Mandriva - End of Extended Partition | Swap | ?

I think I could manage that. Quick question though, what would be the best way to go about backing up my /home files so that I don't lose all of the changes I've made since installing ubuntu? Is it as easy as burning them to a disk and then copying them back in once everything is taken care of or no?

---

### Post by bodhi.zazen on 2007-01-12
See if the gparted CD can help you manage your partitions. You can move or copy whole partitions ...

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)


Also, consider using just use one large data partition to share between all your OS.

Make it ext3 and you can rw from all os.

In /home use links to the data partition.

like this:

ln -s /media/data/documents ~/documents
ln -s /media/data/music ~/music
...

Thus you have all your config files in /home and all your data in /media data.

partition suggestion:

1. NTFS = Windows
2. Ubuntu root
3. Mandriva root
4. Extended partition
[indent]5. data
6. swap[/indent]

Just a thought ....

---

### Post by herrma29 on 2007-01-13
So if I understand you correctly, I will have my /home and /media data from both linux OS's in the same partition? Can I do that?

---

### Post by bodhi.zazen on 2007-01-13
Well, ~ = /home/user_name

So each Distro will have it's own, unique (root) partition. You will have a /home/user_name on each distro. 

The data partition is shared. 

I like this because that keeps all the configuration ("dot files") separate. 

You share the data with links.

 ln -s /media/data/music ~/music

Puts a directory, called "music", in your home directory. The music (data) itself is on the data directory which may be mounted at /media/data/music.

But yes, this is what I do. I hope I am clear on this ??

---

### Post by herrma29 on 2007-01-14
Hmm, not too sure if I'm following you entirely. I went ahead with my partitions last night though and this is what I dide:

NTFS
Extended
 - Ubuntu /home
 - Mandriva /home *not installed yet*
 - Media files
 - Swap
Ubuntu root
Mandriva root *not installed yet*


I was really happy to see Ubuntu still working this morning after deleting the swap partition so I could make my extended partition, moving my /home folder to the extended partition and placing my swap partition in the extended partition. Sometime, probably later tonight, I'm going to dive into installing Mandriva onto my hdd.

Thanks for all the help guys! This is going smoother than I was thinking it would, hopefully I didn't just jinx it...

---

