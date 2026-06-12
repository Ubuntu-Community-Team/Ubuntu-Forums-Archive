---
title: "Cannot boot imac g3"
date: 2009-05-19
forum: Apple Hardware Users
---

### Post by Albertint on 2009-05-19
Now, I think this is a pre-existing problem, as I cannot seem to boot my imac g3 (I'm getting that flashing question mark folder icon). I have none of the original mac os 9/os x install disks, and I've already tried restarting the pram. Help quickly, I'm trying to acomplish this: [http://ubuntuforums.org/showpost.php?p=2845897&postcount=5](http://ubuntuforums.org/showpost.php?p=2845897&postcount=5), and so far I've gotten this:
[IMG]http://lowendmac.com/conachey/05/art0116/question_mark.gif[/IMG]
[SIZE=1]Well, this is obviously an older version of mac os, but I mean the mac os 9 version, so...[/SIZE]

I have an idea of how to fix this:
Is there any way to boot debian from the net install disc I created, or is this futile a attempt, and I should go for plan b...? 

Thanx,
  Albertint ):P

---

### Post by stream303 on 2009-05-20
The project you have described is about the only reasonable way to get anything useful out of a G3 iMac.

I'm assuming that since you don't have the original mac-os disks, and that you can't even get that to boot, you are wanting to dedicate the whole machine to Linux.

One problem you may be running into is if a larger-than-oem drive has been placed into the machine at some later date.  If that is the case, some G3 iMacs have an 8gb root-partition boundary limitation.  In other words, the install goes just fine, but upon reboot you see the above.

To make sure the system gets the special apple-partitions made, in addition to the normal linux root and swap is to do the following:

If you DON'T have the 8GB partitioning limitation (you won't know until you try or know the actual size of the disk) just allow guided partitioning to "use the whole disk" and follow the install.

But it appears you have already done this.

This time, reinstall again, BUT now, choose MANUAL PARTITIONING.  Delete everything but the first two special apple partitions.  Now define the third partition (root) to be under 8gb, make it 7gb to be safe.  Make a 4th partition of swap about 256mb.  (not knowing if that early imac was 64 or 128mb for example - this should get you started).  Then partition the rest of the disk for /home

At least this will get you started, and then you can fine-tune it afterwards.  (In my case after the system was shown to be workable, I'd just do this whole procedure all over again now that you will be able to discover how much ram you have, the size of the disks, etc)

Just remember our old Ubuntu nemesis of the splash screen should it just come up black.  (use *nosplash* as a kernel parameter)  - That is if you are using Ubuntu - with Debian, no worries about a splash screen.

Even though the following is geared towards pc's, and seems ubuntu specific, it has more good info you might want to look at:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Debian or Ubuntu - either way doing a very minimal netinstall is a great way to go for low-spec G3 iMacs, because you know up front the limitations!

This would be one G3 I wouldn't mind seeing come up! :)

---

### Post by Albertint on 2009-05-21
Thanks man, I'll try this out soon enough.
(watch this spot)

SIDE NOTE: Now I know I haven't gotten it to work for sure yet (about 2 hours soon enough, I'll be near the imac), I was wondering if instead of fluxbox, that xfce would be a safe option for my computers processor and ram requirements at their minimum

---

### Post by stream303 on 2009-05-21
It all depends on your amount of tolerance for pain.

The thing is, no matter if you choose a DE Desktop-Environment such as XFCE, or just a WM Window-Manager like Fluxbox,  if you do anything major like bring up a browser with many tabs, GIMP, etc, the programs themselves will tend to make a 64mb box sluggish.

If you must have a desktop environment, at the very best I'd suggest LXDE, which is conveniently part of the Debian XFCE+LXDE installation image.  Leafpad, lxterm etc are right from LXDE, so you may want to look into that first.  XFCE is not so light as many people think, especially with all the Ubuntu-isms thrown in.  Even Debian's lighter version of xfce may not be a nice fit for what you have.  You'll have to be the judge.

Fluxbox is a very safe bet as a window manager, but so is IceWM, OpenBox, etc.  All are very light on resources - but that is just your "desktop" interface - the programs you run will tend to make the real difference.

Ideally, to get the most out of limited ram and resources, you may want to look into commandline programs running in an xterm or two.

