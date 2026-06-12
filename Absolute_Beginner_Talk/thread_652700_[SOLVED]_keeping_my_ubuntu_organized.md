---
title: "[SOLVED] keeping my ubuntu organized"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by bcn17 on 2007-12-29
I am must making the switch from windows to ubuntu and am trying to figure out the best way to organize my computer. 

My past windows systems have always had an operating system/microsoft update partition, a programs partition, and a data partition. I was/am religious about directing all programs to a respective folder on the data drive for saving files and keeping my C drive (windows) as separate from my data and programs as possible. If I ever had a problem a fresh install was relatively easy although i did have to reinstall all the programs. 

What I'm wondering is if their is a way to set up ubuntu so that a complete reinstall could happen to one partition and still have all my programs and data working and happy when the re install is complete. And how the organization is actually taking place in the computer.  In windows I would install a program to a folder and it would be IN THAT FOLDER and in some places in the registry on the main partition (As far as i understand). However, when install different things I find myself following commands and not fully understanding what is happening or how I could potentially change things (like folder locations to better keep myself organized.) I installed k3b, amarok,and WINE. I have also installed OSS for sound (ALSA wouldn't work) and flash. In windows i would relate these 2 categories to programs and drivers... but how is this organized in ubuntu and is it possible for either of these types of things to be separate from the root partition. Additionally, in windows different partitions were each given a different "drive" like C: D: and E: however i made a /home partition in the partition manager on install however it is located in /. not a lateral step in the tree but down. My NTFS partitions are also down the tree in /media rather than a lateral step.

I know this is many questions and somewhat convoluted. I searched for some sort of guide and all over the forums but couldn't something that could put it all together. If anyone knows of any links that might be helpful to boost me up the learning curve or has any answers they would be most appreciated!

*I have read starcraft.man's guide on repositories/installing programs with  synaptic.
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by PeterJS on 2007-12-29
> **bcn17 said:**
> I am must making the switch from windows to ubuntu and am trying to figure out the best way to organize my computer. 

My past windows systems have always had an operating system/microsoft update partition, a programs partition, and a data partition. I was/am religious about directing all programs to a respective folder on the data drive for saving files and keeping my C drive (windows) as separate from my data and programs as possible. If I ever had a problem a fresh install was relatively easy although i did have to reinstall all the programs. 

What I'm wondering is if their is a way to set up ubuntu so that a complete reinstall could happen to one partition and still have all my programs and data working and happy when the re install is complete. And how the organization is actually taking place in the computer.  In windows I would install a program to a folder and it would be IN THAT FOLDER and in some places in the registry on the main partition (As far as i understand). However, when install different things I find myself following commands and not fully understanding what is happening or how I could potentially change things (like folder locations to better keep myself organized.) I installed k3b, amarok,and WINE. I have also installed OSS for sound (ALSA wouldn't work) and flash. In windows i would relate these 2 categories to programs and drivers... but how is this organized in ubuntu and is it possible for either of these types of things to be separate from the root partition. Additionally, in windows different partitions were each given a different "drive" like C: D: and E: however i made a /home partition in the partition manager on install however it is located in /. not a lateral step in the tree but down. My NTFS partitions are also down the tree in /media rather than a lateral step.

I know this is many questions and somewhat convoluted. I searched for some sort of guide and all over the forums but couldn't something that could put it all together. If anyone knows of any links that might be helpful to boost me up the learning curve or has any answers they would be most appreciated!

*I have read starcraft.man's guide on repositories/installing programs with  synaptic.
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)


Root is root, it is absolute, there is no such thing as a file system that exists outside of /. /media is a common place for non-system drives to reside. The linux file system is built around a very different paradigm as programs are built around a very different paradigm.  In windows as you said there is a folder per application, but in linux things are organized by function, so all essential programs would be installed in /bin, all non-essential programs in /usr/bin, settings  in /etc, and shared stuff like documents, icons, etc in /usr/share.

