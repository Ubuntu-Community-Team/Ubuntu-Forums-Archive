---
title: "The frustrated tale of a Noob-How I liked the idea but just can't get it to work."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-09
Folks,
I have been at this for 2 weeks or so now.

I am a middle aged guy who used to program a ZX81 in basic years ago and then eventually got windows and pointed and clicked.
I don't like monopolies and fancied trying something new.

Got Ubuntu, liked it, tried changing its appearance didn't like Beryl, but got on with Gtk themes and stuff.  I even managed to get hold of my windows partition stuff.

However when it comes to making what I consider to be something simple to work ALL of MY inadequacies come to light and show the problems with Ubuntu ownership.

Getting a 2nd Gen Nano to work with a music player.

I understand there might be a bug with this particular model (just my luck!) but I was hoping that the change to Linux meant that nothing was impossible and there was always someone out there who could get a solution.

I have had real problems trying to mount an ipod.  I expect to be able to plug it in and synch it to a media player.

I tried several and thought I'd have a go with Banshee.  So I get banshee from add/remove and no iPod button or whathaveyou.  

I go to Banshee's site and notice that you need a libqt3c102-mt thingamabob.
I check my Synaptic manager and see that I have an old version.  I download the tar.gz and then get stuck, what to do next?  Post a Q on the forum no replies.  Learn how to IRC and some very nice people there guide me through.

It boils down to the fact that I need some dependencies.  The ones it tells me I need aren't on the list but the guys on IRC tell me to get some related dev packages.  I do as I'm told and eventually I get the lib thing to work.

I have given it another go and still no buttons or connectivity!

It appears I might need some other thing called ipod-sharp  and here we go again.

I haven't bothered yet.

This is one heck of a steep learning curve.

I know iPods are probably the devil and all that but seriously should I have to go through this many hoops just to get stuff to connect?](*,)

I hace Edgy Gnome, should I have tried a different OS like Kbuntu?

---

### Post by xyz on 2007-03-09
Well one thing at a time maybe!
So you downloaded a tar.gz? You need to install it then.
[How to install anything]("http://monkeyblog.org/ubuntu/installing/")...tar.gz among other things.
Hang in there.

---

### Post by megamania on 2007-03-09
> **Roger_Melly said:**
> Folks,
I have been at this for 2 weeks or so now.

What's not clear to me is whether your ipod is mounted or not.

Before running any program, if you plug-in the ipod, does an icon appear on the desktop? If it does, then try using another program (like GtkPod) to avoid the dependency-nightmare you're stuck into.

If it doesn't mount, I'm not able to help you, but I'm sure others will. Just don't give up and try to report the exact problems you're experiencing. I've used several ipods with ubuntu (gtkpod) so far with no problems.

---

### Post by Songwind on 2007-03-09
During your attempts at figuring this out, did you try Amarok by chance?  It has a "sync with mp3 player" feature.  I haven't had a chance to use it, unfortunately, because my MP3 player was sadly killed.

---

### Post by xyz on 2007-03-09
also post the output of:
```
cat /etc/fstab
``` if possible.
and 
> sudo fdisk -l

---

### Post by easyease on 2007-03-09
Yes Id say the Amarok idea is deffo the way forward.....

---

### Post by Roger_Melly on 2007-03-09
Thanks guys.

I have tried Amarok, no joy.

I have gone deep into the Banshee site and ran a bug detector called Raid or something lkike that.

My nano has this problem.  I then went round in circles.  I need to get 7 deb packages and install these which lets Hal mount un-mount the player.  This is a known bug and apparently is fixed in Feisty but not Edgy and won't officially be!!!!!

The thing is I have gone through all this before and it clearly isn't a permanent fix.  Or I'm doing something very wrong.  Looks like I'm going to have to become an expert in this RAID thing now!:(

---

### Post by Roger_Melly on 2007-03-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=14528419-e4f3-48f6-98df-dce42c0221fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=AA7C5E4E7C5E1583 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=283946e4-08da-419f-81df-5192770d45ab none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sde2 /media/ipod vfat umask=000 0 0
/dev/usbdevices/ipod  /media/ipod vfat defaults,umask=000,auto,rw,user 0 0rowland@Hector1234:~$ 


and 

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7916    63585238+   7  HPFS/NTFS
/dev/hda2            7917       14657    54147082+  83  Linux
/dev/hda3           14658       14946     2321392+   5  Extended
/dev/hda5           14658       14946     2321361   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sde: 4060 MB, 4060086272 bytes
255 heads, 63 sectors/track, 123 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1           3       96264    0  Empty
/dev/sde2               4         123     3855600    b  W95 FAT32

---

### Post by easyease on 2007-03-09
> **Roger_Melly said:**
> Thanks guys.

