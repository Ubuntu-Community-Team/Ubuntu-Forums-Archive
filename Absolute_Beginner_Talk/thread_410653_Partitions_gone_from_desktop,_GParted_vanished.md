---
title: "Partitions gone from desktop, GParted vanished?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by brit0n on 2007-04-16
OK I don't boot into Ubuntu every day. So when I booted it today, I found over an hour of updates to download and it took two reboots to do that. OK. I know this is not Windows, but XP updated more easilt and Vista does it invisbily. But I will accept that this is OSS so I move on and notice that two of my partitions are no longer showing on my desktop which is strange especially as I wanted to use GParted to do something.

Anyway, I tried to find out how to get them back. I have read a LOT since I first installed this beastie and found that there is a LOT of misleading information on the forums and the help files inside Ubuntu don't tend to be definitive - probably because there are not enough people volunteering to write them, so I accept that too.

But when I can no longer find GParted (whose Live CD was the reason I installed a new Linux release in the first place so that I could learn enough to be a more useful member of the forums there), I begin to wonder.

Using the install thing, I find only QTParted (sorry, don't know it and never used Partition Magic). So I browse to download GParted and then find there is some other thing which will download and install it - it wasn't there before. Does that mean I have to manually download something because it is "not available" but when I do download it, I can then use the download and install thing and it downloads it all again? (Sorry, it is hard to remember all the names of things when you are not actually runnning Ubuntu and it is certainly not ready for me to use it and I am not ready to LEARN in it if it keeps throwing me curve balls.)

Why does GParted not stay where it was when I installed Ubuntu? (Ubuntu uses GParted during installation!)

Why is it not on the "available" list to install?

Why would disk partitions which were showing on the desktop disappear between Ubuntu boots?

How do I get them BACK! There is no "explorer" equivalent that I can find, but I know they are there - I PUT them there myself manually!

Why is there no "Guide for Windows users" to translate some of the stuff? I mean it seems that if you know NOTHING as a Windows user, you can use Linux without trouble. But if you know too much about Windows, DOS (and even earlier systems), Linux will drive you mad before you can learn anything because some of the same terms are used for something different (root is a good example which one hits fairly soon after using Linux the first time) and other things don't seem to have any equivalent at all (explorer is the most obvious example).

All help gratefully appreciated!

---

### Post by amohanty on 2007-04-16
I think you ought to read a couple of essays first :)

