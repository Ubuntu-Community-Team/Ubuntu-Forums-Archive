---
title: "backing up ubuntu"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-05
Hello Forum,

Please can you advise me about which directories and sub directories to back up in ubuntu that concern software tool location...and the installation of new software tools...

I always want to make a back up those important directories before i do any new software install...(everytime)

if i do a software install and it goes bad/problems....i want to be able to reset those important directories to my previuos backup....(the backup i made before i started doing the new software install)

i believe there are 2 or 3 important directories....very core directories..

the tool i use is called sbackup and it is easy to use.....i just want to know which directories to back up....the full path names of them

thanks

Vince.

---

### Post by cwmoser on 2008-04-05
Ironically, this is the same question I was about to post and I noted yours.
Must be a lot of us who are interested in this.
You mentioned sbackup.  Some are really complementary about BackupPC.

I would also like to add -- what is the restoral process?  
Would you have to go back to the CDROM and do a base install of the OS and then sbackup?
Is there an image capability?  A best practice?

Carl

---

### Post by vinceUUUU on 2008-04-05
Hello there,

well your questions are good ones....i am also interested in using an IMAGE style of backing up the entire ubuntu OS (snapshots).....something that is relatively quik but completely SHADOWS the OS.....so to speak...

i had not heard of backupPC...

the only way that i know of doing specific ubuntu directory back ups....is by using something like the sbackup tool.....

i do not yet know of any way of creating proper IMAGES of the entire Ubuntu OS...(snapshots)...so to speak...

Vince

---

### Post by LaRoza on 2008-04-05
> **vinceUUUU said:**
> Hello there,

well your questions are good ones....i am also interested in using an IMAGE style of backing up the entire ubuntu OS (snapshots).....something that is relatively quik but completely SHADOWS the OS.....so to speak...

i had not heard of backupPC...

the only way that i know of doing specific ubuntu directory back ups....is by using something like the sbackup tool.....

i do not yet know of any way of creating proper IMAGES of the entire Ubuntu OS...(snapshots)...so to speak...

Vince
For full system backups: [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/) or you can use a cloning tool, I recommend Clonezill, see the link in my sig.

Clonezilla can make an image of a drive or partition and restore it.

---

### Post by vinceUUUU on 2008-04-05
Hello,

thanks very much....that is really helpful...

the cloning tool looks perfect for me...because it says it does not take too long ....and it's simple to use...

basically, cloning is a fool proof method for keeping my ubuntu in perfect condition....

as long as i always clone my ubuntu before any new installs or system alterations.....then i can always return to the clone..... if the changes had caused any problems or failed...

thanks,

Vince.

---

### Post by bumanie on 2008-04-05
You could also use partimage. It works via gui or cli. It will compress the drive image as well, to save on storage space.

---

### Post by vinceUUUU on 2008-04-05
Hello again,

this is very helpful again....thanks so much...

