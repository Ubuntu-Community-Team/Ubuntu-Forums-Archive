---
title: "[SOLVED] Having truble burning ISO in fiesty."
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Teddy_P on 2007-09-01
I am running Fiesty I put in an old CD R,RW and it will not work.
I want to copy an ISO of linux Mint.
When I put in a blank CD I get an Icon but I do not get the window asking me what I want to do like I used to on Edgy. If I right click on the ISO and select write to disk, it looks like its the right CD writer and I select Write it askes me to ```
Please put a disc, with at least 578.0 MiB free, into the drive.  The following disc types are supported:
CD-R, CD-RW
``` Well its in there because I see the Icon on the desktop that says CD-ROM disc. The disc says 700 MB. But I can not open the blank disc in anything that I know of that will tell me free space. When I put in a music cd in the CD writer Sound juicer comes on and it plays fine.

We cleaned house the other day and through out all my OS disc's because well I don't use them much any more other then down loading new release but now I need one and the last one I made is Fiesty and that was on Edgy.


TIA

Teddy

---

### Post by wolfen69 on 2007-09-01
did you try using k3b to burn with? great program.

---

### Post by kellemes on 2007-09-01
> **wolfen69 said:**
> did you try using k3b to burn with? great program.

Agree, never had any issues with it, and it looks cool too.

---

### Post by southernman on 2007-09-01
You can use the command line to burn it with by doing:

> cdrecord /path/to/file/nameoffile.iso

---

### Post by jingo811 on 2007-09-01
ignore me.

---

### Post by Teddy_P on 2007-09-01
I extracted the music cd and tried to burn it using sound juicer it went half way then asked me to put in a blank cd. Same message as before. But the program let me add music to reach 80 min.


K3b is KDE?
I will try that soon.


Teddy

---

### Post by Teddy_P on 2007-09-01
The command line is doing something but from what I can see there is no status bar. I will let it run while I am at the store and get some new cd-RW.

The out put of the command line was
```
teddy@kids3:~$ cdrecord /home/teddy/Desktop/LinuxMint-3.0-e17-beta1.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PHILIPS '
Identification : 'CDD4801 CD-R/RW '
Revision       : 'C1.3'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET RAW/R16
Speed set to 1411 KB/s
Starting to write CD/DVD at speed   8.0 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.

Track 01: Total bytes read/written: 606154752/606154752 (295974 sectors).

```

Well now it looks like its done.

it says the speed was 8.0 is there a way to make this slower?


Teddy

---

### Post by Teddy_P on 2007-09-01
I ejected the cd using the right mouse button and put it back in and it looks like its there thanks.


Is there some reason why this was so easy in edgy but fiesty did not work?



Teddy

---

### Post by rsambuca on 2007-09-01
All you have to do is right-click on the iso and select "write to disc" and it will burn the iso for you!

---

### Post by mgmiller on 2007-09-01
When you installed the burner, did you check the position of the jumper on it?  Make sure it's set to master or slave as appropriate.  I don't like to use the cable select position, as it tends to give weird problems.

---

### Post by southernman on 2007-09-01
> **Teddy_P said:**
> The command line is doing something but from what I can see there is no status bar. I will let it run while I am at the store and get some new cd-RW.

The out put of the command line was
```
teddy@kids3:~$ cdrecord /home/teddy/Desktop/LinuxMint-3.0-e17-beta1.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PHILIPS '
Identification : 'CDD4801 CD-R/RW '
Revision       : 'C1.3'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET RAW/R16
Speed set to 1411 KB/s
Starting to write CD/DVD at speed   8.0 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.

Track 01: Total bytes read/written: 606154752/606154752 (295974 sectors).

```

Well now it looks like its done.

it says the speed was 8.0 is there a way to make this slower?


Teddy

There is. If you do "man cdrecord" or "man wodim" you can read through the help files for different command line options to use.

---

### Post by Teddy_P on 2007-09-01
> **rsambuca said:**
> All you have to do is right-click on the iso and select "write to disc" and it will burn the iso for you!

This is what I have tried first it did not work.



Teddy

---

### Post by Teddy_P on 2007-09-01
> **mgmiller said:**
> When you installed the burner, did you check the position of the jumper on it?  Make sure it's set to master or slave as appropriate.  I don't like to use the cable select position, as it tends to give weird problems.

It is set to cable select.
This computer has a hard drive and cd writer and a dvd player.
Where would you put the jumpers?
Should I have two slaves?



Teddy

---

