---
title: "Getting ready to install"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by chesman on 2006-12-27
Okay, I am going to install Ubuntu very soon. I am just wondering if my hard drive is setup for the installation. 

As it stands my hard drive is currently setup with two partitions, one sitting at 60 gig, which i am currently useing as my system partition, and the rest which stands at about 170 gigs for files etc.

Now will the 60 gig partition be ample enough to install Ubuntu onto? or will iahev to allocate more space?


As well, i have played with red hat a while ago, and upon installing that, it configured my partition for installation, just wondering if Ubuntu is the same?


basiclly i am curious as how the whole setup will go.


Thank you very much Ubuntu land.:p

---

### Post by Sef on 2006-12-27
> Now will the 60 gig partition be ample enough to install Ubuntu onto?

It is more than enough.   I believe 8 gb is recommended for root, a swap of 1 gb, and 51 gb for your home partition.

> the rest which stands at about 170 gigs for files etc.

What is the file system here?

> As well, i have played with red hat a while ago, and upon installing that, it configured my partition for installation, just wondering if Ubuntu is the same?


It wil install to an empty space if you choose that option.

---

### Post by chesman on 2006-12-27
The file system currently on the disk is NTFS

---

### Post by Stephen Howard on 2006-12-27
Are you proposing a clean install - ie erase everything and start from scratch?  If so, I'd recommend creating a few more partitions:

/
var
home
usr
swap
tmp

I also have another partition (/usr/local) in which I keep my large games - civ, ET etc.

Separate partitions allows a clean install instead of a sometimes difficult upgrade, and allows me to experiment with other distros without having to lose my configuration (/home) and without having to reinstall games.

---

### Post by Sef on 2006-12-27
> The file system currently on the disk is NTFS

Linux will read, but not write to NTFS.  There are some drivers in beta that write to it.   Usual file system is ext3, which is the default in Ubuntu.

---

### Post by chesman on 2006-12-27
Okay,

well ym question to you guys would be:

Is there an auto format function when installing the os taht will 1) format and clean teh partition 2) automaticlly crate the needed partitions for installation wihtout bothering with the data parrtition i currently have setup in the left over 150+ gigs on my drive?

---

### Post by punx45 on 2006-12-27
since you are trying to preserve one partition on the disk i would highly reccommend editing the partitions manually.   there is an auto install option but i wouldnt trust it to leave the keeper partition alone.   it may atempt to format the entire disk.   with that in mind, make sure to back up all the stuff you dont want to lose on the data partition.   no matter what method of partitioning you use, there is always a risk of losing the contents of the entire physical drive.

i like to suggest installing a second scratch disk on your system to do the install, that way, if you mess up the partitions theres no loss.   you can get smaller used drives pretty cheap.

my drive situation goes like this:

hda = Windows system disk ~ 40G?
hdb = Ubuntu system disk includes /, /home, and swap partitions ~ 20G
hdc = data disk formatted in ext3 ~ 300G


with a normally working grub you can select windows or ununtu even when they are on other drives, however my grub is messed up for totall different reasons, so i just select whatever drive i want to boot with through BIOS.

---

### Post by chesman on 2006-12-27
Ideally i plan on purchasing an external HD so i can store all my files tehre, so i am free to play with my computer rather then always worrying about losing all my data i have created / saved over the years.

But in terms of these customer partitions, i was thnking, with these created and allocated space already, would the os look for these during installation? or would you have to direct each step of the install to install the files in these places. i.e. tell it to install the usr dir's in the /usr partition?

---

### Post by MrKlean on 2006-12-27
My past limited experience recommends you defrag the windows first.  It can save you a bunch od problems in the long run ; )

---

