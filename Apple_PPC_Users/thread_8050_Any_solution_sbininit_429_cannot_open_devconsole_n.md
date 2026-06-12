---
title: "Any solution?: /sbin/init/: 429: cannot open dev/console: no such file"
date: 2004-12-13
forum: Apple PPC Users
---

### Post by menachem on 2004-12-13
[COLOR=Red]*****EDIT*** This problem has been solved. To skip straight to the solution go [here](http://ubuntuforums.org/showpost.php?p=42546&postcount=14) ***EDIT*****[/COLOR]

Hello,

I installed Ubuntu PPC on a PowerMac G4 (Dual Boot with Panther) and got the following error:

[b][TUX LOGO]
audit (*string_of_numbers*): initializes
starting ubuntu
pivot_root no such file or directory
/sbin/init/: 429: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init![/b]

A quick search on the Ubuntu Forum reveals that other people have had this problem as well:

[http://www.ubuntuforums.org/showthread.php?t=7156](http://www.ubuntuforums.org/showthread.php?t=7156)
[http://www.ubuntuforums.org/showthread.php?t=7784](http://www.ubuntuforums.org/showthread.php?t=7784)
[http://www.ubuntuforums.org/showthread.php?t=5285](http://www.ubuntuforums.org/showthread.php?t=5285)
[http://www.ubuntuforums.org/showthread.php?t=7075](http://www.ubuntuforums.org/showthread.php?t=7075)
[http://www.ubuntuforums.org/showthread.php?t=7452](http://www.ubuntuforums.org/showthread.php?t=7452)

And others.

I was able to install Debian Sarge RC1 without a problem, but I couldn't get Ubuntu to work. (Although Ubuntu did do a better job of automatically finding and configuring my network card).



Has anyone found a resolution to this?

Suggestions included:
recompiling the kernel
reburning the cd
editing initrd.gz

If someone did get this solved, could they post step-by-step directions for solving this problem?

Thanks,
menachem

---

### Post by Random Juju on 2004-12-13
Hey.

I'm having an identical problem with a Blue/White G3.  I think I may have actually found the cause of the problem, but I'm really not sure how to actually correct it.

The Ubuntu installer detects my two hard drives as hdc and hdd.  Everything else (i.e. Ubuntu itself upon booting) calls them hda and hdb.  It seems that the installer is somehow getting confused as to which bus my drives live on.  Consequently, it places references to hdc EVERYWHERE, whereas they should really be references to hda.  I imagine that this is what's confusing pivot_root.

I booted from a Gentoo livecd and poked around inside the installation, finding and replacing several references to hdc.  The boot process now goes further, but still has the same problem, leaving me to suspect that there's yet another reference that I (and grep -r) haven't found or worse, that it's somehow in a binary file.

In another thread, somebody mentioned that we should be able to edit /sbin/init to correct a bad reference to dev/console on line 429, but my /sbin/init file appears to be a binary.  Having checked with several other users of several other distributions (all of whom have similar-looking init files), I'm inclined to believe that the user that suggested editing /sbin/init may be wrong, or at least omitting a few critical steps.

I'm very curious as to whether anybody else with this problem is experiencing the hda/hdc switch during installation.  If so, how would one reverse the change?  Failing that, where are all of the referenes that would need to be manually fixed?

Thanks!

(Edit:

To be clear, I opted to install the 2.6.8 kernel at install-time and the MD5 checksum and the expert mode "verify this CD" test both indicate that the media is fine)

---

### Post by Random Juju on 2004-12-13
Booting the installer with the ide=reverse argument does not solve the problem.  The CD drive the installer lives on is still hda, and the two hard drives are still hdc and hdd.

---

### Post by Random Juju on 2004-12-15
Installing with reversed drives and then booting the installed system with the ide=reverse problem doesn't work, either.

---

### Post by Rohan on 2004-12-22
I'd say that init is a binary and that we'll have to get it fixed by the ubuntu team (file a bugzilla report) or maybe simply replace the init from a good debian install?

---

### Post by menachem on 2004-12-22
[QUOTE=Rohan]I'd say that init is a binary and that we'll have to get it fixed by the ubuntu team (file a bugzilla report) or maybe simply replace the init from a good debian install?[/QUOTE] I think that it is more likely that it is a file **/sbin/init** is reading that is causing the error.
If I remember correctly, **/sbin/init** uses information in **/etc/inittab** to load things during startup. What may be happening is that there is an error in line 429 of **/etc/inittab** that is missconfigured. It may be as easy as editing the **/etc/inittab** found in the initrd.

Menachem

---

### Post by Rohan on 2004-12-22
do you care to try it.. because I just installed Sarge and I don't want to hav eto go through it all over again if your method doesnt work

---

### Post by Random Juju on 2004-12-23
Mm..  nothing's jumping out at me, but I'll keep fiddling with it.  /etc/inittab itself doesn't even approach that many lines, but I've found a reference to /dev/console in one of the many scripts it calls.  I can't spot anything wrong with that line, though (logically or syntactically).

I guess the next step is to start liberally throwing echos around.

---

### Post by Random Juju on 2005-01-01
It should be pointed out that the development people are hard at work on this problem.  See:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=3363](https://bugzilla.ubuntu.com/show_bug.cgi?id=3363) and
[https://bugzilla.ubuntu.com/show_bug.cgi?id=496](https://bugzilla.ubuntu.com/show_bug.cgi?id=496)

---

### Post by Rohan on 2005-01-02
hmm that is nice to know..... hopefully we'll have a fix soon

thanks for the update

---

### Post by Random Juju on 2005-01-02
So I modified the loadmodules file on the ramdisk as suggested in [https://bugzilla.ubuntu.com/show_bug.cgi?id=496](https://bugzilla.ubuntu.com/show_bug.cgi?id=496).  Now when I try to boot, I get the following:

[tux logo]
PCI: Cannot allocate resource region 0 of device 0000:01:02.0
audit(1104724407.122:0): initialized
mount: mount point proc does not exist
cat: proc/sys/kernel/real-root-dev: No such file or directory
/linuxrc: 9: cannot create proc/sys/kernel/real-root-dev: Directory nonexistent
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0)

I half-suspect that this may have something to do with how I created the new initrd.img (boot from a livecd, chroot into the Ubuntu install, mount the initrd image, copy the contents, modify the loadmodules file, create a new image from the copy, replace the old image).  I'd be happy to post the details of what I did, if anybody's interested.

Any more ideas?  Thanks!

---

### Post by afonit on 2005-01-03
I am also getting this exact error, on my pc
I have a single HD and it is a single partition.

---

### Post by Random Juju on 2005-01-03
Further details..  it looks like my new initrd DID get screwed up.  In copying the contents of the bogus ramdisk to the new ramdisk, I get (but missed the first time):

cp: will not create hard link `./initrd/devfs' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/mnt' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/proc' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/scripts' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/sys' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/tmp' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/var' to directory `./initrd/dev2'

Why they would be hard links in the first place, I don't know.  Attempting to fix the problem by creating empty directories.  If that doesn't work, I'll just go ahead and try it again with hardlinks.  Either way, I'll report back with what happened.

---

### Post by Random Juju on 2005-01-03
WOO!  WE HAVE A SOLUTION!

Okay.  So here's what needs to happen to make this work on a blue/white G3 or similar box...

1)  Go through a normal installation process, but do not reboot at the end.
2)  When the installer prompts you to remove the installation CD and reboot, press ctrl-option-F2 (same as ctrl-alt-F2) to get to a terminal.
3)  From the terminal, type ```
chroot /target
```  This will use the freshly installed Ubuntu system as the working root (that is, you'll be working with the file tree and binaries that you just installed).  You will notice that the command prompt changes.
4)  Type ```
mkdir /mnt/initrd
```  This will create a mount point for the initrd (initial RAM disk) image that we're about to modify.
5)  Type ```
mount -o loop /boot/initrd.img-2.6.8.1-3-powerpc /mnt/initrd
```  You may have a different kernel/initrd version.  I trust your ability to improvise here.  This mounts the initrd image to the mountpoint we just created using a loopback device.  Don't sweat the details there if you're not comofortable with them -- basically we've put a bunch of files someplace where we can get at them easily.
6)  We can't directly edit the contents of the initrd image, so we'll copy them somewhere else, make the necessary changes, and then create a new initrd image.  Copy the contents of the ramdisk by typing ```
cp -a /mnt/initrd /tmp
```.  You should now have an "initrd" directory in /tmp.
7)  Switch to the directory of the new copy with ```
cd /tmp/initrd
```
8 )  If you're like me, you'll have seen the following when you made the copy:

