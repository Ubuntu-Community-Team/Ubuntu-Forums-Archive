---
title: "deafult HDD mount points - disks manager interface"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-02
Hi,

Question 1
Using the Disks Manager, "Access Path", the default for the 1st HDD (with ubuntu on it) is:

/

I want to add a 2nd HDD but am unsure of the recommended "Access Path". What should I type there in order to mount the HDD. It is empty and formated as ext3. I will be using it for data storage.


Question 2
When I click the help button in Disks Manager I am told, "Could not display help". How do I get the help docs installed?

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-02
I will try another question.

I have 2 HDD. #1 with ubuntu and it works fine. #2 HDD is empty and formated as ext3. It is for data storage.

How do I add #2 HDD so I can access it from the desktop? I have asked before and thought I had an answer but now I am unsure. My #2 is unmounted.

In XP the HDDs show automatically in Windows Explorer. I want the same functionality with ubuntu. I have no idea how to achieve this.

Suggestions welcomed.

Thanks.

---

### Post by catlett on 2006-06-02
[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by u.b.u.n.t.u on 2006-06-03
I created a new directory for my data HDD.

```
 sudo mkdir /storage
``` 

When I do. 

```
sudo nano /etc/fstab
```

I only see my first HDD.

my 1st HDD is dev/hda1
my  2nd HDD is dev/hdb1

What do I do next?

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-03
"XXXXX@ubuntu:~$ mount /dev/hdb1 /mnt/storage
mount: only root can do that"

hdb1 = my 2nd HDD that I want to mount, data only
storage = my folder I have created

What should I do?

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-03
OVERVIEW ONLY
How to set up a 2nd HDD for storage.
(aka welcome to hell) :P

You need to format the HDD. Use Gnome Partition Editor (Gparted). ext3 is a good file system at this time.

You need to mount your HDD. You do this by editing a file called "fstab". This is done through the terminal. Basically you add a new line to the information there, that details your HDD, eg:

"/dev/hdb1 /storage ext3 defaults 0"

So it looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /storage ext3 defaults 0

Then you need to save "ctrl-O" or "^O" or "F3" - I think they all mean the same here.

Once saved you need ubuntu to confirm the changes, so in the terminal we type:

sudo mount -a

Then we have to give ourselve permission to use our own HDD. Assume our name is gatesy:

sudo chown -R gatesy: /storage

then

sudo chmod -R 755 /storage

The nightmare isn't over yet.

You now need to create a link to your HDD on your desktop.

Is this ubuntu at it's most user unfriendly? In my view yes. It has taken me over a week and many questions to understand and implement this. On XP it takes under 1 minute - go figure! Hopefully this will all be gui-ed out in the future.

No flaming please!  lol

NB: the above is only is idea. Do not rely on it. Verify everything yourself.

](*,)   :mrgreen:

---

