---
title: "gptsync: GPT partition of type 'Unknown' found, will not touch this disk."
date: 2009-10-21
forum: Apple Hardware Users
---

### Post by proycon on 2009-10-21
This is a post for anybody who comes across this difficult problem, reported by gptsync , shipped with rEFIt in its partition editor. The error is: 
  GPT partition of type 'Unknown' found, will not touch this disk.

This is what I got when I resized my linux partition using parted, resulting in the GPT and MBR partitions going out of sync. Now this is something rEFIt's gptsync should be able to solve fairly easily, but if you have a so called 'BIOS Boot Partition', a small partition created by grub2 (as shipped with Karmic), then you're in quite some trouble. The partition tables won't sync and you'll find yourself unable to boot your linux system.

It took me numerous hours to fix this issue. And now that the necessary package has been fixed, the solution is fairly simple:

- Grab an Ubuntu live CD and boot
- Install gptsync_0.13-10 or higher from *Debian* packages (Ubuntu doesn't ship it, and the original rEFIt doesn't have the fix (yet?). Download from packages.debian.org and install with dpkg --install
- Run gptsync on the affected disk
- Reinstall grub ( $ sudo grub-install /dev/sda )

More about the issue can be read here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545190](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=545190) , note though that the issue was erroneously believed to be fixed in 0.13-4, for the actual fix you need at least 0.13-10 . 

I hope this post saves someone from two days of headaches :)

---

### Post by domedmunds on 2009-10-22
I have been experiencing this issue my self on  new MacBook Pro 5,1 and it has been interesting to say the least. However I am a newbie with Ubuntu and terminal and such and would be really grateful if you could explain the process is easy steps.

Much appreciated if possible.

---

### Post by proycon on 2009-10-22
I'll try to describe the steps that worked for me more verbosely. It may seem a bit intimidating at first. You also have to be *well aware* that you are messing with partition tables and bootloaders, which always comes at a *certain risk* of not being able to boot or even losing data, so make sure to have backups !!! 

( In this example I assume your disk is /dev/sda , default for macbooks )

[COLOR="Red"]Please follow updated instructions in next post instead![/COLOR]

[COLOR="Silver"]
1) Download an Ubuntu Live CD  ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)  ) and burn the ISO to CD.
2) Boot your macbook from the CD 
3) When in Ubuntu, download gptsync-0.13-10 from [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync)
4) Open a terminal and install the package you just downloaded:
  $ sudo dpkg --install gptsync*deb
5) Run gptsync on the affected disk
  $ sudo gptsync /dev/sda
6) Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy of rEFIt on CD if you're concerned)
  $ grub-install /dev/sda
7) reboot, the system should be able to boot again now[/COLOR]

---

### Post by domedmunds on 2009-10-22
Proycon,

Thanks for the speedy response I will have a go later on today and let you know if i get it working.

cheers

d

---

### Post by domedmunds on 2009-10-22
Proycon,

everything goes well until I reach...
6) Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy of rEFIt on CD if you're concerned)
  $ grub-install /dev/sda

running this command returns the following error:
grub-mkdevicemap: error: cannot open /boot/grub/device.map

does it matter which directory I am in when I type this?

Thanks in advance

d

---

### Post by proycon on 2009-10-22
Oh, that is actually quite a good point which I completely overlooked in my earlier explanation. I think you'll have to chroot into your original distribution as otherwise it can't properly reinstall grub.

Here are revised instructions for the whole process:

( In this example I assume your disk is /dev/sda , default for macbooks, and your root partition is /dev/sda4 , adapt these if necessary! )

1) Download an Ubuntu Live CD ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) ) and burn the ISO to CD.
2) Boot your macbook from the CD (hold option key at startup if you don't have rEFIt)
3) Open a terminal, mount your original root partition
- $ sudo mkdir /mnt/root
- $ sudo mount -t ext4 /dev/sda4 /mnt/root
4) Find the correct package for your architecture on [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync) and download it to somewhere under /mnt/root/ 
5) Set up /proc and /dev
- $ sudo mount -t proc none /mnt/root/proc
- $ sudo mount -o bind /dev /mnt/root/dev
6) Chroot into your original system, you're now in your own system.
- $ sudo chroot /mnt/root /bin/bash
7) Install the package downloaded in step 4
- $ sudo dpkg --install gptsync*deb
8) Run gptsync on the affected disk
- $ sudo gptsync /dev/sda
9) Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy of rEFIt on CD if you're concerned)
- $ sudo grub-install /dev/sda
10) reboot, the system should be able to boot again now 

Hopefully it works for you, this is what I did in my situation as well.

---

### Post by domedmunds on 2009-10-22
[COLOR=Magenta]DON'T WORRY - I FOUND OUT ABOUT $ sudo nautilus[/COLOR]
[COLOR=DimGray]
point 4. how can i copy to this directory? if i try and drag the file over it tells me I do not have permissions and forces me to cancel.

is it possible to download via terminal at point 6/7?

i'm very grateful for your help and the speedy introdution to terminal and the command line, quite a change for a macuser ;)


[/COLOR]

---

### Post by proycon on 2009-10-22
Or you could of course use plain cp ;) Or download in terminal using wget . If would be a good idea to familiarize yourself with the basics of the command line.

---

### Post by domedmunds on 2009-10-22
indeed. i'll try that next as it has'nt worked, still getting the original message. so contemplating starting from right at the beginning.

---

### Post by proycon on 2009-10-22
Hmm.. It didn't work? What caused your problem in the first place?

---

### Post by domedmunds on 2009-10-22
a bit of history...

i've got me a new MacBook pro (MacBookPro 5,3), and have been trying to set it up with dual booting (os x and ubuntu 9.10 - i understand this is a beta until next week).

