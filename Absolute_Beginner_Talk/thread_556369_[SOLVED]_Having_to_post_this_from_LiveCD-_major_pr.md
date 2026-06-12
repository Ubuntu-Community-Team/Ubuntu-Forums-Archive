---
title: "[SOLVED] Having to post this from LiveCD- major probs cant boot, need help"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-21
Here I am posting this from the livecd. Thank god for it eh.

Last night I was trying to drop a file onto cdrw and system froze so had to button it. When I tried to boot it drops out and runs fsck every time. Finds same errors.So then i run fsck -v fix the errors get to pass5 all clean back to prompt. gdm command doesn't work. Have to ctrl d.  Stuck in this continuous cycle. Tried diff kernel and diagnostic - same thing.

1. need to back up/copy my home folder from my ubuntu HD to my other windoze drive. I dont know how to get permissions etc.

2 need to fix my system?

---

### Post by NIT006.5 on 2007-09-21
I had a very similar experience with a Fedora server a few months ago. Never did figure out what the problem was and ended up reinstalling at around 3am just to get us up and running again. Hope you win though.

---

### Post by Dr Small on 2007-09-21
Did you try:
```
fsck /dev/xxx
```

xxx = the location of your hard drive
Example. Mine is sda3

---

### Post by philinux on 2007-09-21
Here is output 
ubuntu@ubuntu:~$ sudo fsck /dev/hda1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: clean, 157389/14548992 files, 5184767/29071617 blocks

However when I reboot fsck starts to run after a quarter way through boot and starts reporting errors.

1. need to back up/copy my home folder from my ubuntu HD to my other windoze drive. I dont know how to get permissions etc from the livecd

---

### Post by Bothered on 2007-09-21
Could you post the errors you're getting - maybe write them down?

---

### Post by philinux on 2007-09-21
/dev/hda1 unexpected inconsistency
fsck died error status 4
automatic check failed.

Error reading block 14057978 (Attempt to read block from filesystem resulted in short read) while doing inode scan
It goes from 14057978 - 14057985. But I can force rewrite and get a clean system by  sudo fsck -y -f -v /dev/hda1
Then now I get
sudo e2fsck  /dev/hda1 
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda1: clean, 157389/14548992 files, 5184767/29071617 blocks

But if I reboot it starts over again

---

### Post by SpiritIsReality on 2007-09-21
howdy

