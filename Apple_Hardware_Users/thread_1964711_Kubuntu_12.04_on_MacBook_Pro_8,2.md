---
title: "Kubuntu 12.04 on MacBook Pro 8,2"
date: 2012-04-24
forum: Apple Hardware Users
---

### Post by the8thstar on 2012-04-24
Hello all,

I'm a regular Kubuntu 12.04 user (in VirtualBox with OS X).

I am quite satisfied to have overall seamless integration of my bluetooth keyboard and trackpad. I also extensively rely on shared folders b/w OS X and Kubuntu and I don't have to worry about partitions formats anymore (i.e. HFS+ on one side and ext4 on the other).

However, this is only a virtual machine after all. 

So here are my questions to the board :

[COLOR="Blue"][LIST=1]
[*]Would Kubuntu run much better on its own native partition than in a virtual machine ?
[*]Has anyone got any experience with installing/troubleshooting Kubuntu 12.04 on a MacBook Pro 8,2 ? 
[*]Is it really worth it after all ?
[/LIST][/COLOR]

Thanks for your feedback !

---

### Post by ph4nt0m117 on 2012-04-24
> **the8thstar said:**
> Hello all,

I'm a regular Kubuntu 12.04 user (in VirtualBox with OS X).

I am quite satisfied to have overall seamless integration of my bluetooth keyboard and trackpad. I also extensively rely on shared folders b/w OS X and Kubuntu and I don't have to worry about partitions formats anymore (i.e. HFS+ on one side and ext4 on the other).

However, this is only a virtual machine after all. 

So here are my questions to the board :

[COLOR="Blue"][LIST=1]
[*]Would Kubuntu run much better on its own native partition than in a virtual machine ?
[*]Has anyone got any experience with installing/troubleshooting Kubuntu 12.04 on a MacBook Pro 8,2 ? 
[*]Is it really worth it after all ?
[/LIST][/COLOR]

Thanks for your feedback !

Question to you is why use Kubuntu when OSX is already there?  OSX and Linux are practically the same thing and with a little work you can make apps interchangeable.

In any case ANYTHING in it's own partition runs better outside of a VBox.

I haven't had any experience, but then again I despise Macbooks for the unibody case and the pull-out-battery=reset-trololololol problem.
Why?

It may be worth it EVENTUALLY, but linux is a project OS in and of itself.  K only makes it so simple that a monkey could use it.  (No offense)  It may be worth it, and it may not.  I personally don't like KDE for its dependency on you will have all the software on a CD, but then again as you said you are a normal user.

If you're used to K and not OSX, then ok, use it.  If you luike the factor of running KDE and OSX all at once so you can instantly flip in between instead of rebooting, then use a VBox.  To be honest this is more down to your opinion of what you like to use.

---

### Post by the8thstar on 2012-04-24
> **ph4nt0m117 said:**
> Question to you is why use Kubuntu when OSX is already there?  

Because I'd like to say that I can, of course! I don't need people's opinions to make my own about the worth of the experience. All I meant when I said is it worth it was to know if there is a significant difference (effects, speed, etc...) b/w native and virtual machine when it's Kubuntu running.

For the record, I have already ran Windows on its own partition thanks to Bootcamp. It didn't bring me much more than it did in the VM, except maybe to play a couple of old games that needed directX. So I switched back to the VM version, which is going to stay as it is.

From what I read, Ubuntu seems to be complicated to install and run correctly on Apple computers. I'd like to know if my efforts would be worth the try or not.

Last but not least, I am a normal user, but I do sense differences b/w Linux and Unix beyond the technicalities, in the way corporations deal with them.

---

### Post by canhoto on 2012-04-24
I have a Linux distro (the portuguese Caixa Mágica) very much based on Ubuntu running on its own partition (via BootCamp) in my Macbook 2,1. It works perfectly (the only thing I couldn't fix - but I didn't try very much - was the use of the iSight). It's quite fast (it's not KDE, but Gnome 3 - with Gnome Shell).

I never tried it with a virtual machine, but it would probably be slower, since it's always two OS's running at the same time on the same computer. Unlike with a dedicated partition.

I think you don't loose anything if you try it (if you have enough disk space, of course).

