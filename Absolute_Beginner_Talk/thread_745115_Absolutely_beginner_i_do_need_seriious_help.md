---
title: "Absolutely beginner i do need seriious help"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by twisteddeeds on 2008-04-04
hello thanks for taking the time to read this... i am a beginner with linux and after a lonnnng time and  playing around with the live CD I have decided to take the plunge into linux but i need some help in where to start and any help would be much appreciated 

I will try to put my questions as clearly as i can just so that it wont require too much "trying to understand what im getting at" on your part.

ok here goes:

1) Im currently using a laptop running windows XP,I am thinking of getting an external harddrive Now at the moment I am going to get a 500 gb drive but i am unsure which one that would be the easiest "and i do use that term liberally" to set up for linux.  i have trawled through hundreds of pages on the web and to be honest i am starting to get really confused by the amount of options. And if anyone could recommend a few choices i would really appreciate it

2) ok, now i was thinking i have a load of stuff which i need on the windows system for work etc which rules out fully formatting the computer.  I was thinking of putting the ubuntu onto the external harddrive just to keep them seperate. If anyone could point me in the right direction it would help a lot.  

3) If possible i would like to have the choice to be able to switch between the OS's I would be partitioning the external harddrive into seperate partitions with my intentions of giving ubuntu 20gb.
what is the recommendations for this any tutorials etc would be appreciated i am "used" to windows more than linux

4) If possible i would like to be able to be able to switch computers with the external hd also, i have read on these very forums about the persistant live cd, and i have made sure that my bios can boot from usb. is this the only option for this choice, as in i mean if i wanted to be able to boot up any machine with the hard drive?

5) If i partion off unbuntu would i be able to access for example mp3s or pictures  on the external drive with both operating systems "obviously not at the same time by giving ubuntu its own partition, although in windows it would show as a 480gb drive. is this correct?
and if that is possible what would i need to do to work.

thanks again for taking the time to read this,
any help would be much appreciated

---

### Post by cmnorton on 2008-04-04
I could not tell from your post if you had used the live CD. I suggest you do that first, so you can get a first linux expereience without carving up your PC for a dual-boot.

---

### Post by bren on 2008-04-04
> 1) Im currently using a laptop running windows XP,I am thinking of getting an external harddrive Now at the moment I am going to get a 500 gb drive but i am unsure which one that would be the easiest "and i do use that term liberally" to set up for linux. i have trawled through hundreds of pages on the web and to be honest i am starting to get really confused by the amount of options. And if anyone could recommend a few choices i would really appreciate it

any one.... buy the cheapest etc
for me western digital essential 500GB

> 2) ok, now i was thinking i have a load of stuff which i need on the windows system for work etc which rules out fully formatting the computer. I was thinking of putting the ubuntu onto the external harddrive just to keep them seperate. If anyone could point me in the right direction it would help a lot.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
very big site with every possible install config option inclu your

> 4) If possible i would like to be able to be able to switch computers with the external hd also, i have read on these very forums about the persistant live cd, and i have made sure that my bios can boot from usb. is this the only option for this choice, as in i mean if i wanted to be able to boot up any machine with the hard drive?

pendrivelinux.com shows you can do this...
however if you are plugging into diff machines with different hardwares/screens/peripherals you can expect some wrinkles

> 5) If i partion off unbuntu would i be able to access for example mp3s or pictures on the external drive with both operating systems "obviously not at the same time by giving ubuntu its own partition, although in windows it would show as a 480gb drive. is this correct?
and if that is possible what would i need to do to work.


dual access is easy
for example you 

1) put data on a FAT formatted partition - native ability to read write this in Ubuntu and XP
2) put data on an ext3 (native to Ubuntu) partition and install ext3 read/write driver in XP (this is what i do)
3) put data on an NTFS partition (native to XP) and install ntfs-3g driver in Ubuntu (actually i think this might be pre-installed in new version Hardy Heron)

Hope that helps
bren