[http://www.psychocats.net/essays/linuxtroll](http://www.psychocats.net/essays/linuxtroll)
[http://www.psychocats.net/essays/index.php](http://www.psychocats.net/essays/index.php)

then use google, there are 100s of linux guides for windows users.

Now to your problem:
Depending on when you last used ubuntu a _lot_ might have changed, which means that some or a lot of file may have been updated and your custom files will be backed up and present where the new ones are. A lot of  times the custom files are kept as is, and the new files are marked *.new. 

I am surprised you required two reboots. Techinically even if there was a kernel update you dont really _need_ to reboot, but you ought two. As to Windows updates, if you find it seamless and no problems at all, try talking to your corporate IS dept sometime, you will be quite surprised at their response :) Not to say that ubuntu updates are always smooth, somtimes things go wrong, but in my experience far fewer.

To see what partitions you have, in terminal (Applications->Accessories->Terminal) type the following:
sudo fdisk -l

Check to see that all your partitions are there.

If yes then check the contents of **/etc/fstab** to make sure that those partitions are auto-mounted. If not look in the /etc folder to see if fstab has been updated, by looking for a file whose name starts with fstab.

Re: gparted qtparted is gparted cousin. The actual application is gnu parted [http://www.gnu.org/software/parted/index.shtml](http://www.gnu.org/software/parted/index.shtml). GParted is the GTK based frontend for it and QParted is the QT based frontend for it. I am quite surprised that you have QParted if you installed ubuntu (as opposed to Kubuntu).

The explorer equivalent is called nautilus. It can be accessed via Places->Copmputer. 
Some more applications you can use are listed at:
[http://en.wikipedia.org/wiki/List_of_open_source_software_packages](http://en.wikipedia.org/wiki/List_of_open_source_software_packages)

HTH
AM

---

### Post by brit0n on 2007-04-16
> **amohanty said:**
> I think you ought to read a couple of essays first :)

[http://www.psychocats.net/essays/linuxtroll](http://www.psychocats.net/essays/linuxtroll)
[http://www.psychocats.net/essays/index.php](http://www.psychocats.net/essays/index.php)

then use google, there are 100s of linux guides for windows users.

I read the essays for which thanks - one was rather useless to my case, but I guess that's why you cited both. The other was food for thought. The google comment was rather insulting, but you probably didn't intend that. I'm not sure whether to feel insulted or vindicated, but I'll take them in the spirit I think they were intended. Sorry I made the mistake of putting not so useful off-topic comments in my own threadhead -  call me a well-intentioned troll if you must but make sure you include the "well-intentioned" part. It is too easy to forget when posting something like this that too many Linux users, helpful though they may be on these forums, can't understand how anyone with a brain can possibly be using Windows or anything else. Usually, I find that they don't actually know very much about anything beyond the basics of using a few things which is fine and very useful for people who don't want to know much. Probably my problem with this distro is that I know TOO much. It isn't about "the Windows way" because the Windows way doesn't exist - I go back too far in computing to have allowed anyone to get me away from the code. The difficulty for you in helping us people stumbling in here is that we are all different! I am primarily here to be able to continue learning enough about Linux to get back to where I was in helping the development of a linux program which I believe should be used by Windows users even if they don't have a Linux distro installed!

Enough of that. I have taken your point and I hope others accept that I have. AND I shall try to remember it before I post another time in frustration because "I know Linux is better than this" lol

> 
Now to your problem:
Depending on when you last used ubuntu a _lot_ might have changed, which means that some or a lot of file may have been updated and your custom files will be backed up and present where the new ones are. A lot of  times the custom files are kept as is, and the new files are marked *.new. 
That's interesting and thankyou. But you have already lost me. Although I am reading up Linux a lot and want to get on to developing something, for the time being, I am trying to be a basic user although I suppose partitioning is something basic users avoid. So those files might be marked *.new, I don't see files do I? Ubuntu doesn't SHOW me files although I do tend to click the "Show details" button simply because it is nice to be allowed to see a terminal window without having to hack a registry!

> I am surprised you required two reboots. Techinically even if there was a kernel update you dont really _need_ to reboot, but you ought two. 
My guess was that it went through two kernels. Does it do it step by step and require a reboot for each or can it jump kernels? My assumption now is that it loads each new kernel to allow me to choose - thankyou Linux ;)

> As to Windows updates, if you find it seamless and no problems at all, try talking to your corporate IS dept sometime, you will be quite surprised at their response :) Not to say that ubuntu updates are always smooth, somtimes things go wrong, but in my experience far fewer. Thanks, I talked to me and I laughed ;)

> To see what partitions you have, in terminal (Applications->Accessories->Terminal) type the following:
sudo fdisk -l

Check to see that all your partitions are there.

You're joking, right? I know what partitions I have because I wrote the table manually! They are all there happily working. Once I loaded GParted, it could see them fine. My question was that they are no longer showing where all the other partitions show - on the desktop, on various menus etc. Now PLEASE don't shout "that's the Windows way" because I know it might be a dumb way to DO it, but it is an easy way to EXPLAIN what I wanted to do and expected to find an easy Help entry to tell me how to do. Here's what I want to do the equivalent of: IF I were in Windows and IF I wanted to be able to see some kind of link to each partition on my desktop (which I wouldn't because the Windows desktop is a clutterbox lol), I could do it a number of ways but I would probably throw up an explorer window (old-fashioned style, folders left pane, subfolders/files right pane), hit the move up a level key until I got to My Computer and then right-click drag my partitions as a group onto my desktop and tell it to shortcut them. HOWEVER (and it is a BIG however), I wouldn't ever want to do that because if I want to get to my partitions in that way, I can do it any number of easier ways through the explorer, through a command window, in DOS, through Disk Management and even in raw table form!