[http://www.partimage.org/Screenshots](http://www.partimage.org/Screenshots)

according to the screenhots here....Partimage is very quik at doing images of Linux partitions...

By the looks of things...it will only take a couple of minutes to create an image file.......also it does not write un-used empty blocks.....only blocks that are used in the partition.

thanks

Vince.

---

### Post by Tews on 2008-04-05
I have found a little app called Quick-Start. Developed specifically for Ubuntu, I can restore a backup perfectly in about 30 minutes. See pic for available options..

[IMG]http://www.libertymanor.org/menu.png[/IMG]

Read more about it here ===>> [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by fatality_uk on 2008-04-05
+1 for quickstart. I use it to "clone" and prepare Ubuntu installs quickly.

---

### Post by cwmoser on 2008-04-05
I use the Gparted "live CD" to clone my Ubuntu installation.  Unfortunately, I have to boot the CDROM and connect up a target hard drive that will be the "clone".  The nice thing about Gparted is that it provides a GUI interface where you can drag and drop a partition and also nondestructively resize a partition.

I purchased on eBay a USB to SATA adapter that helps with the cloning process.  It included an AC adapter to power the hard drive and a SATA cable.   I've wanted to use one of those removable hard drive trays to make it even easier.

Another piece of information -- it was raining this morning and I went to Borders bookstore to look at the latest copies of Linux magazines.  There were at least 2 magazines with in depth articles about backup.  The magazines covered dd, netcat to backup over the network, Partimage, ntfsclone, FOG, etc.  One interesting article was about FreeNAS -- an open source NAS backup technology where you dedicate a PC for backup.  FreeNAS installs in a small  partition on a PC with a big hard drive and no operating system.  FreeNAS then presents itself as a presence on your LAN.  You use a Web Browser to work with it.  I think this FreeNAS is something I am going to look into.

Carl

---

### Post by bratliff on 2008-04-05
> **fatality_uk said:**
> +1 for quickstart. I use it to "clone" and prepare Ubuntu installs quickly.

Where do you find clone? It is not in the package manager.
Ratliff

---

### Post by vinceUUUU on 2008-04-10
Clonezilla is a program you download and use in Linux...

not heard of a tool called Clone...

OR

 you can use the program called QUIK START that is free in this forum

QUIK START will do a full system backup...and it is GUI based and simple to use...

Vince.

---

### Post by cwmoser on 2008-04-10
> **vinceUUUU said:**
> Clonezilla is a program you download and use in Linux...

not heard of a tool called Clone...

OR

 you can use the program called QUIK START that is free in this forum

QUIK START will do a full system backup...and it is GUI based and simple to use...

Vince.


I've used Clonezilla to essentially create a bare metal image of the software - operating system, data and all.  When you say QUIK START will do a "full system backup" -- what does this mean?  Say you corrupted your Ubuntu OS where it would not even boot, would QUIK START help any?  

Carl

---

### Post by dje on 2008-04-14
Have a look at my new project linbaku, it creates complete backups of your ubuntu installation for a complete reinstall back to how your computer was when you backed it up. See the blue linbaku link in my sig for more information

hope that helps,
dje

---

### Post by Tews on 2008-04-14
> **cwmoser said:**
> When you say QUIK START will do a "full system backup" -- what does this mean?  Say you corrupted your Ubuntu OS where it would not even boot, would QUIK START help any?  

Carl

Yes!!  Quick-Start was developed for Ubuntu users like me who like to tinker and just cant seem to leave things alone!  Several of my "tweaks" have left my system a pile of smoking trash!  Thanks to Quick-Start, all I need to do is throw in the live-cd, reinstall and run Quick-Start to restore my system to its latest backed up state.  Depending on how much data there is, the total process takes me about 30 minutes.  

[IMG]http://www.libertymanor.org/menu.png[/IMG]

As you can see there are a lot of different options, and Quick-Start does more than just backup your system.  You can read about/get it here ==>> [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by pjnsmb on 2008-04-14
first post from a new Ubuntu user

+1 for Quickstart
 
a great programme for novices like me !

---

### Post by vinceUUUU on 2008-04-14
Hello

yes...the Quik-Start tool is very good.

it creates a full backup of your entire linux OS...

it is simple to use

simple select "create full backup"..then tick all three options and go...

it will generate a single large file...which you store someplace

when you need to restore your Linux OS back to that file....simply start quik-start and click restore...and point to that file

it is very simple to use..

this is not creating disc images of your Linux OS.it is creating a single large backup file of your OS...

Vince

---

### Post by rbradt on 2008-04-14
Wow.  I was just about to post a question about backing up Ubuntu.  I'm glad I came across these threads.

I'm a fairly new Ubuntu user, and these threads were a huge help.  Thanks for all the suggestions.

It looks like I'm going to give QuickStart a try.

-Richard

---

### Post by bratliff on 2008-04-14
Where did you find quick start?
thk bratliff



> **Tews said:**
> I have found a little app called Quick-Start. Developed specifically for Ubuntu, I can restore a backup perfectly in about 30 minutes. See pic for available options..

[IMG]http://www.libertymanor.org/menu.png[/IMG]

Read more about it here ===>> [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by bratliff on 2008-04-14
Where do you find clonezill?
not in the repository nor launchpad.
thks bratliff

---

### Post by Het Irv on 2008-04-14
> **bratliff said:**
> Where did you find quick start?
thk bratliff

Check that link, QuickStart is downloaded from that Thread.  Or you can click the link in my sig.

---

### Post by bratliff on 2008-04-14
Thank you. Quickstart found and installed.
Bratliff

---

### Post by Robertjm on 2008-07-05
Hi all,

If I use Quick Start to backup my system, and it creates a single file, would I be able to use it to restore to different sized partitions?

Thanks!

Robert

---

