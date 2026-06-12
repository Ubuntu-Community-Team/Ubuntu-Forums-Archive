---
title: "Mac Mini Install, the last leg with Lilo"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Didden on 2007-01-06
Hi, first off, let me say in advance, thank you to anybody willing to help. It would be quite cool to get Ubuntu setup and rolling.

I am trying to triple boot (I would wouldn't I!) with my Mac Mini. It's an intel duo core, with 512mb ram.

eFIt is up and running properly. The Partions are all divided properly. OS X is fine, Windows is installed. Just Ubuntu to go on the /sba3 ...

I have been going through the steps to setup Ubuntu at:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

My only real difference from this guide is that I recognize that the Ubuntu Version is more recent (6.10) than the version in the guide and I am ideally trying to setup a LAMP server not a desktop to simulate a web development environment.

Unfortunately, although I managed to get most of the way through this guide, I came across a few hitches along the way, but managed to feel my way to the end.

The first hitch (and frankly the guide I linked to assumes quite a lot of knowledge) is understanding that you can get into a shell from the installer. I missed that at first, and figured out how to get to a shell from the install CD setup later.

From there I successfully managed to create the bash shell, am I right in thinking CHROOT means change root, and thus the shell type? Anyway, I'm a little familar with Bash on OS X after putting MySQL on it. Onwards.

I created the swap file, although SUDO didn't work, but the commands seemed to run without it. I assumed that the Install Shell defaults to SU, but this was a worrying change from the guide!

Now heres where I think things went really pear shaped... Nano!

I tried to run Nano from CHROOT while in Bash, and it tells me:

```
Error opening terminal: bterm.
```

I found if I quit Bash that I could however get Nano to run outside of it, i.e. in the original installer terminal.

With not much experience with Unix, I don't really understand what the CHROOT is actually taking me from, i.e. what is the initial installer terminal and why Nano runs there but not after I CHROOT into Bash.

I kludged on, trying to follow the guide and managing to edit the files using Nano and create the Lilo.conf file, seemingly succesful, but just not in CHROOT.

I ran the apt-get install lines in the guide, and figured out that it appears that the last module is no longer needed for this version of Ubuntu (linux-kernel-headers).

Now I have reached the last part, where he runs Lilo. But perhaps not unsurprisingly, this refuses to run. It says clearly that Lilo.conf cannot be found saying:

```
etc/lilo.conf: No such file or directory.
```

It does this both inside and outside of Bash. This seems to be the last hurdle in creating an effective boot and so is thus, quite frustrating.

If anyone knows of a better guide for beginners triple booting like this, or can explain why Nano won't run as it should inside of Bash and lastly why Lilo.conf is apparently missing after I have created it and why Lilo won't run, I'd be very grateful.

Many thanks,

- Stephen

---

### Post by kebes on 2007-01-06
Okay this sounds like a very complex support request, but I'll do my best to offer suggestions. Note, the guide you linked to, he says "To install edgy, you will either need a network connection or the DVD version." Is this the case for you?


First off, the "chroot" (change root) command brings you into a new "root" environment at the point specified. That way you can operate in this sub-directory (which will eventually be your actual root on your installation). However in that sub-environment your programs (which are supposed to be stored in "/bin/" or whatever) can't be found. Hence why nano wouldn't load. As you saw you can quickly switch back to the non-chroot environment to use a command that requires it. It seems like you figured all of that out.

You could also copy (or link) files from "/bin/" to the chrooted bin (which is located at /mnt/ubuntu/bin/ in the non-chrooted environment).


As for lilo, I don't think it's available on the standard install CD. At the least I know it's not installed by default. In the instructions it tells you to do:
apt-get install lilo lilo-doc
(along with other installs)...
Did that work? Did you do that in the chrooted environment? If yes, then you should have lilo and lilo.conf at the appropriate locations in your chrooted filesystem. Since nano doesn't work inside the chroot you'll probably be doing something like this:

[in chrooted terminal]
apt-get install lilo lilo-doc
[now in non-chrooted terminal]
nano /mnt/ubuntu/etc/lilo.conf

Does that make sense?

---

### Post by kebes on 2007-01-06
Another thought... Does your chrooted environment have any binaries in it? If you go:

[in chrooted environment]
ls /bin/
ls /usr/bin

Do you get anything? If you get nothing, then try doing:

[in non-chrooted environment]
mount --bind /bin /mnt/ubuntu/bin
mount --bind /usr/bin /mnt/ubuntu/usr/bin

That way you should have access to "nano" and "apt-get" inside the chrooted environment. Then you can install lilo and do "nano /etc/lilo.conf" inside your chrooted environment.

---

### Post by Didden on 2007-01-06
Thanks for responding Kebes. Indeed, it does seem more complex when I went through it than I'd hoped, although I think you're on the right path by suggesting that lilo has been installed in the wrong root.

The guide clearly stated that these things should be run inside of the CHROOT that is setup in the middle of the guide and takes me into Bash.

Because I couldn't run Nano in Bash, it figures that I've setup everything in the wrong root and thus the pain and the Lilo.conf missing.

Im still reading through your other message. BRB.

---

### Post by Didden on 2007-01-06
> Note, the guide you linked to, he says "To install edgy, you will either need a network connection or the DVD version." Is this the case for you?

I have the downloaded CD-ROM for either desktop or server, no DVD sadly. Is it possible to download this? I did get the network working successfully through wireless, and the Auto DHCP was a success.

> First off, the "chroot" (change root) command brings you into a new "root" environment at the point specified. That way you can operate in this sub-directory (which will eventually be your actual root on your installation). However in that sub-environment your programs (which are supposed to be stored in "/bin/" or whatever) can't be found. Hence why nano wouldn't load. As you saw you can quickly switch back to the non-chroot environment to use a command that requires it. It seems like you figured all of that out.

In an indirect way, yeap, but the root concept is new to me, as my command line days are rooted in DOS (No pun intended). Am I right in thinking that the root, is the very start of your system essentially, and all the sub directories sit there? If thats the case, is the Install Terminal starting from a Root thats not actually on the Hard Drive, but purely in Memory? (Remember the install saying something about this).


> You could also copy (or link) files from "/bin/" to the chrooted bin (which is located at /mnt/ubuntu/bin/ in the non-chrooted environment).

It seems the guide does not include that link or copy as you suggest here. I know you mention this more in your second reply.

> As for lilo, I don't think it's available on the standard install CD. At the least I know it's not installed by default. In the instructions it tells you to do:
apt-get install lilo lilo-doc
(along with other installs)...

Did that work?


Yes... however...

> Did you do that in the chrooted environment?

I am pretty sure this didn't work in the Chrooted environment, as it didn't understand the command. I will rerun the install and check this hypothesis.

There is a fault in the guide, in that the last module for the linux-kernels isn't needed, I've seen this catch other folks out I discovered (When i searched for the fault). So I skipped this as others seem to have successfully.

> Does that make sense?

Getting there! Im thinking at this stage it's best to just do a quick reinstall up until Grub fails, and then try again using your suggestions.

- Stephen

---

### Post by kebes on 2007-01-06
> **Didden said:**
> I have the downloaded CD-ROM for either desktop or server, no DVD sadly. Is it possible to download this? I did get the network working successfully through wireless, and the Auto DHCP was a success.

Well if you have the network working in the LiveCD environment then that's great... because you'll be able to install any software you need using "apt-get". (I'm guessing this is why he suggests using the DVD--because it will have lilo on it.)


> In an indirect way, yeap, but the root concept is new to me, as my command line days are rooted in DOS (No pun intended). Am I right in thinking that the root, is the very start of your system essentially, and all the sub directories sit there? If thats the case, is the Install Terminal starting from a Root thats not actually on the Hard Drive, but purely in Memory? (Remember the install saying something about this).

Yes, "root" refers to the base of the filesystem. It's the lowest-level directory, the one that is just "/". (It's confusing because "root" also refers to the "superuser" because only that user has control over the filesystem starting at the root-level...).

If you look at the commands the tutorial suggests:
```

mkdir /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash

```

-You start out in the LiveCD filesystem. It has a root "/" with all kinds of files in it. (Resident in memory or on the CD.)

-First you make a new directory called "/mnt/ubuntu" (you could call it anything really).

-Then you "mount" the parition sda3 to the directory you just created. sda3 means that it is a SATA drive ("sd"), and it's the first drive ("a"), and we're talking about the third partition ("3"). So basically what we're saying is that now all the files/directories on the third partition (where you want to install Ubuntu to) will be located at "/mnt/ubuntu" in the LiveCD filesystem. This is convenient because it lets us now work with the partition.

-The next line creates a new "process" directory in your new filesystem.
-The next line then "binds" (copies) all the devices from the LiveCD root filesystem to the location "/mnt/ubuntu/dev". Thus, your hard drive partition will now have access to the devices that were autodetected when you booted your LiveCD

-Lastly we "chroot" into "/mnt/ubuntu". After changing root, we now "appear to be" inside the hard drive partition 3, which is the partition that will eventually become your Ubuntu install. This is neat because now anything we do is basically being done inside your new filesystem. So if, inside this environment, you install a new program (with apt-get), then you're actually installing it to your hard drive, and it will be there after you finish the install.



So basically "chroot" is a great way during manual installs to "step into" the new root filesystem that you are trying to set up. It can also be used to "jail" a user into a sub-region of the filesystem, making them unable to access or even see the "true root".


> It seems the guide does not include that link or copy as you suggest here. I know you mention this more in your second reply.

Yes and this seems weird to me. The guide tells you to setup proc and dev but no binaries, so how can "apt-get" and "nano" possibly work in the chrooted environment? So my suggestion is to run:
mount --bind /bin /mnt/ubuntu/bin
mount --bind /sbin /mnt/ubuntu/sbin
mount --bind /usr/bin /mnt/ubuntu/usr/bin

Just before the "chroot" step. Then continue following the guide.


> Getting there! Im thinking at this stage it's best to just do a quick reinstall up until Grub fails, and then try again using your suggestions.

I think you may actually be reasonably close to getting this all working. Good luck...

---

### Post by rccharles on 2007-01-07
> **Didden said:**
> Hi, first off, let me say in advance, thank you to anybody willing to help. It would be quite cool to get Ubuntu setup and rolling.


On the PPC Macs, you can hold down the option key ( on on a PC keyboard, this is the alt key) to get the list of bootable partitions. On my iMac when I hold down the control key, I can see an icon for Ubuntu.  Maybe the Intel Macs work the same.

Have you thought about virtual mahcines?  This would let you run all three OSs at the same time.

Have you thought about Parallels which creates virtual machines?
  [http://www.parallels.com/en/products/desktop/](http://www.parallels.com/en/products/desktop/)

Vmware has a free beta virtual mahcine.  See:
  [http://www.vmware.com/products/beta/fusion/](http://www.vmware.com/products/beta/fusion/)

Robert

---

### Post by Didden on 2007-01-07
Excellent reply! Thanks Kebes, is their some sort of reward I can nominate you for? LOL

With your description, I've totally clicked now with that the Chroot is doing, and it's relation to the Live CD thanks.

It's clear to me now, after putting in the desktop CD, that it is different from the Server CD in that I can boot to the nice shiny desktop on the CD and play with Gnome, which the Server CD doesn't let you do.

Im going to have another go with the advice you've given and see what happens. Probably be tomorrow now, as it's midnight here alas.

Speak soon,

- Stephen

---

### Post by Didden on 2007-01-07
Hi Robert,

Thank you for the suggestions.

At present I can't see a bootable Linux partition, it's there, and from the live CD I can see it, I just formatted it for example using Ext 3.

Because there is no loader as such (The lilo issue), I think rEFIt is not showing it yet. Fingers crossed it does when it is ;)

I did consider a virtual environment, this would at least allow Grub to work on the install and let everything go smoothly.

I am not sure if Parallels would work 1.0 as I understood this was only supported Windows. I do know the new VMware fusion beta supports Linux, but frankly, this ran like a dog with fleas, worms and a broken leg with it's Debug mode on. I am also locked into 512 MB of RAM, so any virtual machine runs a bit slow with OS X eating what it does.

The alternative, buying Parallels is a luxury I can't really afford. I have a pot of money, and I am trying to start my own businesses online (My background is in web development, but on Windows originally).

My ultimate goal is to have the mac mini act as a development web server (maybe even a live one in time). Because I am shifting my skills over to PHP etc i'd like to mirror the typical environment found on my live hosts virtual (linux) environment. The more I can learn about Linux the better basically. OS X comes in very close, and I can, and have had it setup with MySQL and PHP. But it's not quite the same structure, and having Apache 1.3 built in is sweet, but doesn't mirror my live hosts linux setup (Apache 2.0).

I will resort to OS X again, if I can't get this up and running, but I think with enough gusto and the fine folks like Kebes and yourself's help, I'll get the bugger running.

- Stephen

---

### Post by rccharles on 2007-01-07
> **Didden said:**
> 
I did consider a virtual environment, this would at least allow Grub to work on the install and let everything go smoothly.

I am not sure if Parallels would work 1.0 as I understood this was only supported Windows. I do know the new VMware fusion beta supports Linux, but frankly, this ran like a dog with fleas, worms and a broken leg with it's Debug mode on. I am also locked into 512 MB of RAM, so any virtual machine runs a bit slow with OS X eating what it does.

The alternative, buying Parallels is a luxury I can't really afford. I have a pot of money, and I am trying to start my own businesses online (My background is in web development, but on Windows originally)

Seems parallels has tested a bunch of OSs now.  See:
[http://www.parallels.com/products/desktop/os/](http://www.parallels.com/products/desktop/os/)

Parallels is fairly expensive.  I might speed up your testing since you could run all OS at the same time.

> 
My ultimate goal is to have the mac mini act as a development web server (maybe even a live one in time). Because I am shifting my skills over to PHP etc i'd like to mirror the typical environment found on my live hosts virtual (linux) environment. The more I can learn about Linux the better basically. OS X comes in very close, and I can, and have had it setup with MySQL and PHP. But it's not quite the same structure, and having Apache 1.3 built in is sweet, but doesn't mirror my live hosts linux setup (Apache 2.0).

I will resort to OS X again, if I can't get this up and running
- Stephen
Have you heard of Fink?  "The Fink project wants to bring the full world of Unix Open Source software to Darwin and Mac OS X." See:
[http://fink.sourceforge.net/](http://fink.sourceforge.net/)

The package page is here:
[http://pdb.finkproject.org/pdb/index.php?phpLang=en](http://pdb.finkproject.org/pdb/index.php?phpLang=en)

Fink includes Apache 2.


Thanks for the fine words.  Kebes posts are great.

Robert

---

### Post by rccharles on 2007-01-07
> **Didden said:**
> Hi Robert,


At present I can't see a bootable Linux partition, it's there, and from the live CD I can see it, I just formatted it for example using Ext 3.

Because there is no loader as such (The lilo issue), I think rEFIt is not showing it yet. Fingers crossed it does when it is ;)

n

Maybe you could user superGrub to get it to boot.  You put superGrub on a cd and boot the cd. It has lots of options and says you can boot a partition without a MBR.

Main page:
 [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
 [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

I haven't tried boot a partition with superGrub.

Robert

---

### Post by rccharles on 2007-01-09
> **rccharles said:**
> Maybe you could user superGrub to get it to boot.  You put superGrub on a cd and boot the cd. It has lots of options and says you can boot a partition without a MBR.



I put superGrub on a CD and got it to boot a partition without Grub/LILO.  Here is what I did:

burnt the cd on my Mac with Mac OS 10.4 in the terminal:
  hdiutil burn fileNameWhichEndsIn.iso

I run this test in Virtual PC

boot from the CD

press enter on English Super Grub Disk

press return & space key a couple of times afer reading the messages

cursor down to Gnu/Linux

press enter to read message

cursor down to Boot Gnu/Linux Directly and press enter

cursor down to IDE ( or SCSI ) and press enter


...........


System now BOOTS!!!

The first time I tried the boot went for awhile and then failed, but worked twice since.  I guess I had played around too much in superGrub.

The screen shots page will give you some hints on how to use Grub.
  [http://supergrub.forjamari.linex.org/screenshots.php](http://supergrub.forjamari.linex.org/screenshots.php)

Robert

Robert

---

### Post by Didden on 2007-01-15
Kebes, Rc,

I actually managed to get Ubuntu installed today, but really not in the way I expected and not to a satisfactory end result. Although, I found a technique that I haven't seen documented, which I hope is useful for anybody else doing this.

I have been trying both the Ubuntu DVD and the Ubuntu Server CD.

With both, Grub fails to install as expected, but on a text install for both versions the installer doesn't just "give up" like on the normal GUI install. The text install gives you several more options. One of these options is to install Lilo, right there, as part of the install.

On the Server CD, this actually worked, and I rebooted into a nice erm... empty shell. One Ubuntu Server, but with no GUI sadly.

I figured I should try the same technique on the DVD, but this fails! Giving a Lilo "general error 1" fault.

As a precaution, I rebooted, and used the rEFIt Parition Tool, which "fixes" the partitions. I have a feeling while it failed, and will be trying again, because I made a configuration change to the swap partition, it's unavoidable if you use a swap file, and I think this affects the rEFIt fix.

I tried eLilo, which is a mistake, as this screws up the boot, by making the first Mac Mini partition bootable, which is far from ideal as it screws with OS X, so I'm doing a clean slate and trying again.

I also think I can get this bugger triple booting as was the original goal without to much trouble now I know how rEFIt fixes the partitions and MBR tables.

- Stephen

PS: Rccharles SuperGRUB CD failed to boot for me, it just hung at "loading stage 2", if it did boot nicely, I think this would indeed allow you me get GRUB installed after a rEFIt fix, but it doesn't seem to work on my particular Mac Mini for some reason.

---

### Post by kebes on 2007-01-15
> **Didden said:**
> On the Server CD, this actually worked, and I rebooted into a nice erm... empty shell. One Ubuntu Server, but with no GUI sadly.

Not having a GUI in the server install is easily fixed. You can install the standard ubuntu desktop with:

sudo aptitude install ubuntu-desktop

Thus, if you can get the Server version installed properly, then you can easily convert it to being a functional desktop system. (I believe some of the configs and even the kernel are server-optimized, but that shouldn't be much of a concern...)


So if you can get the system working with the server install and LILO, it would seem that you are very close to a solution...

---

### Post by Didden on 2007-01-15
YES!

I'm looking at a nice Ubuntu Desktop Install! 

Woohoo! I'll post the details shortly - but I think I've found a completely simple and code free way of installing Ubuntu on a Mac. I'll post this shortly.

Thanks for your help guys!

- Stephen

---

