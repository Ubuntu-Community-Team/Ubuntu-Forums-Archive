---
title: "Ubuntu/Linux Utilities?"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by CybaCowboy on 2006-05-14
Okay,


I need software that is for:
* Anti-virus
If you need to ask what anti-virus software is, you probably shouldn't have a computer...

* Backup
I want to backup data to my MP3 player, which Ubuntu sees as a portable HDD ("Removable Volume")

* Cleaning
I want to wipe downloaded files, history, temporary & other un-needed files using one program, without having to resort to manual methods

* Defragmentation
I want software that will defrag my Ubuntu partition...


*Ideally*, I'd like this software as part of a suite (think Norton BloatWare), but in the end, anything that does the job will do (to an extent).

---

### Post by aysiu on 2006-05-14
[QUOTE=CybaCowboy]
I need software that is for:
* Anti-virus
If you need to ask what anti-virus software is, you probably shouldn't have a computer...[/quote] You don't need anti-virus in Ubuntu. > * Backup
I want to backup data to my MP3 player, which Ubuntu sees as a portable HDD ("Removable Volume") Try KDar. It's in the repositories. If you don't know what repositories are, read this: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) > * Cleaning
I want to wipe downloaded files, history, temporary & other un-needed files using one program, without having to resort to manual methods Hm. For all that, you might have to write a custom script--it's not as hard as it sounds. **Edit**: Here it is. Paste these commands into a terminal: ```
gksudo gedit /usr/local/bin/cleanitup
``` if you're using Gnome or ```
kdesu kwrite /usr/local/bin/cleanitup
``` if you're using Kubuntu. Copy and paste the following code into the text editor: ```
#!/bin/bash
rm ~/.mozilla/firefox/*/Cache/*
sudo rm /var/cache/apt/archives/*
sudo rm -rf /tmp/*
``` Save and exit the text editor. ```
sudo chmod +x /usr/local/bin/cleanitup
``` Then, any time you want to clean everything out, run the command ```
cleanitup
``` in the terminal. > * Defragmentation
I want software that will defrag my Ubuntu partition...  Not necessary. Ext3 doesn't get fragmented--unlike NTFS and FAT32 (what Windows uses).

---

### Post by Perfect Storm on 2006-05-14
[QUOTE=CybaCowboy]Okay,


I need software that is for:
* Anti-virus
If you need to ask what anti-virus software is, you probably shouldn't have a computer...
[/quote]

Not needed other than if you want to protect windows machines you are interact with. Check here: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

> 
* Cleaning
I want to wipe downloaded files, history, temporary & other un-needed files using one program, without having to resort to manual methods


Easy just clean your web-browser build-in temp-storage. Nothing much else to clean. You could run sudo apt-get clean if you want to clean your package storage now and then.

> 
* Defragmentation
I want software that will defrag my Ubuntu partition...



Not needed in Linux.

---

### Post by deanjm1963 on 2006-05-14
aysiu is 100% correct.

Linux cleans up after itself very well, unlike that "pay per use" operating system ;) 

Linux file systems are not like FAT/NTFS, they don't fragment. Occasionally they'll start to fragment slightly when disk capacity is running very low.

I know where you're coming from, I was the same when I first switched to linux over 18 months ago, those things are not needed. 

The only linux file system that has a built-in defrag is XFS, and the defrag utility that comes with XFS is only really worth using on a drive that has hundreds of gigabytes of files that are constantly being used, like a file server. I tried it once on my measly 30gig worth of files.. found 1 file fragmented... pffftttt.. waste of time.

---

### Post by skippy81 on 2006-05-14
* Anti-virus
Not really needed, but you could download clamav if your paranoid.  Viruses are very rare on the linux platform.  Remember that files are not given execute permission by default in linux.  Also that windows executables wont work.  Security wise it is more important to have strong passwords and make sure you don't have services running which you don't need (ie smtp, ssh)

* Backup
sbackup is a good one for casual users. backuppc for powerusers.  

* Defragmentation
Linux disks don't defragment to any noteworthy extent.  Defragmenters for linux are widely believed to be pointless - remember linux different file systems to windows. EXT2 and 3 do not fragment.  

You can use the search function on synaptic to find suitable packages.  To do the 'cleanup' you could just use a simple 2 line shell script.  I'll post one later when I get the chance.

---

### Post by aysiu on 2006-05-14
[QUOTE=skippy81]To do the 'cleanup' you could just use a simple 2 line shell script.  I'll post one later when I get the chance.[/QUOTE] Don't bother. I posted it in my earlier post. You're welcome to revise it if you think it's missing something, though.

---

### Post by CybaCowboy on 2006-05-14
[QUOTE=aysiu]Ext3 doesn't get fragmented--unlike NTFS and FAT32 (what Windows uses).[/QUOTE]

[QUOTE=Artificial Intelligence]Not needed in Linux.[/QUOTE]

I may not be a Linux expert, but I *know* that you are both wrong on this...

While Linux may take certain steps to minimize fragmentation, it is theoratically possible for *any* computer/PDA/device with a hard drive to become fragmented!

Think about what fragmentation actually is and what defragmentation software does, then you'll know I'm right.

---

### Post by skippy81 on 2006-05-14
Hehe I took to long writing my post obviously :D

[QUOTE=aysiu] Copy and paste the following code into the text editor: ```
#!/bin/bash
rm ~/.mozilla/firefox/*/Cache/*
sudo rm /var/cache/apt/archives/*
sudo rm -rf /tmp/*
```[/QUOTE]

The asterisk * trick for 'guessing' the name of a directory as part of a path is awesome - never seen it before.

---

### Post by tommcd on 2006-05-14
I was thinking of asking the very same questions that were answered with this thread. Glad to know I don't have to worry about this stuff.
On Windows I ran:
Registry First Aid (registry cleaner) 
Crap Cleaner (cleaned out temp folders and lots of stuff)
Windows Defrag and Disk Cleanup.
NOD32 antivirus
Zone Alarm
Spybot
Ad Aware
Microsoft Antispyware
Rootkit Revealer
Process Explorer
Autoruns

Glad to know that Ubuntu is 'low maintenence'. Thanks!
I just run Firestarter, and ChkRootkit (cause I'm paranoid about security) thats it!

---

### Post by aysiu on 2006-05-14
[quote=skippy81]The asterisk * trick for 'guessing' the name of a directory as part of a path is awesome - never seen it before.[/quote] Yeah, I just tested it out on my own .mozilla folder (after backing it up, of course) to make sure it didn't delete the whole thing--only the cache contents. [QUOTE=CybaCowboy]
While Linux may take certain steps to minimize fragmentation, it is theoratically possible for *any* computer/PDA/device with a hard drive to become fragmented!

Think about what fragmentation actually is and what defragmentation software does, then you'll know I'm right.[/QUOTE] Cite a source that's credible, and I'll believe you.

This is from [Wikipedia](http://en.wikipedia.org/wiki/Ext3): > There is no ext3 defragmentation tool. An offline ext2 defragmenter, e2defrag, exists but requires that the ext3 filesystem be converted back to ext2 first. However, defragmentation has long been considered a non-issue for ext2/ext3, since they are much better at placing files on the disk versus old FAT-based filesystems. From [ITworld.com](http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html): > The ext2 and ext3 file systems most often used on Linux systems also attempt to keep fragmentation at a minimum. These file systems keep all blocks in a file close together. How they do this is by preallocating disk data blocks to regular files before they are actually used. Because of this, when a file increases in size, several adjacent blocks are already reserved, reducing file fragmentation. It is, therefore, seldom necessary to analyze the amount of fragmentation on a Linux system, never mind actually run a defragment command. An exception exists for files that are constantly appended to as the reserved blocks will only last so long. The point is that you do not need to defragment--not that absolutely *no* fragmentation occurs.

---

### Post by Perfect Storm on 2006-05-14
[QUOTE=CybaCowboy]I may not be a Linux expert, but I *know* that you are both wrong on this...

While Linux may take certain steps to minimize fragmentation, it is theoratically possible for *any* computer/PDA/device with a hard drive to become fragmented!

Think about what fragmentation actually is and what defragmentation software does, then you'll know I'm right.[/QUOTE]

You need to understand how the partition system works in linux before posting such assumptions.
Other have posted exceptional cases where it might needed, like a huge server which are full.

---

### Post by CybaCowboy on 2006-05-14
[QUOTE=aysiu]Copy and paste the following code into the text editor: ```
#!/bin/bash
rm ~/.mozilla/firefox/*/Cache/*
sudo rm /var/cache/apt/archives/*
sudo rm -rf /tmp/*
```[/QUOTE]

It appears that this would remove Firefox's temporary data and while Firefox *is* a decent browser, I prefer Opera...

What shall I put in its place to remove Opera's temporary data, or the temporary data for *both* programs?


[QUOTE=aysiu]Save and exit the text editor.[/QUOTE]

Ideally, where should I save the file?


[QUOTE=tommcd]I just run Firestarter, and ChkRootkit (cause I'm paranoid about security) thats it![/QUOTE]

What does ChkRootkit do?

---

### Post by aysiu on 2006-05-14
[QUOTE=CybaCowboy]It appears that this would remove Firefox's temporary data and while Firefox *is* a decent browser, I prefer Opera...

What shall I put in its place to remove Opera's temporary data, or the temporary data for *both* programs?[/quote] Well, seeing as how I don't have Opera installed, it's going to be a bit tough for me to add in a command to clear out Opera's cache.

Someone else who has Opera will have to add in that line.

> 
Ideally, where should I save the file? The commands I gave you are comprehensive, and they already save the file to /usr/local/bin/cleanitup

> What does ChkRootkit do? It checks to see whether you have a rootkit installed on your computer:
[http://en.wikipedia.org/wiki/Rootkits](http://en.wikipedia.org/wiki/Rootkits)

---

### Post by skippy81 on 2006-05-14
And ChkRootKit is a utility for searching your box for a rootkit a.k.a a trojan horse.  The traditional way of hacking a linux box is to gain access to a working account of someone who has access to the root account (userpasswords are often poorly chosen and easy to guess).

The hacker then writes and compiles a simple C program that grabs the root password.  He will usually use an ssh or telnet session to do this. He will name the C program 'sudo' or 'su' so that the user will be tricked into thinking it is the real superuser commmand. The 'real' sudo or su is then called by the rootkit and the user assumes they just put in the wrong password the first time.  Infact the first time they typed the password it was logged and written to a text file for easy recovery by the hacker - he then has root and 'owns' the system.  

You do not have to worry about this with ubuntu, since you do not know what your root password is - sudo is set up to work of your user password, which the hacker would allready have to know in order to compile a rootkit on your PC.

---

### Post by CybaCowboy on 2006-05-14
[QUOTE=aysiu]Well, seeing as how I don't have Opera installed, it's going to be a bit tough for me to add in a command to clear out Opera's cache.[/QUOTE]

I'll try and work it out myself in the meantime.

It shouldn't be too hard if I use the Firefox version as a guide...

---

### Post by ProjectGod on 2006-05-14
cleaning up after downloads...

try this if you've downloaded a lot of things lately.

at the terminal. "df -h"
then. "sudo apt-get clean"
then "df -h" 

avail space should increase.

---

### Post by aysiu on 2006-05-14
[QUOTE=CybaCowboy]I'll try and work it out myself in the meantime.

It shouldn't be too hard if I use the Firefox version as a guide...[/QUOTE] Just about every application you use stores your settings in hidden folders in your home directory.

So your Firefox settings live in /home/cybacowboy/.mozilla
Your Opera settings probably live in /home/cybacowboy/.opera

Any directory that starts with . is hidden. To view those hidden directories, you press Control-H in Ubuntu or Alt-V, then H in Kubuntu.

---

### Post by CybaCowboy on 2006-05-14
You will find screen-shots of my Opera directory below...


Will this help?

---

### Post by aysiu on 2006-05-14
[QUOTE=CybaCowboy]You will find screen-shots of my Opera directory below...


Will this help?[/QUOTE] Definitely. Here's the revised script: ```
#!/bin/bash
rm ~/.mozilla/firefox/*/Cache/*
rm ~/.opera/cache4/*
rm ~/.opera/cacheOp/*
sudo rm /var/cache/apt/archives/*
sudo rm -rf /tmp/*
``` I'm assuming that second directory is cacheOp (the letter o) and not cache0p (the number 0). You should confirm that before you run the script.

---

### Post by CybaCowboy on 2006-05-14
[i]cowboy@kubuntu:~$ gksudo gedit /usr/local/bin/cleanitup
(gedit:9218 ): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/i]


Then when I try to save the file:
*Could not save the file "/home/cowboy/'/usr/local/bin/cleanitup'"*

---

### Post by skippy81 on 2006-05-14
try using > sudo gedit /usr/local/bin/cleanitup to create the file instead.

---

