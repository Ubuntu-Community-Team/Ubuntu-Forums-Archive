---
title: "I gave my swap-partition the wrong name"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-06-05
Hi!
When I installed Ubuntu I selected manual partitioning. I named one partition "swap" because i had learned that Ubuntu needs this. I got an error message telling me that I was hadn't made a swap partition yet, but eager as I was I ignored this message. Now I have learned the importance of the swap partition, and I now know that it should be named "linux-swap", instead of only "swap". As I now have used my computer much since I installed Ubuntu, I don't want to start all over again with a completely fresh install. Therefore I wonder if there's any way to change this partition of mine? How can I tell my computer to use this partition as swap without installing Ubuntu from scratch? And, do I need to resize it as well? How? At this time it is 2 gb.

Thanks!
Joakim

Ps. Please bear in mind that I'm still a newbie. :)

---

### Post by jonward0690 on 2007-06-05
Well you can go back into the live cd and do this or use gpartitoner.

---

### Post by dstew on 2007-06-05
You can make a new swap partition without re-installing Ubuntu. The size should be about twice your RAM size, so if you have 512 Mb RAM, a 1 Gb swap partition would be right.

First, you have to create the partition. To do this, boot from the Live CD or boot a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). You have to boot from a CD because you cannot re-partition a disk that is in use. Open the partition editor gparted, and delete the old "swap" partition. Create a new partition and format it as type "linux-swap". Then quit GParted, take out the CD, and reboot.

