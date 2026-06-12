---
title: "How much space does your average system use?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-08-25
Just out of curiosity, and also because i'm using a "fairly small" partition for my total linux system.  How much space does your "typical" installation use?
I've had Ubuntu installed for approximately 6-7 weeks now, not installed much beyond the daily updates...well, a few programs. eg google earth, music and dvd players and the necessary codecs etc. Plus some stuff for the kids.
Using "Baobab" i can see the following.

Partitions Linux = 16Gb
USR              = 2.3 GB
   /USR/SHARE       = 1.2 GB
   /USR/LIB         = 0.97 GB

HOME             = 346 mb
LIB              = 298 mb

Is there anything i should be doing to keep the "size" down?
Stuff that can be thrown out after time? Files to keep an eye on? hidden files, trash cans etc?

In Grub i see the following by start up.

Ubuntu, kernel  2.6.15-26-386
Ubuntu, kernel  2.6.15-26-386 (Recovery mode)
Ubuntu, kernel  2.6.15-25-386
Ubuntu, kernel  2.6.15-25-386 (Recoery mode)
Ubuntu, kernel  2.6.15.23.386
Ubuntu, kernel  2.6.15.23.386 (Recover mode)
Ubuntu, memtest 86+
other operating systems
Microsoft windows xp professional

All necessary? (yep - i Know windows is superfluous, before you say it!)

Any feed back would be very much appreciated.

---

### Post by calvinthomas on 2006-08-25
You might be able to get a small amount back by going to a terminal and typing:

sudo aptitude clean

This will delete all packages that you've downloaded (not your installation, just the installlation files that you've downloaded through synaptic etc) 

I do it every so often and it usually frees up a lot of space. You have plenty of free space though, I use 8GB for my Ubuntu partition and have everything I need and more installed and still have 1.5GB free. With your 16GB partition you haven't really got much to worry about!

You can remove the two oler kernels if you are happy with the latest one, will give you a small amount of extra space can't remember exactly what to delete but if you search for kernel in synaptic you'll find it!

Calv

Calv

---

### Post by stoer on 2006-08-25
Hey, thanks for the reply.
Nice to hear that there's still alot of room to play with.  I'm sort of used to the exponential growth of windows over time and usually like to leave myself some 'growing room'.

I guess i'm interested to hear from others what they use, what is the "typical installation" in terms of space used.

My own interests, as far as my laptop is concerned, are fairly heavily wieghted towards Internet, usenet (binaries), light gaming (for the kids(ok myself included)) and some occaisional dvd/music ripping/burning.  The dvd stuff, obviously eats disk room as do the binary downloads and thats why i need to be carefull. (found some "failed rips" in .trash (root) that were costing me 8 gigs - took me ages to track them down!!!)

Ive a pc with aroound 400GB stoorage and an external usb drive with another 250 gigs, but thier for film working and for stooring/backing up dvd's and digital film.  If i finally become confident enough, i'll try to add linux to the PC aswell.

Thanks again for your tips and i hope others will take the trouble to share a little knowledge aswell.
Cheers.

---

### Post by kerry_s on 2006-08-25
You could start by uinstalling all the extra software you don't use (synaptic>status>installed) and those 2 extra kernels. You can also clean out>  /usr/share/doc <and> /usr/share/man <just delete everything in there(only if you don't use it  or have never used it, it's just info and examples, instructions). If you really want to get the most space you should build up from a server install. I used the (alternate cd)server install and built up, using fluxbox as my desktop and just the apps i use, i'm only useing 583mb of 28.63g. I have plenty of room for any desktop and apps, but prefer to have only what i need with no bloat. Here's a pic->

---

### Post by djsroknrol on 2006-08-25
My whole Linux install runs about 5-6 GB not including my media files.

---

### Post by arsenic23 on 2006-08-25
Another trick I've picked up, more then likely in this forum, is to run this command:

> $ find ~/.thumbnails -type f -atime +7 -exec rm {} \;

It will remove saved thumbnails that are more then 7 (weeks?) old.  If you have a lot of images/movies, that can add up.

---

### Post by msak007 on 2006-08-25
> **stoer said:**
> I guess i'm interested to hear from others what they use, what is the "typical installation" in terms of space used.

I don't recall how much space was being used after a fresh install, but after a couple of months and lots of app installations including numerous games (both free repo games and Doom3), my install is at ~12.6 gb. Without my home directory, it's ~ 9.7. Doom3 alone is 1.5 gb, so I guess you could cut that down to ~8.2 gb. I'm not short on space, but if I was I'm sure I could uninstall lots of packages I don't use and games I don't play. Even though this is a lot for a Linux install, it's nothing compared to a typical Windows install where I would be lucky to be 30 gb after installing all the apps I needed (not including any games).

---