I have tried Amarok, no joy.

I have gone deep into the Banshee site and ran a bug detector called Raid or something lkike that.

My nano has this problem.  I then went round in circles.  I need to get 7 deb packages and install these which lets Hal mount un-mount the player.  This is a known bug and apparently is fixed in Feisty but not Edgy and won't officially be!!!!!

The thing is I have gone through all this before and it clearly isn't a permanent fix.  Or I'm doing something very wrong.  Looks like I'm going to have to become an expert in this RAID thing now!:(well if i were you id be taking the lazy route around it and create a partition to install feisty on just for the sake of transfering music. not saying thats the right thing to do but it sounds easier in the long run.

---

### Post by Roger_Melly on 2007-03-09
Thanks for listening folks,

I've re-installed the fix and the iPod is recognised.

I just hope it stays permanent and for all users this time.

Amarok v. Banshee

Banshee is nice and clean/simple but I can't seem to access complicated file levels ie hda1/documents/my document/my music.

Just Local folder and so on!

Amarok all this and more.

But Crikey must it all be such a nightmare?

P.S.  How do I get Feisty?

---

### Post by easyease on 2007-03-09
Yep cant fault Amarok! glad you fixed it, If you fancy trying feisty it can be found here...
[http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/)
 you'd probably need the alternate install version but handle with care because its still buggy.

---

### Post by Henry Rayker on 2007-03-09
One thing I'd like to point out is that Edgy isn't a LTS release and, as such, some things (such as this iPod mounting business) just don't get backported. This problem also seems to be relatively isolated to the iPod (my girlfriend's Zen Micro works without a problem).

The real issue at hand is the fact that the Ubuntu devs have to work twice as hard as the Windows developers -- the hardware developers take care of drivers and testing and everything, Windows just has to make sure they adhere to specific layers of protocols (which they get to define). Because you can't honestly expect the developers (lots of volunteers, as well as some who get paid) to work literally twice as hard as a MicroSoft employee (who all get pretty good pay and full benefits) some of that work will fall into the lap of the user.

---

### Post by graywizard on 2007-03-09
I too am very frustrated. so I am a member of the club.  re:  the post above about how to install anything. I read and reread the same thing over and over across posts and therads and sites.  drop the tar.gz or tar.bz or .gz files into he themes winows - well it doesn't work!!!! Invalid file type pops up - so now what? and then People say well do it it works but it doesn't and I have tried maybe 43 times.

Nothing!

I am far from being a dunce but this linux thing just doesn't work for newbies like me.

---

### Post by Roger_Melly on 2007-03-09
Henry,
You make a **_VERY_** good point.  I do see that stuff _is_ fixed.  One thing though?  As a new user why are repositories and the like updated?  I have NOW noticed that the version of Banshee I have just been fiddling about with is outdated.  I have been sudo get updating or something and am often renewing my Synaptic.  What gives?  Don't repositories refresh i.e.  Did the banshee package come from a banshee repository and when a new one turns up should that not install?

---

### Post by xpod on 2007-03-09
> I am a middle aged guy who used to program a ZX81 in basic years ago and then eventually got windows and pointed and clicked.
I don't like monopolies and fancied trying something new.


Your not alone roger-melly.I`m getting on for being middle aged myself(only in body :)  and just like you i thought i`d "try something new" about this time last year so i sat down in front of a computer for the first ever time really..:confused: 

