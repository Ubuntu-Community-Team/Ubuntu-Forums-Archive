---
title: "How do I create more than 4 partitions?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-10
I am trying to set ubuntu 7.04 up like this;

sda1 - windows NTFS 30 gb
sda2 - / root 20 gb
sda3 - /home 15 gb
sda4 - swap 2 gb

Here is where the problem begins; After creating those 4, weather using GParted or just running the partition manager from the installer, I am unable to create any more partitions in the unused space. In the partition manager/installer, it just says "unusable".

In GParted, I get the "cannot create more than 4 primary partitions". I have tried to create "extended" ones, but I still get the same result.

Anyone have any ideas? :confused:

---

### Post by Bachstelze on 2007-05-10
You must delete one of your primary partitions and create an extended one instead. Then you can populate your extended with as many logical partitions as you want.

---

### Post by discmaster on 2007-05-10
Do I create the extended partition as the total remaining disk size, & then create all the smaller partitions in there? Or create the "/" partition as extended?

This is where it is getting confusing for this "newb"!

---

### Post by Bachstelze on 2007-05-10
Yep, the extended partition will act as a "container" for the logical ones so you want to make it the total of the remaining disk space cause it you don't, that space will be unusable.

---

### Post by discmaster on 2007-05-10
Thanks so much, HymnToLife!

So let me narrow it down once again, just so I am absolutely sure, since I have been beating this thing for a few days, & trying to research on the 'net, only to get caught up in more confusing circles of info.!

Are you saying to:

Create Windows primary first., as primary.

Create an extended partition next, using the remainder of the drive size, & then create all smaller partitions in there, such as root, home, swap, etc.?

 If so, great, 'cause it looks like it worked! I didn't realize that the root didn't have to be a primary? partition...

---

