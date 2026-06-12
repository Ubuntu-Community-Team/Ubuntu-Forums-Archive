---
title: "jus installd ubuntu but no cd plays &quot; unable to mount media&quot;"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by drshrikant on 2007-05-21
me in love with ubuntu already... but.. no cd from my drive is read givin msg unable to mount media... there is probably no media in the drive... please help me... im an absolute idiot otherwise about computing

---

### Post by drshrikant on 2007-05-21
when i add the disk mounter to the panel it is only for my floopy drive... but nothin frm my cd drive is playin.. im in urgent vneed... please help

---

### Post by darkworld on 2007-05-21
I can try but im a newbie too.  have you just done an installation? can you do the following and post results.

> cat /etc/fstab

then do
> 
ls -al /dev/cdrom*

then do

> ls -al /media

and please tell me what you are trying to play and in what?

---

### Post by drshrikant on 2007-05-21
hey.. thanks a lot for considerin... i'm in urgent need for help... heres what i got when i followed your instructions..

shrikant@shrikant-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f7b51862-b487-47ff-b26d-26054c4604bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=67a048ae-84f3-4353-9c95-145c60aaf5b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
shrikant@shrikant-desktop:~$ ls -al /dev/cdrom*
lrwxrwxrwx 1 root root 4 2007-05-20 23:25 /dev/cdrom -> scd0
shrikant@shrikant-desktop:~$ ls -al /media
total 16
drwxr-xr-x  4 root root 4096 2007-04-15 17:26 .
drwxr-xr-x 21 root root 4096 2007-05-20 13:06 ..
lrwxrwxrwx  1 root root    6 2007-05-20 12:33 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-05-20 12:33 cdrom0
lrwxrwxrwx  1 root root    7 2007-05-20 12:33 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2007-05-20 12:33 floppy0
--wxr-x---  1 root root    0 2007-04-15 17:26 .hal-mtab-lock
shrikant@shrikant-desktop:~$

---