error 4
[http://www.google.com/custom?hl=en&client=pub-7825705102693166&channel=3833691868&cof=FORID%3A1%3BAH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fcoop%2Fimages%2Fgoogle_custom_search_sm.gif%3BLH%3A55%3BLP%3A1%3BGFNT%3A%23666666%3BDIV%3A%23cccccc%3B&adkw=AELymgU4FlscxlaHddDbXldhort3gmkgUPfpE-6mOr8-1wp6tRWqBgVPpd5hQRg6eD82dncUmHOIQt1VYarHY-XkF4J_itJJRkwqy4VZ4HrzUWs9iVnaCezcCl7K-5L9HIErxgpHC7ZrZtI9XU1SsAaqSeubpug5zp_ZEhUwI0mKuRZf-6_ablpMKcSL_O-5RH0XZUQUIKipAYcVTE8aoWDw-A817DO27Q&q=fsck+%2B%28%22error+4%22+%7C+%22+error+status+4%22%29&btnG=Search&cx=002165917076592449621%3Ay8jmiivon3o](http://www.google.com/custom?hl=en&client=pub-7825705102693166&channel=3833691868&cof=FORID%3A1%3BAH%3Aleft%3BCX%3ALinux%2520search%2520Engine%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fcoop%2Fimages%2Fgoogle_custom_search_sm.gif%3BLH%3A55%3BLP%3A1%3BGFNT%3A%23666666%3BDIV%3A%23cccccc%3B&adkw=AELymgU4FlscxlaHddDbXldhort3gmkgUPfpE-6mOr8-1wp6tRWqBgVPpd5hQRg6eD82dncUmHOIQt1VYarHY-XkF4J_itJJRkwqy4VZ4HrzUWs9iVnaCezcCl7K-5L9HIErxgpHC7ZrZtI9XU1SsAaqSeubpug5zp_ZEhUwI0mKuRZf-6_ablpMKcSL_O-5RH0XZUQUIKipAYcVTE8aoWDw-A817DO27Q&q=fsck+%2B%28%22error+4%22+%7C+%22+error+status+4%22%29&btnG=Search&cx=002165917076592449621%3Ay8jmiivon3o)
[http://www.google.ca/search?hl=en&q=linux+fsck+%2B%28%22error+4%22+%7C+%22error+status+4%22%29&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+fsck+%2B%28%22error+4%22+%7C+%22error+status+4%22%29&btnG=Google+Search&meta=)

live cd  root permissions
[http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+livecd+root+permissions&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+livecd+root+permissions&btnG=Google+Search&meta=)
[https://lists.ubuntu.com/archives/ubuntu-users/2006-January/062880.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-January/062880.html)

oh, and this one was humurous (humour easier seen once the problem is solved of course)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22error+status+4%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22error+status+4%22&btnG=Search&meta=)

hopin' for [solved]
trails

---

### Post by philinux on 2007-09-21
Nope still fails to boot with fsck. Keep fixing errors and get clean pass but on reboot it finds em agin!

---

### Post by SpiritIsReality on 2007-09-21
as far as root on the live cd, it looks like sudo -i should work but I have yet to try it.
[http://calypso.tux.org/pipermail/ma-linux/2006-December/000169.html](http://calypso.tux.org/pipermail/ma-linux/2006-December/000169.html)
bottom of this RootSudo page, (you didn't hear this from me)
[https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

on the site aboutdebian.com he recommends using the fsck command like so, it has worked for
me once when  lightning cut the power.
[http://www.google.ca/search?hl=en&q=site%3Aaboutdebian.com+fsck&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aaboutdebian.com+fsck&btnG=Google+Search&meta=)
(I use the click edit at top of firefox, click find in this page, enter fsck in box at bottom of window)
I ran it from a different linux partition, with the partition being fsck'd not mounted
should work from the live cd with the sudo -i  or sudo su or sudo -s hopefully
trails

---

### Post by graigsmith on 2007-09-21
do you have seperate partitions? 

a home partition? and a / partition?

if not. then you COULD use the live cd to resize the main partition, and create a second partition just for /home.  and then reinstall on the first drive.  

i think gparted  is the one you should use to change the partition sizes.  I'm not sure if it's on the live cd, if it's not you can use synaptic to get it.   and you know you should have a backup before trying a partition move like this.

once you have a seperate home and / partition you can easily reinstall on /, and it wont mess up your home partition. just make sure the format option is deselected on home when you reinstall. you dont want to format it. that wipes the disk.

---

### Post by SpiritIsReality on 2007-09-21
a thought
it could be possible to use the gparted live cd, create a small(maybe 3G) partition, shrink the 
ubuntu partition or a data partition if needed to.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
then install a linux to the small partition. hopefully can reboot the rig? if it's your windows partition
causing the probs, it would be good to, when installing, to not let that partition have an auto
mount point.
oh oh, another thought, maybe you could use the live cd, in /etc/fstab, comment out the partition where your windows is on, so it won't try to auto mount, then reboot.

I'll head back to the cactus now
trails

---

### Post by SpiritIsReality on 2007-09-21
oops, I got beat to the punch

graigsmith ...thanks

there's probably a super grub disk somethingorotherplan that might work here too.
[http://www.google.ca/search?hl=en&q=site%3Ausers.bigpond.net.au%2Fhermanzone+supergrub&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ausers.bigpond.net.au%2Fhermanzone+supergrub&btnG=Search&meta=)
no that's dumb, it's booting, isn't it.

LowSky ...thanks

________________
praise the lord,... and pass around the ammo and internet

---

### Post by LowSky on 2007-09-21
if the files you need to move are small, why noot upload them to you email clients  (yahoo or gmail or whaever) servers for a little bit, then re-install then grab  them

---

### Post by SpiritIsReality on 2007-09-21
If'n I was me, I'd try bumping this or reposting at a prime guru hour...whenever that is.
an op title that a guru couldn't resist....hmmm,
like a bucket of oats to a horse...but wild horses don't know oats from...
they know mares though...haha!
what's torvald's address again?
does richard stallman have a cell phone?
where does the upper echelon reside...it's some irc or mailing list isn't it?

trails

---

### Post by philinux on 2007-09-21
Thanks f ore replies so far Im away from machine now so will try the suggestions. 
By the way my home is just /home folder 2.8 gig I think so I would like to back it up before I really tinker around.

---

### Post by bliffle on 2007-09-21
You can backup a 2.8g partition on a USB stick, a DVD or in a partition on another HDD, like maybe an HDD in a USB box. Or even on one of your regular HDDs if you have a safe place.

---

### Post by Pumalite on 2007-09-21
Get a Knoppix Live CD: [http://www.knoppix.org/](http://www.knoppix.org/), boot from it (mounts all partitions, drives automatically), in the terminal you'll be root. From there save your data to external drive, dvd's, etc. Then use Gparted to reformat and repartition your hard drive and then do your installations.
Use rescuecd: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download) to check your drive.
Hope it helps.

---

### Post by philinux on 2007-09-23
Stiil cant boot locked into cycle of correcting errors with fsck only for it  to find same errors on reboot.:(

---

### Post by philinux on 2007-09-23
bump -posting this from knoppix live cd - tried everything

---

### Post by Pumalite on 2007-09-23
Make sure you are not trying to install in 'unallocated space'.Were you able to partition with Gparted?. Did you use rescuecd to check your drives?

---

### Post by philinux on 2007-09-23
Not got any cdr's left, been trying varios fsck options but it keeps correcting errors the refinding them on reboot. Going to get some tomoz and burn rescuecd to try that.

i read I need to delete contents of lost+found but when running live cd it says its a locked folder. What I really need now is how to access lost+found from live cd?

---

### Post by Pumalite on 2007-09-23
Boot Live CD
Mount your partition
At the terminal:
sudo chmod 777 /path/to/lost+found

---

### Post by philinux on 2007-09-23
ok I'm in m$ windoze (arrgghhhh) at the moment will that need a reversal if and when i get my ubuntu back.

also if I run gparted and create a /home partition and copy my home folder to it will/how a new install pick it all up?

Delay coming booting to live cd.

---

### Post by philinux on 2007-09-23
ok got live cd up. 

1. how do I get access to locked folder lost+found

2. how do I create a /home partition with gparted

---

### Post by EchoBeach on 2007-09-23
Hi Phil
Did you find 'lost+found' and try pumalite's chmod suggestion?
Echo

---

### Post by philinux on 2007-09-23
er no nobody seems to know how to give full access to hda1 from the live cd  :confused:

---

### Post by EchoBeach on 2007-09-23
When you use Knoppix (3.8), you mount the drive and then right-click on the drive icon and there should be an option to switch to read/write (toggle with read-only).
Echo

---

### Post by Pumalite on 2007-09-23
If you cannot mount the partition, get a Knoppix Live CD (it will do it automatically for you): [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by philinux on 2007-09-23
> **EchoBeach said:**
> When you use Knoppix (3.8), you mount the drive and then right-click on the drive icon and there should be an option to switch to read/write (toggle with read-only).
Echo

Done that but lost+found is marked locked even after changing switch
also using gparted comes up with error - guess what - use fsck errors on disk use fsck -v ect do that still cant do anything

need to delete contents of lost+found on hda1 from the live cd I think this might be the key . but need permissions

---

### Post by philinux on 2007-09-23
I'm a bit dismayed no admins have not chimed in with a solution

---

### Post by SpiritIsReality on 2007-09-23
Pumalite ... said to try this
> %
ubuntu@ubuntu:~$ mkdir /mnt/hdb9
mkdir: cannot create directory `/mnt/hdb9': Permission denied
ubuntu@ubuntu:~$ sudo mkdir /mnt/hdb9
ubuntu@ubuntu:~$ mount /dev/hdb9 /mnt/hdb9
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount /dev/hdb9 /mnt/hdb9
ubuntu@ubuntu:~$ cd /mnt/hdb9/
ubuntu@ubuntu:/mnt/hdb9$ ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
ubuntu@ubuntu:/mnt/hdb9$ cd lost+found
bash: cd: lost+found: Permission denied
ubuntu@ubuntu:/mnt/hdb9$ sudo cd lost+found
sudo: cd: command not found
ubuntu@ubuntu:/mnt/hdb9$ ls -la
total 148
drwxr-xr-x  21 root root  4096 2007-07-25 00:58 .
drwxr-xr-x   3 root root    60 2007-09-24 00:12 ..
drwxr-xr-x   2 root root  4096 2007-08-03 01:35 bin
drwxr-xr-x   3 root root  4096 2007-08-03 01:44 boot
lrwxrwxrwx   1 root root    11 2007-06-17 13:49 cdrom -> media/cdrom
drwxr-xr-x  12 root root 40960 2007-08-03 01:44 dev
drwxr-xr-x 117 root root 12288 2007-09-16 14:06 etc
drwxr-xr-x   3 root root  4096 2007-06-17 14:45 home
drwxr-xr-x   2 root root  4096 2007-06-17 13:51 initrd
lrwxrwxrwx   1 root root    32 2007-07-25 00:58 initrd.img -> boot/initrd.img-2.6.22-8-generic
lrwxrwxrwx   1 root root    28 2007-07-25 00:57 initrd.img.old -> boot/initrd.img-2.6.22-8-386
drwxr-xr-x  17 root root 12288 2007-08-03 01:35 lib
drwx------   2 root root 16384 2007-06-17 13:48 lost+found
drwxr-xr-x  12 root root  4096 2007-09-16 14:00 media
drwxr-xr-x   7 root root  4096 2007-07-22 01:11 mnt
drwxr-xr-x   2 root root  4096 2007-06-17 13:51 opt
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 proc
-rw-------   1 root root  1024 2007-06-17 14:12 .rnd
drwxr-xr-x  11 root root  4096 2007-07-10 18:11 root
drwxr-xr-x   2 root root  4096 2007-08-03 01:40 sbin
drwxr-xr-x   2 root root  4096 2007-06-17 13:51 srv
drwxr-xr-x   2 root root  4096 2007-04-10 21:45 sys
drwxrwxrwt   6 root root  4096 2007-09-16 14:06 tmp
drwxr-xr-x  12 root root  4096 2007-07-20 15:46 usr
drwxr-xr-x  15 root root  4096 2007-06-17 14:19 var
lrwxrwxrwx   1 root root    29 2007-07-25 00:58 vmlinuz -> boot/vmlinuz-2.6.22-8-generic
lrwxrwxrwx   1 root root    25 2007-07-25 00:57 vmlinuz.old -> boot/vmlinuz-2.6.22-8-386
ubuntu@ubuntu:/mnt/hdb9$ sudo chmod 777 lost+found
ubuntu@ubuntu:/mnt/hdb9$ ls -la
total 148
drwxr-xr-x  21 root root  4096 2007-07-25 00:58 .
drwxr-xr-x   3 root root    60 2007-09-24 00:12 ..
drwxr-xr-x   2 root root  4096 2007-08-03 01:35 bin
drwxr-xr-x   3 root root  4096 2007-08-03 01:44 boot
lrwxrwxrwx   1 root root    11 2007-06-17 13:49 cdrom -> media/cdrom
drwxr-xr-x  12 root root 40960 2007-08-03 01:44 dev
drwxr-xr-x 117 root root 12288 2007-09-16 14:06 etc
drwxr-xr-x   3 root root  4096 2007-06-17 14:45 home
drwxr-xr-x   2 root root  4096 2007-06-17 13:51 initrd
lrwxrwxrwx   1 root root    32 2007-07-25 00:58 initrd.img -> boot/initrd.img-2.6.22-8-generic
lrwxrwxrwx   1 root root    28 2007-07-25 00:57 initrd.img.old -> boot/initrd.img-2.6.22-8-386
drwxr-xr-x  17 root root 12288 2007-08-03 01:35 lib
drwxrwxrwx   2 root root 16384 2007-06-17 13:48 lost+found
drwxr-xr-x  12 root root  4096 2007-09-16 14:00 media
drwxr-xr-x   7 root root  4096 2007-07-22 01:11 mnt
drwxr-xr-x   2 root root  4096 2007-06-17 13:51 opt
drwxr-xr-x   2 root root  4096 2007-04-12 09:11 proc
-rw-------   1 root root  1024 2007-06-17 14:12 .rnd
drwxr-xr-x  11 root root  4096 2007-07-10 18:11 root
drwxr-xr-x   2 root root  4096 2007-08-03 01:40 sbin
drwxr-xr-x   2 root root  4096 2007-06-17 13:51 srv
drwxr-xr-x   2 root root  4096 2007-04-10 21:45 sys
drwxrwxrwt   6 root root  4096 2007-09-16 14:06 tmp
drwxr-xr-x  12 root root  4096 2007-07-20 15:46 usr
drwxr-xr-x  15 root root  4096 2007-06-17 14:19 var
lrwxrwxrwx   1 root root    29 2007-07-25 00:58 vmlinuz -> boot/vmlinuz-2.6.22-8-generic
lrwxrwxrwx   1 root root    25 2007-07-25 00:57 vmlinuz.old -> boot/vmlinuz-2.6.22-8-386
ubuntu@ubuntu:/mnt/hdb9$ cd lost+found
ubuntu@ubuntu:/mnt/hdb9/lost+found$ ls
ubuntu@ubuntu:/mnt/hdb9/lost+found$could 
sudo rm <any file in the lost+found>
don't you think?
my ubuntu partition is hdb9 you will have to replace that with yours```
sudo fdisk -l
```after removing files in lost+found and ready to reboot, unmount the ubuntu partition,
```
cd
``` to the ubuntu live cd home, then
```
sudo umount /dev/hdb9
```replace hdb9 with your partition
(sorry, don't know how to do the scroll bar window yet)
there's probably a gui way, but I couldn't get it
a suggestion:time spent at [http://linuxcommand.org](http://linuxcommand.org) is well worth it

---

### Post by philinux on 2007-09-24
ok sudo chmod 777 lost+found got me in but there was nothing in there DOH.

antway it was worth checking cos apparantly fsck writes info into there about recovered files.

Situation now - tried to run gparted to create /home partition but it says disk has errors run fsck arrrgghhh

HELP....

---

### Post by SpiritIsReality on 2007-09-24
howdy
the next step seems to be to find out how to use the [www.sysresccd.org](www.sysresccd.org) to check the hard drive.under, system tools included, test-disk?
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
the manual page for [www.sysresccd.org](www.sysresccd.org)
[http://www.sysresccd.org/Manual.en.php](http://www.sysresccd.org/Manual.en.php)

this is one of those ' "opportunities to learn" dressed in wolf's clothing' . some gnu/linux authors 
use this kind of statement to try and encourage us through times like this....
you got any cd-r or cd-rw yet?
man if we knew what we were doing, I could probably send the rescue cd to you over the internet and you could install it onto your hard drive or something wild like that....ok, back to the cactus...well, you might be able to do that?

trails

---

### Post by SpiritIsReality on 2007-09-24
do you have a knoppix live cd made yet? it says here that test-disk is on it
[http://www.cgsecurity.org/wiki/Damaged_Hard_Disk](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk)
course I don't know if this is the answer or not...just going up this hill to have a look at
the other hills...haha! (ahem..ok)
edit: looks like it might be an idea to get a walk thru on checking the hard drive from somebody.
back to the cactus for me. I'm with you on your #30 post
trails

---

### Post by SpiritIsReality on 2007-09-24
ok
I looked at these sites here, and it looks like a new thread would be good, this one has
solved some things, but is getting long enough that it's a negetive to someone to have to
read it all in order to come up to speed with the problem. Their time is rationed/valuable...understandable
aysiu recommends looking at this
[http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)
and I looked at some of the main headings here
[http://www.catb.org/~esr/faqs/smart-questions.html#id272405](http://www.catb.org/~esr/faqs/smart-questions.html#id272405)

I'll leave it up to you to figure out the details.
besides another good heading for your new post, if you decide to make one,
what  might be good is a screenshot of the error message.
or maybe better yet is to hightlight the error message on your screen, (hold left mouse
button down and drag it along the words, release the left button, right click the selected
(highlighted) words, choose copy. 
then in your post you can type [ quote ] with no spaces between [ and q, and e and ]
then left click to get a cursor, then right click the cursor, click paste, then at the end of
the pasted text, type the following, with no spaces, [ /quote]
or type the error message in if it's on a virtual terminal.
sorry, I don't know if you know this or not, I just got it from here, it's called bulletin board code
[http://www.google.ca/search?hl=en&q=bbcode&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=bbcode&btnG=Google+Search&meta=)
[http://www.google.ca/search?q=how+to+use+bbcode&revid=801427859&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=3](http://www.google.ca/search?q=how+to+use+bbcode&revid=801427859&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=3)
maybe can mention what you have tried as far as fsck again.
how that turned out.
maybe ask what logs to check, and if,  how to set the debugging level
which is beyond me right now.
if you're advised to check the hard drive, you could respond by asking how that's done. 
for example, when 
Pumalite said to use the sysresccd.org to check the drive.
all the best
trails

I see you're right after it. cheers
[http://ubuntuforums.org/showthread.php?t=558882](http://ubuntuforums.org/showthread.php?t=558882)
[http://ubuntuforums.org/showthread.php?t=558777](http://ubuntuforums.org/showthread.php?t=558777)


>permissions when copying files to your /home.
ubuntu linux bible says, and man umask, that your files will have that permission set automatically
just type umask at the prompt and it says ours is 0022, so permissions will be for files, 0644, -rw-r--r--
and directories 0755, drwxr-xr-x. the umask is subtracted from 0777for directories, 0666 for files. 
 I heard you have to make sure to copy the files with a . (dot) in front of them, the hidden files
when copying your /home partition. not sure how yet.
>copying /home ... I think sudo cp -r will work for the hidden files.
if you are using the gui, and selecting and sending, or dragging and dropping
I think you have to select "show hidden files" to make sure they're listed in the window

---

### Post by SpiritIsReality on 2007-09-24
how's it goin'  pard

---

### Post by philinux on 2007-09-24
Hi fmat,

tried knoppix testdisk no improvement. Back to ubuntu live cd

The reason my home folder was big was cos trash had some stuff in but report empty, anyway got rid of that now. Live cd reports my home directory is now 90 meg. At this moment only got one spare cd rw formated incd. But cant drop files on it permissions all wrong. CD/DVD creator wont perform either from live cd. Must be doin something wrong.

anyway off in to town tomoz and will pick up some blank cdr's.

Once home backed up wil reinstall.

---

### Post by SpiritIsReality on 2007-09-24
good to hear you've got a plan. the job's half done when you've got a good plan.
I'll work a bit with the ubuntu live cd and see if I can get the gui to copy to cdrw.
the cdrw disks are good, cause you can use them over and over, 
the pII here  doesn't read cdrw, just cd-r disks. 
the pIII I'm using now will read both.

trails

---

### Post by SpiritIsReality on 2007-09-24
howdy
knoppix live cd, and using k3b works.
I can tell you about how it worked out if you have trouble.
trails.

---

### Post by SpiritIsReality on 2007-09-25
howdy
found this about runnin' a knoppix cd for system recovery
[http://www.ibm.com/developerworks/linux/library/l-knopx.html](http://www.ibm.com/developerworks/linux/library/l-knopx.html)

trails.

---

### Post by philinux on 2007-09-30
Al sorted apart from installing missing progs. Used a 4 gig pen drive to back up and restore home folder. I'm off to psychocats  to create a home partition.

---

### Post by SpiritIsReality on 2007-09-30
howdy
good to hear. that was a rough ride.
a brand new shiny /home
all the best
buds:popcorn:=D>

---