### Post by Bachstelze on 2007-05-10
You can have up to three primary partition (since you also have an extended, you can make four primaries if you have no extended, that's jow you were setup earlier) so if you want, you can make your root partition primary too, though it wouldn't make much difference.

---

### Post by discmaster on 2007-05-10
Bear with me; which file format do I create the extended partition? I ask this since "home" will be ext3, my data part. will be NTFS, & there is the linux-swap partition also...

---

### Post by Bachstelze on 2007-05-10
What software are you using to create it ?

---

### Post by discmaster on 2007-05-10
Well, this may not be the correct way, but this is how I am doing it;

Using the Installer to create the primary partitions, since I can select the mount point with it; then I shut that down & run GParted to finish the job? I'm sure that probably isn't right, but there is so much info. out there on the partitioning, & hardly any of it seems to make any sense, at least not to me! :(

---

### Post by Bachstelze on 2007-05-10
The, in GParted when you select "Extended" in the partition type, the "File system" list should be greyed out so there's not much you can do with it anyway ;)

The way you're doing it should work but I personnally prefer to create all my patitions in GParted before launching the installer.

---

### Post by discmaster on 2007-05-10
Ok, here is what I am ending up with.

sda1 - windows NTFS - 30 gb.
sda2 - root ext3 - 20 gb
sda5 - home 15 gb
sda6 - swap 2 gb
sda7 - ntfs data 165 gb (approx)

The windows & root are primary, the other parts. are "logical".

I guess this looks right? Why do the numbers skip, i.e., where are sda 3 & 4 ?

---

### Post by Bachstelze on 2007-05-10
sda1/2/3 are the three first primary partitions, so since you have only two, you don't have any sda3. sda4 is the fourth primary or the extended (the extended in your case, which is nt mounted, that's why you don't see it here).

---

### Post by discmaster on 2007-05-10
> which is nt mounted, that's why you don't see it here)Ok...do I need to mount it before continuing the install? If so, how?

---

### Post by Bachstelze on 2007-05-10
No, as I told you, the extended partition only acts as a "container" for the logical partiton. It does not contain any data of it's own so you cannot mount it.

---

### Post by discmaster on 2007-05-10
>  the extended partition only acts as a "container" for the logical partiton. It does not contain any data of it's own so you cannot mount it. Very good. Thank you for clearing that up for me. I am an experienced windows user, & I can create partitions galore with no problem on there, but using the other partition manager with ubuntu just throws me somehow.

Maybe it is the different terminology that I am not used to. I just wanted to be sure of doing it right this time, as I am on my 5th install! (I think, might be more) & I am anxious to get this thing up & running so I can move on to having fun with it, instead of doing continual installs, lol! 

You've been an excellent help in clearing this up for me, and again, 

Thank You so much! :D

---

### Post by discmaster on 2007-05-10
Ok, guess I am doing something wrong here again. I have tried installing 2 times now on the root directory, & I have the partitions set up as described earlier. After the install completes, & I reboot, a black screen appears with;
> 
Error 17: Cannot mount selected partition

Press any key to continue... 

If I press a key, it takes me to the selection screen where I can select ubuntu ...generic, recovery mode, memtest.

Anything I select there just sends me back to the error message.

After 2 attempts at installing, I am obviously doing something else wrong; is it during the partitioning?

---

### Post by Bachstelze on 2007-05-10
Seems GRUB is trying to mount the wrong partition, I guess you could just edit it's config by hand to fix it.

---

### Post by discmaster on 2007-05-10
I read some other posts on the subject, & as I figured, I didn't understand them. Is it because I have a windows partition created first, & I haven't installed windows on it yet?

Either way, how do I edit the config?

---

### Post by Bachstelze on 2007-05-10
```
sudo nano -w /boot/grub/menu.lst
```

I'm going to bed now so wait for someone else to help you and feel free to PM me if the thread gets lost.

---

### Post by discmaster on 2007-05-11
Hello!

I decided to delete everything & start from scratch, using GParted all the way.
Using GParted, I cannot seem to get the extended partition deleted, the "delete" button won't work?

---

### Post by Bachstelze on 2007-05-11
You mus delete all the logical partitions it contains first.

---

### Post by dptxp on 2007-05-11
If you format any data partition as NTFS, you will have problems accessing it from
Ubuntu. So format in FAT32 if you want both Windows and Ubuntu to access it.

And Windows shall not be happy with EXT3 partitions.

---

### Post by Bachstelze on 2007-05-11
FAT32 is old and ugly, prefer ext2/3 for shared data between Windows and Linux.

---

### Post by discmaster on 2007-05-11
On my first install, I didn't have any problems accessing my windows drive, formatted to NTFS. After I figured out how, of course! At any rate, I could not get gparted to delete the ext. partition, so I ran the installer again & created the partitions from there. I am installing the OS at this point, & I figure I can go back in & fix the partitions with gparted after the install, if I need to.

If not, I guess I can always wipe it clean again & start fresh. Have to admit, I am getting tired of dealing with this OS...A friend recommended ubuntu to me, telling me how easy it is to use now, etc., & that has not been my experience at all over the last couple of weeks.

I first installed the 64 bit vers. (I have a AMD 64 pc), & that was very buggy; nothing seemed to work right, including the ff browser/thunderbird mail, & more...

So, this is the 32 bit install that I am doing now...we'll see how it goes...

---

### Post by discmaster on 2007-05-11
Install is finished, rebooted, now I get the same error again;

Error 17:

Why is this happening on a fresh install? Easy way to resolve?

---

### Post by Bachstelze on 2007-05-11
That shouldn't happen on a fresh install... Could you please paste your GRUB config ? Also, the output of *blkid* might help.

---

### Post by discmaster on 2007-05-11
> Could you please paste your GRUB config ? Also, the output of blkid might help. I am clueless as to how to do that - what do I need to do?

---

### Post by Bachstelze on 2007-05-11
```
cat /boot/grub/menu.lst
blkid
```

Run those two commands and for each one, paste what the terminal returns.

---

### Post by Billy McCann on 2007-05-11
~

---

### Post by discmaster on 2007-05-11
How/where do I open a term. if I can't get past this error?

(Please be gentle, I told you I'm a newb! I know windows, but not very much on linux at all)!

---

### Post by Bachstelze on 2007-05-11
Live CD ?

---

### Post by discmaster on 2007-05-11
> cat /boot/grub/menu.lst Typed that & I get "no such file or directory"

---

### Post by Bachstelze on 2007-05-11
That could very well be your problem, then. Do you happen to have multiple hard drives, by any chance ?

---

### Post by discmaster on 2007-05-11
I have an IDE drive on IDE1 (80gb) that is empty; I planned on using it for data storage at a later date.

I am installing ubuntu on my larger sata drive. Is there a conflict/other by having that ide drive connected?

---

### Post by Bachstelze on 2007-05-11
No, but it's very possible that the Ubuntu installer installed GRUB on the wrong drive and you'll have to install it manually on the correct drive.

---

### Post by discmaster on 2007-05-11
Well, I have read on some websites about installing GRUB on the correct drive. 

I don't really think I want to go through with all that. What are my options here? Would it work out better if  I just remove the IDE drive temporarily & reinstall ubuntu with only the sata drive connected?

---

### Post by Bachstelze on 2007-05-11
Yes, I guess that would work too...

---

### Post by discmaster on 2007-05-11
The reinstall would be easiest for me, as I don't have alot of time (& patience) to be fighting problems like this, as I have 2 full time jobs & kids to look after!

Speaking of which, I gotta run for now; I will work on this later & keep you informed of my progress.

Thank you for your time! :)

---

### Post by discmaster on 2007-05-11
I have removed the IDE drive. Using gparted, I have created;

sda1 ext media/disk (primary)
sda2 ext media/disk-1 (primary)
sda3 ext media/disk-2 (primary) (this will be home partition)
sda4 extended
sda5 linux-swap
sda6 ntfs (data partition)

(swap & data are in the extended partition)

Is this the correct way, now, before I start the install again? And I am still kinda confused when/where I mark the "/" root drive; is that done during the installation procedure?

---

### Post by Bachstelze on 2007-05-11
I don't know much about the "installation from Live CD" procedure as I pretty much never use it. Your setup seems correct, though the NTFS partition is a bit disturbing but you do as you wish...

---

### Post by discmaster on 2007-05-11
> Your setup seems correct, though the NTFS partition is a bit disturbing but you do as you wish. disturbing in what way? I that that should be ntfs so my windows drive could access it; what would you do in this situation?

---

### Post by Bachstelze on 2007-05-11
It will be troublesome if you want to write to it in Linux. If I were you, I'd rather make it ext3 and install a driver to access it in Windows.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by discmaster on 2007-05-11
I thought there was a linux driver/program that you install to allow writing to ntfs?

---

### Post by Bachstelze on 2007-05-11
Yes but it is not 100% safe.

---

### Post by discmaster on 2007-05-11
ok, I trust your judgment on this, so I will go with ext3 :)

