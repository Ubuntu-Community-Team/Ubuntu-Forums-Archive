---
title: "Selecting Mounting Point Designations"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by ucsdrake on 2007-01-01
hey,

I am currently very new to Linux overall and I am looking to install Ubuntu for the first time on my laptop.  However I am only doing so on my external drive (my internal drive is for work only).  I was able to successfully partition my drive (its a 250gb Kaser USB 2.0 that was previously running windows.  Please however note that I want to slowly intergrate myself to Linux and at the time being I left about half of the drive for windows.  The full breakdown of my partitioning is as follows:

180gb - Windows NTFS (primary) NTFS
2gb - Windows VM (primary) NTFS
2gb - Linux Swap (primary) EXT3
10gb - Linux Root (primary) EXT3

In an Extended Partition
31gb - Sharded linux/Windows Fat32
2gb - Linux Swap (primary) EXT3
15gb - Linux/Home EXT3
5gb - Linux/tmp EXT3
5gb - Linux/var EXT3

now i was able to create partitions for all of these so here comes my question(s)

Im on the mounting stage of the installation and I dont know if I need to create mount points for even the windows partitions which I wont be touching with ubuntu (such as my internal drive which I didn't list because I wont be using with ubuntu) and what should I call them.

and second

What should I mount my FAT32 partition as (such as / or /tmp or /var, etc.) I know I wont be using those names but thats the type of name I'm looking for.  Up to this point in time ive been following this guide 

[http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html)

but the "WIN/LIN Shared" usage doesnt work when I'm trying to mount

I've also looked at the following links for help with no sucsess

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.ubuntuforums.org/showthread.php?t=282018&highlight=Fat32+Size+Limitations](http://www.ubuntuforums.org/showthread.php?t=282018&highlight=Fat32+Size+Limitations)

Thanks for any help in advance and if any more information is required to help answer the question please just ask.

---

### Post by kepos on 2007-01-01
if you are new to linux, i would suggest you not to use different partition for different directorys, like partition for /var, partition for /tmp, etc.
Split your hdd in three pieces:

one for windows
one for linux swap
and one for other linux things.

that is joust my suggestion.
well, you don't need to make mounting points for partitions you want use.
For secound one, i'm not shure what realy are you tryng to say but let me try: in directory /media create folder called whatever you like and mount your shared parition there.
and i would also suggest you to use [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by ucsdrake on 2007-01-02
hey,

thanks for the advice although i came to that conclusion before and ended up partitioning it just like you said but with one more primary involved (that being lin/win shared as a Fat32 file system)

now my problem lies in the boot up of the system.  when i finished installing i installed my GRUB in hd0 (my internal drive) while all of my other linux files is in my exernal HDD ( which is hd1).  this is where i think my problem lies, as when i start up i get a GRUB error 21

any advice on that?

currently im looking to see if i can change the GRUB location and im looking at this thread:
[http://ubuntuforums.org/showthread.php?t=24113&page=3&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&page=3&highlight=reinstall+grub)

that the right way to go by any chance (id prefer to be able to do it by coding rather than reinstalling if theres any chance id be able to do that)


thanks again

---

### Post by ucsdrake on 2007-01-02
as an update to my situation, its something very strange, i found out that when i start up fresh (not a restart but like a cold start) the initial time i boot i get the Error 21 message after the option to go to bios or changing the boot order.  then when im stuck at the Error 21 all i have to do is press ctrl + alt + del and then the next time i boot around the GRUB loads properlly and i can choose either windows or linux as id like to 


anybody heard of the situation of having to restart to properlly run the GRUB and if so how can i fix it?

im looking through the Wiki now for info

---

