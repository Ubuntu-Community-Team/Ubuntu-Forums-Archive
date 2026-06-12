---
title: "ntfs-3g i dont think i get it?!?!"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Jmejme on 2008-01-20
ok heres the deal:
I am somewhat new to ubuntu i forgot what version. right now i only boot from live cd. i am awaiting my ne laptop. but here is where my prob is. i want to find out what exactly what im getting into with ntfs-3. from what i understand it makes it possible to access a hard drive with the windows ntfs file format. does this mean that ntfs-3g can be used as a rescue tool? and what is FUSE??? can someone shine some light on this im very new to linux/ubuntu and   need some help

Thanks  alot!!!

---

### Post by st33med on 2008-01-20
NTFS-3G enables read-write support with an ntfs partition. This means that you can now write to Windows files and change them instead of just being able to read from it. It is not useful as a recovery option. 

I forget what FUSE was, however, maybe someone else knows...

---

### Post by Jmejme on 2008-01-20
ok thats ok i dont really need it as a rescue disk....but lets just say i was on a computer and wanted to pull some files from a harddrive that was using that file system. what permissions does this give me. and FUSE is something you need to install ntfs-3g atleast thats what one site said. and new question. 

How do i use/install ntfs-3g with ubuntu live cd?

---

### Post by PeterJS on 2008-01-20
FUSE, is the usersapce filesytem extension, I can only assume that the FUSE acronym is derived from a non-english language, or they just chose that acronym because it's more readable than UFSE.

What fuse does is provide a frame work for writing file system drivers in a plugin fashion. Once fuse is installed you can add as any driver based on fuse. The ntfs-g3 driver uses the fuse interface instead of loading as a direct kernel module. Another cool file system based on fuse is sshfs.

One application of ntfs-g3 would be a recovery tool. But it's just another file system driver I use it to access all of my music that's stored on my windows parition.

---

### Post by PeterJS on 2008-01-20
> **Jmejme said:**
> ok thats ok i dont really need it as a rescue disk....but lets just say i was on a computer and wanted to pull some files from a harddrive that was using that file system. what permissions does this give me. and FUSE is something you need to install ntfs-3g atleast thats what one site said. and new question. 

How do i use/install ntfs-3g with ubuntu live cd?

The live CD acts just like a full (but slow because it's live) install, so you can use apt to install the ntfs driver to the live environment. Install and run ntfs-config and apt will take care of all the dependencies, and ntfs-config will take care of all the configuration stuff for you.

---

### Post by st33med on 2008-01-20
Installation:
```
sudo apt-get install ntfs-3g
```

To be able to use the partition in nautilus, you just go to Places>>Computer and click the Volume.

ntfs-3g gives you total admin access over the partition.

---

### Post by rosegarden78 on 2008-01-20
It should still say kernel versions available when booting with GRUB.  I think the latest kernel is 2.6.24 or possibly higher.  NTFS is a file system invented in the Northwest United States.  The company that invented it has refused to share its other proprietary file formats, such as Word documents, to the public so that others may write compatible software.  The company, however, seems glib and ready to lose yet another $750M class action lawsuit brought by Intel, Sun and the EU.

EDIT: I no longer dual boot or use ntfs-fuse it's built-in to 7.10 and besides XP in  VirtualBox networks automatically with Ubuntu desktop.

---

### Post by Jmejme on 2008-01-20
Thanks for the quick replies!!!

So should i install FUSE first and then install ntfs-3g? and what is sshfs (sp?) and where are the programs stored while running in live environment? lol sorry im so newbish about this!

---

### Post by st33med on 2008-01-20
> **rosegarden78 said:**
> It should still say kernel versions available when booting with GRUB.  I think the latest kernel is 2.6.24 or possibly higher.  NTFS is a file system invented in the Northwest United States.  The company that invented it has refused to share its other proprietary file formats, such as Word documents, to the public so that others may write compatible software.  The company, however, seems glib and ready to lose yet another $750M class action lawsuit brought by Intel, Sun and the EU.

Well said :). But that is kinda redundant and not useful here wouldn't you think ;).

