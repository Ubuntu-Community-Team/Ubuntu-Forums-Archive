---
title: "Yaboot wont load after installing 11.10 - Mac Mini"
date: 2011-10-31
forum: Apple Hardware Users
---

### Post by raposadaplanicie on 2011-10-31
Hi folks!
I just got an old G4 Mac Mini from a garage sale. I'm aimming to use it as a secondary computer when surfing the web - much more silent and less power comsuming than my main CPU used to render 3D scenes.
Here's the thing. I got rid of the OSX when installing Ubuntu - chose to take the entire HD. But when the system finishes the instalation and asks for reboot... well, after rebooting there is no bootloader loading, no yaboot at all, I just get the MacOS log blinking with an question mark.
Could anyone help me up here?
Thanks in advance :)

---

### Post by rsavage on 2011-10-31
The 11.10 cd has been having a lot of problems. Did you get a mirror server error? There is a possible fix here [http://ubuntuforums.org/showpost.php?p=11409752&postcount=27](http://ubuntuforums.org/showpost.php?p=11409752&postcount=27) .  If you didn't could you post back please on that thread what country you are in or if you were connected via ethernet cable at the time?
 
I don't know if there is a further problem with the mac mini [http://ubuntuforums.org/showthread.php?t=1871276](http://ubuntuforums.org/showthread.php?t=1871276) .
 
You'll definitly be able to install 11.04 va the mini cd [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1) .

---

### Post by raposadaplanicie on 2011-11-01
In fact I got the mirror error bur since I'm installing from CD and not connected to the internet I just thought that I was a natural error for not being able to update some packages.
Sorry if it's a stupid question, but does not being able to do this step prevents the bootloader from installing itself? 'Cause even with the mirror error the installation shows the "completed" message and the system reboots.
Maybe I'll just try 11.04.
Thank you!

---

### Post by rsavage on 2011-11-01
No stop!  We can try something out!

---

### Post by raposadaplanicie on 2011-11-01
Is there a way to call yaboot from openfirmware console? I mean, when I boot the live CD I can see that the system is installed so maybe I should just try to run yaboot manually.
Thanks for the replies btw

---

### Post by rsavage on 2011-11-01
Yes, that is what I was going to suggest.  You should be able to boot your cd to the yaboot prompt and then put in the openfirmware path to the vmlinux file in the /boot directory.  Have a look at the link in the mirror server thread for suggestions for the openfirmware path.
 
Will be back on in 20 mins or so when I can give more detail....

---

### Post by rsavage on 2011-11-01
hd:3,/boot/vmlinux root=hd:3 ro
 
hd:3,/boot/vmlinux root=hd:3 initrd=hd:3,/boot/initrd.img ro

/pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux root=/pci@f4000000/ata-6@d/disk@0:3 ro

/pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux root=/pci@f4000000/ata-6@d/disk@0:3 initrd=/pci@f4000000/ata-6@d/disk@0:3,/boot/initrd.img ro

 
Once booted we can then install yaboot properly to the hard drive.

---

### Post by raposadaplanicie on 2011-11-01
Alright them. It may just take some time here ' cause Brazilian internet connections can be pretty slow - especially mine since the place I live is far away from big cities :). Seriously, it takes like 10 minutes to get a page to load sometimes ¬¬.
But this old little G4 fellow will have to boot someway or another :D

---

### Post by rsavage on 2011-11-01
Brazil!  Cool!  That's like half a world away!  This internet thing is great!

I'm saying you can do this stuff because the documentation says you can [http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html#s9.3](http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html#s9.3) !  I've not tried it and it is a real pain not having a powerpc machine available to me!

I'm guessing you may hit a busybox prompt....

---

### Post by raposadaplanicie on 2011-11-01
Ok. Tried what you said but it returns me "Please wait, loading kernel... not a valid elf image".
Now thinking of it, when i tried "sudo yabootconfig -r /dev/sda3" before from the live CD (after installing the system and checking that the files where present at th HD) it said it couldn't find a kernel at all.
Could it be possible that Ubuntu setup haven't copied all the files to my system?

---

### Post by rsavage on 2011-11-01
.... if you do hit a busybox prompt then enter the command:
 
modprobe pata_macio
 
Then ctrl+D to resume the boot.

---

### Post by rsavage on 2011-11-01
> **raposadaplanicie said:**
> Ok. Tried what you said but it returns me "Please wait, loading kernel... not a valid elf image".

Did you get that on the openfirmware paths I gave?  Have you checked the files exist in the /boot directory?

---

### Post by rsavage on 2011-11-01
> **raposadaplanicie said:**
> 
Now thinking of it, when i tried "sudo yabootconfig -r /dev/sda3" before from the live CD (after installing the system and checking that the files where present at th HD) it said it couldn't find a kernel at all.
Could it be possible that Ubuntu setup haven't copied all the files to my system?
 
If you are going to do it from the live cd you'll need something like this I think (we're getting a bit beyond my level of knowledge):
 