It's a different approach, Apple's on one side, all the Linux's on the other. Mac OS is (almost) perfect. But I really feel that Apple is the owner of my computer, not me. Unlike with Ubuntu (which I use in my Power Mac) or Caixa Mágica (and probably any Linux distro). 

So, actually, installing Kubuntu like a real OS doesn't bring more life quality. You can do everything with Mac OS. But you feel more free. And Apple deserves it.

---

### Post by the8thstar on 2012-04-29
Well, I've tried many different tutorials out there and I'm sad to report that nothing worked.

So, for the time being, Kubuntu 12.04 LTS cannot be installed on a MacBook Pro 8,2.

Back to the virtual machine... :-(

---

### Post by mode7 on 2012-04-29
I have Kubuntu installed on my Macbook Pro 8,1. Very similar, with exception to gfx cards, I believe.
I will go over what I do to get mine working with 12.04 (Easier than 11.10)

Things that will not work right off the bat:

1. Booting into Kubuntu from Refit. Easily fixed using gdisk whilst in OSX.
2. Wireless. Can be fixed easily.
3. HFS+ readability. I do not know why Dolphin cannot open my Macintosh HD partition, while it can be opened just fine under Ubuntu. It says "Filesystem not recognized". Obviously, there is something in Gnome giving it the ability to read HFS+ filesystems. hfsutils did not work for me. I'll figure out what to do..

Okay.. here we go:

**1: **Setup Refit. I can't remember exactly how I did this, but I believe I just used a dmg with an automatic installer from the [Refit site]("http://refit.sourceforge.net/doc/c1s1_install.html").
Next, use Disk Utility to create a partition at the end of your hard drive with enough space for Ubuntu and a swap partition. I think I gave mine only 30 GB.

**2: **Download and burn the Kubuntu 12.04 ISO to a disk. [s]Next, use Unetbootin to burn the image onto a spare flash drive.[/s]

**3: **Edit: I tested this, and it seems you can now boot normally from the disc in 12.04. [s]From now on, to boot Kubuntu live, insert the pen drive AND the disc. When your Macbook is starting up, press C to boot from the disk. Select to start Kubuntu. The computer will attempt to search for the live filesystem from the disc, fail for some reason, then search the pendrive and succeed. I do not know why this occurs, but the pendrive+cd combo works for me.[/s]

**4: **In the live Kubuntu session, use a partition editor to delete that last partition you made, then make an ext4 partition and a swap in that order. The sizes are up to you. 
(Note: you only need to do this once. Once the partitions are setup, you no longer have to touch Refit or a partition editor when reinstalling *buntu.)

**5: **Now to install Kubuntu... Start up the installer and install Kubuntu to your ext4 partition. Format and set the mount point to root. IMPORTANT: Set GRUB installation to your Kubuntu partition! Most likely dev/sda3.

**6: **When this is done, you must boot into OS X and make Kubuntu bootable using Gdisk. Basically, follow the instructions [here]("http://ubuntuforums.org/showpost.php?p=11215214&postcount=185"). Read the instructions CAREFULLY.
If you don't do this, you will only get a "Missing operating system" error (Or something like that), when selecting Linux in the Refit menu.

**7: **After that, Kubuntu should boot successfully! You'll notice quickly that wifi does not work, though. I used a usb dongle for this. You could use that or ethernet. (Or manually transfer the packages..)

**8: **Add these repos: "ppa:mactel-support/ppa" and "ppa:mpodroid/mactel".

**9: **Install the macfanctld package if you don't want your Macbook to catch fire.

**10: **Next, to get wireless working, install the firmware-b43-installer package. Use your favorite text editor (Or nano like me) as root, and edit/create the file etc/pm/config.d/modules. Add the line "SUSPEND_MODULES="b43 bcma" and reboot. Wireless should now work. A LOT easier than it used to be.

**11: **For the touchpad, you probably want to go to settings, and disable the single tap that causes left mouse click. 

**12: **If you see a red light coming out the headphone jack, you have to mute the SPDIF line. For me, "amixer set IEC958 mute" does the trick. 

This seems like a lot.. and frankly, it is. You definitely get used to it. I've installed multiple copies of Ubuntu on here, and I'm quite used to it. I hope one day this really changes for the better.
Wow, what a post.. I hope that helps somebody out somewhat. I apologize if I missed something or messed something up..

---

### Post by the8thstar on 2012-04-30
Thanks a lot for your tutorial **mode7** ! I will try it later today and report here how it went.

---

### Post by the8thstar on 2012-04-30
Unfortunately, it didn't work. The partition was created but the installer hung from there. I tried several variants (Ubuntu Mac 64bit, Kubuntu Mac 64bit, Ubuntu 64bit...)

No go. I even tried to erase recreate the partition with partition manager and it wouldn't let me !

I guess my computer has locked down the partitions, one way or the other. The only way I reverted back to one partition was to use disk utility in Mac OS X.

Too bad. I guess I'm REALLY stuck with my virtual machine.

---

### Post by sicvolo on 2012-04-30
I can happily report that I DID get Kubuntu 12.04 running on my MacBook Pro 8,2 and are quite happy with it. 
I just followed the Oneric guide - [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric)
Make sure to read the post referenced early on in the guide.

I am now working on switching from the power hungry ATI to the embedded Intel GFX.

---

### Post by sicvolo on 2012-04-30
I remembered, there was a trick to get it done. I had to install Kubuntu from a CD, but then boot with the Kubuntu 12.04 USB stick plugged in for Grub to work after the install, then update grub after booting. 
I've stumbled on this fix myself but then found it referenced somewhere on the web. Here is my crude list of steps:

0. Use MAC's partition editor to reduce existing partition and leave a bunch of empty space. Install gdisk and make a backup: 'sudo disk /dev/disk0'. enter 'b', and type a file name, it will be saved to the home folder
1. get Kubuntu amd64 MAC variant from the list of alternative downloads, burn to a cd and make a USB stick (I used another ubuntu install for the that)
2. get and manually install refi
3. reboot and install Kubuntu from the CD
4. do auto partition in the Kubuntu installed to add needed partitions
5. Instruct it to put grub on /dev/sda
6. Reboot - if stuck at an Kubuntu logo get into macos, do the GPT manipulations per [http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210). Here is what it says: "At the moment you now have a screwed up hybrid mbr table (this is because most likely your lion recovery disk uses one of your precious mbr slots). In order to fix this we are going to create a new hybrid mbr table. i have attached screenshots of this process.
 reopen terminal and again type 'sudo gdisk /dev/disk0'. this time enter 'r'. and then 'p'. this will print your partitions. now you need to create your hmbr so type 'h'. it will now ask you for the partitions you wish to enter. referring to the printed partition list, add your lion, windows and linux partitions. (in my case 2 4 5). next it will ask you to place efi partition first, select 'y'. now it will ask you for the mbr hex code for each partition. the codes you want are 'AF' for lion, '07' for windows, and '83' for linux. don't set any of the bootable flags. once finish enter 'w' to write these changes to the disks. You can also enter 'q' if you want to quit without saving changes. reboot and now you should be able to boot into each of your OSes."
6. Reboot. Now it would still not boot and show "no operation system found"
7. Fix the partition table with refit's partition fixed
8. Put the usb key in
9. Boot Kubuntu from the hardrive (NOT the usb). This time it should boot
10. When you are finish booting, login and reinstall grub
 sudo grub-install /dev/sda
11. Enjoy

---

### Post by mode7 on 2012-05-01
Hm.. I am positive that is what I did to partition the disk.
I should note that I did the initial partitioning using Ubuntu 11.10.
Also, I have never used the +mac images. For whatever reason, I could not get it to boot, with just cd, or with cd+pendrive. So I used the standard images. The difference is explained [here.]("http://ubuntuforums.org/archive/index.php/t-1901511.html")

I suppose you should just follow sicvolo's instructions for partitioning. Perhaps my walkthrough is only for a stock 8,1 MBP.

Anyways, I am sorry my instructions didn't work for you! Do follow my notes for post-install, though! =)

---

### Post by the8thstar on 2012-05-17
Eventually I stuck with the virtual machine instead of a real KDE installation. Given the amount of work needed to get it to run properly, I don't think a real installation is worth it. The risk clearly outweighs the benefit.

---

