---
title: "Another Partition Post"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by zallarak on 2007-12-22
I realize a TON of posts are about how to make a partition, etc. but I really screwed mine up. Basically what I want is a dual boot, windows xp and ubuntu. Whenever I run the ubuntu installation, I do not get the option of automatically creating a partition. I got partition magic and tried to manually create partitions. This did not go so well. I tried to make a 17 gb partition for ext 3 and a 3 gb for swap. My computer has a 70 gb hd and 2 gb RAM. I now have no idea what I have done to my computer. I would really appreciate help. Here  are screenshots before my I used partition magic.

[http://farm3.static.flickr.com/2280/2129661670_783f0d6b19_o.png](http://farm3.static.flickr.com/2280/2129661670_783f0d6b19_o.png)
[http://farm3.static.flickr.com/2339/2128885381_0ddd267895_o.png](http://farm3.static.flickr.com/2339/2128885381_0ddd267895_o.png)

Here is my partition status now as from partition magic. To make it all worse, partition magic is not lettign me edit the unallocated space anymore. I think this is because I have too many "primary" ones, but I cannot change anything.

[http://farm3.static.flickr.com/2110/2129665688_38399b8afe_o.jpg](http://farm3.static.flickr.com/2110/2129665688_38399b8afe_o.jpg)

Again, my major goal is to have dual boot; xp and ubuntu. If possible, I would also like a 500 mb space where I can save documents to share them with xp and ubuntu (open office/microsoft office).

Thanks very much everyone. And again, I realize this is a pretty stupid question, I am new to all of this and am just making the switch to linux.

---

### Post by StGeorge on 2007-12-22
Do not do anything yet.
Do not touch drive.
Just use browser.
I have done samething but recovered.

---

### Post by StGeorge on 2007-12-22
Just wait while I look through my notes.

---

### Post by StGeorge on 2007-12-22
DO NOT MOVE.
I use Partition Magic 2

---

### Post by zallarak on 2007-12-22
thanks so much^ will wait patiently

---

### Post by StGeorge on 2007-12-22
I am about to give you my Pidgeon.
I have to install1st.
Wait and do not try anything.
All can be recovered.

---

### Post by StGeorge on 2007-12-22
ok i have downloaded.
forgot i did not have it on comp.

---

### Post by zallarak on 2007-12-22
thanks again st george, i appreciate it alot. one thing is i havent lost any data or anything like that. my windows is fine. i just do not know how to install ubuntu on dual boot!

---

### Post by StGeorge on 2007-12-22
ok so i'm doing my control panel

---

### Post by StGeorge on 2007-12-22
contact me on messenger

---

### Post by kellemes on 2007-12-22
Please read the following first, if you have any question.. let us know.
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by StGeorge on 2007-12-22
you must let grub do the boot loading 1st.
it will write to your mbr.
then u change it later.

---

### Post by zallarak on 2007-12-22
the only thing is i dont know how to fix my current situation. should i just delete all my new partitions and resize my xp to its original?

---

### Post by StGeorge on 2007-12-22
i have suffered grub.
that is the boot loader.
do not worry it can be changed.
i hve done it before.
but now i want to use a boot loader of my choice.
ubuntu wants to use grub.
let it.
change it later.
it's only the mbr.

---

### Post by zallarak on 2007-12-22
i just deleted some stuff so now i have:

dellutility FAT 47 mb
local disk nfts 52 gb
**20 gb unallocated**
3.7 gb dos, etc

i just want that 20 gb unallocated to be for ubuntu.
thanks again for help

---

### Post by StGeorge on 2007-12-22
you are using Partition magic to do this?
If not be careful.
When I used PM iI created space as free for linux.
It is not a great partitioner.
But neither is GParted.
If you are under a windows OS then create free space with PM and let Ubuntu find the free space.
Unformatted.
Remember the free space you creatyed and on what drive when you run Ubuntu. with GParted.
You can run CD let it open a (live) windows type enviroment to see a similar partititioner to Partition Magic.

---

### Post by StGeorge on 2007-12-22
Bye the way.
If you create free space on a second drive for Ubuntu.
Put it at the beginning.
With PM you might to apply alot of changes to do this.
But it is worth it.
PM is a great Partitioner cos it relies on Common Sense to complete the tasks.
GParted can be danger cos it relies on Linux KNOW HOW.

---

### Post by kellemes on 2007-12-22
> **zallarak said:**
> i just deleted some stuff so now i have:

dellutility FAT 47 mb
local disk nfts 52 gb
**20 gb unallocated**
3.7 gb dos, etc

i just want that 20 gb unallocated to be for ubuntu.
thanks again for help

What's the 3.7 Gb dos partition?

Anyway.. when you have 20Gb free you can simply use the Ubuntu installer to create partitions for Ubuntu. (better not use Partition-Magic)

An example..
a 8Gb partition formatted ext3 mounted at /
a swap-partition size: 2 x the size of your memory with a max of 2Gb
the rest you can format ext3 and mount at /home.

Edit: O yeah.. and create a fat32 partition as you wished for.

I really advise you to read [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by zallarak on 2007-12-22
thanks for the link kellemes. the DOS partition came with my computer, i have no idea what it is. maybe i am saying it wrong.

so if i have 20 gb unallocated, ubuntu will find it my itself? will i have to use manual partitioning, bc i have no idea how to use it.

and how do i select certain partitions to be mounted for linux? do i check it off or delete the ones im not using for linux? the hwole manual partition thing i dont understand.

thanks again for all the help.

---

### Post by StGeorge on 2007-12-22
This can be described as ********.
Not the poster.
Why when running an OS can it not suit my needs.
I tell u why.
Cos it thinkks it's the master
It ain't.
I am.
If only we people try to write this stuff for the machines then OK.
So I will try to pass on what I know ,(or don'tknow).
So No. Well only if it helps people who really want to understand.
There are easy options for a Linux User out there.
I will, when I get time give a full download list of all known .exe files for Liunux users of WinBlow  machines.
Happy New Year.

---

### Post by kellemes on 2007-12-22
> **zallarak said:**
> thanks for the link kellemes. the DOS partition came with my computer, i have no idea what it is. maybe i am saying it wrong.

so if i have 20 gb unallocated, ubuntu will find it my itself? will i have to use manual partitioning, bc i have no idea how to use it.

and how do i select certain partitions to be mounted for linux? do i check it off or delete the ones im not using for linux? the hwole manual partition thing i dont understand.

thanks again for all the help.

I don't remember how the partitioner looks in detail I'm afraid.
I'd use manual partition, you'll see for yourself how it works, simply create these partitions in the unpartioned space. You'll see the option to give a mountpoint for the partition you just created.
Don't worry, just don't touch your other partitions and you'll be fine..

---

### Post by zallarak on 2007-12-23
thanks so much kellemes and st george. i finally have ubuntu thanks to you guys. i really appreciate the advice/links you posted. ubuntu is seriously amazing. amazingly supportive community.

---