here's the wikipedia article on it
[http://en.wikipedia.org/wiki//etc#Directory_structure](http://en.wikipedia.org/wiki//etc#Directory_structure)

As for keeping apps and settings between re-installs/upgrades the best way is to have /home on a separate partition and just not over writing that. That will preserve your settings as for applications given that they're spread all over the place the best way to preserve them across re-installs is to make a list of what's installed, there a guides on how to do that but I don't have one handy, and then re-install it first thing. Good news is that since 7.04 they've got upgrading working smoothly like it should, so just wait for the next release to come out and the update manager to pester you to upgrade.

---

### Post by Can+~ on 2007-12-29
Yeah, I'm also like strictly ordering my applications, never as strict as you though (no offence). And true.. your question is hard to chew, so, I'll try to make a general explanation, and see if you can narrow down your question.

Windows uses C, D, E for each partition.
Linux; uses a root partition "/" and every other partition is mounted on different sections.

Example, you have a full pc running on ubuntu (or any other *nix OS) and you want to create your own server, with it's own separate hard disk, on a folder named "www". Instead of having a "D:" or whatever, you create a folder named "www", and mount it on that particular folder. When a device is mounted, you can access is content, and basically, you can mount anything as you like.

By default, when you install ubuntu, after windows, it will add any partition of windows as a "/media/" device. In your case, you said that it you set the /home/ to a partition, that will be completely transparent to you, but it is there, and yes, everything will pop out from the tree "/".

My personal recommendation; I created the following array:

[40 Gb Windows NTFS]
[20 Gb Ubuntu Ext3] [1 Gb SWAP] [220 (approx) Gb NTFS]

As ubuntu can read/write in both File systems (NTFS), I created a partition dedicated as a common place for both OSs (called.. "common"). And created folders in that partition for each OS specific stuff. Also, I dislike the "/home/" specific partition, since many of the common user's configuration files are dumped there, possibly creating incompatibilities when formatting the OS partition. 

If you want to edit how the partitions are made, use Gparted. If you need to change where a partition is mounted, edit /etc/fstab (but proceed with care, and with a proper reference).

Hope it helps.

---

### Post by jas0 on 2007-12-29
As you probably know in Ubuntu everything is under the root or /. All drives that you will ever use will start with /. That doesn't mean that they're not segregated from your OS and application stuff.

Let's say you have 3 drives. You have one drive house the / paritition. Within that, you can have another drive house the /home partition, and yet another the /media/files partition. If your / drive somehow dies, you still have the /home and /media/files housing drives intact! You can simply reinstall the OS and get back to work. The point I'm trying to make is that while it seems that everything in Ubuntu is a single drive, is may only seem this way.

By default, unfortunately, everything like / and /home and /etc and /bin and al the other directories are on the same drive. In this case, you are putting everything on the equivalent of the C: drive in Windows. So the thing that you need to do if you happen to be a neat freak like me, is put /home on a separate partition (or preferably drive). This will allow you to keep using your /home after reinstalling and often even using other flavors of Linux. And best of all, you keep most of your program settings. This is the equivalent of being able to move Windows user folders located under documents and settings between computers (which you can't). Most people I know who use more than a couple of hard drives simply mount all their hard drives under /media. Let's say that you have /media/storage and /media/storage2. This is the equivalent of D: and E: in windows. If you lose the main OS install for some reason, you will still be left with both storage and storage2.

So in conclusion, in Ubuntu you will always see the same basic structure, but beneath it you can have the order you love.

Note: Always back up your data and don't run commands you don't understand.

---

### Post by meindian523 on 2007-12-29
There's no problem with your partitions,only with your concept of them.You have created a separate partition for /home,it means it will be accessible at a folder(home) under root(/),that's why it's /home.Don't worry,all your data and settings are safe in case you ever want to reinstall or upgrade to a newer version via a clean install unless you format the /home partition by mistake.....in Linux you never have a lateral step outside the directory tree unlike in Windows wherein you have C:,D:,E: etc where each of them is a separate directory tree along with being partitions.......maybe a graphic would do the job?
```

                                                                          /
                                                                          |
                                                                          |
          -----------------------------------------------------------------------------------------------------------------
          |              |               |              |           |                  |          |          |          |
        usr               home          bin          root         etc             media           tmp      boot           mnt


```
Note that each of these directories is referred as /mnt,/media,/home,/usr,etc ie you may read it as "the folder mnt under /","the folder media under /",etc wherein you can access the files of whatever partition the folder points to,got it?

---

### Post by meindian523 on 2007-12-29
and jas0 is correct,though it looks like one partition,it really is different partitions accessible(mounted) under one partition(/),though this doesn't mean that the / partition has any say on what data is read/written/moved inside those partitions or between those partitions that is even if / gets blown,you still have your /home and whatever other partitions you decided to make safe on your HDD.

---

### Post by bcn17 on 2007-12-29
Thanks everyone! This helps **a lot**.

---

### Post by meindian523 on 2007-12-29
Then please mark the thread as solved.

---

### Post by hyper_ch on 2007-12-29
I'd recommend to use three partitions for linux:

(1) SWAP --> about the double size of your ram (up to 1 GB in size)

(2) ROOT ("/") --> make that about 10-15GB --> it will contain program files, system files, ....

(3) HOME ("/home") --> all the rest - as much as you want. That one would be equivalent of the Windows "users and settings" folder. That's where user Data goes into. It's good to have that one on a seperate partition.

---

### Post by Perfect Storm on 2007-12-29
A full list of linux structure:

[img]http://www.imageviper.com/displayimage/99007/0/linux_file_structure.jpg[/img]

---

### Post by PeterJS on 2007-12-29
> **Artificial Intelligence said:**
> A full list of linux structure:
<Really Awesome Diagram>


That's just plain awesome, I'm totally saving a copy of that for next time one of these threads surfaces.

---

### Post by Perfect Storm on 2007-12-29
No problem. I use it myself, my memory slip sometime when I have to do stuff a place where I sometimes rarely do anything. So it's a nice to have a quick map.

---

### Post by bcn17 on 2007-12-29
That map is gonna be my desktop for a while ;)

---