Discovered Ubuntu some few months later and to be honest i probably would`nt be half as interested in the things as i seem to have become if it were not for this thing called Ubuntu.

Your 2 weeks in so stick at it m8........you`ll soon be looking back wondering what all the fuss was about i`m sure.

[http://www.ubuntu.com/testing/herd5?highlight=%28feisty%29](http://www.ubuntu.com/testing/herd5?highlight=%28feisty%29)

Good luck

---

### Post by Roger_Melly on 2007-03-09
Grey wizard, where are you getting your theme bits?

---

### Post by Roger_Melly on 2007-03-09
Xpod, How's your marriage???:lolflag:

---

### Post by Songwind on 2007-03-09
> **Roger_Melly said:**
> Thanks for listening folks,

I've re-installed the fix and the iPod is recognised.

I just hope it stays permanent and for all users this time.

Amarok v. Banshee

Banshee is nice and clean/simple but I can't seem to access complicated file levels ie hda1/documents/my document/my music.

Just Local folder and so on!

Amarok all this and more.

But Crikey must it all be such a nightmare?

P.S.  How do I get Feisty?

First off, congrats on getting the fix installed.

I haven't used Banshee, myself.  So far I have tried out JuK, Rhythmbox, Amarok, XMMS.  Amarok is by far the one I prefer.  Songbird looks like it will be good, but I haven't installed it yet because it's so early in it's development life cycle.

Here are my suggestions on dealing with the stresses of setting new things up on Linux:
1)  Keep a backup of any critical documents.  That's the main thing, right there.
2)  Breathe!  It's just a computer.  Try to have fun with it.
3)  Since the software is free (or at least most of it is), you can afford to experiment, unless you're trying to get something done on a deadline for work.  Just don't commit yourself to any huge amount of work in a proprietary format that you aren't sure you like yet.
4)  Don't be afraid to ask.  I find that although there are many vocal.. well.. jerks in the Linux community, most users seem enthusiastic and sincere in their desire to help people get the system under their own control.
5)  "man" or in-depth online tutorials are your friend.  You can follow all the step-by-step tutorials in the world, but it won't help you in the long run if you don't know why you're doing what you're doing.  So take a few extra minutes to understand what the commands mean.

Good luck,
Eric

---

### Post by Songwind on 2007-03-09
> **Roger_Melly said:**
> Henry,
You make a **_VERY_** good point.  I do see that stuff _is_ fixed.  One thing though?  As a new user why are repositories and the like updated?  I have NOW noticed that the version of Banshee I have just been fiddling about with is outdated.  I have been sudo get updating or something and am often renewing my Synaptic.  What gives?  Don't repositories refresh i.e.  Did the banshee package come from a banshee repository and when a new one turns up should that not install?

Think of it as a pipeline.  Banshee gets updated at the source but it's not going to get added to the Ubuntu repositories until the Ubuntu devs can check it out and package it and put it out there.  So there's definitely a lag from the time a new version gets rolled out to the time it will be available to a "vanilla" Synaptic set up.

You can always get packages from the developers of your favorite software (if they are available) or you can wait for the "official" release on Ubuntu.  There are benefits to doing it both ways.

---

### Post by Roger_Melly on 2007-03-09
Songwind,
I was under the impression that a repository was a sort of web page with packaged code on it.  Using Synaptic makes the whole thing easier although Add/remove is the easiest as it unpacks and installs everything like a Windows user is used to!!

I had downloaded the new version but on looking inside the box theres a lot of stuff.

I take it my problems arise when I want to "run" or install these packages.  To do so I have to enter a load of commands.......

Whereas the repositories on Ubuntu are those that provide already compliant packages???

---

### Post by Songwind on 2007-03-09
> **Roger_Melly said:**
> Songwind,
I was under the impression that a repository was a sort of web page with packaged code on it.  Using Synaptic makes the whole thing easier although Add/remove is the easiest as it unpacks and installs everything like a Windows user is used to!!

I had downloaded the new version but on looking inside the box theres a lot of stuff.

I take it my problems arise when I want to "run" or install these packages.  To do so I have to enter a load of commands.......

Whereas the repositories on Ubuntu are those that provide already compliant packages???

You're exactly right about what a repository is.  Synaptic (or apt-get, or any other Debian "apt" package management utility) also unpacks and installs the package.

If you download a package manually you have to enter command lines to install them, and you are more likely to have to do extra work to find all the dependencies.

You can add additional repositories to your set up so that Synaptic can install software from other sources.  [Here is a pretty good tutorial from Ubuntu on the subject]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by megamania on 2007-03-09
> **graywizard said:**
> I am far from being a dunce but this linux thing just doesn't work for newbies like me.
Nothing works when you don't know how to make it work. Just think about when you had to learn how to ride a bicycle or to drive a car.

I still know very little about Linux, but I smile when I think of all the problems I had two years ago.

---

### Post by graywizard on 2007-03-09
gnome-look mostly. and it turns out the extensions are not really correct in many places or so I have been told. many of the tar.gz is supposed to be have a . before tar - most of the time I rename and add the . and it works --- sometimes it doesn't the gz. don't the tar.bz or tar.bz2 or whatever doesn't work either.

the .tar.gz never just dropped I had to add it with the install button. the others I also did try with the install button and no luck either.

---

### Post by Roger_Melly on 2007-03-09
Thats kind of the whole Ubuntu experience!

---

### Post by xpod on 2007-03-09
> Xpod, How's your marriage???

hehe..your ipod might be problematic but theres certainly nothing wrong your powers of deduction as far as the xpod are concerned...lol

She`s ok but i`d wait till the end of THIS year and check back on that ok:twisted:

---

### Post by Roger_Melly on 2007-03-10
NOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO and NO again!!!!!!!](*,) ](*,) ](*,) 

I really thought it was sorted.

I had followed the instructions to get around the HAL RAID iPod problem and managed to get the iPod to work.

I have just plugged it in again and NOTHING!!!!

Will I have to go through this each time???

---