---

### Post by PeterJS on 2008-01-20
> **Jmejme said:**
> Thanks for the quick replies!!!

So should i install FUSE first and then install ntfs-3g? and what is sshfs (sp?) and where are the programs stored while running in live environment? lol sorry im so newbish about this!


All changes made to the live environment are saved to ram using a copy on write version of the CD. Don't worry about installing FUSE, or even ntfs-g3 itself. If you install the ntfs-config tool it will require ntfs-g3, and automatically install it first, which will require FUSE and automatically it first, which may require other stuff and so on.

SSHFS is an other FUSE based file system for accessing remote computers over secure shell, it really has nothing to do with the matter at hand, it's just nifty and also uses the FUSE framework.

---

### Post by Jmejme on 2008-01-20
well lets just say that im workng my way to some sort of remote computer access... but thats not till i completely figure out what i am doing with this first..
Ok so i have the zip file with ntfs-3g... do i install wiht the three basic commands???
what is apt-get install do i need the file first or does it find it for me somehow??? wow i feel  kind of ....hmmm needie i should say!

---

### Post by eapache on 2008-01-20
If you're running 7.10 then ntfs-3g is installed by default, just go to Places and the ntfs partitions should show up. If you're running a previous version, then run the following in the command line```
sudo apt-get install ntfs-config
```

It will download and install it automatically.

---

### Post by Faud on 2008-01-20
apt-get is liking installing using the package manager under systems-->administration and wont give you a zip file, apt-get install "program" will install it on your system for you. Did you download the zip file from somewhere ?

So...
```

sudo apt-get install ntfs-config

```
will download and install it for you

---

### Post by Jmejme on 2008-01-20
yes i downloaded the zip from the site ntfs site and when i put that in this is what i get

E: Couldn't find package ntfs-config

??? why??? lol

---

### Post by PeterJS on 2008-01-20
> **Jmejme said:**
> yes i downloaded the zip from the site ntfs site and when i put that in this is what i get

E: Couldn't find package ntfs-config

??? why??? lol

What version of the live CD are you using? If you open up synaptic (System > Administration > Synaptic Package Manager) does anything show up? Does anything happen if you try to reload the package list in synaptic?

---

### Post by Jmejme on 2008-01-20
6.06 Dapper Drake when i open it it gives me a list of packages it has ntfsprogs with a green  box beside it...? now what? is that what i need and what do you mean reload the packet list???

---

### Post by PeterJS on 2008-01-20
> **Jmejme said:**
> 6.06 Dapper Drake when i open it it gives me a list of packages it has ntfsprogs with a green  box beside it...? now what? is that what i need and what do you mean reload the packet list???

That would be your problem, Dapper is older than dirt, it's 18 months old. NTFS-3g didn't exist when dapper was released. If you get a copy of 7.10 it should clear all your problems up.

---

### Post by Jmejme on 2008-01-20
lol...see some how i was expecting that sooner or later lmao...
well looks like im bumming a blank disk so does that version come with ntfs slready on it? and thank you alot!!!

---

### Post by PeterJS on 2008-01-20
> **Jmejme said:**
> lol...see some how i was expecting that sooner or later lmao...
well looks like im bumming a blank disk so does that version come with ntfs slready on it? and thank you alot!!!

7.10 I believe has ntfs-3g installed by default but not the ntfs-config. But what's installed by default isn't as important was what can be pulled from the repos*, and everything you'll need for working with NTFS is in the 7.10 repos.

*There are reasonable limits on this like installing KDE on a live Gnome session just because most computers don't have multiple gigs of ram to spare for CoW disk overlays, but for things that are going to take up a few megs at most like the ntfs tools you'll be fine.

---

### Post by Jmejme on 2008-01-20
ok two questions where do i get 7.10 on the ubuntu site and with my new laptop if i give some specs would you be able to tell me how well it will work with ubuntu and the other downloadable tools? 
thanks greatly i hope one day to be a helper to the newbies like me :)

