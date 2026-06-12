---
title: "I can't see my freshly added hd in Hardware Information"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by OldboyJack on 2007-10-06
Hi,

Just added a new hard disk, but I don't know what to do, because I can't see it in Hardware Information... :-(
What am I supposed to do?

Sincerely yours

OldboyJack

---

### Post by Pumalite on 2007-10-06
Make sure your BIOS recognizes it first.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Make sure your BIOS recognizes it first.

I didnt use BIOS for ages... How am I supposed to check it?

Thanks for answer and sorry for trouble

Your

OldboyJack

---

### Post by ryanVickers on 2007-10-06
I know it's not the Linux way, and there's another way, I know, but if you just reboot it should recognize it and add it to the /etc/fstab and anywhere else it needs to - I just did this yesterday :)

But yes, make sure it's recognized by the bios - usually to get into the bios, there's a key or something, like F12 or F2 or "del", but once your in, however you do it, it would likely list all the devices on the main page - look for something like "companyname_randomnumbers"

---

### Post by Pumalite on 2007-10-06
At boot: 'Esc', or 'Del', or 'Tab', some key combination that is different for each board. Consult your Manual. Go to IDE Configuration or similar.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> At boot: 'Esc', or 'Del', or 'Tab', some key combination that is different for each board. Consult your Manual. Go to IDE Configuration or similar.

OK. After some manipulations my new hd is seen by BIOS. It shows: "IDE CHannel 2 Master Samsung HD501LJ". And, it is also seen by Ubuntu's Hardware Information under "VIA VT6420 SATA RAID Controller". So my next question is: what am I to do to mount it???

Thanks for your answers and patience :-)

Yours

OldboyJack

---

### Post by Pumalite on 2007-10-06
sudo mkdir /media/newdrive
sudo mount -t (format) /dev/? /media/newdrive

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> sudo mkdir /media/newdrive
sudo mount -t (format) /dev/? /media/newdrive

Let me understand everything what you wrote above, OK?

1) "newdrive" is my chosen name fo my new harddisk, am I right?
2) What means this format in brackets? "(format)"? Am I suppose to write it as it is or fill it with some additional information?
3) How am I supposed to check what to write instead of this question mark after /dev.... In other words: how am I suppose to recognize which hd is my new one??

Sorry for stupid questions, but I really need very badly to fix it today...

Your

OldboyJack

---

### Post by Pumalite on 2007-10-06
With sudo mkdir /media/newdrive, you are creating a mount point.
For the rest, lets make it easy and post:
sudo fdisk -lu

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> With sudo mkdir /media/newdrive, you are creating a mount point.
For the rest, lets make it easy and post:
sudo fdisk -lu

Thanks.
My fdisk -lu is as follows:

- - - - - - - - - - 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   149838254    74919096   83  Linux
/dev/hda2       149838255   156296384     3229065    5  Extended
/dev/hda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   142592939    71296438+  83  Linux
/dev/hdb3       142592940   156360644     6883852+   5  Extended

- - - - - - - - - - 

Your

OldboyJack

---

### Post by Pumalite on 2007-10-06
sudo mount -t ext3 /dev/sdb1 /media/newdrive
Then go and look in /media and open newdrive

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> sudo mount -t ext3 /dev/sdb1 /media/newdrive
Then go and look in /media and open newdrive

Thanks a million!
BTW: "newdrive" can be replaced by any other name, right??

Totally gratefull

OldboyJack

PS: System told me: **mount: special device /dev/sdb1 does not exist**.

What to do??? :-(

---

### Post by Pumalite on 2007-10-06
You are welcome. You can call it Trotsky if you want.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> You are welcome. You can call it Trotsky if you want.


System told me: mount: special device /dev/sdb1 does not exist.
Maybe I should replace **sdb1** with **sda1** ??

Your

OldboyJack

---

### Post by Pumalite on 2007-10-06
Funny thing is fdisk says that it does exist. 2nd, you have a boot flag on sda1, so I thought your new drive was sdb. Try /dev/sdb. The other thing is you should be able to see it and mount it with a double click in Places>Home on the left column.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Funny thing is fdisk says that it does exist. 2nd, you have a boot flag on sda1, so I thought your new drive was sdb. Try /dev/sdb. The other thing is you should be able to see it and mount it with a double click in Places>Home on the left column.

I was told (by system): **mount: special device /dev/sdb does not exist**...

Sorry for trouble... Any ideas what to do next? :-(

Your

OldboyJack

---

### Post by Pumalite on 2007-10-06
Did you check Places>Home?

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Did you check Places>Home?

Yes, I did. In vain. :-(

Your

OldboyJack

---

### Post by Gwasanaethau on 2007-10-06
Sorry to interrupt here, but I'm just wondering - have you formatted the new hard disc with a filesystem? Your fdisk output says 'sda' doesn't have a valid partition table, so you might need to format it first if you haven't done so already. You can use gparted to do it (it's in the repositories).

---

### Post by Pumalite on 2007-10-06
How many drives are you supposed to have including your new one?

---

### Post by OldboyJack on 2007-10-06
> **Gwasanaethau said:**
> Sorry to interrupt here, but I'm just wondering - have you formatted the new hard disc with a filesystem? Your fdisk output says 'sda' doesn't have a valid partition table, so you might need to format it first if you haven't done so already. You can use gparted to do it (it's in the repositories).

You are very welcome to interrupt :-)
Nope, I haven't formatted the new hard disc, yet. I will do it right now.
PS. When I saw that you live in Dublin I thought that maybe you are also Polish ;-)

