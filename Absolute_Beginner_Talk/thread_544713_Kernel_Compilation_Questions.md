---
title: "Kernel Compilation Questions"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-09-06
I love compiling from source, and I guess Im ready to take a bigger step -- to compile a kernel.  Ive found a lot of instructions and from what I can tell they are pretty specific.  I have some simpler questions

1. How much space do I need to compile and install a new kernel?  I have about 6Gb left.  If I delete older kernels, would that be sufficient?
2. Is there anything different about compiling the latest vanilla kernel as compared to the sources from gusty's repository?  Are there any customizations in the kernels provided by ubuntu or is it pretty much the stock kernel?
3. If I go ahead and compile the latest vanilla kernel, and later upgrade to Gusty, could there be a potential problem?
4. Other than the wireless ndiswrapper modules that Ive compiled, as there anything else I should be expected to possibly recompile/reinstall after the new kernel installation?

Im not exactly sure if there is any good reason for me to compile a new kernel, other than "I just want to do it!"  I dont really want to break my machine or prevent the ability to upgrade in the future however.

Thanks for any insights.

My two cents: compiling pidgin and the purple plugins from source are the only way to go!

---

### Post by Bachstelze on 2007-09-06
1) 6 G is far more than enough. At most, the compiling process will use ~500 M.

2) The official Ubuntu kernel has additional drivers that are not in the vanilla one. AFAIK, that's all.

3) You might need to recompile your custom kernel with the new GCC version to make it operate nicely with the rest of the system but that's all.

4) All kernel modules that are not in the vanilla kernel. That includes all proprietary drivers, especially.

By the way, "I want to do it!" seems good enough a reason, to me ;) And it certainly won't prevent you from updating.

---

### Post by HermanAB on 2007-09-06
Some words of caution:
First rebuild the kernel without changing anything (make oldconfig), install it and confirm that it works as before.  Only then try to change something.

Cheers,

Herman

---

### Post by BobCFC on 2007-09-06
I ran out of space the first few times I compiled.  Maybe 64bit needs more space.  Also I found the first time when I went through the options and removed everything I didn't need it took about 19min,,  But later when I did a default setup just changed a few things it took nearly an hour..   Maybe the options effect the space needed too.

6gb is plenty.. I needed about 4gb. But that is just for temporary files which are mostly deleted when finished.  The only thing to be aware of is if you have a small seperate /boot partition.  I had 64mb at first and it got tight..  expanded to 128mb and I have room for several kernels.

Also when the distro's differ from the vanilla kernel it's not just patching code it's the config, turning options on and off.

I did it all with instructions from the [master kernel thread]("http://ubuntuforums.org/showthread.php?t=311158").


As for reasons to compile you own kernel, I did it because I had to enable DMA on my Core2Duo motherboad.  While you look at the kernel config you will see lots of stuff you can enable to make it less generic and also tons of stuff that can be cut out such as radio support or infrared etc.  The thing builds a nice .deb package which adds a grub menu entry for you so you can always go back I wouldn't worry about breaking your system.

Anyway hacking is fun, you will learn alot an feel more confident about you system.. especially what all those messages mean when booting.  Turn you boot logo off and get to know them.   (change splash to nosplash in the /boot/grub/menu.lst)

EDIT:  re 4)   if you install your own 3D drivers from the nvidia web site they need to be reinstalled every time the kernel or the xserver changes

---

### Post by Bachstelze on 2007-09-06
> **BobCFC said:**
> I ran out of space the first few times I compiled.  Maybe 64bit needs more space.  Also I found the first time when I went through the options and removed everything I didn't need it took about 19min,,  But later when I did a default setup just changed a few things it took nearly an hour..   Maybe the options effect the space needed too.

Of course, the more modules you compile, the more time and diskspace it will take ;)

---

### Post by rsambuca on 2007-09-06
Bob, did it take an hour to compile with the default settings on that rig you have listed in your signature?

---

### Post by BobCFC on 2007-09-06
> **rsambuca said:**
> Bob, did it take an hour to compile with the default settings on that rig you have listed in your signature?

hmm... over 45 mins i'm sure..  I only really timed the first one where I stripped out everything and that was 19mins on 64bit stock no overclocking.


Now that I think about it, it could have been the DMA issue that I was compiling to fix..  hdparm went from 1.6mb/s to 70.9mb/s with the latest from kernal.org.    But source code is lots of small files anyway.

---