---

### Post by PeterJS on 2008-01-20
> **Jmejme said:**
> ok two questions where do i get 7.10 on the ubuntu site and with my new laptop if i give some specs would you be able to tell me how well it will work with ubuntu and the other downloadable tools? 
thanks greatly i hope one day to be a helper to the newbies like me :)

Here you go:
[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

Yeah I'd be happy to look at specs and give you any advice. Everybody was a newbie once, it happens, we learn. I've been using linux for 6 years and I'm still finding new stuff out.

---

### Post by rosegarden78 on 2008-01-20
It's my understanding you can only mount NTFS drive as read-only in the current version of Ubuntu.  Personally, I use FAT32 for my XP partition in part because my LACIE 250 GB USB Drive also uses FAT32.  I wouldn't recommend risking the use of write-access to NTFS from Ubuntu at this time.

EDIT:  I don't know what I just said ... but your USB devices show up in /dev folder.  Now I use XP in VirtualBox it networks with Ubuntu desktop automatically.

---

### Post by PeterJS on 2008-01-20
> **rosegarden78 said:**
> It's my understanding you can only mount NTFS drive as read-only in the current version of Ubuntu.  Personally, I use FAT32 for my XP partition in part because my LACIE 250 GB USB Drive also uses FAT32. 
That was true with ntfs kernel driver, but the fuse based ntfs-3g drive is an entirely different code base and works really well for both read and write access.


> I wouldn't recommend risking the use of write-access to NTFS from Ubuntu at this time.

I would, I've written several gigabytes of data to NTFS from ubuntu using NTFS-3g.

---

### Post by Jmejme on 2008-01-21
ill post the specs in a sec thanks in advance. do you know what the fastest download of ubuntu is or was. i m on a college campus and i was going to download the 7.10 but it said it would take 6 hours.....!!! is there a quicker way to download it?

---

### Post by Jmejme on 2008-01-21
here are the specs for my laptop that will ship in 8 days!!!!!

HP Pavilion dv6700t customizable Notebook PC

    * Genuine Windows Vista Home Premium (32-bit)
    * Intel(R) Core(TM) 2 Duo Pprocessor T7250 (2.00 GHz, 2 MB L2 Cache, 800MHz FSB)
    * 15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
    * FREE Upgrade to 2GB DDR2 System Memory (2 Dimm)!!
    * Intel(R) Graphics Media Accelerator X3100 - For Core 2 Duo Processors
    * HP Imprint Finish (Radiance) + Microphone
    * Intel(R) PRO/Wireless 3945ABG Network Connection
    * 120GB 5400RPM SATA Hard Drive
    * SuperMulti 8X DVD+/-R/RW with Double Layer Support
    * No TV Tuner w/remote control
    * 6 Cell Lithium Ion Battery
    * Microsoft(R) Works 9.0
    * HP Home & Home Office Store in-box envelope

---

### Post by PeterJS on 2008-01-21
> **Jmejme said:**
> ill post the specs in a sec thanks in advance. do you know what the fastest download of ubuntu is or was. i m on a college campus and i was going to download the 7.10 but it said it would take 6 hours.....!!! is there a quicker way to download it?

Does your campus have an on site mirror for open source projects, that would probably have Ubuntu ISOs. If not here's the list of mirrors, see if you can find one close to you: [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by Jmejme on 2008-01-21
how would i find out if my campus did?

---

### Post by PeterJS on 2008-01-21
> **Jmejme said:**
> here are the specs for my laptop that will ship in 8 days!!!!!

HP Pavilion dv6700t customizable Notebook PC

    * Genuine Windows Vista Home Premium (32-bit)

That's cute, vista how nice.
> 
    * Intel(R) Core(TM) 2 Duo Pprocessor T7250 (2.00 GHz, 2 MB L2 Cache, 800MHz FSB)

That's nicer than mine, no fair :)
> 
    * 15.4" WXGA High-Definition HP BrightView Widescreen Display (1280 x 800)
    * FREE Upgrade to 2GB DDR2 System Memory (2 Dimm)!!
    * Intel(R) Graphics Media Accelerator X3100 - For Core 2 Duo Processors

Intel actually releases the specs for their cards so the open source drivers are very good for them, so you won't have to deal with any driver BS, it will just work.
> 
    * HP Imprint Finish (Radiance) + Microphone
    * Intel(R) PRO/Wireless 3945ABG Network Connection

As with their graphics cards intel provides good open drivers for their wireless cards so they also work out of the box.
> 
    * 120GB 5400RPM SATA Hard Drive
    * SuperMulti 8X DVD+/-R/RW with Double Layer Support
    * No TV Tuner w/remote control
    * 6 Cell Lithium Ion Battery
    * Microsoft(R) Works 9.0
    * HP Home & Home Office Store in-box envelope

---

### Post by PeterJS on 2008-01-21
> **Jmejme said:**
> how would i find out if my campus did?

Check around the CS department website. Search around to see if there's a LUG at your school. Find a CS major and ask?

---

### Post by Jmejme on 2008-01-21
lmao yeah i wasnt too thrilled about vista either but i didnt have the option for xp plus i need a windows os so i can test scripts that i will be writhing for a coffee shop i used to work for. they have laptops for use for free so im writing simple scripts and batch programs so that it only starts internet explorer. requires a password (thats changes everytime according to a set list of passwords). and will only let you stay logged on for (however long i see fit Muahahaha!!!!) lol so..yeah

---

### Post by Jmejme on 2008-01-21
> **PeterJS said:**
> Check around the CS department website. Search around to see if there's a LUG at your school. Find a CS major and ask?

Lol by cs im assuming that you mean computer science... and by cs major you mean computer science major...lol hmmm that means... ME lol im a computer science major of course im only a freshmen so i haven't had the chance to start my major...but i catch your drift...i just thought it was funny and coincidental

---

### Post by rosegarden78 on 2008-01-21
Thanks!  It's always good to have first-hand experience before giving a go-ahead.  I'll have to try that some day.  It's too bad I've given up already on ntfs drives, but at least now I know I can access them in the future. :)