Thanks

OldboyJack

---

### Post by Gwasanaethau on 2007-10-06
> **OldboyJack said:**
> …PS. When I saw that you live in Dublin I thought that maybe you are also Polish ;-)…

I'm afraid not, I was born and grew up in London but moved to Dublin a few years ago. My Granddad was Slovak, though, and as a consequence I have a Slovak surname…

Anyway, hopefully when the drive is formatted, the commands that Pumalite mentioned should work…

---

### Post by OldboyJack on 2007-10-06
> **Gwasanaethau said:**
> I'm afraid not, I was born and grew up in London but moved to Dublin a few years ago. My Granddad was Slovak, though, and as a consequence I have a Slovak surname…

Anyway, hopefully when the drive is formatted, the commands that Pumalite mentioned should work…

OK. Formatted. Now my fdisk is:

- - - - - - - - - - -

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001   83  Linux

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   149838254    74919096   83  Linux
/dev/hda2       149838255   156296384     3229065    5  Extended
/dev/hda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   142592939    71296438+  83  Linux
/dev/hdb3       142592940   156360644     6883852+   5  Extended

- - - - - - - - - - -

So now I am supposed to use sda1, am I?

Your

OldboyJack

---

### Post by Gwasanaethau on 2007-10-06
Yeah, I'd give sda1 a try and see how you get on with that. ;)

---

### Post by OldboyJack on 2007-10-06
> **Gwasanaethau said:**
> Yeah, I'd give sda1 a try and see how you get on with that. ;)

OK, it worked! :-) :-({|=
The system created a new disk and called it - very wisely - "disk". Now this "disk" is visible on my desktop - but is restricted to root only... So my last question is: how can I change the rights to use this disk freely?

Your

OldboyJack

---

### Post by ryanVickers on 2007-10-06
I think this is normal - automatically "restricting the access to 'this' internal disk for security reasons", but there might be a way to change it - if so, I"m interested too... :)

---

### Post by Pumalite on 2007-10-06
Try:

sudo nautilus
Also:

sudo chmod 777 /media/disk

---

### Post by ryanVickers on 2007-10-06
That will just open a root file browser to view it as root.  I think what he means is just let it be mounted/written to/read from as a normal user

---

### Post by Gwasanaethau on 2007-10-06
> **OldboyJack said:**
> OK, it worked! :-) :-({|=&#8230;
Woohoo! =D>\\:D/

Unfortunately, I don't know how to change the permissions. I have a feeling that it means changing your /etc/fstab file, but I don't know what to do to it. Sorry&#8230; :(

Just for kicks, post your /etc/fstab file and we'll see what we can do&#8230;

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Try:

sudo nautilus
Also:

sudo chmod 777 /media/disk


Big thanks for this and all the others good advices! :-)
Now I have rights (permissions), but after reloading my system it occured that my new disk is NOT mounted permanently :-( To use it I have to go to Computer and then point the hard disk drive icon and with right-click monut it again and again. So, could you help me and tell me how to mount it for good??

Thanks!

Your

OldboyJack

---

### Post by Pumalite on 2007-10-06
You have to edit /etc/fstab. Post:
sudo /etc/fstab
blkid

---

### Post by Gwasanaethau on 2007-10-06
EDIT: Pumalite beat me to it&#8230;see above.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> You have to edit /etc/fstab. Post:
sudo /etc/fstab
blkid

I tried :-(
Result:

jacek@jacek-desktop:~$ sudo /etc/fstab
sudo: /etc/fstab: command not found
jacek@jacek-desktop:~$ 

Why?

Your

OldboyJack

---

### Post by ryanVickers on 2007-10-06
:p  Maybe open it *with* something

```
sudo **gedit** /etc/fstab
```  (not your fault :))

---

### Post by Pumalite on 2007-10-06
gksudo gedit /etc/fstab

---

### Post by Gwasanaethau on 2007-10-06
Ahh, that should be:
```
sudo gedit /etc/fstab
```
It might be worth backing up your fstab file before we go any further too, just in case! ;)
```
sudo cp /etc/fstab /etc/fstab.bak
```

EDIT: Man am I slow - two people beat me this time! :lolflag:

---

### Post by OldboyJack on 2007-10-06
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=26ef5238-8567-4449-891d-c6417ba848bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=1fb689b7-60b9-49fe-8ddd-656e0eb0ef68 /media/hdb1     ext3    defaults        0       2
# /dev/hda5
UUID=620f24cf-a07d-4f4e-8c5f-205ac53c1426 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Pumalite on 2007-10-06
We need, at the Terminal:
blkid

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> We need, at the Terminal:
blkid

As you wish, Master :-)

jacek@jacek-desktop:~$ blkid
/dev/hda1: UUID="26ef5238-8567-4449-891d-c6417ba848bf" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="620f24cf-a07d-4f4e-8c5f-205ac53c1426" TYPE="swap" 
/dev/hdb1: UUID="1fb689b7-60b9-49fe-8ddd-656e0eb0ef68" SEC_TYPE="ext2" TYPE="ext3" 
jacek@jacek-desktop:~$

---

### Post by Gwasanaethau on 2007-10-06
EDIT: Actually, better leave it to the experts! ;)