### Post by catlett on 2006-06-03
Sorry I haven't checked back in. It is simple but compicated at the same time. Lets keep it simple to start. We'll mount the drive for just one session. First you have to find out where the partition is and what it is labeled as, enter ```
sudo fdisk -l
``` This will list your partitions and drives. I'll mount my external drive so you can get the idea.  My output is a little confusing because I multi boot but I want to show you the whole process 
```
tj@ubuntu:~$  sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1899    15253686    7  HPFS/NTFS
/dev/hda2            1900       12161    82429515    f  W95 Ext'd (LBA)
/dev/hda5            1900        2644     5984181    b  W95 FAT32
/dev/hda6            2645        2709      522081   82  Linux swap / Solaris
/dev/hda7            2710        3654     7590681   83  Linux
/dev/hda8            3655        5475    14627151   83  Linux
/dev/hda9   *        5476        6117     5156833+  83  Linux
/dev/hda10           6118        6987     6988243+  83  Linux
/dev/hda11           6988        7618     5068476   83  Linux
/dev/hda12           7619        8318     5622718+  83  Linux
/dev/hda13           8319        9578    10120918+  83  Linux
/dev/hda14           9579       10746     9381928+  83  Linux
/dev/hda15          10747       12161    11365956   82  Linux swap / Solaris

Disk /dev/sda: 128 MB, 128450560 bytes
8 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         979      125296    6  FAT16

Disk /dev/sde: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        4865    39078081    c  W95 FAT32 (LBA)
```
What I'm looking for is disk /dev/sde 40 gb. That is my other hard drive. It is external so yours will not be labeled sde. It will most likely be /dev/hdb. Just look for the gb number that goes with it.
So now I need a place to put it. If you mount disks in trhe media folder it will get a desktop icon. So I'll make storage in media ```
sudo mkdir /media/storage
```
Next is to give the mount command. You need to know the label of the drive. The type of filesystem and the location you want to put it.
```
sudo mount /dev/sde -t vfat /media/storage
``` That's it. It will mount and there will be an icon on the desktop. (For this session only. editing /etc/fstab makes it permanent)
Just to get a little more specific. sudo=gives you administrative powers, mount=the command to moiunt, /dev/sde=the label of the drive, -t= is an option to the mount command, vfat=filesystem type (fat32 and fat or any fat filesystem is listed as vfat), /media/storage=the location to mount to.
Start with this and then you can move on to editing your /etc/fstab.
 Quickly with /etc/fstab you have to manually add the text to the document. You need to know the label of the drive, file system, location to mount and the options for /etc/fstab. The options are different but they are outlined iun the /etc/.fstab link I posted.

P.S. If your other hard drive is partitioned, you have to mount the partitions individually. I mounted the drive as sde because it is one partiton. If it was made into /dev/sde1 and /dev/sde2, I would have had to mount them seperately i.e.do the whole process but make a different location and obviously put sde1 the first time and sde2 the second. Just wanted to make sure I didn't leave anything out.

P.S.S. If you post your fdisk -l output I'll make your /etc/fstab entry for you and then you just have to copy/paste it into /etc/fstab.

---

### Post by u.b.u.n.t.u on 2006-06-03
Thank you catlett.

My storage HDD is working  ```
/storage
```

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-03
Hi catlett,

I redid this exercise and my fstab is now

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/storage  ext3    defaults        0       0

```

I even spaced out the entry :-D 

```
/dev/hdb1       /media/storage  ext3    defaults        0       0
```

I rebooted and voila! "stoarge HDD icon on my desktop".

As the entry is in fstab, is it now permanent, that my storage HDD will appear as does my ubuntu HDD?

Thank you again!

:D

---

### Post by catlett on 2006-06-03
Your welcome. I didn't see your repost so I didn't know things went your way. Everything is so different at first it can be very frustrating but once you get going you'll see that linux is very logical.
The biggest issue (myself included) is that we expect every operating system to work like windows did. Linux is not windows and wasn't meant to be but everyone (usually) learns about computers on windows and they just assume that is how all computers work.
I was the "windows expert" in my group of friends/family. I could do just about anything with XP. That's why I got into linux. I thought I was so "smart" that I should be running linux or something instead of this easy windows. 
I partitioned, booted the install and got a dual boot. I thought "I'm so g-d--n smart. Look at me, I can do anything with a computer." That was the last thing I did with ubuntu other than logging on. I COULDN'T DO ANYTHING?!?!
I went from downloading torrents, cracking activations, mounting iso with daemons to not be able to access a floppy. (nevermind burn an iso to disc)
That is where these forums came in. Everything I know comes from here. Posting and getting a response or just being in a thread and seeing something posted that I didn't know.
Now I know a little but I still learn just by reading other posts and being in threads. Plus this forum make you think there is hope for mankind after all (sorry to get corny but everyday you see or hear of some terrible thing man is doing to man. whether it be a war or just class domination that leads to poverty and suffereing and thern you come here and there are people from all over the world brought together by a common interest and they help each other for the sake of helping)