And the BIG point is that I didn't PUT those partition (links? shortcuts? whatever they are...) things on my desktop or in the menus - the Ubuntu installer did. But for some reason some of them are no longer there even though they exist. So Ubuntu did something IN MY COMPUTER WITHOUT TELLING ME WHAT! (Sounds like Windows, doesn't it? ;) ) OK, I am just kidding. It probably did it for a good reason. So I searched and found no answer as to what or how to find out what it did, why, and how to change it. In fact, I never really found out why Ubuntu put those (things) on my desktop in the first place.

Oh and fdisk? I know that the Linux version of fdisk is not as dumb as the REALLY dumb Windows one, but until I have learned a LOT more, I am not allowing anything other than GParted near my partition table and then only under close supervision! I hate being forced to go back and edit my partition table or MBR manually the way I like them, but I do it because as yet the only really good partition managers do too much for me and don't allow me to control them enough.

> If yes then check the contents of **/etc/fstab** to make sure that those partitions are auto-mounted. If not look in the /etc folder to see if fstab has been updated, by looking for a file whose name starts with fstab.Great. Thanks. I THINK I can find out how to do that. If I can't after reading for a week, I'll come back, but I think you answered the question I didn't know how to ask. If I understand correctly, Linux mounting is not anything like any kind of mounting I used on computers other than Linux/Unix (earlier mounting was used for things like compressed drives and virtual drives). It's merely a virtual thing which allows access (by software, by the OS, by the user depending on the type of mounting/permissions) not the same as, but similar to, mapping a network drive in Windows? And if that is right and I extrapolate, if mounted, they will re-appear in desktop/menus etc. Is that right? If so, i can go off tinkering happily.