### Post by BobCFC on 2007-09-06
> **HymnToLife said:**
> Of course, the more modules you compile, the more time and diskspace it will take ;)

I thought so but I drop lots of maybes and I-thinks because yesterday someone picked my up for saying you *cannot* build your own laptop to a beginner who was choosing a system.  Pedantic or what.

---

### Post by kevdog on 2007-09-06
Hmm, both you guys have given me good ideas

Just a couple of questions

1. New gcc version -- I dont understand what you mean by this.

2. Proprietary drivers -- Hmm this could be a problem.  Im installing on a laptop with synaptic touch pad, really old ati rage mobility 128 mb vid card, pcmcia slots.  Im not exactly sure if there will be a problem with the video card:
     ```
      *-display
                description: VGA compatible controller
                product: Rage Mobility M3 AGP 2x
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: iomemory:f8000000-fbffffff ioport:2000-20ff iomemory:
```
I dont know exactly what driver this device is using.   I know for a fact I didnt install a driver for this guy when I installed edgy, only really needed to screw around with the xorg.conf file for a while.

I wish I knew more since I dont really know what Im doing -- hence the whole purpose of the exercise.

---

### Post by BobCFC on 2007-09-06
> **kevdog said:**
> 
1. New gcc version -- I dont understand what you mean by this.


He means the latest C compiler, which is the program used to build other software from source code, such as the kernel.

gcc = gnu c compiler.

---

### Post by ayenack on 2007-09-06
Just a thought here. Don't delete your present kernel. Make a backup of /etc/X11/xorg.conf then download and compile the new kernel and if all goes wrong boot into safe mode on the old kernel copy xorg.conf backup to xorg.conf and you should be back where you were with the old kernel.

Best of luck. ayenack.

---

### Post by kevdog on 2007-09-06
Thanks guys for the tips, Ill proceed and see what trouble I can get into

---

### Post by kevdog on 2007-09-07
Ive run into some problems and I really dont know how to proceed.  I made the kernel using the old .config options as previously suggested.  The kernel was compiled overnight (vanilla 2.6.22.6) producing the image and header .deb files.

I went to install the image deb but got the following errors:
```
Setting up linux-image-2.6.22.6-compiled-kernel-2.6.22.6 (2.6.22.6-compiled-kernel-2.6.22.6-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22.6-compiled-kernel-2.6.22.6
find: /lib/firmware/2.6.22.6-compiled-kernel-2.6.22.6: No such file or directory
find: /lib/firmware/2.6.22.6-compiled-kernel-2.6.22.6: No such file or directory
find: /lib/firmware/2.6.22.6-compiled-kernel-2.6.22.6: No such file or directory
find: /lib/firmware/2.6.22.6-compiled-kernel-2.6.22.6: No such file or directory
find: /lib/firmware/2.6.22.6-compiled-kernel-2.6.22.6: No such file or directory
find: /lib/firmware/2.6.22.6-compiled-kernel-2.6.22.6: No such file or directory

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.22.6-compiled-kernel-2.6.22.6
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22.6-compiled-kernel-2.6.22.6 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22.6-compiled-kernel-2.6.22.6
```

The one error that concerns me is that it states no space left on device.  Currently now I have 14.27 Gb or 17.25 Gb full leaving roughly 3 Gb free, along with 1 Gb Swap, and 100 Mb /boot
 
What exactly do I do know??

This process up to know has consumed 3Gb -- Ive gone from 11gb to 14 gb in downloading and compiling the sources.  I thought I would have plenty of space.

---

### Post by ayenack on 2007-09-07
As I'm sure you've worked out for yourself what you mentioned in an earlier post about running out of space has happened. gzip: stdout: No space left on device means that the build did not complete as there was not enough space amazingly. You said you had 6GIG left I would have thought that would be plenty but it seems not. You need to make some space. If you have a big amount of RAM maybe turn swap of a grab back some space. other than that its a new HD I think. I'm sure you know all this but anyway. Is all the space in one partition because if it's not as far as I know it'll only compile in that partition.

---

### Post by kevdog on 2007-09-07
I think Im out of luck -- Im compiling on a 1998 laptop with a 20gb HD with the largest partition 17gb, 512 mb ram.  I really cant believe it would take more than 6 gb to compile and install a kernel because that is roughly the amount of space I had when I started.  No where have I read in any google post that it would take this much space.

I dont really know

The source directory after compilation was 2.9Gb in size, however I cant believe the installation would take another 3gb.