So like the catch phrase goes "don't pay me back, pay it forward"


P.S I'm rambling and I didn't see your post. YES. It is permanent now that it is in your /etc/fstab.:)

---

### Post by u.b.u.n.t.u on 2006-06-03
Good post catlett !

I had to laugh when I read "I went from downloading torrents, cracking activations, mounting iso with daemons" - :-k (5th ammendment for me!) lol

I'm a former member of the "wave pub board" - if one was there they'd know what I mean. They closed their doors a few years ago.

I hear FTI is "happening" :cool: 

"I was the "windows expert" in my group of friends/family." Exactly the same here. Though I still am.

I used to write about IT for a rag and we even had *cough*  as a client. So I don't want to say anything too bad. Nice people! I think that the time of XP is close to over.

Vista is like the Spruce Goose of Operating Systems whereas ubuntu has  a Formula One pedigree.

Consider this. XP was the main operating system for Microsoft for what, 5 years? (25 October 2001).

So contenders start your engines on the release date of Vista. 5 year development cycle for the next one? In that 5 years will there be 10 releases of unbuntu?

Microsoft = 1 (plus service packs)
ubuntu = 10

Is this going to be a turkey shoot or what?

If the improvements from 5.10 to 6.06 are any indication, then we are going to see a significant change in the way computers serve mankind.

A shift from greed is good to lets work together and share. Like sharing food at a table with family and friends rather than giving each a bill at the end.

It took several tries for me to adopt Firebird/Firefox. That was some time ago now. It took about 2 years for me to adopt Linux. I tired 3 distros in that time - never seriously considering a move.

I looked in at the Dapper RC about a week ago. I made the switch on 2 June 2006. I deleted almost all of my windows software. I won't be going back except for a games based experience. An XP-box.

Why ubuntu? A test drive of Dapper RC was enough. This community made it happen.

There are some compelling reasons ubuntu is so popular. 

In 10 years, people will talk about windows as they once talked about Wang. Wang who? I may hear some people ask! lol

:D 

I will now become the "expert" for my friends when they make the change to ubuntu. I know their computers cannot run Vista. I know they are not about to either buy Vista or the new box just to run it!

Vista is arguably the best thing that ever happened for Linux.

ubuntu is like a snowball at the top of a huge mountain, growing and gaining speed every day.

As IE replaced Netscape, ubuntu will replace windows. It is free, leaner, faster, more secure, online community help. If one were to make a comparative list of the features, it would be very dramatic, so great are the advantages of ubuntu.

I found XP a right pain. Always forcing me to do it their way. With ubuntu I have choice. If I don't like the browser I just delete it. If I don't like the media player I just delete it. Actually it is even better - I don't need to install such in the first place!

With windows you can have it any base configuration you like, as long as it is the Microsoft way. Don't even think you have any rights to remove their software!

With Microsoft, Windows OWNS the user. With Linux, the user OWNS ubuntu!

Good bye windows (ctrl-alt-del), hello world ubuntu!!!

:D

---

### Post by confused57 on 2006-06-03
[QUOTE=catlett]
That is where these forums came in. Everything I know comes from here. Posting and getting a response or just being in a thread and seeing something posted that I didn't know.
Now I know a little but I still learn just by reading other posts and being in threads. Plus this forum make you think there is hope for mankind after all (sorry to get corny but everyday you see or hear of some terrible thing man is doing to man. whether it be a war or just class domination that leads to poverty and suffereing and thern you come here and there are people from all over the world brought together by a common interest and they help each other for the sake of helping)

So like the catch phrase goes "don't pay me back, pay it forward"
[/QUOTE]
Thanks for sharing...Most of what I know about Ubuntu & Linux, I learned in this forum...I agree, it kind of gives you faith in mankind to know there are such "nice" people all over the world...seems you just hear or read about bad news in the world, this forum makes you realize there is "much" good everywhere.

---