For instance, when I want to listen to streaming ogg-vorbis audio, I use *ogg123* from the vorbis-tools package, rather than rely on any graphical package.  Leafpad is nice and light gui editor, but I just prefer to run nano in an xterm.  (Actually vi, but you get my point)  Example:

```
ogg123 -b 256 http://radio.hbr1.com:19800/ambient.ogg
```

No need to remember this - just make it an alias or shell script.

I then call up another xterm while this is running, and use *alsamixer* to control my volume levels.  I don't need Totem, Rhythmbox etc to do this even though on my 1.5gb G5, I could.

In the end, you'll have to be the judge, but what is very exciting about a low-memory box is that when you try to make the most of it, and want to learn the commandline, or become proficient at using low-resource gui programs, you learn something that will far outlast the life of your iMac and can take with you wherever you go or whatever architecture you find yourself using.

Personally I'd try seeing if LXDE fits the bill.  You can even easily test it on another pc box running Knoppix 6.0.1 live, and see if it is to your liking:

[http://www.knoppix.org/](http://www.knoppix.org/)

Knoppix, like Ubuntu, is Debian based of course.

NOTE: if you do decide to go ahead with Debian for the iMac, let us know since there is a very important addition to help speed up that slow disk even more with the *relatime* option in /etc/fstab on your ext3 partitions, since Debian doesn't include it by default - cross that bridge when you get there...

Good times ahead if you keep it fun - which is sometimes a problem with ppc. :)

---

### Post by Albertint on 2009-05-21
Actually, considering the imac's previous owner has a job at a local university setting up the campus macs, I doubt he left the standard 64mb of ram in there, but I'll try out lxde and tell you what I think.

---

### Post by Albertint on 2009-05-21
Curses, it didn't work... [SIZE=3]again! ](*,)
[SIZE=1]And btw, the computer has 30GBs of memory, so I'm assuming that what you said was true... I did all the partitioning options you told me to. Could there be any detail you could rattle off to me that maybe I missed...
[/SIZE]
[/SIZE][SIZE=3][SIZE=1]I really need this to work... plan c?[/SIZE][/SIZE]

---

### Post by tiresia on 2009-05-21
You booted the Debian Installer and you made 
1. bootstrap partition
2. >8GB Partition for /root (ext3)
3. /home Partition
4. SWAP partition

You installed the OS without errors (also the bootloader was installed)
When you restart, you get the same screen as in the first post?

---

### Post by stream303 on 2009-05-21
Tiresia's right.  However, we may be shooting in the dark.  What exactly is the model of your G3 iMac?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Have you ever known that iMac to work?  Is it possible that you received it pretty much "doa", but your friend gave it to you to "see if you can fix it?"  :)

It is possible that there is a major hardware issue preventing this from working and not the 8gb limitation at all depending on the model!

---

### Post by Albertint on 2009-05-21
Ok, so currently, I'm going on tiresias plan. My setup for partitioning (which I've paused for the moment to make this reply) is as read:

Apple default partition: 32.3 KB
At #2, a Boot (Worldboot something or other as the instller interface calls it) Partition: 1.00 MB
at #3 (my first homebrewn partition on the list) An 8.0 GB partition for the os, which I titled debain, an ext3 partition, and set its root file to well, literally, "/root", is that the correct?
at #4, 256 MB for the swap partition, like, if you saw the monitor, and since there is no divider telling you what is what, there is three "swap"s in a row next to #4.
#5, the latter memory for files is 21.8 GB of space and is ext3, as well as being linked to /home...

Does this sound right to try again? :(

---

### Post by stream303 on 2009-05-21
Sounds great but DON'T sit on the 8gb boundary!  Make it no larger than **7gb** to be safe.  So 8gb is the spec, but I've seen quite a few pull their hair out when it failed because of being on that knife-edge. :)

---

### Post by Albertint on 2009-05-21
But its a 30gb hard drive... did the ppl you know who had these problems have a hard drive larger than 8GB?

---

### Post by tiresia on 2009-05-21
The easiest way is in two steps:

1. choose the GUIDED partioning (with the option for a /home partition)
The installer will set for you everything you need to install Debian.
And it will ask you if you accept the solution

2. Edit the proposed partition scheme, so that it fits to your need - i.e. resize the /root partition if it's bigger than 8GB. Don't touch the Bootstrap partition

---