---

### Post by Pumalite on 2007-10-06
At the Terminal:
mount

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> At the Terminal:
mount

jacek@jacek-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/disk type ext3 (rw,noexec,nosuid,nodev)
jacek@jacek-desktop:~$

---

### Post by ryanVickers on 2007-10-06
Yeah, you should be able to just type "mount /dev/*"

*=hda1 or hda5 or hdb1, all possibly without the numbers :)

---

### Post by Gwasanaethau on 2007-10-06
Won't that just mount it for the current session again? I think Oldboy Jack wants it to mount automatically on login&#8230;

It looks like your new drive isn't in your fstab file, Oldboy Jack. I think adding the following line to your fstab file might help:
```
/dev/sda1   /media/disk   ext3   defaults   0   3
```
**Make sure you've backed up your fstab file first!!!**. Also, the spaces above should be tabs.

---

### Post by Pumalite on 2007-10-06
Did you do:
sudo cp /etc/fstab /etc/fstab.back

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Did you do:
sudo cp /etc/fstab /etc/fstab.back

I did it right now.

---

### Post by Gwasanaethau on 2007-10-06
Excellent - and did you add the line to your fstab file? If so, try rebooting to see what happens. Hopefully it'll detect your new drive! [-o<

---

### Post by Pumalite on 2007-10-06
They beat me to it.

---

### Post by ryanVickers on 2007-10-06
> **Gwasanaethau said:**
> Excellent - and did you add the line to your fstab file? If so, try rebooting to see what happens. Hopefully it'll detect your new drive! [-o<

There are other ways to do this but rebooting is the simplest :p

When I added a drive, I didn't even have to do anything - I just plugged in a drive and rebooted and it worked perfectly - it was automatically configured, it added a button in the disk mounter applet, added a mount point, set up options, blah, blah, blah... :p

In short, this is good - it should just work

---

### Post by mgmiller on 2007-10-06
There is a nice gui tool in the repos that can automate a lot of this stuff.  It's called pysdm.

After install, look in System>Administration>Storage Device Manger.

It can set your mount points and will write the changes to /etc/fstab for you.

---

### Post by Pumalite on 2007-10-06
System>Preferences>Removable Drives and Media

---

### Post by Gwasanaethau on 2007-10-06
I'm a little concerned we've lost you there, Oldboy Jack. If so, and you're reading this from somewhere else, you can restore your old fstab file by copying the backup you made back to your original:
```
sudo cp /etc/fstab.bak /etc/fstab
```
You'll probably need to do this through the Live CD. If that's the case, you'll need to mount your hard disc partition first:
```
mount /dev/hda1
```

---

### Post by Pumalite on 2007-10-06
I think OldboyJack is probably busy filling up his new drive.

---

### Post by Gwasanaethau on 2007-10-06
> **Pumalite said:**
> I think OldboyJack is probably busy filling up his new drive.
Hehehe! I don't blame him either! It's a huge drive to fill!