```

sudo mount /dev/sda3 /mnt
sudo yabootconfig --chroot /mnt -r /dev/sda3 -b /dev/sda2 
sudo umount /mnt

```
 
This may still fail because it can't automatically figure out the ofboot argument.  If this is the case you will have to pass this to the mkofboot/ybin commands instead of yabootconfig.  e.g --ofboot hd:2

---

### Post by raposadaplanicie on 2011-11-01
Sorry for the dalay, dial up conection here sometimes wont reconect no matter what.
Anyway, I'm going to boot again to check for all the files - it taka a few minuts to boot from the cd.

---

### Post by rsavage on 2011-11-01
No problem.  I haven't had broadband for that long and I remember too well that dial-up was so slow!

---

### Post by raposadaplanicie on 2011-11-01
> **rsavage said:**
> Did you get that on the openfirmware paths I gave?  Have you checked the files exist in the /boot directory?

Hoe exactly do I navegate through the openfirmware conselo? Always used pc... 
Ok, at the boot directory I got vmlinux-3.0.0-12-powerpc

What I did is boot the yaboot console from the CD and tried to follow your instructions.

---

### Post by rsavage on 2011-11-01
Sorry my bad typing or brain working faster than hands or something.  Should have read "did you get that on all the openfirmware paths I gave?".  I meant the list I gave in post #7 to try at the yaboot prompt.

Okay staying in the /boot directory what files are there?  Can you list them?

---

### Post by raposadaplanicie on 2011-11-01
Yes, tried the paths and got the error message I told.
Here are the files at the boot directory:

abi-3.0.0-12-powerpc
abi-3.0.0-12-powerpc64.smp
config-3.0.0-12-powerpc64
config-3.0.0-12-powerpc64.smp
System.map-3.0.0-12-powerpc64
System.map-3.0.0-12-powerpc64.smp
vmlinux-3.0.0-12-powerpc

That's all :(

---

### Post by rsavage on 2011-11-01
Okay so that explains why those openfirmware paths weren't working.  You don't have a vmlinux file or an initrd.img file.  The vmlinux file is no problem.  We can use at yaboot the openfirmware path

hd:3,/boot/vmlinux-3.0.0-12-powerpc root=hd:3 ro

I don't know if it will work without a initrd.img file though.  My lack of basic knowledge of linux is pretty bad at times!  You could try copying the one from your cd into that directory maybe?  Then amend the openfirmware path to whatever it is called.

hd:3,/boot/vmlinux-3.0.0-12-powerpc root=hd:3 initrd=hd:3,/boot/initrd.img ro

By the way, it is evening here so I'm not doing much.  Avoiding watching TV mainly.  But, I realise it must be day with you.  Are you still okay to be messing with this or do you need to be doing something else?  I can research this a bit more on my own.

---