---

### Post by discmaster on 2007-05-11
And then, what about this? Where/when do I "label"? the drives as home/root, etc. I am a bit fuzzy on that stuff...seems I had a bit of a prob. the first time when I initially installed ubuntu...> And I am still kinda confused when/where I mark the "/" root drive; is that done during the installation procedure?
Edit/Delete Message

---

### Post by nubutu on 2007-05-11
I don't mean to confuse you even more, but I think the current state of affairs with accessing ntfs drives from linux is pretty evolved now. In any case, I'm of the opinion too of not using ntfs, although you can always have a compromise solution and divide that large partition into two halves and later, when you are convinced of the best solution change to whatever you prefer based on your experience.

I wish you manage to set your system up, those problems are a bit annoying, but don't let yourself down, it'll pay the effort. And remember that most of them are not a particular issue of linux/ubuntu, partitioning is not a trivial issue, as you have already seen...

---

### Post by discmaster on 2007-05-12
Something wrong here;

I installed ubuntu, all went well, got to desktop, & now in Places > Computer, I have 3 drives listed;

sda5 - (the data drive)
sda1 - the windows drive
filesystem.

The total gb of the sda 5 & 1 add up to 197.5. This is a 250 gb. sata drive.
sda2 is supposed to be 30gb
sda3 (home) is supposed to be 15gb
sda4 is the extended part...