---

### Post by OldboyJack on 2007-10-06
I'm back, my dear friends! I was out to have a smoke, for doing all those things was stressfull :-)
I think everything is OK now :-)
I would like to thank all of you - for your help and support. I hope one day I'll be able to repay you - this wasy or another! :-)
PS. I don't even start to fill my new hd... Why? I am a bit affraid that I'll fill it up completly TOO quickly :-)

Take care, guys, and one more time: BIG THANKS! :-)

Yours

OldboyJack

---

### Post by Pumalite on 2007-10-06
Don't forget ktorrent.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Don't forget ktorrent.

Thanks, but as a GNOME fan I don't use software for KDE ;-)

Your

OldboyJack

---

### Post by Pumalite on 2007-10-06
You can use KDE software in Gnome without any problem. I use Gnome and I have Amarok, ktorrent and konqueror installed. They are interchangeable.

---

### Post by Gwasanaethau on 2007-10-06
> **OldboyJack said:**
> I'm back, my dear friends! I was out to have a smoke, for doing all those things was stressfull :-)…
Tut tut tut. We'll have you off those death sticks soon enough! :lolflag:
> **OldboyJack said:**
> …I think everything is OK now :-)
I would like to thank all of you - for your help and support. I hope one day I'll be able to repay you - this wasy or another! :-)…
You're very welcome! I'm just glad it all worked out fine!
> **OldboyJack said:**
> PS. I don't even start to fill my new hd... Why? I am a bit affraid that I'll fill it up completly TOO quickly :-)

Take care, guys, and one more time: BIG THANKS! :-)

Yours

OldboyJack
Hahaha, very true! Though I have to admit, I only have 80GB to mess around with, so I'm usually very conservative about my disc space.

Take care now and best of luck! :popcorn: :guitar:

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> You can use KDE software in Gnome without any problem. I use Gnome and I have Amarok, ktorrent and konqueror installed. They are interchangeable.

Yes, I know that, but I stick to pure Gnome-based software for more aestethical, than technical reason :-) I don't like how KDE enviroment and its components are designed - but it is, of course, a matter of taste :-)

OldboyJack

---

### Post by Pumalite on 2007-10-06
Yeah.. I know I'm a bum.

---

### Post by OldboyJack on 2007-10-06
> **Gwasanaethau said:**
> Tut tut tut. We'll have you off those death sticks soon enough! :lolflag:

You're very welcome! I'm just glad it all worked out fine!

Hahaha, very true! Though I have to admit, I only have 80GB to mess around with, so I'm usually very conservative about my disc space.

Take care now and best of luck! :popcorn: :guitar:

In fact I need my disc space NOT only for fun, but also for work (which is somehow entertaining) :-) So I really badly need those few more GBs - mostly for musical files :-)

Your

OldboyJack

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Yeah.. I know I'm a bum.

Oh, no! I am a bum... :-) A bum with aesthetical principles! :-)

Your

OldboyJack

---

### Post by ryanVickers on 2007-10-06
what are the size of your disks?  And the one you added?...

---

### Post by Pumalite on 2007-10-06
Well, I'm a bum with principles too: try everything; if it doesn't kill you, it will make you stronger and wiser.

---

### Post by OldboyJack on 2007-10-06
> **ryanVickers said:**
> what are the size of your disks?  And the one you added?...

Old ones are (together) around 300... The new one is 500...

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> Well, I'm a bum with principles too: try everything; if it doesn't kill you, it will make you stronger and wiser.

I have NO doubts, that you have your own strong principles... Now I know for sure... :-)
BTW: Hw do you like zenwalk? I have never tried it, but it looks as if it was a nice OS...

OldboyJack

---

### Post by OldboyJack on 2007-10-06
> **mgmiller said:**
> There is a nice gui tool in the repos that can automate a lot of this stuff.  It's called pysdm.

After install, look in System>Administration>Storage Device Manger.

It can set your mount points and will write the changes to /etc/fstab for you.

Thanks for your advice! I'll try this software.

Take care

OldboyJack

---

### Post by Pumalite on 2007-10-06
It's a very nice light distro for older computers. I'm quite happy with it. Now if you want a light distro that will knock your socks off; try Puppy.

---

### Post by OldboyJack on 2007-10-06
> **Pumalite said:**
> It's a very nice light distro for older computers. I'm quite happy with it. Now if you want a light distro that will knock your socks off; try Puppy.

Thanks one more time! I'll look at puppylinux distro :-)

Take care

OldboyJack

---