the process i have been going through is based on the the documentation I have come across on the Ubuntu forums as well as this: [https://help.ubuntu.com/community/MacBookPro5-3/Karmic](https://help.ubuntu.com/community/MacBookPro5-3/Karmic)

i'm in good situation as i am moving from an older machine so have used superDuper to create a backup of my os x files which I can restore when I need to reinstall everything.

once i have my base os x system up and workingi have been...
1 - creating a 100gb partition as free space using disk utility
2 - booting up from the cd i have created containing the 32bit version of ubuntu 9.10
3 - using gparted to ensure that we have space
4 - installing ubuntu to the largest continuos space
5 - ensuring that grub is installed to /sda3
6 - restarting the computer

rEFIt is on my machine so this boots up and show a generic icon for the new partition, i have then used the partition tool to resync but i get the message which is the title of this thread.

here are the details:

[COLOR="DarkOliveGreen"]Starting gptsync.efi

Current GPT partion table:
#	Start LDA	End LDA	Type
1					EFi System (FAT)
2					Mac OS X HFS+
3					Unknown
4					Basic Dara
5					Linux Swap

Current MBR partition table:
# A	Start LDA	End LDA	Type
1			EE EFi Protective
2 *			AF Mac OS X HFS+
3			BA Unknown
4			03 Linux

Status: GPT partition of type 'Unknown' found, will not touch this disk.
Error: Not Found returned from gptsync.efi[/COLOR]


[URL="http://gallery.me.com/wetrynottobe/100018"]i'll take a photo of the full message and post shortly. i'll also take a shot of the display in gparted when i boot from the disk.
[/URL]

---

### Post by proycon on 2009-10-22
Ok, you're on the very same hardware I am with an almost identical problem. I resized my partition using gparted and that's when the trouble started.  gparted is not GPT-aware so things got out of sync, gptsync usually corrected for this but chokes on the BIOS Partition. But you say the gptsync in Ubuntu (not gptsync.efi in rEFIt!!) still gives the same error? And you're sure you installed version 0.13-10 ?

Paste your $ sudo showpart  output (after chrooting into your system again, but no need to reinstall gptsync, it should be still there)

---

### Post by domedmunds on 2009-10-22
sorry chap i don't understand this sudo showpart output.

---

### Post by proycon on 2009-10-22
Oh, never mind..  When you ran gptsync itself ut already outputted the partitions on your disk right? If you can paste that output here it might be useful.

---

### Post by domedmunds on 2009-10-22
here you go:

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    780936343  Mac OS X HFS+
 3      780936344    780938297  BIOS Boot Partition
 4      780938298    968717594  Basic Data
 5      968717595    976773134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    780936343  af  Mac OS X HFS+
 3      780936344    780938297  da  Non-FS data
 4      780938298    968717594  83  Linux

Status: Tables are synchronized, no need to sync.


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    780936343  Mac OS X HFS+
 3      780936344    780938297  Unknown
 4      780938298    968717594  Basic Data
 5      968717595    976773134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    780936343  af  Mac OS X HFS+
 3 *    780936344    780938297  da  Unknown
 4      780938298    968717594  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 780936344:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Unknown
 Listed in MBR as partition 3, type da  Unknown, active

Partition at LBA 780938298:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 968717595:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by domedmunds on 2009-10-22
proycon

OK. I have got it working. it's nice too :)

So I followed your instructions then decided to try removing rEFIt from my Mac partition. Now when I boot up with ALT to define startup it will let me boot into the windows (linux) partition.

So I have Ubuntu 9.10 dual booting. Hurrah.

There was a weird moment where GRUB appeared in a loop however I booted via the live cd and went through the process again and all is well.

Thanks for all your help. D

---

### Post by arctanx on 2009-10-27
Thanks very much! Your instructions worked perfectly and I now have Karmic RC on running on my MacBook 5,1.

---

### Post by Red Nelb on 2009-11-07
Hi.

First of all - thanks a lot for posting this. I'm experiencing similar problems and this is without a doubt helping out a lot.

However, I've been having problems going through your instructions.

What package should I download? I'm using a 1st gen white macbook. I've tried the first one, but some error occurred and stopped my download. I then tried the second package (i386), which popped up an "install" button.

I first ignored it, although the next step didn't work. It said the file couldn't be found (or something along those lines - sorry for not noting the exact text. I can try again if it may help). I then tried following the automatic installation process (which was probably a horrible idea I guess), but it didn't change a thing.

I have pretty much 0 knowledge of how to use the terminal by the way. So sorry if I end up asking stupid questions :P

Any idea of what may causing this?

---

### Post by lhall on 2009-11-08
Im in a similar position as Red. I have it installed to a new partition on a first gen mac book. I am not exactly new to ubuntu or the terminal but this is the first time i have made it a native boot. I used to run ubuntu from virtual box, so i never had to deal with boot problems.

The problem i am having is that none of the commands i type were actually working. So i used the synaptic package installer to get gpt. When i ran it i got

ubuntu@ubuntu:~$ sudo gptsync /dev/sda3

Current GPT partition table:
 No GPT partition table present!

Current MBR partition table:
 MBR partition table is invalid!

what am i missing.  Also i dont understand how the chroot command works. I have never worked from a live CD. I usally go straight to install and never touch the cd again.

---

### Post by kevpatts on 2009-11-08
You should use:
sudo gptsync /dev/sda
instead of:
sudo gptsync /dev/sda3

On a separate note, I have a related problem. I have synced my GPT partition, reinstalled grub, but I still get a black screen when I try to boot ubuntu. I'm using rEFIt 0.13 and Partition Inspector gives me a report like this:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    591544359  Mac OS X HFS+
 3      591544360    591546313  Unknown
 4      591546314    615593189  Basic Data
 5      616753807    625142414  Linux Swap
 6      615593190    616753806  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    591544359  af  Mac OS X HFS+
 3 *    591544360    591546313  da  Unknown
 4      591546314    615593189  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 591544360:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Unknown
 Listed in MBR as partition 3, type da  Unknown, active

Partition at LBA 591546314:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 616753807:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

Partition at LBA 615593190:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap
```

---

### Post by Red Nelb on 2009-11-08
Alright, I tried again, and kept the results this time.

Should I add the $ sign after the chroot thing or not? I tried both, although none worked. 

This time I also saved it in the right place I believe (I did right-click / save link as/ file system / root (it said the folder was last modified at 17:00, which was exactly when I entered the last few commands).

Here is what I got:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# $ sudo dpkg --install gptsync*deb
$: command not found
root@ubuntu:/# sudo dpkg --install gptsync*deb
sudo: unable to resolve host ubuntu
dpkg: error processing gptsync*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gptsync*deb
root@ubuntu:/#

EDIT: okay, I found /mnt/root now, altough when I try saving the package into it I get this: 

"Error opening file '/mnt/root/gptsync_0.13-10_i386.deb': Permission denied"

---

### Post by kevpatts on 2009-11-08
just sounds like you're not using sudo with your dpkg command.

I was able to boot into Ubuntu by using the Option (Alt) key, and bypassing rEFIt, but then when I updated grub, and removed rEFIt, but then when I booted into Ubuntu again the screen just fills with the word GRUB GRUB GRUB GRUB repeatedly.

Not having any luck yet. going to use GParted live cd to remove all non-mac os partitions and restore the mac os x partition to the full drive capacity, and then start again.

---

### Post by lhall on 2009-11-08
Thanks for the help guys. The chroot command was giving me problems for some reason. But it seemed to work when i just switched in to super user. Now it seems to be all is well when i boot without rEFIit.

---

### Post by kevpatts on 2009-11-08
Glad you got it working. 

I'm also keeping an eye on [this]("http://ubuntuforums.org/showthread.php?p=8273366#post8273366") thread as it's a similar issue for me.

---

### Post by Red Nelb on 2009-11-08
@kevpatts

What do you mean? I'm pretty much copy-pasting the said commands.

By the way, I'm trying to install 9.10, if that may be a source of problems.

I'll try bypassing rEFIt at this point I guess.

---

### Post by Red Nelb on 2009-11-08
Okay, so now I've gone through all the steps but nothing seems to have changed.

I still only see Mac Os X and a generic partition icon on rEFIt and the partition tool still isn't working.

Any idea on what is not working?

---

### Post by mistermartin75 on 2009-11-15
I'm having similar problems. The partition tool doesn't work and I can only boot OS X, not the installed Ubuntu nor the Live CD. Tried installing rEFIt 0.12 but that doesn't even load.

**Update:** Knoppix to the rescue, once again. While Ubuntu always fails to boot from the Live CD when you actually need it, Knoppix never does. Started Knoppix, added Debian's sid repository and install gptsync. Ran it and everything worked!

---

### Post by proycon on 2009-11-19
I'm glad to see this thread solved the problem for several users.

[quote="Red Nelb"]
Okay, so now I've gone through all the steps but nothing seems to have changed.

I still only see Mac Os X and a generic partition icon on rEFIt and the partition tool still isn't working.

Any idea on what is not working?
[/quote]

If you've gone through all steps correctly, then the "gptsync: GPT partition of type 'Unknown' found, will not touch this disk" error should at least be gone. Isn't this the case?  If not, what was reported when you ran gptsync ? Running gptsync 0.13-10 (and no lesser version!) is the whole key here in resolving this problem. If you run gptsync twice, it should report that there is nothing to be done the second time around.

---

### Post by Nohtanhoj on 2009-11-20
This is what I did to get Ubuntu working: Nothing.

I figured that I was going to try the stuff in this thread (it all sounds like good advice), so I inserted my Live CD and held down Option as my Mac was booting (this looks for bootable devices by default). My main Mac OS X hard drive shows up, followed by the Live CD, and surprise, so does the Linux partition!!! I booted from it, set up my user account, and I'm typing from Ubuntu right now...

Even doubly better, if I just boot normally without holding down Option, my iMac boots to OS X and bypasses rEFIt (I was planning to do this anyway)...

I know it sounds pretty obvious, but I suggest you give this a quick try before you mess with your partition table... I didn't even try it consciously and it worked. =D

---

### Post by phorque on 2009-11-29
> **proycon said:**
> Oh, that is actually quite a good point which I completely overlooked in my earlier explanation. I think you'll have to chroot into your original distribution as otherwise it can't properly reinstall grub.

Here are revised instructions for the whole process:

( In this example I assume your disk is /dev/sda , default for macbooks, and your root partition is /dev/sda4 , adapt these if necessary! )

1) Download an Ubuntu Live CD ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) ) and burn the ISO to CD.
2) Boot your macbook from the CD (hold option key at startup if you don't have rEFIt)
3) Open a terminal, mount your original root partition
- $ sudo mkdir /mnt/root
- $ sudo mount -t ext4 /dev/sda4 /mnt/root
4) Find the correct package for your architecture on [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync) and download it to somewhere under /mnt/root/ 
5) Set up /proc and /dev
- $ sudo mount -t proc none /mnt/root/proc
- $ sudo mount -o bind /dev /mnt/root/dev
6) Chroot into your original system, you're now in your own system.
- $ sudo chroot /mnt/root /bin/bash
7) Install the package downloaded in step 4
- $ sudo dpkg --install gptsync*deb
8) Run gptsync on the affected disk
- $ sudo gptsync /dev/sda
9) Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy of rEFIt on CD if you're concerned)
- $ sudo grub-install /dev/sda
10) reboot, the system should be able to boot again now 

Hopefully it works for you, this is what I did in my situation as well.


The only part that doesn't make sense to me is installing grub to /dev/sda ... can't you install it to /dev/sda3 (as per the generic install instructions) if you still want to use rEFIt to select which system to boot into?

---

### Post by phorque on 2009-11-29
> **Nohtanhoj said:**
> This is what I did to get Ubuntu working: Nothing.

I figured that I was going to try the stuff in this thread (it all sounds like good advice), so I inserted my Live CD and held down Option as my Mac was booting (this looks for bootable devices by default). My main Mac OS X hard drive shows up, followed by the Live CD, and surprise, so does the Linux partition!!! I booted from it, set up my user account, and I'm typing from Ubuntu right now...

So does that mean you need to have the liveCD in every time you want to boot into Linux?

---

### Post by phorque on 2009-11-29
Also, just for anyone reading this. I installed Karmic 9.10 on a MacBook Pro 5,4 and just chose "Legacy OS" from the rEFIt menu and it boots fine.

I'm wondering if it's even worth running the partition sync becuase both OSs boot fine

---

### Post by linuxopjemac on 2009-11-29
Not necessary. rEFIt does not recognise ext4 yet, so it does not know that it's actually your Linux partition. Don't touch a working system...

---

### Post by dmtactical on 2009-11-29
First, diagnosis: I get the 'unknown' message from rEFIt. If I boot from legacy OS, nothing happens, except for the legacy OS picture showing on the center of the screen. If I boot from OSX, it boots OSX. If I boot from Windows (which is actually my Ubuntu partition), it says operating system not found.

I'm going through the steps in post #6.

First, I have no idea how to know that the package from step 4 is under /mnt/root. I went to Downloads, where the file was located, and typed 'sudo cp gptsync_0.13-11_i386.deb /mnt/root' .Then I moved on to step 5. Both steps of step 5 return a "does not exist" message. When I run step 6 (which probably should not work anyway if step 5 didn't work) I get a "no such file or directory."

Perhaps I should just install again in the Windows partition that was created by Boot Camp? I don't know if that would fix anything, if I erased the install and started over again.

---

### Post by JohnAtilano on 2009-11-29
> **dmtactical said:**
> First, diagnosis: I get the 'unknown' message from rEFIt. If I boot from legacy OS, nothing happens, except for the legacy OS picture showing on the center of the screen. If I boot from OSX, it boots OSX. If I boot from Windows (which is actually my Ubuntu partition), it says operating system not found.

I'm going through the steps in post #6.

First, I have no idea how to know that the package from step 4 is under /mnt/root. I went to Downloads, where the file was located, and typed 'sudo cp gptsync_0.13-11_i386.deb /mnt/root' .Then I moved on to step 5. Both steps of step 5 return a "does not exist" message. When I run step 6 (which probably should not work anyway if step 5 didn't work) I get a "no such file or directory."

Perhaps I should just install again in the Windows partition that was created by Boot Camp? I don't know if that would fix anything, if I erased the install and started over again.

I had some difficulty doing this.  The way I solved it was the following:

After step 6 and before step 7, do the following:

$ cd /mnt/root
$ wget [http://http.us.debian.org/debian/pool/main/r/refit/gptsync_0.13-11_i386.deb](http://http.us.debian.org/debian/pool/main/r/refit/gptsync_0.13-11_i386.deb)

This will download the file, again, into /mnt/root

Continue with step 7.  It should install.

Note that the link I provided is the 32-bit version from a North American site.  You may need to alter your link depending on version and location.

---

### Post by dmtactical on 2009-11-30
Ok, I managed to go through all of the first 9 steps with no issues. However, when I run gptsync, it tells me that everything is fine and it does not need to synchronise. Here is what happens when I reboot: If I hold option, I get the boot menu with two options, the rEFIt menu, which takes me to rEFIt, where I have the choice of Legacy OS or Mac OS, or I have the choice of Windows (the boot camp partition). If I choose Windows, I am brought to an Ubuntu boot menu, which reads: GNU Grub version 1.97~beta4
Then I can choose between Ubuntu Linux 2.6.31-15-generic, ""(recovery mode), 2.6.31-14-generic, or ""(recovery mode). It also has options for memory test and Mac OSX. If I select any of the Ubuntu options (not the recovery ones), I get the Ubuntu logo for a few seconds, then it says something about setting splash to 1024x768 (flashes too fast to read it exactly), and then the screen goes black and nothing happens.

If I use the sync in rEFIt it give the same error message that is in the thread title. 

Earlier when I was trying to work on this, I was getting confused and I just started skipping steps and trying the steps out of order, then I shut down and rebooted and suddenly Ubuntu worked. I installed updates, and started to install proprietary drivers, when it froze completely. I did a hard shut down, and when I restarted I got what I am experiencing now.

---

### Post by psasidhar on 2009-12-03
HI Proycon,

I followed the detailed instructions in your comment 6. 

And after all the steps and after rebooting, I don't see any 'Linux' in the rEFIt menu. At least, before these steps, I used to see an 'unknown' item, next to Leopard and Vista tabs in the rEFIt menu.

Right now, I have this from fdisk:

Command (m for help): p

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000001f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       30426   244187136   af  HFS / HFS+
/dev/sda3   *       30442       35786    42923472+   7  HPFS/NTFS
/dev/sda4           35786       35786         977   da  Non-FS data

Any helpful pointers?

Thanks,
Sasi.

---

### Post by psasidhar on 2009-12-03
Hi proycon,

My apologies, I spoke too soon.

I am able to boot into Ubuntu. I am getting "OS X/Windows" option in rEFIt menu, and then when I choose "Windows", I am getting grub menu to load Ubuntu/Vista etc. 

I wish I could avoid this two step boot menu option to get to Ubuntu. Is this because I installed grub to /dev/sda at step 9 in your list?

But I am happy that I am able to install Ubuntu (with triple booting). 

Thanks for your instructions.

I am curious, is there a way to have a triple boot option at rEFIt menu level itself? (instead of this circuitous route of rEFIt -> Windows selection -> grub -> Ubuntu selection?

-Sasi.

---

### Post by Darrell B. on 2009-12-05
Alright guys, so I have a 1st generation macbook, and I'm at the part where i'm trying to download the gptsync file to my /mnt/root folder. It is not allowing me to save it to that location because it's saying my permission is denied, how to I get around this guys??? I've gone back to my mac partition and granted read/write access to everyone for my hd, and it's still not letting me save the gptsync file to /mnt/root....also how will the number after "ext" be different for everyone, or will it always be "ext4"???

Thanks, 

Darrell

---

### Post by Darrell B. on 2009-12-05
okay so i was finally able to save gpt file to the root folder, now i have problems with step #5, when i run the command "sudo mount -t proc none /mnt/root proc" it says that "mount point /mnt/root/proc does not exist???

is there an easier way of running gptsync than the aforementioned solution on the first page of the post?

---

### Post by Darrell B. on 2009-12-05
Okay guys, so when refit boots when I startup the computer, I see that my two options are to boot to mac os, or to boot to legacy os. I wasn't able to successfully run gptsync as mentioned above, so I just tried to boot to the legacy os partition at the refit bootup screen, and then grub runs and i'm allowed to choose ubuntu, and it works! so I was just wondering if this means that everything is ok, or that I still need to do the aforementioned steps as mentioned on the first page to fix the partition, since it doesn't actually show the partition as being ubuntu.....

---

### Post by Ostrava on 2009-12-06
> **dmtactical said:**
> Ok, I managed to go through all of the first 9 steps with no issues. However, when I run gptsync, it tells me that everything is fine and it does not need to synchronise. Here is what happens when I reboot: If I hold option, I get the boot menu with two options, the rEFIt menu, which takes me to rEFIt, where I have the choice of Legacy OS or Mac OS, or I have the choice of Windows (the boot camp partition). If I choose Windows, I am brought to an Ubuntu boot menu, which reads: GNU Grub version 1.97~beta4
Then I can choose between Ubuntu Linux 2.6.31-15-generic, ""(recovery mode), 2.6.31-14-generic, or ""(recovery mode). It also has options for memory test and Mac OSX. If I select any of the Ubuntu options (not the recovery ones), I get the Ubuntu logo for a few seconds, then it says something about setting splash to 1024x768 (flashes too fast to read it exactly), and then the screen goes black and nothing happens.

If I use the sync in rEFIt it give the same error message that is in the thread title. 

Earlier when I was trying to work on this, I was getting confused and I just started skipping steps and trying the steps out of order, then I shut down and rebooted and suddenly Ubuntu worked. I installed updates, and started to install proprietary drivers, when it froze completely. I did a hard shut down, and when I restarted I got what I am experiencing now.

This is the same issue I had, and when I restarted Ubuntu, GRUB continually looped on my screen.

---

### Post by haxple on 2009-12-06
> **Ostrava said:**
> This is the same issue I had, and when I restarted Ubuntu, GRUB continually looped on my screen.
That happened to me the first time, thats because you installed grub on /dev/sd3 (sudo grub-install /dev/sda3 .. its supposed to be /dev/sda). 
-----------------------

My problem is I alredy did all the steps (twice) without problems.. "If I choose Windows, I am brought to an Ubuntu boot menu, which reads: GNU Grub version 1.97~beta4.."

However, when i select to start ubuntu, the screen just goes black.

---

### Post by Ostrava on 2009-12-12
So, the only way to rectify this is to start over? I'll follow your advice and see what happens. Thanks.

---

### Post by teugon on 2010-01-01
> **proycon said:**
> Oh, that is actually quite a good point which I completely overlooked in my earlier explanation. I think you'll have to chroot into your original distribution as otherwise it can't properly reinstall grub.

Here are revised instructions for the whole process:

( In this example I assume your disk is /dev/sda , default for macbooks, and your root partition is /dev/sda4 , adapt these if necessary! )

1) Download an Ubuntu Live CD ( see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD) ) and burn the ISO to CD.
2) Boot your macbook from the CD (hold option key at startup if you don't have rEFIt)
3) Open a terminal, mount your original root partition
- $ sudo mkdir /mnt/root
- $ sudo mount -t ext4 /dev/sda4 /mnt/root
4) Find the correct package for your architecture on [http://packages.debian.org/sid/gptsync](http://packages.debian.org/sid/gptsync) and download it to somewhere under /mnt/root/ 
5) Set up /proc and /dev
- $ sudo mount -t proc none /mnt/root/proc
- $ sudo mount -o bind /dev /mnt/root/dev
6) Chroot into your original system, you're now in your own system.
- $ sudo chroot /mnt/root /bin/bash
7) Install the package downloaded in step 4
- $ sudo dpkg --install gptsync*deb
8) Run gptsync on the affected disk
- $ sudo gptsync /dev/sda
9) Reinstall grub (this shouldn't overwrite rEFIt, but you can keep a copy of rEFIt on CD if you're concerned)
- $ sudo grub-install /dev/sda
10) reboot, the system should be able to boot again now 

Hopefully it works for you, this is what I did in my situation as well.



ok man my problem is this I follow the istruction in ubuntuforums about macbook 5.2 karmik but when I used tried to boot the other partition I had a simple common bootcamp skin stuck in the center of the screen without any chance to run ubuntu, I tried to make what you said in this topic but it is useless: I booted by cd then I've open the terminal and at point 3) and others command line alwais happens that after I give the command I got a new line without any error or I only have like reply the command doesn't exist. can you explain me what I have to do please? I'm working on it since 4 days and I don't stand a chance

---

### Post by togril2010 on 2010-01-03
Same error for me.
I have:
1XMacOS system partition
1XHFS "Data" partition (I can not remove this due to radmind stuff at work)

So I made some space after Data and followed the instructions for dual boot (mactelsupport). 

I am now confused: 
In the instructions on the mactel page GRUB must be written to the Linux partition...
Here you are saying intstall in /dev/sda..???
..... then what about my osx?
So I'm pretty nervous about this.

I realise I am a noob, even having used such systems before, and really appreciate the support, but Ive spent 2 days on this, and I am just stacking up grey icons in rEfit.


_____UPDATE_____manged to get it to boot in generic mode, but it's still not working as the above suggests.

---

### Post by jeromemoisan on 2010-01-04
Hello, I'm new in Forums and in Ubuntu, and english is not my first langage, so I will do my best to be clear. I'm having the same problem, and I'm not able to boot in Linux. I installed linux Karmic koala, and rEFIt. I'm having the message: 
gptsync: GPT partition of type unknown, will not touch this disk. 


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1      459423784    459425737  Unknown
 2         409640    459423783  Mac OS X HFS+
 3      459425738    487083941  Basic Data
 4      487083942    488397134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1      459423784    459425737  ef  EFI System (FAT)
 2         409640    459423783  af  Mac OS X HFS+
 3 *    459425738    487083941  83  Linux
 4      487083942    488397134  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 459423784:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 1, type Unknown
 Listed in MBR as partition 1, type ef  EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 459425738:
 Boot Code: Unknown, but bootable
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 487083942:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

I really not know what to do next. Can somebody help me please!

Jerome

---

### Post by Ostrava on 2010-01-12
> **haxple said:**
> That happened to me the first time, thats because you installed grub on /dev/sd3 (sudo grub-install /dev/sda3 .. its supposed to be /dev/sda). 
-----------------------

My problem is I alredy did all the steps (twice) without problems.. "If I choose Windows, I am brought to an Ubuntu boot menu, which reads: GNU Grub version 1.97~beta4.."

However, when i select to start ubuntu, the screen just goes black.

I've done this and followed the instructions carefully but the GPT partition error still occurs and when I'm able to boot into Ubuntu, it says that there's no proprietary drivers available.

Pretty much I'm unable to access the internet nor change the appearance settings. Only when booting from the CD am I able to activate the drivers for the network and graphics.

Any help?

Edit: Well, I figured a workaround for this. I installed Ubuntu 9.04, did the updates then upgraded to 9.10 and everything worked fine. No need to sync the partition tables because it's already done in 9.04.

---

### Post by yiannisp on 2010-01-28
Hi, 

I tried the fix as proposed in the first page but...

1. The gptsync runs correctly and synchronizes the mbr and gpt from the ubuntu live cd. 

2. When I restart the computer and enter the disk utility of refit, I still get the same message.

To sum up, the gptsync in the terminal of the ubuntu live cd says that everything is correct and synchronized, but refit still sees an Unknown disk...

Any help?

---

### Post by linuxopjemac on 2010-01-28
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

### Post by yiannisp on 2010-01-28
Sorry, but those are the exact same instructions given in the first page.

As I have already said, I have followed those but still refit does not see a synchronized mbr/gpt. However, through the ubuntu live cd the mbr/gpt tables seem to be synchronized (at least this is what gptsync says in terminal). 

Moreover, I can boot into Ubuntu by holding the options key, which brings up Apple's startup screen. My Ubuntu partition is called "Windows" there, obviously due to Bootcamp...

I have erased rEFIt and can login into both operating systems succesfully.

I still want to understand what went wrong if anyone can help. 

Sometime in future I might try installing windows as well...

Thanks for any help

---

### Post by langmore on 2010-01-31
The steps posted in response #6 worked.  I should add that if you use the "Update Manager" for the first time after following these steps it will attempt to update grub and give you a list of options.  It seems that all options will (temporarily) ruin the work you have just done!  So, here's what worked for me (32 or 64 bit Karmic).

1.  Choose to use the version of grub on the repository
2.  sudo grub-install /dev/sda
3.  sudo update-grub
4.  sudo grub-install /dev/sda

Of course only two of steps 2,3,4 are needed, but I wasn't sure on the proper order for update/install so I did all of them.

---

### Post by kev0153 on 2010-02-01
I have this exact same problem on my Macbook pro 1,1 and Ubuntu 9.1 I would like to solve this as I plan on triple booting with windows as soon as my new hard drive shows up.  


> **yiannisp said:**
> Sorry, but those are the exact same instructions given in the first page.

As I have already said, I have followed those but still refit does not see a synchronized mbr/gpt. However, through the ubuntu live cd the mbr/gpt tables seem to be synchronized (at least this is what gptsync says in terminal). 

Moreover, I can boot into Ubuntu by holding the options key, which brings up Apple's startup screen. My Ubuntu partition is called "Windows" there, obviously due to Bootcamp...

I have erased rEFIt and can login into both operating systems succesfully.

I still want to understand what went wrong if anyone can help. 

Sometime in future I might try installing windows as well...

Thanks for any help

---

### Post by kev0153 on 2010-02-05
Well I managed to solve my problem.  I had to use the advance option during the ubuntu install when setting up the partitions.  If I didn't it wanted to install an extra swap partition and that messed everything up.  By going advanced you force it to NOT install a swap (it b*tches at you but I ignored it).  I then installed grub on /dev/sda3 (again it bitches at you).  This worked but I lost windows.  I booted off from windows disc and did FIXMBR and this brought windows back.   I think I did a gptsync but can't remember, it was getting late.  Anyway everything works now.

One interesting note is that while my linux partition boots refit shows the generic legacy boot icon still.   I found a thread that shows how to fix it.   

[http://ubuntuforums.org/showthread.php?t=1346933](http://ubuntuforums.org/showthread.php?t=1346933)

some talk of it here as well

[http://ubuntuforums.org/showthread.php?t=1306308](http://ubuntuforums.org/showthread.php?t=1306308)

I should add I'm using Mac OS X 10.6, Ubuntu 9.1 and Windows XP on an older Macbook pro 1,1

---

### Post by Devilot on 2010-02-08
I have a problem myself. I tried doing what the guide suggested... but when I ran GPTsync (using 13-10 and Ubuntu 9.10), it instead synced it so the drive in question was unknown on both GPT and MBR, instead of being recognized by both. From there, I continue, and when I restart, the drive is still listed as "Legacy OS" rather than Linux, the Partition Tool in rEFIt still spits up a GPT error like before I started, and trying to start it up causes it to load up in text mode rather than starting the GUI. Any idea what's going on?

---

### Post by srs5694 on 2010-03-11
> **Devilot said:**
> I have a problem myself. I tried doing what the guide suggested... but when I ran GPTsync (using 13-10 and Ubuntu 9.10), it instead synced it so the drive in question was unknown on both GPT and MBR, instead of being recognized by both. From there, I continue, and when I restart, the drive is still listed as "Legacy OS" rather than Linux, the Partition Tool in rEFIt still spits up a GPT error like before I started, and trying to start it up causes it to load up in text mode rather than starting the GUI. Any idea what's going on?

I realize my reply is very late, but if you (or some other reader) still have the problem, I recommend you try my [GPT fdisk](http://www.rodsbooks.com/gdisk/) program. This program is modeled after Linux fdisk, but it's for GPT partitions. It includes the ability to create a hybrid MBR (similar to what gptsync does), but it's much more flexible about it. Clean up the GPT side, and when it's working right, create a new hybrid MBR via the 'h' option on the recovery & transformation menu.

Also, I recommend *not* using a hybrid MBR on a Linux/MacOS dual-boot; use a hybrid MBR *only* when Windows or some other GPT-unaware OS is involved. As many of those posting to this thread have found out the hard way, hybrid MBRs are flaky and dangerous.

---

### Post by mrg201 on 2010-05-02
This fix is linked to from the documentation in several of the guides for installing various Ubuntu distributions, including Lucid, on models of the Macbook Pro.

Just thought I would point out that this fix is no longer "solved" and so someone may want to remove that comment, or set up a new thread, because the fix does not work for Lucid - even though the Lucid guide links to this.

I have got this fix to work for 64Bit Karmic, however, I was trying a clean install of Lucid and the fix no longer works, at least on my set-up.

I have a Macbook Pro 5,2, I installed the 64Bit Lucid using all the standard options and got the GPT error on refit as expected. I followed the instructions in comment 6 (which all worked fine in Karmic), but when I try step 8 (sudo gptsync /dev/sda) to sync the GPT and MBR then the process fails with the following:


root@ubuntu:/# sudo gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    625409639  Mac OS X HFS+
 3      625409640    625411593  BIOS Boot Partition
 4      625411594    962435031  Basic Data
 5      962435032    976773134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    625409639  af  Mac OS X HFS+
 3              1    625411593  ee  EFI Protective
 4      625411594    962435031  83  Linux

Status: MBR partition table is invalid, partitions overlap.


I'm far from an expert so I have no idea how to solve that problem, but if anyone has any bright ideas then I'd greatly appreciate them. Failing that I am going to go back and try installing Karmic then updating to Lucid rather than trying a clean install and will report back if that is successful.

---

### Post by mrg201 on 2010-05-02
Installing Karmic, doing the fix, then upgrading to Lucid worked. Although there was a Grub install error warning during the upgrade (I chose the option: keep local configuration file), so I followed the instructions in comment 52 after the upgrade but before restarting. The first boot didn't work but the second attempt and all thereafter have been fine.

---

### Post by rabidcentipede on 2010-05-02
> **mrg201 said:**
> This fix is linked to from the documentation in several of the guides for installing various Ubuntu distributions, including Lucid, on models of the Macbook Pro.

Just thought I would point out that this fix is no longer "solved"

...


root@ubuntu:/# sudo gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    625409639  Mac OS X HFS+
 3      625409640    625411593  BIOS Boot Partition
 4      625411594    962435031  Basic Data
 5      962435032    976773134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    625409639  af  Mac OS X HFS+
 3              1    625411593  ee  EFI Protective
 4      625411594    962435031  83  Linux

Status: MBR partition table is invalid, partitions overlap.


I'm far from an expert so I have no idea how to solve that problem, but if anyone has any bright ideas then I'd greatly appreciate them. Failing that I am going to go back and try installing Karmic then updating to Lucid rather than trying a clean install and will report back if that is successful.


I'm having this same problem - gptsync stil thinks that my partitions overlap, even though I'm able to bypass rEFIt by holding "option", and then selecting "Windows" from the choices, and then picking Lucid from the options, and it works just fine. 

I don't particularly want to have to start all over, install karmic, and then update - is there any way to get this working from a fresh lucid install?

---

### Post by srs5694 on 2010-05-02
I'm not familiar with the whole procedure, and I'm only somewhat familiar with gptsync; however, it appears to me as if the version of gptsync you're using has created two 0xEE (EFI GPT) protective partitions, one of which overlaps other partitions (it's MBR partition #3, which begins at sector 1 and ends at sector 625411593). Perhaps you can find another version of gptsync that's not broken; or you could try my [GPT fdisk](http://www.rodsbooks.com/gdisk/) instead, since it can create hybrid MBRs similar to those made by gptsync.

---

### Post by rabidcentipede on 2010-05-03
How are you suggesting we use gdisk? from the recovery menu, selecting option g?

In my case, when I ran gparted, I got the following configuration:
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    711385767  Mac OS X HFS+
 3      711387136    711389183  Unknown
 4      711389184    965910527  Basic Data
 5      965910528    976773119  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    711385767  af  Mac OS X HFS+
 3              1    711389183  ee  EFI Protective
 4      711389184    965910527  83  Linux

Status: GPT partition of type 'Unknown' found, will not touch this disk.

Will gdisk handle this "unknown" partition?

Sorry, I'm a bit of a novice at dealing with partitions. I've used gparted before, but never had to mess with GPT vs. MBR issues.

---

### Post by linuxopjemac on 2010-05-03
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

---

### Post by srs5694 on 2010-05-03
> **rabidcentipede said:**
> How are you suggesting we use gdisk? from the recovery menu, selecting option g?

No, option 'h' from the recovery & transformation menu. The 'g' option converts GPT to MBR (wiping out the GPT data structures). See my [page on hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) for all the gory details.

> Will gdisk handle this "unknown" partition?

Yes. The partition is only "unknown" to gptsync. GPT fdisk will accept any partition as one to hybridize, whether or not it recognizes its type code. (You can adjust its MBR type code as you see fit.)

---

### Post by klausenm on 2010-05-04
Hi,

i had a working dual boot setup with OSX and Ubuntu until yesterday where i tried to reinstall grub2 during a lucid install to a unused partition. Now i can no longer boot linux, when i choose one of the linux partitions in rEFIt either a totaly black screen or a black screen whith a blinking cursor shows up.

i think my hybrid mbr/gpt partition table is messed up and thats why i cant install grub cleanly. right now it looks like: (i didnt know that no extended mbr partitions are possible in a hybrid setup, thats why there are so many partitions)

```
root@ubuntu:/var/tmp# gptsync /dev/sda

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         411648      2514943  EFI System (FAT)
 3        2514944      8374271  Linux Swap
 4        8374272     27903999  EFI System (FAT)
 5       27904000     47433727  EFI System (FAT)
 6       47433728     86496231  Mac OS X HFS+
 7       86758376    976510983  Mac OS X HFS+

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       411648      2514943  83  Linux
 3        2514944      8374271  82  Linux swap / Solaris
 4        8374272     27903999  83  Linux

Status: Tables are synchronized, no need to sync.
```when i try to install grub it shows:

```
grub-install  /dev/sda  /usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!. 

```so i guess the fact that grub does not find the bios partition table could be the problem.

any ideas what i have to do to fix it? why does  gptsync find the mbr(=bios?) partition table and grub doesnt?

installing grub to one of the other linux partitions (which would be ok for me) gives an error as well (something about embedding not possible / unreliable block lists)

---

### Post by rabidcentipede on 2010-05-05
> **linuxopjemac said:**
> [http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

This still doesn't work for me.

Now, I just get this error:

```

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    711385767  Mac OS X HFS+
 3      711387136    711389183  BIOS Boot Partition
 4      711389184    965910527  Basic Data
 5      965910528    976773119  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    711385767  af  Mac OS X HFS+
 3              1    711389183  ee  EFI Protective
 4      711389184    965910527  83  Linux

Status: MBR partition table is invalid, partitions overlap.

```

---

### Post by ne0genius on 2010-05-05
i have the same error in gptsync. When I installed Lucid I installed grub to /dev/sda. it would seem like this is the cause of the problem, however refit functions exactly as it should booting both OS X and Ubuntu properly. The only glitch is that know there is like a 20 second pause before the refit boot screen which never happened in the past when i installed grub to /dev/sda3.this is my output from refit gptsync.

[IMG]http://content.screencast.com/users/openRevit/folders/Default/media/8bfed501-f41a-41b5-aac9-f89db3986738/2010-05-05%2023.22.35.jpeg[/IMG]

---

### Post by srs5694 on 2010-05-06
A few points:


[list]
[*]The gtpsync program generates a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is required to let certain versions of Windows boot from a GUID Partition Table (GPT) disk.
[*]Linux can boot from a GPT disk just fine, so in theory you don't need a hybrid MBR; however, I'm unfamiliar with the finer points of booting Linux from GPT on a Mac, so I don't know if there might be certain limitations or requirements in that environment if you do away with the hybrid MBR in favor of a more conventional protective MBR. I know I've run across a Web page somewhere with lots of information on this, but I'm afraid I don't have it bookmarked.
[*]To klausenm: Your GUID Partition Table includes four EFI System partitions, some of which are quite large. I suspect that all but the first of these should actually be marked as Basic Data (GUID partition type EBD0A0A2-B9E5-4433-87C0-68B6B72699C7), which is what both Linux and Windows use to identify their OS and data partitions. (Maybe one should be Linux swap, 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F.) I don't know if changing these type codes would help at all with your problem, but it might. AFAIK, my own [GPT fdisk](http://www.rodsbooks.com/gdisk/) is the only Linux utility that can change GPT type codes without affecting the contained filesystem. It's possible that the text-mode diskutil or gpt utilities under OS X can do so, but I'm not very familiar with them, so I'm not sure of that, one way or the other.
[*]The BIOS Boot Partition (GUID type code 21686148-6449-6E6F-744E-656564454649) is used by GRUB 2 on *BIOS-based* computers. AFAIK, it's not used by GRUB 2 on EFI-based systems such as Macs, but it's possible that I'm misunderstanding something. If GRUB 2 is complaining about the lack of a BIOS Boot Partition, then perhaps it thinks it's running on a BIOS-based system (perhaps because of how Boot Camp works), or maybe it's just plain confused, or maybe I'm mistaken on this score. The BIOS Boot Partition can be quite small (as small as 30-something KB).
[*]klausenm, you've got room between your two OS X partitions to create a BIOS Boot Partition; however, doing so will violate [Apple's partitioning requirements,](http://developer.apple.com/mac/library/technotes/tn2006/tn2166.html) with the result that you may have problems with future OS X installations or upgrades. In any event, the GRUB 2 complaints about the BIOS Boot Partition are warnings, not errors -- it's just telling you about a limitation, not saying that it won't work. See [the GRUB documentation on the BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) for details.
[/list]

---

### Post by aramisbear on 2010-05-08
> **rabidcentipede said:**
> This still doesn't work for me.

Now, I just get this error:

```

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    711385767  Mac OS X HFS+
 3      711387136    711389183  BIOS Boot Partition
 4      711389184    965910527  Basic Data
 5      965910528    976773119  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    711385767  af  Mac OS X HFS+
 3              1    711389183  ee  EFI Protective
 4      711389184    965910527  83  Linux

Status: MBR partition table is invalid, partitions overlap.

```

I'm having the EXACT same error.  I'm wondering what would happen if I deleted the second EFI partition which seems to be causing the issue.  It looks shouldn't be there and appears to be the cause of all the problems.  Just not looking forward to having to do a full restore if I'm wrong.

---

### Post by sambao21 on 2010-05-23
> **rabidcentipede said:**
> This still doesn't work for me.

Now, I just get this error:

```

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    711385767  Mac OS X HFS+
 3      711387136    711389183  BIOS Boot Partition
 4      711389184    965910527  Basic Data
 5      965910528    976773119  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    711385767  af  Mac OS X HFS+
 3              1    711389183  ee  EFI Protective
 4      711389184    965910527  83  Linux

Status: MBR partition table is invalid, partitions overlap.

```

I am also see this exact same error.  Ubuntu and OSX both boots up just fine though, but I can't do anything to remove the ubuntu partition if i wanted to.  In OSX disk utility, I can't modify any partitions because they're all in the MBR.  I'd like to resize the Ubuntu partition as well as try reinstall from scratch.

---

### Post by jamesixgun on 2010-05-23
If you want to reinstall, follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1468240&page=5").

If you don't want to clicky, here's how you go about fixing this. Don't ask my why or how it works, because I don't really know. But it does work, on my revA MacBook (1,1) and on Jacques4x4's machine (whatever it is).

1. Boot from OSX install disc, run Disk Utility, and format your HD with GUID partition table.
2. Reinstall OSX (hopefully from a backup, and if you have a bootable backup, say with CCC or some other cloning tool, you can boot from the backup, use Disk Utility there, and then just clone the drive over).
3. Boot into OSX from the fresh copy on your HD.
4. Get rEFIt.
5. Use BootCamp to partition your drive.
6. Boot from Lucid install disc, open gparted, delete the Bootcamp partition.
7. You should see three partitions: EFI, OSX, and Free Space.
8. At the beginning of Free Space, create a small partition for GRUB (I used 512mb) and format it NTFS.
9. Save changes.
10. Click the install icon on LiveCD desktop.
11. Go through the first couple of screens (language, location, etc.). When it asks you where you want to install Ubuntu, choose 'Specify partitions manually' or whatever it says. The last option anyway.
12. Select the partition you just created (should be /dev/sda3). Choose Change --> use as NTFS. For Check Format, choose 'mount point = /windows.'
13. Select the free space. Within the free space, create a large partition for Ubuntu at the beginning of the free space (for the Ubuntu portion, choose 'Use as Ext4,' mount point = / ), and build a smaller partition (equivalent to the amount of RAM in your machine) for the swap (choose Add --> use as Swap).

If everything worked properly, you should now have 5 partitions (sda1: EFI; sda2:OSX; sda3:NTFS; sda4:Ubuntu; sda5:Swap).

14. Go through the rest of the installation. On the last screen, click the Advanced button and choose to install GRUB at /dev/sda3. Without the above steps (ie. creating the special partition for GRUB, and the one for Ubuntu and the Swap) you will not have an option for /dev/sda3 and GRUB will install itself to /dev/sda, thereby turning your entire HD into MBR, and thus creating the overlapping partition map.
15. Let Ubuntu install itself.
16. After installation of Ubuntu, restart. At rEFIt, choose the partition tool and resync. It should now work flawlessly.
17. Power off.
18. Power on, rockandroll.

Unfortunately, I'm unaware of a fix without a complete wipe and reinstall. If one exists, I hope someone will correct me. 

The problem is that without manually specified partitions, GRUB plants itself in /dev/sda, and by doing so creates the overlapping partition map. 

I hope this helps, and it should as long as you don't mind wiping your drive and installing everything from scratch (or a bootable backup).

---

### Post by srs5694 on 2010-05-23
> **jamesixgun said:**
> Unfortunately, I'm unaware of a fix without a complete wipe and reinstall. If one exists, I hope someone will correct me.

I've posted before in this thread, but people seem to be ignoring me. My own [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) package can create hybrid MBRs with a great deal of flexibility. It should be possible to use it to fix any problems that are caused by corrupt hybrid MBRs. Please review my earlier posts for additional details and other suggestions, and read my [hybrid MBR Web page](http://www.rodsbooks.com/gdisk/hybrid.html) for information on hybrid MBRs generally and on how to create them in gdisk. Note, however, that I don't have a dual-booting Intel-based Apple Macintosh, so I have no first-hand experience with this specific problem.

---

### Post by pclark36 on 2010-06-10
It appears that the dual mac/ubuntu instructions are incorrect.  They tell you to install Grub to sda3.  the "bug" in the installer appears to create a separate partition for Grub rather than installing it on the linux partition itself.  So it installs grub on a 917kb partition with no format.  Hence the error from GPT.  

I booted into my livecd, deleted sda3(917Kb grub partition), got into my ubuntu installation, reinstalled grub, ran the partition manager from refit, and now it works fine. 

I am going to reinstall again, and tell it to load GRUB on sda4 and see what happens.

Edit- going to try reinstalling again if doing system updates causes a GRUB loop again, otherwise, I'm not going to fix whats not broken.

---

### Post by helpnewb on 2010-06-20
Hey everyone,

I'm new to this sort of stuff, but umm I got everything working, all the steps work except that i cant save gptsync.deb in the /mnt/root folder.

It says I don't have permission to do so. Anyone know what to do?

---

### Post by helpnewb on 2010-06-20
bump?

somebody? all i need help with is getting permissions to change one file!

---

### Post by linuxopjemac on 2010-06-21
use sudo

---

### Post by dfacto on 2011-09-13
I had what I believe is a similar problem after installing Oneiric (alpha and beta).  I was seeing the gptsync error (in refit):
Error: Not Found returned from gptsync.efi

I was able to fix it quite easily using gptsync.  [Here]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185") are the steps I took to fix it and [here]("http://ubuntuforums.org/showpost.php?p=11215380&postcount=186") is a dump of my old tables and the new hybrid MBR.

---