```
cp: will not create hard link `./initrd/devfs' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/mnt' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/proc' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/scripts' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/sys' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/tmp' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/var' to directory `./initrd/dev2'
```

If you see those warnings, create the directories that were omitted.  In the case of the warnings above, use:  ```
mkdir devfs mnt proc scripts sys tmp var
```.
9)  What's actually causing the booting problem is the "loadmodules" file.  Use "nano" (a lightweight text editor -- `nano loadmodules` to edit the file) to modify the file to look like this:

```
modprobe -k  unix 2> /dev/null
modprobe -k  sd_mod
modprobe -k  pdc202xx_new > /dev/null 2>&1
modprobe -k  aec62xx > /dev/null 2>&1
modprobe -k  cmd64x > /dev/null 2>&1
modprobe -k  generic > /dev/null 2>&1
modprobe -k  hpt34x > /dev/null 2>&1
modprobe -k  hpt366 > /dev/null 2>&1
modprobe -k  ns87415 > /dev/null 2>&1
modprobe -k  pdc202xx_old > /dev/null 2>&1
modprobe -k  sc1200 > /dev/null 2>&1
modprobe -k  siimage > /dev/null 2>&1
modprobe -k  sl82c105 > /dev/null 2>&1
modprobe -k  trm290 > /dev/null 2>&1
modprobe -k  via82cxxx > /dev/null 2>&1
modprobe -k  ide-disk
```

Save your changes by typing ctrl-o (and then enter) and then close nano by typing ctrl-x.
10)  Now it's time to turn the temporary directory back into a ramdisk.  Do that by backtracking to the /tmp directory (`cd /tmp`) and typing ```
mkcramfs initrd initrd.img-2.6.8.1-3-powerpc
```
11)  Replace the old image with the new one by typing ```
mv /tmp/initrd.img-2.6.8.1-3-powerpc /boot/initrd.img-2.6.8.1-3-powerpc
```
12)  You're done.  If you'd like to clean up, you can (but don't need to) remove the temporary files by typing ```
rm -rf /tmp/initrd
```  Either way, press ctrl-option-F1 (ctrl-alt-F1) to bounce back to the Ubuntu installer.  Select "continue" to reboot into your new (and working!) Ubuntu system.

Whew ;)

Major thanks again to everybody who contributed to bugs 496 and 3363 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=496](https://bugzilla.ubuntu.com/show_bug.cgi?id=496) and [https://bugzilla.ubuntu.com/show_bug.cgi?id=3363](https://bugzilla.ubuntu.com/show_bug.cgi?id=3363)).

---

### Post by Rohan on 2005-01-04
hmm... looks good.. haven't had a chance to try it yet. Thanks for all the leg work though

---

### Post by savetheclocktower on 2005-01-05
My god -- this WORKS!  Huge thanks go to Random Juju for his work on this.

---

### Post by Random Juju on 2005-01-05
Glad to hear it's working for other people.

Be warned that, unless you patch initrd-tools, this will happen again every time you update your kernel.

menachem, can you modify the thread's subject to reflect that we actually have a solution?

Thanks!

---

### Post by Rohan on 2005-01-05
this is probably a dumb question.. but what do you mean by patch initrd-tools

---

### Post by Random Juju on 2005-01-06
[QUOTE=Rohan]this is probably a dumb question.. but what do you mean by patch initrd-tools[/QUOTE]

Not at all.

Bug #496 explains this all in slightly more technical terms, but the idea is basically this...

There's a script that generates a new initrd.img whenever you install a new kernel.  That comes in initrd-tools.  The version that's in Warty has an (easily-fixable) bug that causes it to produce the bogus loadmodules files that we're having to deal with.  One way to deal with the bad initrd.img files is to just keep fixing them every time you install a new kernel.  The other option is to fix the script that's generating the bad ones.

I'll try to give you something more useful/practical tomorrow.  If you're feeling adventurous, though, check out bug #496.

(Is this the kind of thing we should be creating a wiki page for?)

---

### Post by ethn on 2005-01-07
Thank you!

I appreciate and respect your work on this problem!  I thought we might have to wait for the next release!  Thank you again, from everyone that couldn't help themselves.  =)

ethn.

---

### Post by Random Juju on 2005-01-09
Right.  Patching initrd-tools.

For those of you familiar with using patch, just apply this:  [https://bugzilla.ubuntu.com/attachment.cgi?id=336](https://bugzilla.ubuntu.com/attachment.cgi?id=336)

Otherwise...

Edit your /usr/sbin/mkinitrd file.  Find the block that reads as follows:

```
	if [ -d "$MODULEDIR/kernel/drivers/ide/pci" ]; then
		IDE_PCI_MODULES=$(
			find "$MODULEDIR/kernel/drivers/ide/pci" \
				-name "*.$o" -printf '%f\n' |
				sed 's%\.'$o'$%%'
	)
		if [ -n "$IDE_PCI_MODULES" ]; then
			printf '%s > /dev/null 2>&1\n' $IDE_PCI_MODULES
			echo unload_unused_ide "'$oldstyle'" $IDE_PCI_MODULES \
				>&5
		fi
	fi
