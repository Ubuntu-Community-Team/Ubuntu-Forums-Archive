---
title: "Why a login to eject CD-ROM?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-09-15
Here's a snapshot of the message I get when I try to eject the CD-ROM. I suspect this is a continuation of problems I've had in the past with mounting my removables... something fstab-related, perhaps. Any help is appreciated.

---

### Post by coolen on 2007-09-15
Did you use mount when you put the CD in?
If so, then only the root user will be able to unmount it.

---

### Post by ricardisimo on 2007-09-15
This just started happening recently, and I haven't made any changes whatsoever on this compootor in these past few weeks or months.

P.S. - Hmmm... but I do have a 3-1/2-year-old whom I find messing with the desktop regularly... could he have altered something? If so, how do I un-alter it?

---

### Post by dwhitney67 on 2007-09-15
It seems to me that it is a "good" thing that the system is prompting you for a password to remove the media.  It is probably a security thingy, but also it ensures a healthy unmount.

Imagine if you were connecting to your system remotely, accessing critical data on the CD, and then your son (or anybody else for that matter) were to eject it?  Then you would probably be inquiring why there isn't something to protect against that.

Anyhow, my $0.02 worth of an observation.

---

### Post by -SpaZ on 2007-09-15
> **dwhitney67 said:**
> It seems to me that it is a "good" thing that the system is prompting you for a password to remove the media.  It is probably a security thingy, but also it ensures a healthy unmount.

Imagine if you were connecting to your system remotely, accessing critical data on the CD, and then your son (or anybody else for that matter) were to eject it?  Then you would probably be inquiring why there isn't something to protect against that.

Anyhow, my $0.02 worth of an observation.

That sounds logical, what's the big deal about having to enter your password anyway?

---

### Post by coolen on 2007-09-16
Having to enter your password can get rather irritating every time you want to eject a CD.
If you could fix this problem, then I imagine it'd be easy enough to recreate it when you're accessing remotely. If you mount it using mount (as opposed to pmount, which I believe is what Ubuntu uses), then a normal user can't eject the CD. I didn't get the password prompt, but it seems to me that if you need to protect against this, it'd make more sense to set this up explicitly when you need it, and have it work as you expect otherwise.

Now, back to addressing the problem, could you post your fstab (/etc/fstab)? Also, go into System -> Preferences -> Removable Drives and Media and tell us what you have selected under Removable Storage.

---

### Post by coolen on 2007-09-16
> **dwhitney67 said:**
> It seems to me that it is a "good" thing that the system is prompting you for a password to remove the media.  It is probably a security thingy, but also it ensures a healthy unmount.

Imagine if you were connecting to your system remotely, accessing critical data on the CD, and then your son (or anybody else for that matter) were to eject it?  Then you would probably be inquiring why there isn't something to protect against that.

Anyhow, my $0.02 worth of an observation.

There is, actually. If your working directory over ssh is inside the cdrom's directory tree, a user at the computer cannot simply eject it. Even the super user lacks this ability, so short of dismantling the computer and then the drive, that thing ain't coming out.
That, or turning off the computer...

---

### Post by ricardisimo on 2007-09-17
Believe me, the passwords do indeed get very annoying. Besides, having someone eject the CD remotely is hardly what I'd call a security risk... just one less drive for them to access. What would be the point? It's like having a burglar who can't get into my house, but he can turn the bathroom light on and off.

Here's my fstab, where I'm noticing an odd (and probably unrelated) error on one of the hard disks. If anyone can decipher that one as well I'd be doubly as appreciative. Thanks for the responses everyone.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=2ec78ab2-2fe6-4211-abbb-a22984e9648b / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=e34f029b-7b4a-4def-badb-fa40de54314a none swap sw 0 0
UUID=bfe37834-a8da-4f43-81a7-c67928f282e0 /media/storage ext3 defaults 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by dwhitney67 on 2007-09-17
Your /etc/fstab looks fine.  I'm not quite sure what this entry is for though:
[FONT="Courier New"]
UUID=bfe37834-a8da-4f43-81a7-c67928f282e0 /media/storage ext3 defaults 0 0[/FONT]

Do you have an external drive, or is that referring to a partition on your HDD?

---

### Post by coolen on 2007-09-17
My line for the CD-ROM is almost identical...it uses /dev/cdrom rather than /dev/hdc, though. I think Ubuntu automatically maps this during the install, so it makes sense that it'd implement some of the more user-friendly features on that drive.
So, change that to read /dev/cdrom and see if that works better.

---

### Post by dwhitney67 on 2007-09-17
> **coolen said:**
> My line for the CD-ROM is almost identical...it uses /dev/cdrom rather than /dev/hdc, though. I think Ubuntu automatically maps this during the install, so it makes sense that it'd implement some of the more user-friendly features on that drive.
So, change that to read /dev/cdrom and see if that works better.

It wouldn't make a difference.  Your /dev/cdrom is probably a sym-link to /dev/hdc or /dev/scd0.

---

### Post by debianchick on 2007-09-17
> **dwhitney67 said:**
> Your /etc/fstab looks fine.  I'm not quite sure what this entry is for though:
[FONT=Courier New]
UUID=bfe37834-a8da-4f43-81a7-c67928f282e0 /media/storage ext3 defaults 0 0[/FONT]

Do you have an external drive, or is that referring to a partition on your HDD?

Found this 2006 thread from ubuntu_demon that will explain "UUID" and how to fix it 
[U]
[**booting stalls during "mounting root filesystem" -  testing workaround(s)**]("http://ubuntuforums.org/showthread.php?p=1257154")

[/U]Just found this Launch Pad bug report about it 