### Post by stoer on 2006-08-27
I'm slowly collecting some very useful tips here, also from other threads that are running, especially about what is considered to be trash and what not!  That and some useable commands for freeing up space, so thanks alot everyone.  

find ~/.thumbnails -type f -atime +7 -exec rm {} \;
**remove saved thumbnails that are more then 7 (weeks?) old**

sudo aptitude clean
**delete all packages that you've downloaded (not your installation, just the installlation files that you've downloaded through synaptic** 
etc.

So, I'll continue to read the threads, trawl the net and see what else i can find.
I'm totally sold on ubuntu, love the way it works and how accessable it is even for the unexperienced linux user. But i will be keeping Windows for a while yet, still need a reliable games platform (my son has a say in that;)  ) and for a few apps that i haven't found replacements for yet eg Newsleecher with it's "SuperSearch" function.  I guess there's no linux equivelents of "ccleaner"('crap cleaner' - simple program that removes unused and temporary files from Windows machines) yet...


ps nice screens kerry. This is how mine looks just at the moment...


[ATTACH]14948[/ATTACH][ATTACH][ATTACH]14950[/ATTACH][/ATTACH]

---

### Post by tzulberti on 2006-08-27
This is the output for df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              11G  3.9G  6.1G  39% /

This partition doesn't has the home files.

---

### Post by Frank Golden on 2006-08-27
> **tzulberti said:**
> This is the output for df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              11G  3.9G  6.1G  39% /

This partition doesn't has the home files.
I maintain a 3.32GB Ubuntu install on an 18GB partition.
Most of my data I keep on a Fat32 shared partition (XP-Ubuntu dual boot). I regularly use partimage to make an image of Ubuntu (after major changes have proven out)
and store it on the shared Fat32 partition, which is another incentive to keep my install under 4GB.

---

### Post by altonbr on 2006-08-27
Windows XP Pro = ~5.6GiB (NTFS)
Windows XP Pro Apps = ~8.5GiB (NTFS)
Ubuntu Linux 6.06 = ~9.6GiB (ext3)
Linux Swap = 1GiB (swap?)
Data Partition = ~20GiB (fat32)

all on a 250GiB hard drive.

As you can see, if Ubuntu is taking up 9.6GiB then I don't really know what I'm doing either. That idea of installing a basic server and building from there is interesting... all I need if Firefox, amorok, Thunderbird, Apache & PHP, Gaim, OpenOffice and maybe aMule... as for Gimp and whatnot, I'm a Web Developer and need to use Macromedia Flash and therefore have to dual-boot... so saving ~8GiB is an interesting proposition.

---

### Post by stoer on 2006-08-27
Altonbr

Is there a reason for the 9+Gigs? Lot of installs? graphical files, films?

I used the following to find what was hogging all the space on my system, saved me 8 Gigs (Hidden .trash files - ](*,)   )

**_Baobab_**
Via synaptic, search. Gives a nice clear visualisation of where the "big-files" are hiding.

