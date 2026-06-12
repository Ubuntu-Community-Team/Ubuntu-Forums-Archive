---
title: "GRUB error on boot"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by linuxnaab on 2008-03-21
I installed linux a few weeks back after various problems involving the video card,  and in the end couldn't get Ubuntu to recognise my NVIDIA 8800GT, hence I decided to delete the partition using a program called "Partition Magic".  All went well until I rebooted my computer a few days later to be met by an error message involving GRUB,  think the ID was 22?  

More to the point.  I searched for a solution after booting from the Ubuntu liveCD which has been a lifesaver, as I wouldnt be here without it.  The one that seems to fix it all is booting from the Windows XP disc, which I do not have, as I haven't needed it for such a long time, it has gone a walk somewhere (I spent long enough looking for and testing discs).  So with that out of possibility, I thought about burning a new one, then remember I've only got one drive to burn in.

Next I tried Gpartition/Gparted, can't remember the name.  I unmounted my HDD in order for the resize option to become available.  When I tried to resize it, I got a basic error, that it could not complete the operation, not sure what the error number was, but I googled for a solution, and it said about defragging.  As a complete linux noob I don't know how to defrag with Linux, so if it might work, fill me in on how to.  When i retried to resize the partition AFTER the first attempt,  I only had the option of making it several mb's smaller, and I mean tiny tiny several, leaving nowhere enough for a new ubuntu install, which I hoped would let me repair GRUB.

Next I tried a GRUB repair that can boot from USB called "[Supergrub](http://supergrub.forjamari.linex.org/?section=download#usb)",  I followed some [instructions](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Super_Grub_USB_Disk) I found elsewhere but changed them to;

sudo grub
grub>device (hd1) /dev/sdb1
grub>root (hd1,0)

Then this error appears - "Error 18: Selected cylinder exceeds maximum supported by BIOS"

[B]
I'm totally unfamiliar with linux and I can't obtain a windows XP disc for over a week because of the holiday period, and not seeing people who could lend me one.  I need a way of fixing GRUB from inside the Ubuntu liveCD, or booting from a USB, or reinstalling Ubuntu if I can get the partion program to work.  If you're going to help it must be real real beginner precision instructions, nothing over complicatedly vague. :popcorn:

I'll provide further information where necessary.[/B]

Thanks

---

### Post by Bachstelze on 2008-03-21
Hmm, a Windows system and no Windows CD, huh?

Anyway, what exactly do you want to do?

---

### Post by pytheas22 on 2008-03-21
First, try using testdisk, which can search for and clean up some partition errors:
```

sudo apt-get install gpart
```

Once it's installed, just type "gpart" in a terminal to run it.  The interface is pretty intuitive; just tell it to test your hard disk and see what it says.  If it finds errors it will give you an option to correct them, and you may be able to make your system bootable again that way.

If this doesn't help you, the simplest option might be to just reinstall Ubuntu.  The disk partitioner within the installer should be able to straighten things out, especially if you select the option involving wiping the whole hard disk (but don't do this if you want to keep Windows installed, obviously).

I wrote the above instructions under the assumption that your end-goal is to get a working Ubuntu system.  I am not entirely clear what you want, however; if you're trying to get your Windows partition working again and don't care about Ubuntu, let me know and I'll do my best to help you do that, although depending on what's wrong, it may not be possible to fix without a Windows install CD.  Either way, the two steps above should help you arrive at the end you want (reinstalling Ubuntu should also make Windows bootable because it will fix grub).

---

### Post by linuxnaab on 2008-03-21
> **HymnToLife said:**
> Anyway, what exactly do you want to do?

To repair or get rid of GRUB in order to be able to boot Windows, which the first error prevents me from doing, as it displays on the screen after starting the computer.  Without formatting windows of course,  that's a last resort.  I will keep Ubuntu installed next time, now that I've got a better feel of using it because of this problem.  I have to do this without burning any new CD's, as I need the drive for the Ubuntu liveCD, which I'm forced to use right now.

pytheas22;
I have one partition on my single HDD, which I have to unmount to make the resize option appear for the windows partition, which takes up the whole disk (except for 8mb for some weird reason), it's during the resizing (using gpartition) that I get the error, that the operation cannot be completed.  I need to resize it, in order to create a new partition for linux.  I'll get the exact error message as soon as I can, takes quite some time to even start gpartition from disc, which tends to crash alot.