```

It's somewhere around line 360.  Just above that block, you'll find a block that reads:

```
	case $IDE_MODULE in
	ide-probe-mod)
		IDE_CORE=ide-mod
		;;
	ide-detect | ide-generic)
		IDE_CORE=ide-core
		;;
	*)
		IDE_CORE=none
		print_module drivers/ide/ide-disk
		return
		;;
	esac
```

Move the first block (if [ -d...) immediately above the second block.  The section of the file you edited should now look like this:

```
if [ -d "$MODULEDIR/kernel/drivers/ide/pci" ]; then
                IDE_PCI_MODULES=$(
                        find "$MODULEDIR/kernel/drivers/ide/pci" \
                                -name "*.$o" -printf '%f\n' |
                                sed 's%\.'$o'$%%'
                )
                if [ -n "$IDE_PCI_MODULES" ]; then
                        printf '%s > /dev/null 2>&1\n' $IDE_PCI_MODULES
                        echo unload_unused_ide "'$oldstyle'" $IDE_PCI_MODULES \
                                >&5
                fi
        fi

        case $IDE_MODULE in
        ide-probe-mod)
                IDE_CORE=ide-mod
                ;;
        ide-detect | ide-generic)
                IDE_CORE=ide-core
                ;;
        *)
                IDE_CORE=none
                print_module drivers/ide/ide-disk
                return
                ;;
        esac