Once you are in your regular Ubuntu system, enter **sudo fdisk -l** to show a list of the partitions. You should now see the new swap partition there. Look at the name of the partition, and use it in the command```
sudo mkswap **<device>**
```where **<device>** is the name of the partition, for example, dev/sda2. Finally, add the swap partition to the /etc/fstab file:```
sudo nano /etc/fstab
```Put this line at the end of the fstab file:```
**<device>** swap swap defaults 0 0
```Again, substitute the device name of the swap partition in the line. Save the file, quit the editor (ctrl-X, or ^X in nano's language). Reboot and you should be good to go.

---

### Post by Joakim Stokland on 2007-06-05
Thanks so far :)
I tried to reformat the swap partition when I was logged on, before I got your reply, dstew. I rebooted and got an error message with something about "fsck died with exit status 8". (I am now using my girlfriend's computer)
So I tried to boot from the cd, and reformatted the swap partition again (right clicked on it and selected format as linux-swap). Then I rebooted into recovery mode, typed your commands and rebooted. I got the same error message, but I had noticed that /dev/sda6 (my swap) already was mentioned in fstab, so I tried to put a # in front of the line that already was there.
When I now rebooted I got the login screen as usual, but when I tried to log in I got a new error message. My home folder doesn't appear to exist... It asked if I wanted to log in using root as my home folder. Clicking yes brings another error message, telling me that the session only lasted for 10 seconds, and the login screen appears again.
What do I do now? :(

---

### Post by dstew on 2007-06-05
Boot the live CD, and post on the forum the output of **sudo fdisk -l**

---

### Post by Joakim Stokland on 2007-06-05
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        7905    51200000    7  HPFS/NTFS
/dev/sda3            7906       14593    53721360    5  Extended
/dev/sda5            7906        7916       88326   83  Linux
/dev/sda6            7917        8165     2000061   82  Linux swap / Solaris
/dev/sda7            8166       11812    29294496   83  Linux
/dev/sda8           11813       14593    22338351   83  Linux

Just for information, /dev/sda1 is a recovery partition, from factory.

---

### Post by Rui Pais on 2007-06-05
hi, just 2 questions, 
your fstab uses UUIDs or the path /dev/sda6 to point to swap?

And do you only format you partition or deleted and remake one on empty space? Some times this 2nd way changes/mix partition numeration and can make a mess if /etc/fstab uses paths with /dev/.


Can you post your /etc/fstab, please?

---

### Post by Joakim Stokland on 2007-06-05
Sorry, didnt quite understand your question about UUIDs and paths, but I tried to format my original `swap`-partition as linux-swap from gparted. Sorry if I write odd now, but my keybord isnt norwegian anymore when I boot from the cd, so I cant find all the correct buttons... 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=886aa9f6-5ca8-4d2b-80f4-bd11789d7bf7 /               reiserfs defaults        0       1
# /dev/sda5
UUID=a4943a22-0c42-4461-9b2e-4c77f381a856 /boot           ext3    defaults        0       2
# /dev/sda8
UUID=09a20645-1186-465d-b2df-e8cbcd1e3c99 /home           reiserfs defaults        0       2
# /dev/sda1
UUID=E0F84FDCF84FB018 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=84FA5246FA523520 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
#UUID=86281c3d-39dc-46de-92b4-36a99a83f441 /swap           reiserfs defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda6 swap swap defaults 0 0

---

### Post by Rui Pais on 2007-06-05
No prob :)

is that your really /etc/fstab on HD or the one you get from liveCD? 
I assume it was the later case (correct me if i'm wrong) 
Thats an example of mix config. Some partitions are referred using the unique UUID and others by the name that kernel give them (/dev/something) which is deprecated.

When you format a partition it's UUID changes and you need to change /etc/fstab too.

You seems to make some confusion with names and types.
names (labels?) of partition are irrelevant. To swaps even more. 
The important is that you must format swap as swap (seems that you make a partition named swap formated as reiserfs...)

And btw, you don't need to have a swap. It's better to have one, but Linux run without one normally.
Another thing it's not necessary to have twice the space of RAM as swap (you can even have none) thats an old rule from the times when RAM exists on expensive sticks with 32MB (lol) 
Nowadays, even with "only" 0.5G swap is hardly used by the system.

---

### Post by Joakim Stokland on 2007-06-05
I had to look abit around before I found this but, no, its from my hard drive. The fstab from the cd only contained one entry...
The reiserfs swap partition is the one I placed a # in front of, as you see. and this is the one that was created when I selected `format as linux-swap` in gparted. Or at least I suppose so.

Oh, and by the way, I didnt manage to delete the swap partition. Gparted told me to unmount all `devs` with numbers higher than 6. When I tried to unmount /dev/sda7. /dev/sda8 was mounted automatically and opposite. Therefore I chose the format as linux-swap option.

---

### Post by Rui Pais on 2007-06-05
ok, silly me ask about fstab. If it was the livecd HD partitions wouldn't be mounted with that mount points...

lets try to fix the /etc/fsab.

It's better to do this from a liveCD cause you may need copy paste text.

On a console type:
```
sudo vol_id -u /dev/sda6
```and
```
sudo vol_id -u /dev/sda8
```
it should give you the UUIDs of the partitions. 
Now check your /etc/fstab (from HD) 
the answer from sda8 is:
09a20645-1186-465d-b2df-e8cbcd1e3c99
?
If not it needs to be edit copy+paste from terminal the UUID to the line that have a /home.
swap can stay the way you put, and change later when you got your /home back.

If the UUID from command line is the same then the one you got on fstab, post here and we look for other issues.

---

### Post by Rui Pais on 2007-06-05
oops, and it's not
> **Joakim Stokland said:**
> 
/dev/sda6 swap swap defaults 0 0
but
```
/dev/sda6 **none** swap **sw** 0 0
```
or :
```
THE_CORRECT_UUID_HERE  none	swap	sw 	0 0
```

(i'm tired, sorry)

---

### Post by Joakim Stokland on 2007-06-05
ubuntu@ubuntu:~$ sudo vol_id -u /dev/sda6

72c58878-8014-48ce-8460-2a93cddcd4ec

ubuntu@ubuntu:~$ sudo vol_id -u /dev/sda8

09a20645-1186-465d-b2df-e8cbcd1e3c99

Seems like its correct...


What difference will the wrong code do* Will it help to change it to the correct code*
(Couldnt find question mark, so Im using * instead here ;))

I have to bail now guys. Gotta get up early tomorrow. Checking back tomorrow afternoon!
Thanks a lot for all your help so far! :D

---

### Post by Rui Pais on 2007-06-05
> **Joakim Stokland said:**
>  ...

Seems like its correct...


What difference will the wrong code do* Will it help to change it to the correct code*
(Couldnt find question mark, so Im using * instead here ;))

I have to bail now guys. Gotta get up early tomorrow. Checking back tomorrow afternoon!
Thanks a lot for all your help so far! :D

so it's another problem... 
wrong code will repost something like your error:"fsck died with exit status X" and fail to mount the partition... on case of swap will just not make any swap i think (maybe kernel its intelligent enough to mount even with some errors, not sure...)

It's late here too. 
When you got time, post the output of 
```
blkid 
```
so we can make sure that all is ok with fstab and start to try to search on other directions if needed.

Have a good night :)

---

### Post by Joakim Stokland on 2007-06-05
Guys! :D
I changed the code in fstab to "/dev/sda6 none swap sw 0 0", and now I can log on as usual! No errors, nothing wrong! :D

So, how do I check whether my swap partition works or not?
And can I delete the line in fstab with the reiserfs swap, which I put # in front of? How do I "clean up"?