EDIT: Staff told me ntfs mounting is built into 7.10 and later versions so my posts are obsolete.  However XP in VirtualBox networks automatically with Ubuntu desktop.

---

### Post by eapache on 2008-01-21
7.10 has everything required for ntfs-write preinstalled. Your Windows partition should be available from the Places menu without any fiddling required at all. Happy Ubuntuing!

---

### Post by aysiu on 2008-01-21
If you don't need to modify or delete files off the NTFS partition (you mentioned earlier something about rescuing files?), then you can use Ubuntu 6.06 (Dapper Drake) to copy the files off, since Dapper can mount NTFS partitions as read-only.

---

### Post by Jmejme on 2008-01-22
> **aysiu said:**
> If you don't need to modify or delete files off the NTFS partition (you mentioned earlier something about rescuing files?), then you can use Ubuntu 6.06 (Dapper Drake) to copy the files off, since Dapper can mount NTFS partitions as read-only.

and how exactly would i go about doing that...?


Btw thanks to everyone that helped me a few days ago. i just found out last night that one of my fried's boyfriend has the 7.10 on disk already SO im set! just gotta wait for my new laptop 6 days...i think thats right...YEAH!!!!

---

### Post by aysiu on 2008-01-22
> **Jmejme said:**
> and how exactly would i go about doing that...? In [the terminal](http://www.psychocats.net/ubuntu/terminal), paste the command: ```
sudo fdisk -l
``` That will list your partitions and types. Find out which one is the NTFS partition. Let's say, for the sake of this example, it's */dev/hda1*. Then you would make a mount point for it: ```
sudo mkdir /media/recovery
``` and then mount the drive to the newly created directory: ```
sudo mount -t ntfs */dev/hda1* /media/recovery -o nls=utf8,umask=0222
``` Then, your NTFS drive will appear in the /media/recovery folder.

Just make sure you replace */dev/hda1* with the real location of the NTFS drive.

---

### Post by Jmejme on 2008-01-22
-o nls=utf8,umask=0222

hey can you explain what all that means i would like to know so that when i get a lil more into this i know the breakdown of everything.

or maybe you could redirect me to a page of somesort with a list of what these different expressions are.

for example i see -o or - something alot  i know -ls lists the directories and files... see where im gion w this? :)

---

### Post by PeterJS on 2008-01-22
> **Jmejme said:**
> -o nls=utf8,umask=0222

hey can you explain what all that means i would like to know so that when i get a lil more into this i know the breakdown of everything.

or maybe you could redirect me to a page of somesort with a list of what these different expressions are.

for example i see -o or - something alot  i know -ls lists the directories and files... see where im gion w this? :)

-o is is for options, it tells mount that thing things after it are option value pairs, I forgot exactly what nls stands for but it specifies what encoding to use when interpreting file names. umask is the file permission mask, so it's the same thing as regular file permissions but backwards, since it's set to 0222 in this case write permission will be disabled for all users but read and execute will be untouched.

---

### Post by crjackson on 2008-01-22
> **rosegarden78 said:**
> It's my understanding you can only mount NTFS drive as read-only in the current version of Ubuntu.  Personally, I use FAT32 for my XP partition in part because my LACIE 250 GB USB Drive also uses FAT32.  I wouldn't recommend risking the use of write-access to NTFS from Ubuntu at this time.

It's read / write.  I've used it to write hundrededs of gigabytes of data without a hitch.  No worries, just use it and forget about it...

---

### Post by aysiu on 2008-01-22
> **rosegarden78 said:**
> It's my understanding you can only mount NTFS drive as read-only in the current version of Ubuntu.  Personally, I use FAT32 for my XP partition in part because my LACIE 250 GB USB Drive also uses FAT32.  I wouldn't recommend risking the use of write-access to NTFS from Ubuntu at this time.
Your understanding is a bit outdated. In the current version (Gutsy Gibbon), read/write for NTFS is perfectly safe.

---

### Post by rosegarden78 on 2008-01-22
What would we do without each other ?  Thanks again !  I never doubted the ability of Ubuntu to access NTFS but yes I was off-line for three months until this January .  Now who knows the best way to write from Windows XP SP2 to EXT file system ?  Still don't know the answer . eg. NTFS to EXT3

EDIT:  Thanks but now I'm using VirtualBox but good to know shareware just in case.

---

### Post by aysiu on 2008-01-22
> **rosegarden78 said:**
> Now who knows the best way to write from Windows XP SP2 to EXT file system ?  Still don't know the answer . eg. NTFS to EXT3 Try [this](http://www.fs-driver.org/)

---

### Post by stchman on 2008-01-22
> **Jmejme said:**
> ok heres the deal:
I am somewhat new to ubuntu i forgot what version. right now i only boot from live cd. i am awaiting my ne laptop. but here is where my prob is. i want to find out what exactly what im getting into with ntfs-3. from what i understand it makes it possible to access a hard drive with the windows ntfs file format. does this mean that ntfs-3g can be used as a rescue tool? and what is FUSE??? can someone shine some light on this im very new to linux/ubuntu and   need some help

Thanks  alot!!!

Here is a tutorial I wrote on mounting partitions in Ubuntu.  I have included ntfs stuff as well.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by rosegarden78 on 2008-01-26
> **eapache said:**
> 7.10 has everything required for ntfs-write preinstalled. Your Windows partition should be available from the Places menu without any fiddling required at all. Happy Ubuntuing!

Wowzers!  It's about time I can stop talking about FUSE!!  EDIT: Now I'm using my XP in VirtualBox and it networks whatever shared folder I want.

---