### Post by raposadaplanicie on 2011-11-01
thanks for being worried. Actually I work at home and since I finished all my job for the next two days I'm cool and having fun here :D. But, hey, really, thanks!
I already tried to direct yaboot to the vmlinux-3.0.0-12-ppc as you suggested but it was no good :(
I'll try to copy the vmlinux and init from the CD now, let's see what happens :D

---

### Post by raposadaplanicie on 2011-11-01
Ok, after copying the files to my boot directory I was able to make yaboot boot up, 
or at least it tries.

The system starts loading, but it hangs up 'cause of these two lines:

VFS: Cannot open root device hd:3
Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

It seens to my that my partitions aren't beeing mounted, am I right?
Btw, why wouldn't the LiveCD setup copy all the needed files?
Is there a way to run a setup without loading the Live system? A CLI setup or something?

---

### Post by rsavage on 2011-11-01
I don't know why the live cd is failing. It could be that mirror server problem, so it might be worth going through the effort of reinstalling and trying that workaround I posted on the other thread (if you have 2 days spare!).
 
More likely I think is that whatever configures yaboot is struggling with the new kernel modules and is failing to setup. This has the knock on effect that the scripts to install the kernel images fail.
 
Have you tried the "modprobe pata_macio" thing I posted earlier?

---

### Post by rsavage on 2011-11-01
I'm off for a coffee and a break.  Will be back in a hour or so.....

---

### Post by raposadaplanicie on 2011-11-01
Yeah tried everything you said lol
Guess I'll take a bath and go visit my GF. She's got this decent  internet connection so I'll try downloading the alternate text installer  and we'll see it if works.
Thank you VERY much! As soon as I got some news I'll post 'em here :)
*tried reinstalling the system like 10 times, changing the setup of the partitions and stuff but still nothing...

---

### Post by rsavage on 2011-11-01
I'm sorry this is not turning out to be straightforward!

I've found out what we should of done to generate an initrd.img:

 Boot into the LiveCD, then

sudo mkdir /mnt/drive

sudo mount /dev/sda3 /mnt/drive

sudo update-initramfs -c -k 3.0.0-12-powerpc -b /mnt/drive/boot

It should generate an initrd.img file in the boot directory.

See if that works!!!!   If you still get dumped into a busybox shell then you may have to modprobe some other ata module.  You'll have to load the live cd again and maybe you can figure it out by running "lsmod" and "lspci -k".  You can post the results on here maybe?

We can create a yaboot.conf and format the bootstrap partition pretty easily with the mkofboot command, but I think we should concentrate on getting the system booted first.  If the update-initramfs complains then we'll create the boostrap partition.

Anybody else out there got any other ideas.....????

Bed now!

---

### Post by rsavage on 2011-11-02
> **raposadaplanicie said:**
> 
The system starts loading, but it hangs up 'cause of these two lines:

VFS: Cannot open root device hd:3
Kernel panic- not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

It seens to my that my partitions aren't beeing mounted, am I right?


At the 'Busybox' prompt we should of probably typed here the command

ls /dev/

To see if it is seeing any hdaX's or sdaX's (your hard drive partitions).  If you are seeing the partitions then you should have the right modules loaded.

It could be it doesn't like the root=hd:3, but expects something like root=/dev/sda3

---

### Post by rsavage on 2011-11-03
Another thing I've just spotted thanks to Ms. Daisy's posts on another thread is that I misspelled pata_macio!

---

### Post by wall0159 on 2011-11-04
Thanks to all who helped in this thread, it allowed me to get my iBook booting. :-)

I was doing as suggested here, but I kept getting an error, when running ybin -v that /dev/sda2 didn't exist. It took me a few tries to realise that it was not actually writing to the bootstrap partition.

What I needed to do, I read here ([http://castyour.net/running-ybin-yaboot-inside-chroot-fails-hfs-working-directory-error](http://castyour.net/running-ybin-yaboot-inside-chroot-fails-hfs-working-directory-error)) and I typed:
/path/to/chroot/usr/sbin/ybin -C /path/to/chroot/etc/yaboot.conf -v

This wrote to the bootstrap, blessed it with holy penguin pee and all is well :-)

---