And if you still want to know, blkid prints

/dev/sda1: TYPE="ntfs" 
/dev/sda2: TYPE="ntfs" 
/dev/sda5: UUID="a4943a22-0c42-4461-9b2e-4c77f381a856" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="72c58878-8014-48ce-8460-2a93cddcd4ec" TYPE="swap" 
/dev/sda7: UUID="886aa9f6-5ca8-4d2b-80f4-bd11789d7bf7" TYPE="reiserfs" 
/dev/sda8: UUID="09a20645-1186-465d-b2df-e8cbcd1e3c99" TYPE="reiserfs" 

TYPE="swap"? That seems correct, doesn't it? :)

Thanks again, and good night to you too :)

---

### Post by Rui Pais on 2007-06-06
> **Joakim Stokland said:**
> Guys! :D
I changed the code in fstab to "/dev/sda6 none swap sw 0 0", and now I can log on as usual! No errors, nothing wrong! :D 
So you managet to get it back :) 
Good!
It's was a simple thing all. 
When kernel started to mount your partition it goes until swap and ended the mountings with an error.
That's would not be a problem and your Linux would run without it, the problem was that happened before the /home partition mount was done. 
It abort the mounting of partitions before it trying to mount ***all*** in fstab, stopping at first error (not very smart, btw)
 
> **Joakim Stokland said:**
> 
So, how do I check whether my swap partition works or not?
And can I delete the line in fstab with the reiserfs swap, which I put # in front of? How do I "clean up"?

you can use:
```
free -m
``` it will say how much memory it uses (Swap line not zero means it's mounted and ok)

And you can delete that line (it's very wrong) and if you want, replace /dev/sad6 with 72c58878-8014-48ce-8460-2a93cddcd4ec, the UUID. Thats the correct and safe way (for example you may later add a partition that change numeration of partitions... )
> **Joakim Stokland said:**
> 
And if you still want to know, blkid prints

/dev/sda1: TYPE="ntfs" 
/dev/sda2: TYPE="ntfs" 
/dev/sda5: UUID="a4943a22-0c42-4461-9b2e-4c77f381a856" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="72c58878-8014-48ce-8460-2a93cddcd4ec" TYPE="swap" 
/dev/sda7: UUID="886aa9f6-5ca8-4d2b-80f4-bd11789d7bf7" TYPE="reiserfs" 
/dev/sda8: UUID="09a20645-1186-465d-b2df-e8cbcd1e3c99" TYPE="reiserfs" 

TYPE="swap"? That seems correct, doesn't it? :)

The most correct  it can be :) 


Have fun.

---

### Post by Joakim Stokland on 2007-06-06
I see! It all makes sense :)
But free -m prints:

             total       used       free     shared    buffers     cached
Mem:          1002        720        282          0         40        379
-/+ buffers/cache:        299        702
Swap:         1953          0       1953

It says that 0 is used... Or did you mean that total should not be 0? The swap partition won't be used as long as my computer has sufficient memory, right?

And I noticed that when I open media, i can see "swap" (under root folder) in the tree to the left. When I select properties for "swap" it says: 24,2gb out of 27,9gb is free (14%) used. But there are no files or sub folders.
How did this get there? Is it actually my swap-partition? And why is it so large?

---

### Post by Rui Pais on 2007-06-06
> **Joakim Stokland said:**
> I see! It all makes sense :)
But free -m prints:

             total       used       free     shared    buffers     cached
Mem:          1002        720        282          0         40        379
-/+ buffers/cache:        299        702
Swap:         1953          0       1953

It says that 0 is used... Or did you mean that total should not be 0? The swap partition won't be used as long as my computer has sufficient memory, right?
Precisely. And probably it will happen on rarely occasions and never more then a few megabytes. 
Thats why i said before that the rule "2xram" is obsolete these days. Our modern RAM are huge, your 1G is more then enough and Linux is excellent at manage it. But swap is needed, as example, for suspend... 

> 
And I noticed that when I open media, i can see "swap" (under root folder) in the tree to the left. When I select properties for "swap" it says: 24,2gb out of 27,9gb is free (14%) used. But there are no files or sub folders.
How did this get there? Is it actually my swap-partition? And why is it so large?

thats weird. do you mind to post the output of: 
```
df -h
```
please? 
(it should be the old mount point automaticaly maded by the installer, but its important know that nothing is mounted there)

---

### Post by Joakim Stokland on 2007-06-06
Great :)

Yep, here it is:

