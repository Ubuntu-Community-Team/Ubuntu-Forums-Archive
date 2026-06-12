---
title: "Hard Drive Partitions"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-11-15
What is the advantage to making a separate partition for the /home data.  Wouldn't it be just as easy to have just one partition and run everything off of that.

---

### Post by bscbrit on 2006-11-15
Of course it will work but, if you decide that you want to change your distribution (i.e. install a different version of linux for example) then it will overwrite all your data that is stored in the /home directory.  By keeping your /home on a separate partition you can upgrade your Ubuntu, change distribution or do many other things while keeping all of your data (and your current preferences) intact. :D

---

### Post by kinematic on 2006-11-15
a separate /home partition contains all your personal settings.
in the event that you have to re-install you just don't format the /home partition and you keep all those settings.
that way you keep all your browser,e-mail and other program settings.
just open your /home folder and goto view>hidden files and folders.....that's all the stuff that doesn't get lost.

---

### Post by alienexplorers on 2006-11-15
Thanks for the information.  Now how would I go about making a seperate /home partition since I did not make one from the start without loosing all my data.

---

### Post by kinematic on 2006-11-15
just to note something about what bscbrit said.....using 1 /home partition for several distro's doesn't always work....it can create conflicts.

---

### Post by alienexplorers on 2006-11-15
I only run Ubuntu 6.06 and thats it.  Just would like to seperate /home partition in case of a crash.  Could I use the live CD and gparted to correct this.  If so how?????

---

### Post by kinematic on 2006-11-15
the pclinux os wiki has a great explenation on how to do this.
[http://www.pclinuxonline.com/wiki/MoveEntireDirectory](http://www.pclinuxonline.com/wiki/MoveEntireDirectory)

---

### Post by Foxmike on 2006-11-15
> **alienexplorers said:**
> I only run Ubuntu 6.06 and thats it.  Just would like to seperate /home partition in case of a crash.  Could I use the live CD and gparted to correct this.  If so how?????

Do you still have free/unpartitionized space on your hard drive?  If so, it's quite easy with gparted (partitionner GUI).  But if not, I've heard (correct me if I'm wrong) that there are risks to lose data when resizing partitions.  I would then suggest backing up your /home directory into one/several DVD(s) and re-install the stuff.  It might look as an extremist solution, but it is worth the time: last week, while testing a few things, I had to reinstall twice... I was very (very!!!) glad to have my /home on another partition!;)

---

### Post by bulldog on 2006-11-15
Take a look here,

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Very nice site with all the info you can wish.

---

### Post by bodhi.zazen on 2006-11-15
> **bscbrit said:**
> Of course it will work but, if you decide that you want to change your distribution (i.e. install a different version of linux for example) then it will overwrite all your data that is stored in the /home directory.  By keeping your /home on a separate partition you can upgrade your Ubuntu, change distribution or do many other things while keeping all of your data (and your current preferences) intact. :D

Just a thought.

/home/user_name contains two types of information. configuration/preferances and data.

IMO I prefer a /data partition over a /home partition.

I back up and share /data and some system configuration files in /data (background images, xmms skins, etc) in /data

The configuration files do not need backup and if you run multiple distros, as I do, and has been suggested, the configuration files in /home/user_name can conflict.

So a potential (easy) solution: Just create a shared /data partition and move you data out of /home.

Just my 2c 8)

---

### Post by Notbilly on 2006-11-15
> **bodhi.zazen said:**
> Just a thought.

/home/user_name contains two types of information. configuration/preferances and data.

IMO I prefer a /data partition over a /home partition.

I back up and share /data and some system configuration files in /data (background images, xmms skins, etc) in /data

The configuration files do not need backup and if you run multiple distros, as I do, and has been suggested, the configuration files in /home/user_name can conflict.

So a potential (easy) solution: Just create a shared /data partition and move you data out of /home.

Just my 2c 8)

Bodhi, does all my data get saved to /data folder automatically by default, or do I have to explicitly tell the OS and applications to save stuff there?  I haven't tried using Linux yet, so I'm not familiar with how it handles this.  Thanks for any enlightenment you can provide!

---

### Post by mo79 on 2006-11-15
Bare in mind though, the art of assigning partitions is a bit of a science. If you're fine with just root and swap, go for that as folders within root can expand and contract naturally, whereas if you fill up your /home, you'll have either have to delete files or resize it (in turning resizing other partitions).
But don't let that deter you if you proceed. Just letting you know. ;)

---

### Post by bodhi.zazen on 2006-11-15
> **Notbilly said:**
> Bodhi, does all my data get saved to /data folder automatically by default, or do I have to explicitly tell the OS and applications to save stuff there?  I haven't tried using Linux yet, so I'm not familiar with how it handles this.  Thanks for any enlightenment you can provide!

No your user data will be saved to /home/user_name by default.

I personally have a data partition: /mnt/Zen

Fstab: /dev/sda14 /mnt/Zen ext3 auto,users 0 0

Now, make a link in /home/bodhi (cd ~):

ln -s /mnt/Zen Zen

ln -s /mnt/Zen/documents documents

ln -s /mnt/Zen/music music

ln -s /nmt/Zen/bin bin
[indent]for the occasional bash or python....[/indent]


ln -s /mnt/Zen/src src
[indent]for source code I download and ./configure make checkinstall[/indent]


ln -s /mnt/Zen/downloads downloads

Add as many links as you like. Just as good as the "real thing" in /home/user_name, just all on a separate partition. If I re-install Ubuntu, just re-create the links in home. :)

...

---

### Post by alienexplorers on 2006-11-15
Thanks for the information.  Looks like I will keep everything on one partition until I upgrade the system.  Thinking of doing a clean install anyway in the near future.

Donnie

---

### Post by renatosilva on 2007-01-11
Guys woudn't be easiest (since shared /home may conflict and so would exist one for each distro) just do not have a separate /home but a /data as some have said??? Then when re-installing you just backup your /home into /data and bring it back after all. :-k 

I guess I'll proceed this way. Take a look on my thread:

[http://www.ubuntuforums.org/showthread.php?t=335946](http://www.ubuntuforums.org/showthread.php?t=335946)

---