did I wipe out the other partitions during the install? how can I figure this out?

---

### Post by medad on 2007-05-12
Sda4 being the extended part wont show.  Your file system is the 30GB (sda2) and your home system is (SDA3).  I have a similar set up.

---

### Post by nubutu on 2007-05-12
Don't rely that much on what you see in Gnome>Places>whatever...Check instead this three things:

1. To check which partitions are mounted, type in a terminal:

df -h

2. To check which partitions are available, open with a text editor the following file:

/etc/fstab  

Be aware that some of the partitions listed above may not be "real" (the ones not starting with /dev/xxx)

3. It could happen, I guess, that your fstab file lacks something, although I don't see why this should ever be the case. Check how many /dev/sdx or /dev/hdx you have in the /dev directory, just in case.

Anyway, out of the figures you mention, it seems that you're OK: 197+30+15 is almost 250, and some of the space is gonna be reserved for the system, so no worries. As for the "filesystem" partition you mention, it includes everything you have in your system, so, as I said, don't make any conclusions out of that.

---

### Post by Bachstelze on 2007-05-12
1. Wrong, it's *mount*. df will show all mounted filesystems, not only partitions.

2. Wrong, it's *sudo fdisk -l*. The fstab lists only what you put in it, not all the partitions.

---

### Post by discmaster on 2007-05-12
This is what shows up when I type mount;
> tr@tr-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type ext3 (rw)
/dev/sda6 on /media/sda6 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


---

### Post by nubutu on 2007-05-12
>1. Wrong, it's mount. df will show all mounted filesystems, not only partitions.

From mount --help:

mount         :list mounted filesystems

As you see from the output posted above. Besides, df gives you the space available, so you can have an idea of what's going on and possibly recognize which is which.

>2. Wrong, it's sudo fdisk -l. The fstab lists only what you put in it, not all the partitions.

You're right, this is exactly the command you were looking for. But if some problem arises with partitions not being mounted, where would you look for the cause of trouble...? I did guess so, thanks.

Anyway, it seems as you are all done, I don't remember the setup you finally went for, take a look at the /dev/sdx and see whether is what you expected.

---

### Post by discmaster on 2007-05-12
This is what I am supposed to have;

> sda1 ext media/disk (primary)
sda2 ext3 media/disk-1 (primary)
sda3 ext3 media/disk-2 (primary) (this will be home partition)
sda4 extended
sda5 linux-swap
sda6 ext3 (data partition)

(swap & data are in the extended partition)

As you can see, I am missing the swap partiton, & only sda 1 & 6 are showing on the desktop...

---

### Post by nubutu on 2007-05-12
>tr@tr-desktop:~$ mount
>[...] 
>/dev/sda2   on  /                   type ext3 (rw,errors=remount-ro)
>/dev/sda3   on  /home           type ext3 (rw)
>/dev/sda1   on  /media/sda1  type ext3 (rw)
>/dev/sda6   on  /media/sda6  type ext3 (rw)

Don't worry about the swap partition, it's not meant to be mounted, If you are skeptic you can follow the advice you were given and type 

sudo fdisk -l