### Post by Teddy_P on 2007-09-01
> **southernman said:**
> There is. If you do "man cdrecord" or "man wodim" you can read through the help files for different command line options to use.

Thanks I will check those.
Its working fine.
Well I don't mind using the command line but I wander why it did not work with the GUI like it used to.
I tried linux mint because I could not get ubuntu to load on one of the computers. I think that one time I knocked it over did it in because both OS's stopped at the same spot. (well after I try some stuff this would be for a different thread).

Thanks for all your help

Teddy

---

### Post by mgmiller on 2007-09-01
> It is set to cable select.
This computer has a hard drive and cd writer and a dvd player.
Where would you put the jumpers?
Should I have two slaves?

tell me how they are hooked up now.
could you also give me the contents of your /etc/fstab

Then I can suggest the smoothest way for you to do this.

The way I would set this up is to have my hard drive as master on the primary cable and the DVD player as slave on the primary cable and the cd writer as master on the secondary cable.

But, let me see what you have first.

---

### Post by Teddy_P on 2007-09-01
> **mgmiller said:**
> tell me how they are hooked up now.
could you also give me the contents of your /etc/fstab

Then I can suggest the smoothest way for you to do this.

The way I would set this up is to have my hard drive as master on the primary cable and the DVD player as slave on the primary cable and the cd writer as master on the secondary cable.

But, let me see what you have first.

Whats the best way to copy the /ect/fstab file?

Teddy

I will see how its hooked up in a bit.

---

### Post by southernman on 2007-09-01
> **Teddy_P said:**
> Thanks I will check those.
Its working fine.
Well I don't mind using the command line but I wander why it did not work with the GUI like it used to.
I tried linux mint because I could not get ubuntu to load on one of the computers. I think that one time I knocked it over did it in because both OS's stopped at the same spot. (well after I try some stuff this would be for a different thread).

Thanks for all your help

Teddy
The only thing I can come up with is as mgmiller suggested about jumper settings. Usually the drive itself will either have a) a diagram on top of the drive or b) somewhere on the back or top of the drive it will be stamped into the case.

As for your other thread material - depending on how hard the machine hit the floor (and what that floor is covered with), it could have caused the platters inside the disk to get scratched. 

When you get this all straightened out, send me a link via PM to your new thread and I'll give my suggestions for how to check the disk out.

---

### Post by southernman on 2007-09-01
> **Teddy_P said:**
> Whats the best way to copy the /ect/fstab file?

Teddy

I will see how its hooked up in a bit.

Places > Computer > Filesystem > etc

double click the fstab file to open it and just c&p it here

Providing your booted into Ubuntu that is ;)

---

### Post by Teddy_P on 2007-09-01
I was trying a command line way like nano or something.
But here it is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1881596d-e7a7-4114-8ee2-2e5003a5d96f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dfbd7e28-2758-4fbb-a28d-36da854988a3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```


Thank you for offering help for the other computer also.

Teddy

---

### Post by mgmiller on 2007-09-01
ok, based on your fstab, it looks like you have a sata hard drive and ide optical drives.  Is that correct?

Your 2 optical drives are both on the same cable.  Is that correct?

It is usually best to have the burner as the master drive, so set the burner jumper to master and the dvd rom to slave.

after you have done that and rebooted, open a terminal and type:
```
eject cdrom0
```

and tell me which of the optical drives opened its tray.

We will then edit your fstab a bit to optimize burning.

---

### Post by southernman on 2007-09-01
> **mgmiller said:**
> 
We will then edit your fstab a bit to optimize burning.
<---- Pays very close attention to mgmiller

---

### Post by Teddy_P on 2007-09-01
> **mgmiller said:**
> ok, based on your fstab, it looks like you have a sata hard drive and ide optical drives.  Is that correct?

Your 2 optical drives are both on the same cable.  Is that correct?

It is usually best to have the burner as the master drive, so set the burner jumper to master and the dvd rom to slave.

after you have done that and rebooted, open a terminal and type:
```
eject cdrom0
```

and tell me which of the optical drives opened its tray.

We will then edit your fstab a bit to optimize burning.

Sorry it took so long I had to look up sata hard drive. From what I can tell I do not have a sata hard drive. It looks more like ata I did not count the pins but there was a primary and secondary slots. I put the hard drive on the primary and the jumpers look like there set at CS. I left that alone.

The optical drives CD jumpers are now at MA and the DVD is at SL. and they are on the same cable pluged into the secondary slot.

When I typed "eject cdrom0" the DVD tray comes out and when I type "eject cdrom1" the cd burner tray opens.

and what the fstab file looks like now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1881596d-e7a7-4114-8ee2-2e5003a5d96f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dfbd7e28-2758-4fbb-a28d-36da854988a3 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

There is also a floppy drive but I don't have any of those any more I can un plug it if you like but I want to leave it in for little fingers.


Teddy

---

### Post by mgmiller on 2007-09-01
OK.  It seems a little weird that your fstab shows your hard drives as sda instead of hda, but since that ain't broke, we won't fix it.  (I think I read somewhere that new Feisty installs were doing something like this, that is, mounting all hard drives as if they are sata)

On to your optical drives.

First, make a back up of your current fstab:

```
sudo cp /etc/fstab fstab.backup
```

Next, we will open fstab and edit the line for your burner:
```
gksudo gedit /etc/fstab
```

just give it your regular password when asked.

You are going to slightly change the line for your burner, which we now know is cdrom1.

change the line that says:
```
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