Im trying now to undo what I did with the dpkg statement.  Any thoughts??  I think I might be out of luck on this one.

---

### Post by ayenack on 2007-09-07
Did you keep your old linux-image and make a backup of xorg? If you did then just boot into the old kernel in recovery mode and copy the backup to xorg and delete the custom kernel to get the space back.

You know I'm sure that a kernel can be compiled with less space than you've got. Did you configure the kernel before installing it removing all unnecessary modules? Will be loads on that lappy I'm guessing. I compiled a kernel on an old dual 350MHz PII sever with a GIG of ram a couple of weeks ago and it took about 4 or 5 hours if I remember correctly. It dramatically improved the performance of it. I removed all unneeded modules and stripped it down to the bare minimum. Had some issues with USB after but that was from a mistake.

Have you had a look at [this]("http://ohioloco.ubuntuforums.org/showthread.php?t=311158&highlight=compile+kernel") might be of some use.

ayenack.

---

### Post by kevdog on 2007-09-07
Thanks for the link.  I actually found it very useful.  I uninstalled everything.  Freed up some disk space (now 7GB free).  Redownloaded everything.  For my second attempt I took a lot of modules out of the kernel -- didnt realize the sure mass of modules that could be included if you wanted -- however most of the modules for me were worthless since they were hardware specific.  Anyway, am in process of recompiling for second time.  Hopefully in a few hours I wont run into the same problem.

Thanks.

---

### Post by kevdog on 2007-09-07
OK I found part of the problem -- My 100 Mb /boot partition is full:

/dev/hda1                97826     97826         0 100% /boot

How do I resize this partition without losing any data??

---

### Post by ayenack on 2007-09-07
You know something I meant to mention this earlier but totally forgot. Why not just boot the live CD and use GParted to resize the drive. Will this work or will you have issues with permissions doing this? Not sure. I think it'll work. Give it a go.

Just remembered there's a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") might be the better option.

---

### Post by kevdog on 2007-09-07
What a big pain in the ***.  Anyway I found the departed livecd and I went to resize the partitions and it told me it couldnt perform the operations and told me to check the disk for errors.

What program do I use to do this!

---

### Post by ayenack on 2007-09-07
Can you boot into recovery mode? If so fsck to see if anythings wrong. I doubt that there is it's probably just that the root partition is full. If you can boot into your system try deleting some file off the root partition to grab back some space. If not then you'll have to do it from recovery mode. Might try an Ubuntu LiveCD to see what comes of it.

---

### Post by kevdog on 2007-09-08
I might be wrong about this but I think there is no way to add space to the boot partition. My HD is setup like the following

/dev/hda1 - Boot 100mb
/dev/hda2 - / 17.25Gb
/dev/hda3 - /swap 1.00Gb

I tried the gparted live cd however ran into difficulty finding that only free space can be reclaimed off the end of the drive.

I was able to delete the swap partition, but I was unable to shift or move the / partition at all.  It seems like I am unable to do this at all.  I could resize the / partition to use the unallocated space, but Im stuck with the current size of the /boot partition.  Learned something tonight!!!

Well anyway, I uninstalled some old kernels to free up some space on the /boot partition and was able to install the compiled kernel

Few things however Im finding:
1. Seems about as fast as the old generic kernel during the boot process -- I havent timed it but seems about as fast so to me no advantage
2. The initrd-img for the compiled kernel was 31 Mb, whereas in old kernels they were 6.6 Mb.  Why the discrepancy in size??  Possibly b/c some options in the kernel were "baked in" rather than selected to be loaded as modules??
3. Compiling ndiswrapper svn - Im getting a lot of warnings I never got before, but the module does function
4. Getting new errors using iwlist scan (wireless-tools) -- telling me it was only made for rev 11-20 (not 22 the current kernel).  I tried compiling wireless tools from source -- they installed but the executables wouldnt work
5. Firewall is all messed up.  I use guarddog.  I dont know why, I havent debugged it, but its really annoying.

Im finding Im really an amateur at compiling the kernel.  It seems like I turned off most of the options relating to other hardware types  Some of the options however I really never understood what they meant, so I just kept the defaults.

Id like to say that I can notice one thing positive with the compiled kernel, but I cant say that.  Some negatives, but it seems like after all my work, most of the results were neutral.

Just a bummer.  Id like to give it another shot, however taking 5 hours to compile the kernel, its not like making one change you can see instant resutls.

---