Filesystem            Size Used Avail Use% Mounted on
/dev/sda7              28G  3,8G   25G  14% /
varrun                502M  228K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  116K  501M   1% /proc/bus/usb
udev                  502M  116K  501M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda5              84M   33M   48M  41% /boot
/dev/sda8              22G  8,8G   13G  41% /home
/dev/sda1              12G  4,7G  7,1G  41% /media/sda1
/dev/sda2              49G   21G   29G  42% /media/sda2

---

### Post by Rui Pais on 2007-06-06
seems that all is alright.

Check (and delete) any line of /etc/fstab that contain a **/swap** (a bar **/**followed by the word swap)

then do: 
sudo rmdir /media/swap

then logout from gnome and do a login, or better a reboot to clean mtab and kernel reread fstab.

---

### Post by Rui Pais on 2007-06-06
sorry, an error on my previous instructions,
```
sudo rmdir /media/swap
```
just make a new post to get informed (i think edit wouldn't make a new mail warning)

---

### Post by Joakim Stokland on 2007-06-06
Well, in fstab there were two lines with swap mentioned; the line that gparted obviously created before my computer crashed (i had put # in front of this line, but removed it anyway) and, the one you asked me to put there (didn't remove this though).

swap is still in the tree after reboot... Should I try removing your line too?

Oh, and rm /media/swap just printed that the directory doesn't exist...

---

### Post by Rui Pais on 2007-06-06
> **Joakim Stokland said:**
> Well, in fstab there were two lines with swap mentioned; the line that gparted obviously created before my computer crashed (i had put # in front of this line, but removed it anyway) and, the one you asked me to put there (didn't remove this though).

swap is still in the tree after reboot... Should I try removing your line too?
No, no. Just lines with a **"/swap"** not the one with the word **"swap"** alone.
just a precaution, in case you have any besides the one commented and now deleted. 

> 
Oh, and rm /media/swap just printed that the directory doesn't exist...

please see my previous post (i give you the incorrect command is, rmdir, not rm :()

---

### Post by Joakim Stokland on 2007-06-06
Yeah, sorry, it was the rmdir command I used...

---

### Post by Joakim Stokland on 2007-06-06
and ls /media prints:
cdrom  cdrom0  sda1  sda2

Nothing more there...

---

### Post by Rui Pais on 2007-06-06
> **Joakim Stokland said:**
> and ls /media prints:
cdrom  cdrom0  sda1  sda2

Nothing more there...

Sorry, now i'm confused.
I thought that you said that it appear under media on nautilus... 
Ok, i reared your post. Seems that appear on tree when you use nautilus in browse mode... (i'm get it right?) 
i'm not sure how it goes there or what means. Maybe nautilus keep a record of previous mount points and still show it...

---

### Post by Joakim Stokland on 2007-06-06
Yes, you're right. Or, in Konqueror to be precise. I just referred to the menu option in Kubuntu (System menu > Storage media).

ls / prints:

bin    etc     initrd.img      mnt   sbin  tmp      vmlinuz.old
boot   files   initrd.img.old  opt   srv   usr
cdrom  home    lib             proc  **swap**  var
dev    initrd  media           root  sys   vmlinuz

Here you see "swap" listed...

---

### Post by Rui Pais on 2007-06-06
> **Joakim Stokland said:**
> Yes, you're right. Or, in Konqueror to be precise. I just referred to the menu option in Kubuntu (System menu > Storage media).

ls / prints:

bin    etc     initrd.img      mnt   sbin  tmp      vmlinuz.old
boot   files   initrd.img.old  opt   srv   usr
cdrom  home    lib             proc  **swap**  var
dev    initrd  media           root  sys   vmlinuz

Here you see "swap" listed...

ah, ok.
That folder was made by installer because you made a mount point for it, remember your old fstab it had a /swap explicit (silly me i was think in /media; i don't have KDE or Konqueror, i din't  knew the 'Storage media'...)  

So why it says that have that size probably cause its the size of root / partition. 
check if its empty (should be) and remove it is:
```
sudo rmdir /swap
```

If not empty what is inside?

---

### Post by Joakim Stokland on 2007-06-06
Yeah! I should have thought of that! :D I managed deleting it, there was nothing inside it. Now everything seem as it should be to me. Thanks a lot for all your help! :D
Guess I'll be back soon with other problems though ;) Thanks again! :)

---

### Post by Rui Pais on 2007-06-06
> **Joakim Stokland said:**
> Yeah! I should have thought of that! :D I managed deleting it, there was nothing inside it. Now everything seem as it should be to me. Thanks a lot for all your help! :D
Guess I'll be back soon with other problems though ;) Thanks again! :)

You will be welcome :)

Have fun around.

---