[https://bugs.launchpad.net/ubuntu/+bug/94848](https://bugs.launchpad.net/ubuntu/+bug/94848)

---

### Post by tvrg on 2007-09-17
try adding yourself to the cdrom group

---

### Post by ricardisimo on 2007-09-19
> **dwhitney67 said:**
> It wouldn't make a difference.  Your /dev/cdrom is probably a sym-link to /dev/hdc or /dev/scd0.

It's worse than not making a difference. I tried something similar on another computer several months back, and as I recall, all of my CD/DVD apps stopped working properly. Only Sound Juicer would work, for some reason.

---

### Post by ricardisimo on 2007-09-19
> **tvrg said:**
> try adding yourself to the cdrom group

I'm reluctant to mess with permissions at this stage of my Ubuntu life, but who would I add to let an application (a game in this case) access the CD-ROM at will? More than just curious; it's one of the related problems I'm currently having.

---

### Post by ricardisimo on 2007-09-19
This is very curious: there is no cdrom group on this computer. Could my son have deleted it while I was away from the machine? Could the absence of the group explain my problems? Thanks again.

---

### Post by dwhitney67 on 2007-09-19
Absolutely.  Add this entry to /etc/group using your favorite editor:

```
[FONT="Courier New"]cdrom:x:24:haldaemon,*user-id-1,user-id-2,etc*[/FONT]
```

and substitute *user-id-1,user-id-2,etc* with the actual user ids on your system.

Also, when you have the chance, run these commands:

```
[FONT="Courier New"]$ ls -l /dev/cdrom
$ ls -l /dev/hdc         (or /dev/scd0)[/FONT]
```

You will see that the /dev/cdrom is a symbolic link to the other device file.  Back to my earlier argument, it won't make one iota of a difference which one is specified in the /etc/fstab file.  Also note the ownership of the /dev/hdc (or /dev/scd0) file:  I bet it is root:cdrom.

---

### Post by ricardisimo on 2007-09-20
It gets a bit stranger... that line is already in /etc/group exactly as it should be. "cdrom" doesn't appear in the "Manage Groups" dialog of "Users & Groups". I suppose I could add it, but I'm not familiar with how exactly to do that. Clearly it is more than just the name "cdrom".

More weirdness -  the line in my fstab clearly says: ```
[COLOR="Red"]/dev/hdc[/COLOR]        [COLOR="Red"]/media/cdrom0[/COLOR]   udf,iso9660 user,noauto     0       0
```
However, there is no "hdc" in the /dev folder. There is "dvd", "cdrom" and "cdrw", but all three are symlinks.

The coup de gras here is that /media/cdrom0 shows empty, even though there is a Risk game cd in it, and indeed there is a separate folder in /media called "/Risk". Maybe this last bit is meaningless, but I'm pretty certain that if my fstab claims there is a /dev/hdc, then there should probably be such a thing.

More help would be appreciated here. Thanks.

---

### Post by dwhitney67 on 2007-09-20
You stated that /dev/cdrom is a symlink.... a symlink to what?  If you do not have a /dev/hdc, it is perhaps linked to /dev/scd0?

Verify what /dev/cdrom "points to" by examining the output when running this command:

[FONT="Courier New"]$ ls -l /dev/cdrom[/FONT]

Regardless of what it is linked to, you should be able to edit /etc/fstab and specify /dev/cdrom in lieu of /dev/hdc.

---

### Post by ricardisimo on 2007-09-20
```
~$ ls -l /dev/cdrom
lrwxrwxrwx 1 root root 4 2007-09-20 02:59 /dev/cdrom -> scd0
```
I tried editing fstab on my work compootor because of similar issues with the CD and DVD drives, and it went from bad to worse. At one point only Sound Juicer could access either one. I'd like to get it right this time. Do I use "scd0" or "cdrom"? My main concern is that a symlink to the wrong target is wrong as well.

Also, what happened to the "cdrom" group in "Users & Groups"?

---

### Post by dwhitney67 on 2007-09-20
Based on what you have stated about your system, it would appear that the /dev/hdc in your /etc/fstab needs to be replaced with either /dev/cdrom or /dev/scd0.

If in doubt, just add to your /etc/fstab the following (note the first line is commented-out):

[FONT="Courier New"]#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]

---

### Post by coolen on 2007-09-21
Did you copy that straight from a terminal?
If so, then I think it should be sdc, not scd. I think the 0 is wrong too...at least, it's not on my machine. This should point to a drive, not a partition on that drive.

As for the user group issue, I don't have a cdrom group listed, and it works fine for me.

---

### Post by dwhitney67 on 2007-09-21
No, /dev/scd0 is correct!  Other systems have the cd-rom (dvd-rom) drive mapped to /dev/hdc.

On my Ubuntu 7.04 system, /dev/scd0 is owned by 'root', but with group of 'cdrom'.

On my Fedora Core 5 system, the /dev/cdrom points to hdc.  It has root:disk ownership.

On my Fedora 7 system, the /dev/cdrom points to scd0.  It has whitney:disk ownership.  I guess my user ID is set to own that device during login.

---

### Post by coolen on 2007-09-21
I just thought the letters were backwards...the Linux naming convention, from what I understood, is (h/s)dX#, the first indicating the type of device, the X to identify the drive, and the # for the partition.

---

### Post by dwhitney67 on 2007-09-21
Linux does designate partitions of primary SATA drives with the sdaN nomenclature whereas partitions on primary IDE drives are hdaN.  Secondary HDD would be sdbN and hdbN respectively.

I am not sure about the rationale of the scdN versus hdc naming convention, however if I recall the name is set by the HAL-daemon during system startup.

---