### Post by ayenack on 2007-09-08
This was what I was about to post to help you grab some space back on root until I saw your new post. May still be helpful. 

Ok been thinking about how you might get some space back on root. If you can boot into system go to synaptic once opened click on Status Tab in bottom left corner then Not Installed (residual config) this will bring up some app in the main window remove them from the sytem. Once this is done, do this to hopefully gain some more space. Open a Terminal or from recovery mode do this. 

sudo apt-get autoclean

This will grab back a bit more space. Now do this.

sudo apt-get install localepurge

After install you need to configure it with your local language. When this is done type this in terminal.

sudo localepurge

Bit more space grabed back. Now this.

sudo apt-get install deborphan

Once installed type this.

sudo deborphan | xargs sudo apt-get -y remove --purge

A bit more space. Try to boot into ubuntu and see how it goes. After this you could also install wajig to try to claim back a bit more space.

sudo apt-get install wajig

To open type this interminal.

gjig

You probably knew all this but just in case. Well that might help. Hope so. Let me know. ayenack.

One quick question why 100MB boot when you set up the comp?

---

### Post by ayenack on 2007-09-08
It's not for every one that's for sure but it's good experience for future reference.I think everyone who has your level of expertise will try it at one point or another it just has to be done.... I think. I only have two self compiled kernels and these are both for MPS PC's with special needs other than that I don't bother generic kernel is fine. Seems you will have a job on your hands getting your PC up and running as you want. One bit of advice if you ever do compile a kernel again do it on a reasonably clean install not to many probs with previously installed apps that way. There's always [AutoKernel]("http://ubuntuforums.org/showthread.php?t=222018") and [KernelCheck]("http://kcheck.sourceforge.net/"). Never used them but seem to be OK.

We'll it was a ride. Good luck. ayenack.

---

### Post by kevdog on 2007-09-08
I have no level of expertise,  didnt start using Linux until April this year in fact.  Its obvious from what I was trying to do that Im definitely inexperienced.

As far as the 100Mb boot partition, when I installed a long time ago, the documentation out there is very confusing, telling you that you should probably stick /, /boot and /swap on different partitions, and said the /home, /var and possibly /usr should also be on separate partitions.  With an old 20gb HD, I coundnt cut it up into so many pieces.  

I talked to one, guy that told me 100mb would be more than adequate for the /boot, and said swap of 1gb was excessive -- it might be jury is still out on that one.  Anyway I actually doubled what he told me (originally was telling me 50mb boot and 500mb swap).  As you can see I was (and so was he) a little off on the calculations.  Chalk that up to inexperience.

Anyway, Id like to compile the kernel again, but the next time need some pointers on what options to choose.  I can see fine tuning a kernel is a pain in the butt

---

### Post by master_kernel on 2007-09-08
I have a tutorial on kernel compiling, I noticed that someone suggested it here. You are right, it is a pain, especially since I have to compile restricted modules in order for it to work. Linux is also a pain until you learn how to work everything. I used to have a separate boot partition, but I decided it wasn't work the pain for such a small speed increase. Anyway, as ayenack suggested above, Autokernel and KernelCheck are available to ease up on kernel compiling. I don't recommend Autokernel anymore since it was last updated last October, and it uses the Con Kolivas patches, which he stopped making just 2 months ago. That's part of the reason I wrote KernelCheck. It's basically a script to automate the Master Kernel Thread. You still have to configure the kernel, and it does take a while, but it's a little easier than copying and pasting all those commands. You can visit the site I made for KernelCheck [here]("http://kcheck.sourceforge.net").

Good Luck,
master_kernel

---

### Post by kevdog on 2007-09-09
Master Kernel

Thanks for your input -- I followed you guide step by step and have to say it was right on the money.  Ill use the script next time, I usually do things manually at first so that I can understand each step.

Except for the problem with the damn /boot parititon,  I really didnt have any of the problems like many of the users in your thread.

I really dont need any restricted drivers (my computer is so old).

Im not finding my kernel to be any better than before, since probably I didnt configure it properly.  Im getting some strange errors as described before, but nothing that keeps it from non-functioning.

I take it there is no good guide on how to properly configure the kernel.  Since Im running it on a laptop, I was hoping for increase in speed (particularly with booting).  I know most of the hardware in the computer, but since I didnt build the laptop, Im not sure of a few things -- motherboard type, etc.

I guess I was just hoping to see more of a difference that what I do.

---

### Post by kevdog on 2007-09-09
Kernel Check