> Re: gparted qtparted is gparted cousin. The actual application is gnu parted [http://www.gnu.org/software/parted/index.shtml](http://www.gnu.org/software/parted/index.shtml). GParted is the GTK based frontend for it and QParted is the QT based frontend for it. I am quite surprised that you have QParted if you installed ubuntu (as opposed to Kubuntu).QTParted came up on the Synaptic thing or the other thing that installs things (forgive me - I still can't remember until I boot linux). GParted didn't although the Ubuntu used it when it installed and I allowed it to format the partitions I had set. I have reinstalled it, but I think I used an odd method (moree reading for me). Just wondered why it disappeared and why it didn't show in the "Available - All" list when QTParted DID!

> The explorer equivalent is called nautilus. It can be accessed via Places->Copmputer.
Some more applications you can use are listed at:
[http://en.wikipedia.org/wiki/List_of_open_source_software_packages](http://en.wikipedia.org/wiki/List_of_open_source_software_packages)

Thanks, I'll try it next time I have Ubuntu awake. And I need to do some more in the ones I have already before I go off loading more fun stuff lol

Thanks amohanty for a full, helpful and thoughtful reply. Now more reading and no posting for me.

---

### Post by brit0n on 2007-04-16
> **amohanty said:**
> 
If yes then check the contents of **/etc/fstab** to make sure that those partitions are auto-mounted. If not look in the /etc folder to see if fstab has been updated, by looking for a file whose name starts with fstab.

OK. two fstab files - one is fstab and the other is fstab.pre-uuid which contains only a remark:
# UNCONFIGURED FSTAB FOR BASE SYSTEM

so I am ignoring that one.

fstab is shown as modified Wed 25 Oct 2006 which is long before I installed it. Maybe the file dating system is different from DOS etc but that is odd! I am assuming that is actually a creation date (created in the Ubuntu distro).

So of course I have no idea whether it is updated.

As far as the content is concerned, it is showing the same options etc for all the partitions EXCEPT the two linux/swap partitions. If I browse in Nautilus, all the partitions are listed, but if I browse the partitions not showing on desktop and menus, they don't show any files/directories (which they all have) and although they are different file systems, some of the existing "showing" partitions have those file systems.

In fstab, the only reference I can find to "auto" is under the removable media and says noauto for the cdrom and dvdrom, but auto AND noauto for the floppy.

That's as far as I get. Not very far! Sorry.

(In my references to the two ways I was offered to get a program, the names I forgot were "Add/Remove" and "Synaptic Package Manager". I am studying how I am SUPPOSED to use them instead of downloading the installer for them and finding out how to run it!)

---

### Post by amohanty on 2007-04-16
> As far as the content is concerned, it is showing the same options etc for all the partitions EXCEPT the two linux/swap partitions. If I browse in Nautilus, all the partitions are listed, but if I browse the partitions not showing on desktop and menus, they don't show any files/directories (which they all have) and although they are different file systems, some of the existing "showing" partitions have those file systems.

In fstab, the only reference I can find to "auto" is under the removable media and says noauto for the cdrom and dvdrom, but auto AND noauto for the floppy.

the **default** option also means it is auto-mounted. So lets go over this again:
1. You have a linux partition and a swap partition
2. You have windows partitions
3. You want to be able to see the windows partitions auto-mounted and on your desktop.

The reason you see the folders and not the contents are because the partitions are not mounted. Can you do the following:
1. Post your partition layout ie how many partitions, what formats.
2. Post the contents of your /etc/fstab

AM

PS: what are you reading for this? 
[http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/](http://paulstamatiou.com/2005/10/24/how-to-ubuntu-linux-for-novices/) is a good place to start.

---

### Post by brit0n on 2007-04-17
Sorry. I meant that was as far as I had got. I need to read mounting up and I'll get there. Thanks for the help.

(I was reading Ubuntu help, the forums and a lot of other sites most of which seem to be written by people who assume the reader knows less than they do about partitions, coding etc)

---

### Post by amohanty on 2007-04-17
> (I was reading Ubuntu help, the forums and a lot of other sites most of which seem to be written by people who assume the reader knows less than they do about partitions, coding etc)
Reply With Quote

I agree with you there. For some reason or another, almost all forms of tutorials are not written with the windows power user in mind. Historically, these have also been, the linux is not ready, linux is crap crowd. Unfortunately very few linux users are able to resist hitting back instead of helping out and as you saw even I am not above that :)

AM

---

### Post by Patrick K on 2007-04-17
An app you might find helpful is gconf-editor. It is in Synoptic. It has all sort of configuration options. In a remote way it is somewhat like regedit.exe. 

There is an option in "apps > nautilus > desktop" named "volumes_visible" that allows you to control if the mounted volumes are visible or not. 

I suspect you will like it.

---

### Post by brit0n on 2007-04-17
> **amohanty said:**
> I agree with you there. For some reason or another, almost all forms of tutorials are not written with the windows power user in mind. Historically, these have also been, the linux is not ready, linux is crap crowd. Unfortunately very few linux users are able to resist hitting back instead of helping out and as you saw even I am not above that :)

AM

Maybe. But I see an AWFUL lot of jealous guarding of some strange technical "superiority" from people who really have no idea what they are doing bar the things they have learned by rote which makes helping them develop things very difficult. (I am only back in Linux so much because I am trying to learn enough to produce something useful to many but it needs a link to Windows.) There is nothing "new" in Linux and once you are forced back into a terminal window, you are pretty well where you were before Windows came along.

And you have to admit that it would be better to get the GParted dialog box "Not yet implemented" when you click Help than this:

Ubuntu booted. Click the big ? at the top.
Search for: "mount partition" (hoping, fingers crossed)

First result: "Working with your desktop | partitions and booting" (excellent! click.....)

Partitions and Booting

    * 10.1.&#8194;Graphical Partition Editor
    * 10.2.&#8194;Make Windows partitions available from Ubuntu
    * 10.3.&#8194;Make Windows partitions automatically available

Great! Well, i just came from inside GParted and everything was as I expected there except that  the Info tells me that a couple of partitions are no longer mounted..... try 10.2 and 10.3 (fingers crossed, this is looking like a short help hike for a change... click)
10.2 click...
1. Open System &#8594; Administration &#8594; Disk

Yessir, just what I was looking for (the 10.3 "automatically" link will lead to the same menu tree pretty soon too).

All smiles, Clicks System | Administration | Disks

Huh? Disks? Nope, not there. Maybe you have to be logged in as an administrator to see that on the menu but it didn't SAY that so maybe I am thinking like a Windows tweaker.... and anyway, the first advice I was given on the forums was to do things as a line by line super doer (although I had to look up sudo to find out that was what they were telling me to do) rather than exposing my system to insecurity (which it usually is when I am in Windows without too much hassle). OK back to the drawing board, but one wonders why the help files take you to a menu tree which doesn't exist.

And why ARE the hard disk partitions mounted in /media instead of /mnt ? I thought media was for *removable* media. Another help file which leads correctly but the setup doesn't follow the lead. Never mind. Back to [http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html](http://www.debianadmin.com/mount-your-widows-partitions-and-make-it-readwritable-in-ubuntu.html)
but that makes no sense as the existing fstab file entries for the unmounted partitions are the same as the mounted ones already and they don't include ntfs-3g

At least I know how to find out what all these commands are that people tell us to type because I am sure as heck not typing them without knowing! But it does get rather reminiscent of the old DOS only days when one had to type complete pathnames in order to do anything (Apple II was easier because you didn't have a hard disk lol).

Sorry. Not complaining, back to work trying not to use Ubuntu help system lol I KNOW I'll get there soon enough which many people seem to give up too early on. But it would have been nice to be coding something for the GParted on memory stick for Windows users by now. I already had the sticks working and solved the "move the XP partition from one drive to another and multi-boot it with Linux, Vista" etc. Oh well, slowly but surely - looks like I have to become an Ubuntu power user before I can use this great OS - much like when I migrated from a mainframe to an Apple II or from DOS to DOS shells to Windows when it first came out really lol

---

### Post by brit0n on 2007-04-17
OK some kind of success, but..... so now for a few real straightforward QUESTIONS.

After a little extra research, it occurred to me that for reasons to do with the partitioning of these disks, Ubuntu didn't recognise the partitions because of the UUID.

So (using terminal and sudo cp ... and sudo gedit /etc/fstab because the System | Adminstration | Disks is not available as this user if ever) I backed up and edited the *filesystem table* fstab.

For the two partitions which were not mounting automatically, I simply deleted the # from the first of the two lines, combined the lines as one (although if this is like coding I do, this wasn't necessary was it?) and deleted the entire UUID=<uuid> For example:

# /dev/hda2
UUID=1E98D6A298D6782B /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

becomes

/dev/hda2 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

(See below regarding the umask value.)

Then again in terminal, to test it, I use sudo mount -a

Voila, my partitions are now mounted although not yet showing on the desktop/menus. Reboot and they are.

All back to how it should be..... or maybe how it was.

Now for the questions:

1. Should I have access to System | Administration | Disks or is that something I should bug report? (Gparted couldn't mount them either but it appears it can UNmount them.)

2. How do I identify the UUID of the two partitions? One is an NTFS Windows XP Pro partition and the other is a Windows FAT32 LBA Windows 98SE partition. Naturally, neither of them were created or formatted in Linux. (Does UUID matter to anything? If so, I will do more reading. It SEEMED so because Ubuntu didn't like whatever value it put on it when it installed!)

EDIT: OK I found it. vol_id does that. So I rewrote fstab to re-include the (changed) UUIDs. No answer required for 2! (I see many linux users are querying the use of UUIDs but I see Ubuntu only applies them to HDDs and not removables unless it does it to USB drives. I don't mind now I know how to rework fstab if my partition UUIDs change.)

3. That umask=007 was put there when I installed Ubuntu. i don't remember whether I was asked. Is that insecure? It looks to me like I could get a rogue program in Ubuntu which couldn't do a thing to Ubuntu, but could seriously mess with my various Windows partitions and NTFS data partitions! Am I right? (I know what to research if I am so a "yes" would be good - a "no" would be better and a "maybe" would need more info if you have it.)

4. Can you stand me stumbling along before I can crawl? If not, say so and I will go back to the slow track I took to learn how to partition manually or to program C++ for windows and linux simultaneously - all by myself and very slowly and shakily! lol)

(Note, fast type advice is great - I can't DAMAGE anything here too much with backups and my own partition tables etc. So general pointers in some cross-dos-unix-c++-fortran-takeyourpick language rather than a "type this click that" would be GREAT!)

---

### Post by amohanty on 2007-04-18
> 1. Should I have access to System | Administration | Disks or is that something I should bug report? (Gparted couldn't mount them either but it appears it can UNmount them.)


No. AFAIK there never was such a thing. Could be a throwback to some really old version. I tend to use the terminal a lot, even on windows used cygwin, so I dont generally rely on GUI tools. GParted probably has a problem with NTFS partitions, the reason it may not have been able to mount them is that it may have been trying to mount them rw but write support is a bot sketchy. I have been hearing about something called NTFS-3G or something that lets you mount NTFS as rw, but I have not used it.

> 2. How do I identify the UUID of the two partitions? One is an NTFS Windows XP Pro partition and the other is a Windows FAT32 LBA Windows 98SE partition. Naturally, neither of them were created or formatted in Linux. (Does UUID matter to anything? If so, I will do more reading. It SEEMED so because Ubuntu didn't like whatever value it put on it when it installed!)

The whole UUID business is new thing (probably to allow hot-plug drives) Basically you can swap out drives as long as the label/vol_id is the same. I much rather prefer explicit device names, so that I know exactly what I am getting and doing. To rework you fstab try a **sudo fdisk -l ** and use the drives listed there.

> 3. That umask=007 was put there when I installed Ubuntu. i don't remember whether I was asked. Is that insecure? It looks to me like I could get a rogue program in Ubuntu which couldn't do a thing to Ubuntu, but could seriously mess with my various Windows partitions and NTFS data partitions! Am I right? (I know what to research if I am so a "yes" would be good - a "no" would be better and a "maybe" would need more info if you have it.)

So umask is the _reverse_ of what is actually done so all files have 775 set on them. Moreover the **defaults** I think mounts it as root owned. However I think that the gid options may override that. I would suggest using **auto,user,ro,nls=utf8** so that its automounted can be mounted by user and is read-only.

> 4. Can you stand me stumbling along before I can crawl? If not, say so and I will go back to the slow track I took to learn how to partition manually or to program C++ for windows and linux simultaneously - all by myself and very slowly and shakily! lol)

No prblems :) I wont say that I am great at helping windows power users, you would be surprised how many of them think they know a hell of a lot more than they really do :). Fire away and I will try my best.

AM

---

### Post by Patrick K on 2007-04-18
"2. How do I identify the UUID of the two partitions? One is an NTFS Windows XP Pro partition and the other is a Windows FAT32 LBA Windows 98SE partition. Naturally, neither of them were created or formatted in Linux. (Does UUID matter to anything? If so, I will do more reading. It SEEMED so because Ubuntu didn't like whatever value it put on it when it installed!)


The whole UUID business is new thing (probably to allow hot-plug drives) Basically you can swap out drives as long as the label/vol_id is the same. I much rather prefer explicit device names, so that I know exactly what I am getting and doing. To rework you fstab try a sudo fdisk -l and use the drives listed there."

Look in Device manager. Select the partition you're interested in and go to the advanced page. It the bottom entry.

---

### Post by amohanty on 2007-04-18
> Look in Device manager. Select the partition you're interested in and go to the advanced page. It the bottom entry.

Cool :) didnt know that.

Thanks. AM

---

### Post by Patrick K on 2007-04-18
No problem :)

---

### Post by brit0n on 2007-04-18
Thanks both of you. Actually, I edited the post to show I found the answer to 2, but the more information the better:

> Look in Device manager. Select the partition you're interested in and go to the advanced page. It the bottom entry.

The trick I needed was to find out how to ask Linux what UUID Linux was looking for. *vol_id* does that. For example:

```
vol_id -u /media/hda3
```

will give you the UUID of 3rd partition of first hard disk.

Just to confuse the issue, there is Windows usage of UUIDs which will not be the same IDs. Of course it gets MORE complicated with network drives if the UUIDs have not been allocated to ensure that duplicate UUIDs are avoided. Throw security in the pot (device configuration in the system should preferably not be identifiable from the UUID - meaning allocating serially contrived UUIDs should be avoided) and it could be a nightmare. For now, I am letting Ubunut decide and if the UUID renders the partition unmountable, I will use vol_id -u to discover what the "new" UUID is. Easy enough.

Thanks AM and Patrick - I'll read Ubuntu helpfiles with a pinch of salt in my eye and I need to secure my non-linux partitions. The rest is more reading up which I am doing whenever I get the chance.

---

