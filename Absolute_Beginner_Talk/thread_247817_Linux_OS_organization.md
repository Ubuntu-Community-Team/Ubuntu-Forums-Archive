---
title: "Linux OS organization"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Zarate on 2006-08-31
Hi all,

First of all thanks to everybody helping here, you really help : ) After two days reading this and other forums I finally managed to make my microphone work (yeah!), so now I'm planning to start dealing with other stuff.

I'm a (more or less) advanced Win user and I used to make at least two partitions, one for Win itself + programs, and another one just for my files. In the case of a reinstallation, I just needed to remove the "system" partition and didn't have to worry at all (ok, a backup never hurts) about the "files" partition. How can I achive something like that in Linux? I'm fairly sure it's possible.

Then, I don't know "what happens" when I install something in Linux. I mean, in Win I know that the application (usually) goes to "c:\Program files" and many of them write the registry. How this works on Linux?

Sorry for the _so_ basic questions and thanks for helping me organice my new Ubuntu!

Cheers,

---

### Post by amo-ej1 on 2006-08-31
Withing Linux the is no great distinction between your 'operating' system and the software you install. Linux, Ubuntu in this case, is a bundle of software. So 99% of the software you will be using will be available within your distribtion. And the distribution takes care of installing everything in the place it belongs to (isn't that nice ?)
So when you install and application, you simply do so e.g. 'sudo apt-get install amsn' this will install amsn (and dependencies) after this you can request where it has placed which files ('dpkg -L amsn'). 

When you google for 'linux filesystem' you will get different pages all explaining what files go where. So you don't need to worry about keeping you applications seperate from your operating system, both are one big piece already. The only thing you need to know is where to place your data which goes in your home directory.

---

### Post by Kobalt on 2006-08-31
Hi,

To create a new partition you can start your computer with a LiveCD of Ubuntu, then use Gparted (System > Administration > Gnome Partition Editor) to resize your current Ubuntu partition, and after that create one from the space you freed. 

And for you application path : apps are usually stored in /usr/lib/, but you should not worry at all for that, nore try to modify it. Synaptic is here to handle everything you need for apps managment. 


Cheerios !

---

### Post by tribaal on 2006-08-31
> Then, I don't know "what happens" when I install something in Linux. I mean, in Win I know that the application (usually) goes to "c:\Program files" and many of them write the registry. How this works on Linux?

Hum well it works a bit different in linux:

First of all, it really depends if you install stuff from a package or by downloading it from the internet.

Installing from the internet is easy, it will most probably just unpack itself in your current directory, and voilà, it stays there.

Now the rest (packaged programs), files are stored by type, not really by program. Like most binaries (.exe's if you like) are stored in /usr/bin. Most libraries in /usr/lib, and so on.

Does this help any?

- trib'

---

### Post by macdo on 2006-08-31
I always keep the /home directory on a separate partition, as it contains all the data (music, docs, emails, Firefox profiles, etc) That way, if ever I need to reinstall, I wouldn't lose anything. 

The basic difference between the Windows FS and the Linux FS is that Windows starts from the HD (C:\ and/or D:\) while Linux always starts from the same place (/), regardless of what the partitioning scheme is.

For example, your home directory in Windows could be called 'C:\Documents and Settings', or 'D:\Documents and Settings' (I think...), whereas under Ubuntu, it will always be /home/user, whether that directory is on hda1 or hdb2, or any other partition. 

One other point that you may or may not know: in Windows, partitions are given consecutive letters: C, D, E, etc., irrespective of the HD they're on. Linux gives the HD a letter (hda is the first hard drive, then hdb, hdc - or sda, sdb, sdc for serial hard drives), and the partition gets a number (hda2 is the second partition on the first hard drive)

Hope that helps.

---

### Post by DonS on 2006-08-31
Hi,

Within linux, the entire filesystem is stored within '/', or root.

You can mount different partitions within different directories there.  Normally, programs are installed in /usr.  Your home directory (where you store all your documents) is in /home, under your user name (e.g. /home/your_username).

The cool thing is that you can mount different partitions and media anywhere in the filesystem.  For example, inserting a CD mounts it as /media/cdrom.  To keep you're home directory on a seperate partition, you need to create 2 different partitions at install time.  One is the root partition and would contain all the programs etc. and 1 is the Home directory.

I believe the installation procedure allows you choose where to mount different partitions within the filesystem [1].  If so, select the first partition as '/' and the second as '/home'.  This way, if / shen you blow away the root partition and reinstall, the /home (and all you're documents) will hopefully still be intact.

[Wikipedia]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") gives a nice description of the filesystem structure under Linux / UNIX, if you're interested.

[1] Disclaimer: I haven't actually used the installer for a long time.  Someone else can probably give you decent instructions how to use it to set things up properly though.

---

### Post by steve.horsley on 2006-08-31
Normally, the executable goes in /usr/bin and other stuff goes in a special directory maybe under /usr/lib. Sometimes, config files go somewhere in /etc.

The best way to get a feel for this is to use synaptic, pick some already installed packages, right-click them and look at the list of installed files.

---

### Post by Zarate on 2006-08-31
> **macdo said:**
> I always keep the /home directory on a separate partition, as it contains all the data (music, docs, emails, Firefox profiles, etc) That way, if ever I need to reinstall, I wouldn't lose anything. 

Yeah, I like this. It's what I'm thinking and quite close to what I do in Win.

> **macdo said:**
> The basic difference between the Windows FS and the Linux FS is that Windows starts from the HD (C:\ and/or D:\) while Linux always starts from the same place (/), regardless of what the partitioning scheme is.

For example, your home directory in Windows could be called 'C:\Documents and Settings', or 'D:\Documents and Settings' (I think...), whereas under Ubuntu, it will always be /home/user, whether that directory is on hda1 or hdb2, or any other partition. 

One other point that you may or may not know: in Windows, partitions are given consecutive letters: C, D, E, etc., irrespective of the HD they're on. Linux gives the HD a letter (hda is the first hard drive, then hdb, hdc - or sda, sdb, sdc for serial hard drives), and the partition gets a number (hda2 is the second partition on the first hard drive)

Hope that helps.

It really helps, thanks a lot. Other comments and replies as well. Awesome to see 6 answers in 2 hours : ) However, I'll bother again with more trivial stuff, stay tuned!

Cheers,

---