---

### Post by az on 2008-04-04
I think a better use of space and efficiency would be to install Ubuntu to your hard current hard drive and dual boot.  Use an external drive for storage.  That would be safer/more stable, too.

The installer can shrink your windows partition for you.  It should offer to do this by default.  Be sure that's what you are making it do when you install.  The option is called Guided Partitioning, Resize existing partition.  

I would take the default partitioning scheme where you don't have to make anything but a / partition and a swap.  The installer does that for you.  Forget about a separate home partition as this is not needed and less safe than using an external drive for backups.

---

### Post by twisteddeeds on 2008-04-04
thanks for replying so quickly

to answer cmnorton, yeah i have been trying out 7.10 on a live cd.  

thanks bren, the reason why i asked about the external hard drive was because i read that the setup for  seagate and maxtor needed tweaked a bit to make it work correctly with linux or some drives have features that can restrict or cause problems for linux.  thats why i asked which ones would people recommend that would give me the "straight out of the box" accessibility that someone of my linux teething stages  needs lol
 
I was wondering about the file access, if i formatted the external in fat 32 for all partitioins does that mean that no extra drivers would be needed unless it was ext3 or ntfs formatted?. So essentially if the external was formatted already in fat32 you could say it would be compatible with both OS's Straight out of the box?

sorry i must sound like a real noob lol, although when it comes to linux i think im pre noob lol, anyway seriously.  So im assuming most people would recommend doing a dual boot setup, and use the external for back up, 

thanks rez regarding partions, would there be any hiccups when installing the ubuntu i mean if you installed without making a partition in windows would this erase anything from windows . I mean if ubuntu installs, it creates its own partition would this be correct?

and if this is the case, what format would that partition be installed as ext3?

any more elaboration would be great

---

### Post by az on 2008-04-04
A fat16 or fat32 formatted drive will work fine in both OSes without any extra drivers.

The installer will create a partition for you.  Just be careful to not pick the option that says "Use Entire Disk'.  Be sure that the installer will resize an existing partition and create a new one.  By default it will be formatted to ext3, which is what you want it to be.  There is no reason to use any other filesystem than ext3 for Ubuntu.


If you don't get the resize option by default, reboot into windows and defragment.  Try again.

---

### Post by Oldsoldier2003 on 2008-04-04
> **az said:**
> I think a better use of space and efficiency would be to install Ubuntu to your hard current hard drive and dual boot.  Use an external drive for storage.  That would be safer/more stable, too.

The installer can shrink your windows partition for you.  It should offer to do this by default.  Be sure that's what you are making it do when you install.  The option is called Guided Partitioning, Resize existing partition.  

I would take the default partitioning scheme where you don't have to make anything but a / partition and a swap.  The installer does that for you.  Forget about a separate home partition as this is not needed and less safe than using an external drive for backups.

+1 booting from an external drive can become tricky. its just easier to use it for storage.

---

### Post by manixtate on 2008-04-04
Good luck with the problem guys. Am a new user myself and love the system. Getting used to tweaking myself and am glad that this system is so newbie friendly. good luck with the migration. Me I went with the dual boot on one disc. My only recommendation is that whatever you do you back up your valuable data.

---

### Post by az on 2008-04-04
> **manixtate said:**
> My only recommendation is that whatever you do you back up your valuable data.

So buy an external drive first, back up your data and then install a dual-boot.  

The installer can safely resize your windows partition, but that's no excuse for not making a proper backup.

---

### Post by corbett2908 on 2008-04-10
I recently loaded Ubuntu 7.04 on a pc which had been running windows xp, after backing up my data  to my ehd (maxtor mini 100 gb) usb

gee it would be nice if i could access it now

i cant see it in places

no sign of it when i plug it in

any help there for would greatly appreciated

---

### Post by stalkingwolf on 2008-04-10
try looking in places > computer.  it should show there, or file system.  you may have to try
a different plug.  ( mine does that sometimes)

---