Now, all your partitions appear above, with their mount points after the "on". You can go to those places with a file browser and check it yourself. The problem about them not being in your desktop is a minor one, it all has to do with Gnome (I guess this is what you've got) and its configuration. You can set these things with gconf-editor (in a terminal, although you may have it somewhere else as well), which is a sort of registry editor for Gnome. Look for the key /apps/nautilus/desktop/volumes_visible and the likes, I'm not using Gnome right now, so I can't check it for you.

---

### Post by discmaster on 2007-05-12
Ok, I ran sudo -fdisk & came up with this;
> sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2            3648        6079    19535040   83  Linux
/dev/sda3            6080        7991    15358140   83  Linux
/dev/sda4            7992       30401   180008325    5  Extended
/dev/sda5            7992        8257     2136613+  82  Linux swap / Solaris
/dev/sda6            8258       30401   177871648+  83  Linux


All the partitions show up there, however.

sda1 is supposed to be a windows partition (eventually) ??? I see it says "linux" behind it.

And, as I mentioned 1 & 6 are the only ones in "computer" (& filesystem)

what do I do from here? it seems to me that things aren't right, but maybe they are, I just don't understand...Help! :confused:

---

### Post by Bachstelze on 2007-05-12
I guess you overwrited that sda1 partition. Good bye Windows !

---

### Post by discmaster on 2007-05-12
> I guess you overwrited that sda1 partition. Good bye Windows !lol, no I did that the first time around, a few days ago.

What I meant is, that sda1 I am planning to install windows on it in the future. Will that work when it says "linux" behind it?

And what about the other partitions? I am still unclear as to "where" they are, since they don't show up anywhere as in "computer".

Remember, I am used to a windows setup where all the drives & partitions are visible. Does linux not work that way?

---

### Post by Bachstelze on 2007-05-12
Yes, you'll still be able to install Windows on it, it will just format it to NTFS beforehand.

And why do you expect those other partitions to show up in "Computer" ? You can fairly easily have them appear if you want but what for ?

---

### Post by discmaster on 2007-05-12
> And why do you expect those other partitions to show up in "Computer" ? You can fairly easily have them appear if you want but what for ? Why? Well, I guess 'cause I am used to seeing them there, as in a windows type environment.

The don't show up in system monitor either - I guess that is okay?

If I can fairly easily have them show up, would you tell me how to do it? 

P.S. - Can you see how all this is kind of confusing to a windows user?!? :lolflag:

---

### Post by Bachstelze on 2007-05-12
Hmm, actually, you're using Gnome, which I know very little about. In KDE, you just add a line about the device in your fstab and it shows up under the System menu, you might want to try that.

---

### Post by discmaster on 2007-05-12
I am unable to write to sda6, which is formatted ext3.  For example, option to create folder is grayed out. How can I fix?

---

### Post by discmaster on 2007-05-12
> I am unable to write to sda6, which is formatted ext3. For example, option to create folder is grayed out Can anyone tell me how to write to a partition or second HD, i.e. create folders, etc.?  I have done tons of searching, reading about permissions, etc., it is all so confusing to a new user.

I am about ready to throw in the towel & go back to windows, as "it just works". I mean, if I have a fresh install & right from the start cannot create a folder on a partition or drive, what good is that?

Please someone, help this newb out! :confused:

---

### Post by nubutu on 2007-05-12
Tataratararatatararara...OoooK, let us not be nervous, right? You have accomplished the very first step, this is, you've already set up the partitioning scheme you wanted and installed linux on it. That's good, and you should be proud of it, that´s probably far more than anything you've done with windows so far.

Now, I hate to say this, but maybe you should do a bit more of research on your own about the whole thing. One thing is to have problems about Ubuntu not booting or something and very much different is complaining about icons not appearing on the desktop. I hope you appreciate this. There are tons of tutorials in the net about everything you can imagine; I bet you could learn how to build a time machine by just googling around.

Let's go to the point, now. You posted the following:

>tr@tr-desktop:~$ mount
>[...]
>/dev/sda2 on / type ext3 (rw,errors=remount-ro)
>/dev/sda3 on /home type ext3 (rw)
>/dev/sda1 on /media/sda1 type ext3 (rw)
>/dev/sda6 on /media/sda6 type ext3 (rw)

That gibberish means: 

device sda2 (one of your partitions) is mounted (this is, the location where you can find it) on "/", the root directory (the uppermost of the filesystem hierarchy, the top of the pyramid, if you want).

device sda3 (another partition) is mounted on "/home" (this is, "home" is somewhere under "/", right?, pretty much in the same way as "windows32" is under "windows" and this, itself, under "/C:" (or something).

"type", as you have imagined, is the type of filesystem you've set up, in your case, ext3.

"rw" means that you can Read and Write to those partitions, so in principle, you shouldn't have any problems, most of the work is done. 

I believe you said you were good in windows, good. Think, what would you do in windows to go to a partition? Exactly, open a file browser and look for those places (mount points, like /media/whatever/) and try to do things there. If you can't, it's just a matter of permissions, something you can change with the command "chmod", run as super user (this is, typing sudo before the command). Obviously, a google search for "chmod" won't hurt either.

One more thing. I know you're used to do all sort of things everywhere in your windows system...forget about it. Here you are to be more careful, after all, you don't want to end up with an useless OS after you broke it, yeah? What I mean is that you don't have much to do--in principle--in the root partition; leave as it is, nice and clean. You've got your kingdom, where you can move, create, delete things to your taste and split on the ground, so stay there for as much as you can. I'm talking about your /home partition, of course.

The very last thing. I'm not any sure about how you are planning to make windows happy in that ext3 partition. It's been a while since I don't fiddle around with MS, but I would swear that it won't like it that much...Usually you want to install windows first.

And be curious, experiment by yourself, try things, don't let yourself down if you don't understand something, move to something else instead...

Have fun!

---

### Post by discmaster on 2007-05-12
Hi nubutu,

Very nice post, good read! I understand all that you are saying & I surely appreciate it very much! I guess my problem(s) is this, as I stated earlier somewhere: 

You mentioned about doing research & reading up on linux, i.e. ubuntu in this case. Well that is part of the problem. The wikis, forums, & other sources do contain very useful info.,

 & once in awhile I will stumble across something, but unfortunately, there does not seem to be a good "user guide" anywhere to get a fellow started in this. 

Coming from a highly GUI windows environment over to ubuntu command line is intimidating  enough, but then after fighting thru partitioning, doing the install & finally getting to a desktop only to find that the drives/p[partitions can't be accessed/ written to without cli/ terminal window involvement?

That is _not_ user friendly, lol .

Don't get me wrong, however; I did not mean to be bashing linux  in my previous post or this one; I am merely asking for help out of desperation from spending alot of hours behind the keyboard accomplishing nothing!

I am willing to learn, want to learn, definantly like the concept of using linux (free, more secure than windows, etc.), but as mentioned, a good tutorial would be very helpful. 

I can tell you know your stuff, you have the experience & I appreciate your replies to my "elementary, newb. questions"!

Maybe someday I will be there too!

While we're at it, what do you think about this?
> sda1 ext3 media/disk (primary)
sda2 ext3 media/disk-1 (primary)
sda3 ext3 media/disk-2 (primary) (this will be home partition)
sda4 extended
sda5 linux-swap
sda6 ext3 (data partition)

(swap & data are in the extended partition)

Here again, my newb. status will shine thru! Why is only sda 1 & 6 visible to me? It seems to me that all partitions should be displayed in either computer or on the desktop?

Again, thanks very much!!! :grin:

---

### Post by nubutu on 2007-05-12
No, no, no. I only know I know nothing, as Socrates said. I just happened to be here some time before you. It's a matter of chance, it could easily be all the way round. And I anyway don't know much, seriously.

Er...I know exactly how you feel, for the same happen to me when I tried linux for the first time. Thousands of tutorials but it seemed that none of them were quite the right ones for what I wanted to know. You end up like you're doing, progressing step by step, taking some piece of information from this how-to, another from some post in a lost thread of a lost distro, etc...I actually left my first attempt for some months after a bad experience with SuSe...

Anyway, I don't quite understand what do you want us to check out of those lines. What do I think? Fine, I suppose, unless you say there's something wrong with them, which I don't know what it is. 

Do not make assumptions, I know, I know, but just don't: why would you want to have an icon in your desktop for every partition you have? And if you have, like me, 7 partitions (not counting swap and extended)? Would I want all that junk on top of my beautiful wallpaper? Jeeez, I don't even mount all of them at boot time! Of course, you're free to do what you prefer, but you're not gonna tell me now that you're one of those persons who double-click on "My Computer" to open the picture of your dog, are you? You do know what "Windows Explorer" is, don't you? 

Your partitions look right to me, and you will be surprised of how many things you can do without touching the terminal. Do me a favour, open Nautilus--the default file browser for Gnome--from wherever you like ("Places" from the menu will do), and take a tour to your system, nosing around, checking what can you actually do and what can you not. Pay special attention at what actions you are allowed to do in each of the partitions you created, and try to make some sense out of it by checking the files' permissions (I believe you can do this with a mouse right click). 

You will then post back and say "you rotten *******!, I told you I couldn't write to my sda½#$ and I'm stuck cause this is not windows!", so I will tell you that to change the permissions of a file you have to type

sudo chmod 700 /path_to_your_file  (this will give the owner of the file divine powers, and bread & circus for the rest of the world; again, do some research about this topic for there are many different possibilities you can play with)

Then I will tell you to carefully read one of my previous posts and to try to adjust the configuration of Gnome, which is, likely, the desktop manager you are using (more information about desktop managers in the usual place). I'll also tell you to type, in a terminal:

gconf-editor

and to adjust the key I mentioned some hours ago, and if that does not work, before you say anything I'll tell you to type:

volume icons desktop gnome

in the search window of your favorite internet browser, and see what it comes about with.

In short, you're almost there, so hot that it burns. Better said, you're already there, only that you're now already trying to understand what you've got in your hands, what the boundaries are and what possibilities are for you available. Enjoy your trip!

PS. I seriously hope that you are not in the same time zone as I am, otherwise we've got not one, but two psychos in front of the bloody screen.

---

### Post by discmaster on 2007-05-13
nubutu, I believe you may be my twin brother separated at birth! :lolflag: 

Again, another good post, thanks for taking the time to write. I would say you have me figured out pretty well. 

> I actually left my first attempt for some months after a bad experience with SuSe... Similar deal here. I installed 64 bit vers. first, when 7.04 was first released. (I have an AMD 64 pc, so I thought that was correct.)

Nothing but troubles, again with the write access drive thing, most browser plugins weren't installed by default, (they seem to be with the 32 bit vers.) Thunderbird mail didn't work right, & a list of other things that were not going well.

So I am sure you can see the source of my frustration, esp. since it is fueled by the lack of usable tutorials - not saying there aren't good ones out there, I just can't seem to locate the proper ones.

As I mentioned before, the nice thing about windows, esp. these later versions, is that "it just works", pretty much right out of the box. 

To an experienced windows user, it seems very strange to me, for example, to quote my prev. post; That when you first install & boot up, you can't access the drives. I'm not really asking for everything to be a "point & click" icon, but that drive thing is going to throw any newbie for a loop!

I know, comparing apples & oranges I guess! At any rate, I plan on sticking with it, I suppose. I didn't come this far to back out now, but hurdles like these ,when there seems to be no guides through it makes a guy think twice about continuing!

BTW, I have been google-ing all over the place this whole time, looking for answers, but again, mostly my fault, because as the newb. status goes, I don't even know what I'm looking for! lol

:biggrin:

---