### Post by drshrikant on 2007-05-21
the cd im tryin to play contains lectures that i used to play earlier using  winamp... and it contains notes in pdf format, please help:(

---

### Post by apienk01 on 2007-05-21
I suspect the disk was recorded using a newest UDF filesystem (eg. on Vista) which is not yet supported in Linux. I regret to say this, but your only option is to find a computer with Vista or BSD (also supports UDF 2.50), copy all the files to harddisk, and then burn them again to CD using standard ISO mode.

---

### Post by darkworld on 2007-05-21
ok from what I can see there its all linked up ok. I wondering about the formats on the cd. 

Ok what ever package you are trying to read these in check that its pointing to the /dev/cdrom in its settings or configuration or preferences. What package are you using.

also try this if you havent got installed.

system>administration>synaptic package manager>     then search for and instal these,  acroread , acroread-escript, acroplugins

How they run I dont know find in menus after installation....off to gym now....hope that helps

---

### Post by drshrikant on 2007-05-21
no help... no other cd also playin... even the ubuntu cd that i used for installin... all unable to mount... please please help.. cud not find acroread

---

### Post by apienk01 on 2007-05-21
reboot

---

### Post by jatan on 2007-05-21
> **apienk01 said:**
> reboot

same problem here. the cd does not read any data irrespective of the format. however if a cd is inserted at the time of booting then it is able to run perfectly.

---

### Post by apienk01 on 2007-05-21
Obviously your automounter has problems, but I don't know how to fix this. Just one idea: under Preferences/Removable Drives and Media check "Mount removable drives when hot-plugged", "Mount removable media when inserted", "Browse removable media when inserted".

---

### Post by nick24 on 2007-05-21
> **drshrikant said:**
> me in love with ubuntu already... but.. no cd from my drive is read givin msg unable to mount media... there is probably no media in the drive... please help me... im an absolute idiot otherwise about computing

If you just install Ubuntu, have you enable your restricted repositories and downloaded your goodies to play MP3 and such ? Ubuntu doesn't ship with third party proprietary codecs. But enabling these futures is a breeze . Please follow this link and am sure you will find your answer to this problem and many others you might have. 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) 

P.s welcome to the great Ubuntu community

---

### Post by jatan on 2007-05-21
> **apienk01 said:**
> Obviously your automounter has problems, but I don't know how to fix this. Just one idea: under Preferences/Removable Drives and Media check "Mount removable drives when hot-plugged", "Mount removable media when inserted", "Browse removable media when inserted".

All three are ticked on

---

### Post by drshrikant on 2007-05-21
have audacious installed... but no cd.. of any format playin... plz help... nothin workin

---

### Post by drshrikant on 2007-05-21
no answers for  crossed fingers...

---

### Post by mikeize on 2007-07-12
Any answers here yet?  I'm having the same problem running feisty with wubi on my dell laptop.  Drive is fine, since it works when I boot into win xp...  my /etc/fstab is as follows:

---------------------------------------------------

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

---------------------------------------------------------

Seems weird, but it doesn't really mean anything to me, lol!  I've been looking all over for a solution and can't find one that works for me.  I hope someone here has the answer!  Thanks.

-mike

---

### Post by koshimazaki on 2007-07-22
I seem to have the same problem, just installed feisty and the cd/dvd drive doesn't work. Didn't cause any problems during installation. Even when i try "Eject" from the context menu just after boot with no disc in the drive it gives "Unable to mount media". Using eject from the commandline works fine. And when I try to rip cd using cdparanoia the machine hangs completely with Caps Lock and Scroll Lock LEDs blinking.

Cheers

---

### Post by Sumatie on 2007-07-31
Hope I can jump in here, but I am having the same problem. I doesn't matter what I do what DVD I put in the drive it say's "unable to mount volume there is probably no media in the drive" This happens with both data and movie discs. They used to work, the only changes I have made is to revert to the open source ATI drivers for my graphics cards. I have tried to uninstall - reinstall the codecs but it did not help, even when I did not have the correct codecs installed it would read the drive. Any help, please.

My drive is a drw-3s165.

---

### Post by Sumatie on 2007-08-01
Whoops sorry false alarm...or at least not a linux problem. The drive itself had broken down. Slipped in a new one and off it went. Also tried the drive in my windows pc had same problem could not read media. Sorry to bother anyone.

---

### Post by sgtbug on 2007-08-31
err.. the drives will mount by manually mounting them.. but is there a way to do it automatically?

---

### Post by kisstrees on 2007-09-03
I also installed Ubuntu, know almost nothing about it, and can't figure out why I can't open a cd or dvd of any description on my machine.  Both my cd and cdrw/dvd drive worked fine before I installed my new operating system, but when I attempt to open either drive, I get "Unable to mount media."  For both drives.  Someone out there, help?

---

### Post by Gotou on 2007-09-07
I've been having the same problem with this new Feisty version my desktop and laptop.  I had to reformat the desktop and put Dapper back on it.  I need that machine working.  The laptop I've kept Feisty on with the hopes the powers that be will have the problem fixed soon.  Judging by the post this problem has existed for several months now.

---

### Post by Tavathlon on 2007-09-26
Trying to bump all threads I can find that are about this issue...  I have the exact same problem, except that it does not seem to work for me even if the disc is inserted on boot - and the fact that I'm running Gutsy, not Feisty.

It's a rather important issue, disc drives a very important part of using a computer, and I'm afraid Ubuntu will loose a lot of users if this problem will not be solved...   (you're not loosing me though, I'm too stubborn for letting hardware problems scare me away... =P  But others...  =/  )

So, anyone got any ideas? I've noticed that there is indeed no such files as /dev/scd0 or /dev/dvd, just like the error messages tells me when I try to mount a disc.

---

### Post by Tavathlon on 2007-09-26
Problem solved now, following the advice in this thread: [http://ubuntuforums.org/showthread.php?p=3426098](http://ubuntuforums.org/showthread.php?p=3426098) about fiddling around in BIOS. I changed the cdrom setting from 'auto' to 'user', and then it worked.  =)

Still a strange problem, though. Quite annoying for most people.

---

### Post by scottpledger on 2007-11-11
For those having problems with Gutsy, a simple temporary fix is to run:
> sudo /etc/init.d/hald restart
and that will get it going again.

---

### Post by jakoxx on 2007-11-18
it shines I hav same problem here.
I have not cd, external USB HD, other USB devices.
I get message "HAL error".
With 7.04 I has not this problem. I got it after i have installed upgrade to 7.10
Jakoxx:confused:

---