A graphical tool to analyse directory trees
Baobab is able to scan either specific directories or the whole
filesystem (local or remote), in order to give the user a graphical tree
representation including each directory size or percentage in the branch.
A graphical treemap is also provided for any selected folder as far as
a full file-search functionality. Baobab can open/delete folders
and files. Auto-detects in real-time any change to the mounted devices and
to user's home directory.
Web site: [http://www.gnome.org/projects/baobab](http://www.gnome.org/projects/baobab)

---

### Post by toasted on 2006-08-27
XP - 14.5 gigs
XP - Programs and stuff - 45 gigs

Ubuntu 1 - swap-1 gig
Ubuntu 1 - 20 gig

Ubuntu 2 - swap -1 gig
Ubuntu 2 - / - 10 gig
Ubuntu 2 - /home - 20 gig

Fat32 shared - 50 gig

---

### Post by altonbr on 2006-08-27
@stoer

I think the reason why my Linux system (no personal files) is taking up 9Gigabytes is because I don't exactly know what I'm doing... I do alot of asking question on this forum, and the answers usually involve installing some sort of software or a piece of software to install more software (ie: Automatix and EasyUbuntu). I really need to take a course in Linux to understand where the files are going, why they are going to where they end up, and how to start stripping down linux to it's barebones and still have it working. I know I don't need 9GBs... maybe only 3 at the max.

---

### Post by Frank Golden on 2006-08-28
> **altonbr said:**
> @stoer

I think the reason why my Linux system (no personal files) is taking up 9Gigabytes is because I don't exactly know what I'm doing... I do alot of asking question on this forum, and the answers usually involve installing some sort of software or a piece of software to install more software (ie: Automatix and EasyUbuntu). I really need to take a course in Linux to understand where the files are going, why they are going to where they end up, and how to start stripping down linux to it's barebones and still have it working. I know I don't need 9GBs... maybe only 3 at the max.

My dual boot setup on a 120GB SATA HDD, Acer notebook.

C:= 22.53GB = 23070MB = NTFS [11.3GB used]
I:= 2.93GB = 3000MB = NTFS [XP swapfile 2GB used]
U:= 43.95GB = 45004MB = NTFS [XP data files MP3's etc. 22.7GB used]
L:= 23.39GB =23951MB = Fat32 [files shared between XP and Ubuntu 8.12GB used]
linux= 18.19GB = 18626MB = ext3 [Ubuntu 6.06.1 LTS 3.32GB used]
swap= 824MB

I have a fully functional Ubuntu with it's own /home but I only store large files on my Fat32 partition not in /home.
I also periodically purge setup packages after installing programs. I suppose I could move /home to my Fat32 partition
but I won't. If it ain't broke...

---

### Post by bodhi.zazen on 2006-08-28
FYI: I have an Ubuntu server install -> Desktop that takes up 4.7 Gb. Now 1 Gb is a large wine application, this leaves a 3.7 Gb root. Includes X, Abiword, Open Office, Gaim, xmms, firefox to name a few.

---

### Post by Toxicity999 on 2006-08-29
My root partition is 3g and my home 14 =P I'm on a 30g laptop...

---

### Post by altonbr on 2007-07-05
> **altonbr said:**
> @stoer

I think the reason why my Linux system (no personal files) is taking up 9Gigabytes is because I don't exactly know what I'm doing... I do alot of asking question on this forum, and the answers usually involve installing some sort of software or a piece of software to install more software (ie: Automatix and EasyUbuntu). I really need to take a course in Linux to understand where the files are going, why they are going to where they end up, and how to start stripping down linux to it's barebones and still have it working. I know I don't need 9GBs... maybe only 3 at the max.

That's not true at all actually, I just didn't know about
```
df -h
```
and didn't know how to read what I was looking at previously.

---

### Post by coolen on 2007-07-05
Linux does a lot to keep the size down.
On my machine, both Windows (XP Home Edition) and Ubuntu (32-bit Feisty) have 46.57 GB partitions. Excessive for Ubuntu, I know, but it was kind of an experimental thing for the following figures (and a result of me really not wanting Windows on here).
Ubuntu has installed the Ubuntu desktop, Kubuntu desktop, a plethora of games, three alternate window managers, three general purpose music players...all the stuff you need, and want, and want to compare. I've use 6.34 GB so far.
Windows has been updated to the latest software, has codecs to handle Ogg Vorbis files, Firefox, Songbird, and three games (only one of which was published this century). It has 8 GB left.
On a side note, I do have /boot on a separate partition, so that 's 139.44 MB of space I'd normally have taking up my / partition. Oh noes! My figures! They is tainted!

Enjoy the freedom that 10 GB can offer you using Linux.

---

### Post by eentonig on 2007-07-05
My linux is pushing around ~100G or so.


But Most of that ~90G is music and movies.

My partitiong scheme is
- Primary 1 : ext3; 10GB,'/' # contains my main ubuntu OS
- Primary 2 : ext3, 300GB, '/home' # no explanation needed.
- Primary 3 : ext3, 10GB, '/' # will be used to install the 'Development' Ubuntu. So Gutsy for now.
- Extended :
\\\\\ ext3 : 10GB, '/' # To have some room to try out other distro's.
\\\\\ ext3 : 50GB, '/var/ # I would like to run some 'servers'. Ie Apache and ftp. This way, I figure I can keep their data seperate.
\\\\\ 3GB : Swap # I'm going to put 2GB RAM


And I have another USB HD with 400G disk mounted by default. This one is mainly used to an rsync backup 
- Music, Movie & Pictures folders
- Folder with important docs
- /etc

And then some various docs I don't use that much.

---

### Post by bodhi.zazen on 2007-07-05
> **stoer said:**
> I'm slowly collecting some very useful tips here, also from other threads that are running, especially about what is considered to be trash and what not!  That and some useable commands for freeing up space, so thanks alot everyone.  

find ~/.thumbnails -type f -atime +7 -exec rm {} \;
**remove saved thumbnails that are more then 7 (weeks?) old**

sudo aptitude clean
**delete all packages that you've downloaded (not your installation, just the installlation files that you've downloaded through synaptic** 
etc.

So, I'll continue to read the threads, trawl the net and see what else i can find.

Saw your post and thought you might like this information :

Clean/Degunk:

	** [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

	[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

	[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

	[http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

### Post by stoer on 2007-09-16
hi  bodhi.zazen  

Thanks for the links, makes good reading.

I'm still dual booting on a laptop, but i notice that a year on i'm making more room for linux than windows (Shared data partition).
My Pc has some 500GB hd space and is also dual boot but obviously with no space restrictions Linux has been allowed to grow as much as it likes :)

Appreciate the links.
Cheers.
Stoer.

---