```

Save your work and you're done.  This means that subsequent kernel installations should NOT produce the initrd.img problem.  To be fair, I have NOT been able to verify that this will actually work, but have very good reason to believe that it will.

It's my understanding that the next Ubuntu release will include a fixed version of initrd-tools.  See [https://bugzilla.ubuntu.com/show_bug.cgi?id=496](https://bugzilla.ubuntu.com/show_bug.cgi?id=496) for more details.

---

### Post by farruinn on 2005-02-13
[QUOTE=Random Juju]WOO!  WE HAVE A SOLUTION!
[/QUOTE]

Unfortunately I'm still getting the same kernel panic after following the instructions: 

pivot_root: No such file or dir
/sbin/init: 429: cannot open dev/console: no such file
Kernel panic: Attempted to kill init.

Any ideas?
I am also trying to install on a 350MHz B&W G3.
~Nathan

---

### Post by DracosX on 2005-03-15
Actually, the problem seems to still be there, in hoary.  I haven't experienced it on any of my warty boxes, but each and every one of my hoary machines still seem to be suffering.

---

### Post by farruinn on 2005-03-15
[QUOTE=DracosX]Actually, the problem seems to still be there, in hoary.  I haven't experienced it on any of my warty boxes, but each and every one of my hoary machines still seem to be suffering.[/QUOTE]

How are you installing hoary?  I installed with the preview release cd just the other day and it went just fine.  The only problem I'm still having is that /dev/hda and /dev/hdc are still mixed up.

---

### Post by DracosX on 2005-03-21
Generally, I install using the latest daily installer build, but I've had the problem occur using dist-upgraded warty as well.  I just double-checked this with the preview release and lo-and-behold, I still have the problem.  I can work-around it fine, but someone out there will get this besides me.

Interestingly enough, this only seems to occur on my software raid or lvm setups, any configuration I use. (I get the problem with 2.6.10-5-{3,6}86 but not with 2.6.10-4-{3,6}86.  Either way, I can always boot with the live cd, start the array, mount the filesystem, and fix the initrd, but that's a big hassle.  Especially considering  I've double-checked for the aforementioned fix.

---

### Post by farruinn on 2005-03-21
[QUOTE=DracosX]Generally, I install using the latest daily installer build, but I've had the problem occur using dist-upgraded warty as well.  I just double-checked this with the preview release and lo-and-behold, I still have the problem.  I can work-around it fine, but someone out there will get this besides me.

Interestingly enough, this only seems to occur on my software raid or lvm setups, any configuration I use. (I get the problem with 2.6.10-5-{3,6}86 but not with 2.6.10-4-{3,6}86.  Either way, I can always boot with the live cd, start the array, mount the filesystem, and fix the initrd, but that's a big hassle.  Especially considering  I've double-checked for the aforementioned fix.[/QUOTE]

Kernel 2.6.10-[5 | 4]-686?  I thought this was a powerpc problem?  Also, now that I think of it when I installed via preview cd for some reason I installed 2.6.10-4-powerpc and not 2.6.10-5-powerpc.  Upgrading to 2.6.10-5 however didn't cause any problems.  Given that hoary final freeze is **one week** from today, if others could provide some testing with current dailies it would be good to either get this bug fixed if possible.

-Nathan

---

### Post by DracosX on 2005-03-21
> I thought this was a powerpc problem?

No such (bad?) luck.  In my powerpc installs, everything seems to be working normally. Apologies for posting this in the ppc forum, but this is the most relavant topic I've found for this.  In the machine I installed last night (warty, custom, dist-upgrade, install ubuntu-desktop) everything went smoothly.  an apt-get install linux-686 and it ran fine.

Today I installed hoary-preview-i386 on my machine at work.  Everything worked fine until I installed linux-686.

Edit: Confirming problem still exists with today's daily installer image.

---

### Post by DracosX on 2005-03-24
After some painstaking research I finally found the bug in question.  Seems my issue was related to this bug: [https://bugzilla.ubuntu.com/show_bug.cgi?id=5421](https://bugzilla.ubuntu.com/show_bug.cgi?id=5421) 

Thanks for all your help.    :D

---

### Post by Marble2 on 2005-03-29
> **Random Juju]WOO!  WE HAVE A SOLUTION!

Okay.  So here's what needs to happen to make this work on a blue/white G3 or similar box...

1)  Go through a normal installation process, but do not reboot at the end.
2)  When the installer prompts you to remove the installation CD and reboot, press ctrl-option-F2 (same as ctrl-alt-F2) to get to a terminal.
3)  From the terminal, type ```
chroot /target
```  This will use the freshly installed Ubuntu system as the working root (that is, you'll be working with the file tree and binaries that you just installed).  You will notice that the command prompt changes.
4)  Type ```
mkdir /mnt/initrd
```  This will create a mount point for the initrd (initial RAM disk) image that we're about to modify.
5)  Type ```
mount -o loop /boot/initrd.img-2.6.8.1-3-powerpc /mnt/initrd
```  You may have a different kernel/initrd version.  I trust your ability to improvise here.  This mounts the initrd image to the mountpoint we just created using a loopback device.  Don't sweat the details there if you're not comofortable with them -- basically we've put a bunch of files someplace where we can get at them easily.
6)  We can't directly edit the contents of the initrd image, so we'll copy them somewhere else, make the necessary changes, and then create a new initrd image.  Copy the contents of the ramdisk by typing ```
cp -a /mnt/initrd /tmp
```.  You should now have an "initrd" directory in /tmp.
7)  Switch to the directory of the new copy with ```
cd /tmp/initrd
```
8 )  If you're like me, you'll have seen the following when you made the copy:

```
cp: will not create hard link `./initrd/devfs' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/mnt' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/proc' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/scripts' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/sys' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/tmp' to directory `./initrd/dev2'
cp: will not create hard link `./initrd/var' to directory `./initrd/dev2'
```

If you see those warnings, create the directories that were omitted.  In the case of the warnings above, use:  ```
mkdir devfs mnt proc scripts sys tmp var
```.
9)  What's actually causing the booting problem is the "loadmodules" file.  Use "nano" (a lightweight text editor -- `nano loadmodules` to edit the file) to modify the file to look like this:

```
modprobe -k  unix 2> /dev/null
modprobe -k  sd_mod
modprobe -k  pdc202xx_new > /dev/null 2>&1
modprobe -k  aec62xx > /dev/null 2>&1
modprobe -k  cmd64x > /dev/null 2>&1
modprobe -k  generic > /dev/null 2>&1
modprobe -k  hpt34x > /dev/null 2>&1
modprobe -k  hpt366 > /dev/null 2>&1
modprobe -k  ns87415 > /dev/null 2>&1
modprobe -k  pdc202xx_old > /dev/null 2>&1
modprobe -k  sc1200 > /dev/null 2>&1
modprobe -k  siimage > /dev/null 2>&1
modprobe -k  sl82c105 > /dev/null 2>&1
modprobe -k  trm290 > /dev/null 2>&1
modprobe -k  via82cxxx > /dev/null 2>&1
modprobe -k  ide-disk
```

Save your changes by typing ctrl-o (and then enter) and then close nano by typing ctrl-x.
10)  Now it's time to turn the temporary directory back into a ramdisk.  Do that by backtracking to the /tmp directory (`cd /tmp`) and typing ```
mkcramfs initrd initrd.img-2.6.8.1-3-powerpc
```
11)  Replace the old image with the new one by typing ```
mv /tmp/initrd.img-2.6.8.1-3-powerpc /boot/initrd.img-2.6.8.1-3-powerpc
```
12)  You're done.  If you'd like to clean up, you can (but don't need to) remove the temporary files by typing ```
rm -rf /tmp/initrd
```  Either way, press ctrl-option-F1 (ctrl-alt-F1) to bounce back to the Ubuntu installer.  Select "continue" to reboot into your new (and working!) Ubuntu system.

Whew  said:**
> https://bugzilla.ubuntu.com/show_bug.cgi?id=496[/url] and [https://bugzilla.ubuntu.com/show_bug.cgi?id=3363](https://bugzilla.ubuntu.com/show_bug.cgi?id=3363)).
Okay, I'm having this problem too, I can't boot up, I'm getting those errors. I'm chrooted to the drive and I go to run "mount -o loop /boot/initrd.img-2.6.10-4-386 /mnt/initrd" after making the /mnt/initrd and I get these errors: 
ioctl: LOOP_CLR_FD: Device or resource busy
mount: you must specify the filesystem type

Any ideas what I'm doing wrong?
Also, here is a list of initrd files that come up in /boot (in case I'm using the wrong one)
initrd.img-2.6.10-4-386 
initrd.img-2.6.8.1-4-386
initrd.img-2.6.8.1-3-386 
initrd.img-2.6.8.1-5-386

Thanks in advance :)

---

### Post by Marble2 on 2005-03-29
[QUOTE=Marble2]Okay, I'm having this problem too, I can't boot up, I'm getting those errors. I'm chrooted to the drive and I go to run "mount -o loop /boot/initrd.img-2.6.10-4-386 /mnt/initrd" after making the /mnt/initrd and I get these errors: 
ioctl: LOOP_CLR_FD: Device or resource busy
mount: you must specify the filesystem type

Any ideas what I'm doing wrong?
Also, here is a list of initrd files that come up in /boot (in case I'm using the wrong one)
initrd.img-2.6.10-4-386 
initrd.img-2.6.8.1-4-386
initrd.img-2.6.8.1-3-386 
initrd.img-2.6.8.1-5-386

Thanks in advance :)[/QUOTE]
Never mind, I fixed that using -t cramfs but now I have a new problem. I followed your guide to a T and I still get the error. About putting that stuff in your loadmodules file, is that what the WHOLE file should look like, or should we ADD that stuff to the file?

---

### Post by Marble2 on 2005-03-29
[QUOTE=Marble2]Never mind, I fixed that using -t cramfs but now I have a new problem. I followed your guide to a T and I still get the error. About putting that stuff in your loadmodules file, is that what the WHOLE file should look like, or should we ADD that stuff to the file?[/QUOTE]
Ugh, I just realized where this thread is, I'm running hoary and an x86 machine. Will thsi guide still apply to me?

---