### Post by Albertint on 2009-05-21
#-o:icon_frown:](*,)
... Nothing. I did what you said, Tiresia.

---

### Post by tiresia on 2009-05-22
> **Albertint said:**
> #-o:icon_frown:](*,)
... Nothing. I did what you said, Tiresia.
Questions:
When you say nothing, does it means that you get the same screen as in your first post, or that you get a black screen?
Which version of Ubuntu are you trying to install?
Did you install the system with the default desktop or just the 'basic' system? 
Do you get any message during installation?

---

### Post by stream303 on 2009-05-22
AHA!  I think I found the problem.  I was reading so fast I didn't recognize something that burned me when I first started out:

> at #3 (my first homebrewn partition on the list) An 8.0 GB partition for the os, which I titled debain, an ext3 partition, and set its root file to well, literally, "/root", is that the correct?

Nope - not correct.  Go ahead and give it the name of **root** (not debian), and then when asked where you want to mount it, just enter a forward-slash only: **/**

Oh man, this is a gotcha.  The "root" directory is just a forward slash as it needs no name being the parent of all directories, hence / is aka root.  HOWEVER, there is also a directory underneath it with the actual name of root as well, which is normal, which leads to this confusion.  Don't sweat it - just use the name root, and then tell it to mount at nothing but a forward slash /

Make this bad-boy of "/" (no quotes) no larger than 7gb and follow through with the rest of the partitioning..

I guess in speaking terms, we are just saying "I want to mount the partition I call root at the / mountpoint"

I have long wanted to know who was responsible for /root, which really means "root-root" in geek-speak. :)

---

### Post by Albertint on 2009-05-22
> **tiresia said:**
> Questions:
When you say nothing, does it means that you get the same screen as in your first post, or that you get a black screen?
Which version of Ubuntu are you trying to install?
Did you install the system with the default desktop or just the 'basic' system? 
Do you get any message during installation?

> **stream303 said:**
> AHA!  I think I found the problem.  I was reading so fast I didn't recognize something that burned me when I first started out:



Nope - not correct.  Go ahead and give it the name of **root** (not debian), and then when asked where you want to mount it, just enter a forward-slash only: **/**

Oh man, this is a gotcha.  The "root" directory is just a forward slash as it needs no name being the parent of all directories, hence / is aka root.  HOWEVER, there is also a directory underneath it with the actual name of root as well, which is normal, which leads to this confusion.  Don't sweat it - just use the name root, and then tell it to mount at nothing but a forward slash /

Make this bad-boy of "/" (no quotes) no larger than 7gb and follow through with the rest of the partitioning..

I guess in speaking terms, we are just saying "I want to mount the partition I call root at the / mountpoint"

I have long wanted to know who was responsible for /root, which really means "root-root" in geek-speak. :)

Hmm, well, I don't think that what stream is suggesting will work, though I'll contact my friend and see what he says.
PS: Tiresia, I'm installing Debian, not Ubuntu. And I'm aiming for the barebone interface (no gui, nicknacks), so as to add my own WM or DE later...

---

### Post by stream303 on 2009-05-22
Don't take my word for it. Here's a snippet from /etc/yaboot.conf for the bootloader showing the 3rd partition (/dev/sda3 in my case, in your case it might be hda3) as being root from my Debian squeeze/testing install:

```
boot=/dev/sda2
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:
ofboot=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:
[b]partition=3
root=/dev/sda3[/b]
```

Now take a look at /etc/fstab showing that root (/dev/sda3) is mounted at "/" (no quotes)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**/dev/sda3       /               ext3    errors=remount-ro,relatime 0       1**
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Be sure to see this excellent thread for doing exactly what you want to do in Debian, although many of the suggestions are also workable for Ubuntu naturally:

[http://forums.debian.net/viewtopic.php?f=16&t=12256](http://forums.debian.net/viewtopic.php?f=16&t=12256)

.

---

### Post by tiresia on 2009-05-22
Can you please answer to my question:
When you that it does not work, does it mean that you get the same screen as in your first post, or that you get a black screen?

---

### Post by Albertint on 2009-05-24
Sorry, tiresia...
Yes, I get the exact same error from the beginning... I have acquired a copy of the mac os 9 cd and have "initialized" 27.?gbs of the hard drive as "untitled". Maybe reinstalling mac os 9 will hope

---