so it looks like this:
```
/dev/scd0       /media/cdrom1   udf,iso9660 ro,user,noauto     0       0
```

You will notice, all I did was add ro in front of user.  

Save the file (by clicking the save button) and exit.

Next, remount all your drives by issuing the following command:

```
sudo mount -a
```

That should do it.

You should be able to right click an .iso and have it burn to a blank disk.
The rest of the burner weirdness should also stop.

If not, it is possible you have a burner with a firmware that is not 100% Linux friendly.

---

### Post by Teddy_P on 2007-09-01
same problem:

Also could you add a space before -a just in case someone else has this problem.

maybe the burner is just to old.

---

### Post by mgmiller on 2007-09-01
I hope everything worked out for you.  
I am going up to bed now as it's been a longish day for me. (Up since 6:00 AM and it's now 11:20 PM in my corner of the planet.)

Good night all...):P

---

### Post by Teddy_P on 2007-09-01
this is with a blank disc in and clicking on properties



Teddy

---

### Post by Teddy_P on 2007-09-01
Thanks for your help.
Good night


Teddy

---

### Post by mgmiller on 2007-09-01
Damn, just when you think it's safe to go back in the water.  ](*,)

> Also could you add a space before -a just in case someone else has this problem.

OOPS!  I changed it in the earlier post.

The only other thing I would try is changing the jumper on your hard drive to master instead of cable select.  Unless it's a Western Digital drive, in which case, just take it off altogether.

The jumper on the hard drive really shouldn't have anything to do with the two optical drives on a different drive cable, but cable select weirdness may happen.

At least cd/dvd burners are very cheap.  I got a nice dual layer cd.dvd burner from Micro Center warehouse for about US $ 35.00.  I use it in my Ubuntu machine and it works great.

---

### Post by mgmiller on 2007-09-01
And now, I really am going to bed....

---

### Post by Teddy_P on 2007-09-02
Well after you mentioned getting a new drive I put in the newest one I have.
Everything worked the right way.
When I put the disc in a window popped up asking what I wanted to do.
I picked ignore
then right clicked the ISO and clicked write to disc

Everything worked


Thank you for you time and help.


Teddy

---

### Post by mgmiller on 2007-09-02
Glad to hear it's working.  Bad hardware can create problems for any OS.
In general though, I prefer to avoid using the cable select settings on PATA drives.[-X

I just googled your old philips burner and found that a lot of people were having your identical problem of not seeing blank disks, but being able to play music cd's etc.  These posts dated from 2003-2004.  The consensus seems to be that the drives were bad and when they were replaced with a new burner, the problem was resolved.

Here is a typical example:
[http://www.gidforums.com/t-1326.html]("http://www.gidforums.com/t-1326.html")


Have a great day.:cool:

---

### Post by Teddy_P on 2007-09-02
Ya before I put the covers back on I was going to play with those jumpers.

Thank you again for your help
Teddy

---

### Post by mgmiller on 2007-09-02
> Ya before I put the covers back on I was going to play with those jumpers.

I just wanted to clarify the hard drive jumper story.

If the PATA hard drive is on the same cable as another drive, then you set the jumpers as master/slave as appropriate, regardless of the brand of the drive.

If the PATA hard drive is the only drive on the cable, then for stand alone use, if it is any brand EXCEPT Western Digital, then you would set the jumper to master.

If the PATA hard drive is the _only drive on the cable_ and is a _Western Digital drive_, then for stand alone use, you should **remove the jumper completely**, or set it sideways, so it has no action.  Failure to do this on a Western Digital HDD will result in all kinds of boot errors and other weirdness.


Good Luck....

---