Thats a pretty cool program -- now if I could just configure the kernel I would be in good shape

Does it delete any of the source files or the debs at the end of the installation???

---

### Post by dwhitney67 on 2007-09-09
> **ayenack said:**
> Just a thought here. Don't delete your present kernel. Make a backup of /etc/X11/xorg.conf then download and compile the new kernel and if all goes wrong boot into safe mode on the old kernel copy xorg.conf backup to xorg.conf and you should be back where you were with the old kernel.

Best of luck. ayenack.
What does xorg.conf have to do with the kernel??

Ans:  Nothing.

---

### Post by dwhitney67 on 2007-09-09
> **kevdog said:**
> Master Kernel

Thanks for your input -- I followed you guide step by step and have to say it was right on the money.  Ill use the script next time, I usually do things manually at first so that I can understand each step.

Except for the problem with the damn /boot parititon,  I really didnt have any of the problems like many of the users in your thread.

I really dont need any restricted drivers (my computer is so old).

Im not finding my kernel to be any better than before, since probably I didnt configure it properly.  Im getting some strange errors as described before, but nothing that keeps it from non-functioning.

I take it there is no good guide on how to properly configure the kernel.  Since Im running it on a laptop, I was hoping for increase in speed (particularly with booting).  I know most of the hardware in the computer, but since I didnt build the laptop, Im not sure of a few things -- motherboard type, etc.

I guess I was just hoping to see more of a difference that what I do.

Strange errors???   Care to specify?

Hoping that a rebuilt kernel would improve performance is a bit naive.  There's a slim possibility that it might, but very doubtful.

---

### Post by kevdog on 2007-09-09
Here's one example of an error I get:

kevin@Homer:/etc$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:17:D9:68
                    ESSID:"Dorchester"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

kevin@Homer:/etc$ uname -r
2.6.22.6

---

### Post by master_kernel on 2007-09-09
> **kevdog said:**
> Kernel Check

Thats a pretty cool program -- now if I could just configure the kernel I would be in good shape

Does it delete any of the source files or the debs at the end of the installation???

It doesn't, but if you want to delete them enter the following command:
```
sudo rm -rf /usr/src/*.deb /usr/src/*.bz2
```

---

### Post by master_kernel on 2007-09-09
> **kevdog said:**
> Here's one example of an error I get:

kevin@Homer:/etc$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

Warning: Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:17:D9:68
                    ESSID:"Dorchester"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

kevin@Homer:/etc$ uname -r
2.6.22.6

Sounds like iwlist in Feisty is too outdated for the new kernel.

---

### Post by kevdog on 2007-09-09
It is but I tried to compile the latest alpha and beta from source.  I didnt receive any errors, but when I tried to use the utilities, I received like 50 errors.  Has this been a problem for you?

---

### Post by master_kernel on 2007-09-09
> **kevdog said:**
> It is but I tried to compile the latest alpha and beta from source.  I didnt receive any errors, but when I tried to use the utilities, I received like 50 errors.  Has this been a problem for you?
Since I use a wired ethernet, my iwlist reports it can't find wireless. No suprise. I updated to the 2.6.22.6 kernel about an hour ago, compiled the fglrx driver for my ATI card, and it works fine. I went back and read this whole thread, and my question now is what exactly is the problem?

---

### Post by kevdog on 2007-09-09
Ok just for this problem but how do I get rid of this:


Warning:kevin@Homer:~$ iwlist scan
 Driver for device wlan0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...


It works, but I cant compile a useful version of the alpha or beta source.

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html)

---

### Post by ayenack on 2007-09-10
> 
Posted By dwhitney67
[I]What does xorg.conf have to do with the kernel??

Ans: Nothing.[/I]

The reason to copy your xorg.conf is that when you compile the new kernel it'll mess up your xorg.conf... ergo make backup of xorg.conf then if all goes wrong with new kernel simply boot into old kernel and repair xorg.conf with backup. Simple. Same applies if you need to add an updated graphics driver. I would always advise having a backup of xorg.conf among others.

ayenack.

I would also advise using non restricted drivers where ever possible if you are going to compile a new kernel i.e. remove any nvidia drivers and use the standard Ubuntu nvidia driver that is installed by default on the system. Then upgrade the graphics or whatever driver after the kernel is compiled and working. If this means turning off drivers in restricted drivers manager then I would do that. This is how I personally would go about it. Even better is to compile a kernel on a clean machine. Not sure what m_k thinks about this but it does simplify things in my opinion.

---