EDIT:  Ok, I tried the gpartition program, and unmounted the partition to make it resizeable, and a little warning flag appears, giving this message(This didnt appear the first time);
[[IMG]http://img341.imageshack.us/img341/1328/screenshot5qs9.th.png[/IMG]](http://img341.imageshack.us/my.php?image=screenshot5qs9.png)

Then when I try to resize it (This was completely normal, the first time I tried to resize the partition, before the error that the operation couldn't be completed);
[[IMG]http://img211.imageshack.us/img211/7167/screenshot4um1.th.png[/IMG]](http://img211.imageshack.us/my.php?image=screenshot4um1.png)

I also get an error while trying the check function, that it can't be completed, much like the resize.

---

### Post by pytheas22 on 2008-03-21
sorry, I told you to install the wrong program--although this information from gparted (which is not gpart anyway, but that's incidental now) is useful.  Install testdisk with

```
sudo apt-get install testdisk
```

and then run it with "sudo testdisk" (the sudo is important).  This will test your disk and try to fix errors.

Anyway, it looks like your NTFS partition is corrupted...that's what all those complaints about "Cluster xxxx is referenced multiple times!" mean.  Did anything weird happen in Windows lately (like crashing to the BSOD)?  Unfortunately, since NTFS is closed-source, Linux can't fix its problems; the only way to repair it is with chkdsk inside Windows.

Try running testdisk now and see what it says.  Depending on where exactly the corruption lies with the NTFS partition, testdisk might be able to repair it.  If Windows corrupted the NTFS filesystem itself, you're out of luck without a Windows boot CD, as far as I know; if for some reason the partition table is damaged, testdisk will be able to fix it.

---

### Post by linuxnaab on 2008-03-21
> **pytheas22 said:**
> 
```
sudo apt-get install testdisk
```


ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

My username says it all. :(
Sorry.

---

### Post by pytheas22 on 2008-03-21
That's strange...are you using Gutsy?  I thought that the universe repository was enabled by default on it.

Anyway, the simplest solution is to download the package manually from [http://packages.ubuntu.com/gutsy/testdisk](http://packages.ubuntu.com/gutsy/testdisk) (scroll towards the bottom for the actual download).  Once you download it, just double click to install.

---

### Post by keeler1 on 2008-03-21
I recently had to reinstall 7.10 because some dell system diagnostics killed my linux drive.  Anyways I didnt have internet during the installation so every deb line in "/etc/apt/sources.list" was commented out because it couldnt find the repositories during installation.  That could be a reason for the universe repository not being enabled.

---

### Post by linuxnaab on 2008-03-21
> **pytheas22 said:**
> That's strange...are you using Gutsy?  I thought that the universe repository was enabled by default on it.

Anyway, the simplest solution is to download the package manually from [http://packages.ubuntu.com/gutsy/testdisk](http://packages.ubuntu.com/gutsy/testdisk) (scroll towards the bottom for the actual download).  Once you download it, just double click to install.

I'm using Gutsy, yes.  I did what you asked but cant seem to find it in the menus to the top left, and as a noob I've no idea where to launch the application at.  There doesn't seem to be any hints either.

---

### Post by pytheas22 on 2008-03-21
If you are using a 32-bit kernel (most likely), click [http://ubuntu.cs.utah.edu/ubuntu/pool/universe/t/testdisk/testdisk_6.6-1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/universe/t/testdisk/testdisk_6.6-1_i386.deb) and select "Open with gedebi installer."

If you have a 64-bit kernel, click [http://ubuntu.secs.oakland.edu/pool/universe/t/testdisk/testdisk_6.6-1_amd64.deb](http://ubuntu.secs.oakland.edu/pool/universe/t/testdisk/testdisk_6.6-1_amd64.deb) and do the same thing.

If it still doesn't work, click on the System menu, go to Administration, and select Synaptic Package Manager.  In Synaptic, click on the Settings menu, and go to Repositories.  In the Repositories dialogue box, make sure that all of the options under the "Ubuntu Software" tab are checked on.  Then close the dialogue box and the click the Reload button in the upper-left corner of the main Synaptic window.  This will make sure that all of the repositories are enabled and that testdisk is available (this could be done more quickly via the command-line, but I don't know how).

---

### Post by linuxnaab on 2008-03-21
> **pytheas22 said:**
> If you are using a 32-bit kernel (most likely), click [http://ubuntu.cs.utah.edu/ubuntu/pool/universe/t/testdisk/testdisk_6.6-1_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/universe/t/testdisk/testdisk_6.6-1_i386.deb) and select "Open with gedebi installer."

If you have a 64-bit kernel, click [http://ubuntu.secs.oakland.edu/pool/universe/t/testdisk/testdisk_6.6-1_amd64.deb](http://ubuntu.secs.oakland.edu/pool/universe/t/testdisk/testdisk_6.6-1_amd64.deb) and do the same thing.

If it still doesn't work, click on the System menu, go to Administration, and select Synaptic Package Manager.  In Synaptic, click on the Settings menu, and go to Repositories.  In the Repositories dialogue box, make sure that all of the options under the "Ubuntu Software" tab are checked on.  Then close the dialogue box and the click the Reload button in the upper-left corner of the main Synaptic window.  This will make sure that all of the repositories are enabled and that testdisk is available (this could be done more quickly via the command-line, but I don't know how).

Testdisk did the trick!!

I will be eternally grateful, but I'm so excited now after 12 hours of torture, that I have to fire up media player and waste time.

[B]For anyone with the same problem;
[LIST=1]
[*]Install Testdisk
[*]Type "Sudo testdisk" in terminal
[*]Select the option to repair your "MBR", it's in there somewhere, and shouldn't be hard to find
[/LIST][/B]

Again many thanks, for you persistence in helping me.

---

### Post by pytheas22 on 2008-03-21
glad it worked, and I hope you keep playing with Ubuntu even though you have Windows again...I think you will find that if you invest the time to learn the basics of Ubuntu, you'll like it a lot better.

---

### Post by linuxnaab on 2008-03-21
> **pytheas22 said:**
> glad it worked, and I hope you keep playing with Ubuntu even though you have Windows again...I think you will find that if you invest the time to learn the basics of Ubuntu, you'll like it a lot better.

I plan to reinstall it fully again once I get the consistency problem that has arisen with my HDD saolved.  Keep getting this weird problem, where it deletes the same file over and over during the checking/fixing,  it's not a problem for here, so I'll keep it that way and use google for the answer. :)

---

