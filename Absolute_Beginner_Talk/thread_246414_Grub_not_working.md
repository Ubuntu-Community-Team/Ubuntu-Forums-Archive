---
title: "Grub not working??"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Devil's Advocate on 2006-08-29
Complete noobie, so please excuse me.

I downloaded the ISO live and burnt the CD. Computer: P4 3 GHz, 1 Gb RAM, 1 SATA disk 120 Gb used 100% for WinXP Pro SP2. 1 IDE disk 80 Gb with 3 NTFS partitions. I prepared 1 15 Gb Linux3 partition and 1 Linux swap partition 2 Gb.

The Live disk seemed to work OK, so I proceeded with Install. The first time, everything went OK up to the reboot window, where it hung the computer - power down only option. The second time, it closed OK and the CD drawer opened and I removed the CD. On restarting, it went straight into Windows, no dual-booting choice. During the installation, it did show Grub being installed.

Can a kind soul tell me what went wrong, please?

---

### Post by huygens on 2006-08-29
Hmm, I do not know what could have cause your problem.
Perhaps, you could look in the Ubuntu documentation [how to restore GRUB]("https://help.ubuntu.com/community/BackupYourSystem#head-19d41d9b1cdc94b71787cd260282b106dff148ee"). They provide a few links to handle this situation.

Huygens

---

### Post by NESFreak on 2006-08-29
In some OEM PCs the bios his 'virus scan' is enabeled. As far as i know the only thing it does is preventing users to write to the MBR. In moast casses when trying to write to the mbr with this option enabled the system should pause and show you some sort of virus allert.

Check if this is enabled for you,
NESFreak

---

### Post by whizbaby on 2006-08-29
> **huygens said:**
> Hmm, I do not know what could have cause your problem.
Perhaps, you could look in the Ubuntu documentation [how to restore GRUB]("https://help.ubuntu.com/community/BackupYourSystem#head-19d41d9b1cdc94b71787cd260282b106dff148ee"). They provide a few links to handle this situation.

Huygens

I also think that the system crashed (why?) before grub was installed and should be restored. On the above link follow the instructions and keep in mind that your drive will not be /dev/hdaX but /dev/sdaX if you have your linux on your SATA drive(otherwise hda). Try (in rescue mode)

sudo cfdisk /dev/sda (resp.hda)

to determine easily which 'X' it is.
good luck!

---

### Post by Devil's Advocate on 2006-08-31
Thanks for your help. I have tried everything I can think of but I simply cannot get dualbooting to work. I can boot only into Windows.

According to the links you guys gave me, I landed up at HOWTO: Restore GRUB

I first tried the command line suggestion by remmelt:
1-3 OK
4 "Type "root (hd0,6)..."
It tells me the partition isn't mounted: if I try to mount it, it says it's inaccessible.

I then tried the first one by vnbuddy2002
1-5 OK
When I try 6, I'm informed that I must format /, /boot, swap and /usr and there is no way to override this, despite 5. saying DO NOT FORMAT THEM

Of course, they have been formatted umpteen times, at each try to install things.

Then wernst's suggestions are the same as the first one I tried.
I do not have any other Boot Manager on my system.

At the end, there is a post by Rikko (message #10) that may (or may not) be relevant. I am using an IDE disk (/hda) for all the Ubuntu partitions, but the main disk with Windows C: is a SATA one (/sda). 

Am afraid, I'm reaching the end of my tether on this one. It seems I cannot use Ubuntu, short of someone producing a miracle answer, I hope. Please! Pretty please!:confused: :confused:

---

### Post by whizbaby on 2006-08-31
start from live-cd, open terminal.

sudo mount --bind /dev /WhereUbuntuHDisMounted/dev
sudo mount --bind /proc /WhereUbuntuHDisMounted/proc

sudo chroot /WhereUbuntuHDisMounted

sudo grubinstall

sudo reboot

---

### Post by Devil's Advocate on 2006-08-31
Thanks, but sorry, does not work. Tried it 3 times to make sure there was no case or spelling error, with following results:

> **whizbaby said:**
> start from live-cd, open terminal.

sudo mount --bind /dev /WhereUbuntuHDisMounted/dev
[COLOR="Red"]Mount point for /WhereUbuntuHDisMounted/dev does not exist[/COLOR]
sudo mount --bind /proc /WhereUbuntuHDisMounted/proc
[COLOR="Red"]Mount point for /WhereUbuntuHDisMounted/proc does not exist[/COLOR]

sudo chroot /WhereUbuntuHDisMounted
[COLOR="Red"]Cannot change root directory: No such file or directory[/COLOR]

sudo grubinstall
[COLOR="Red"]Command not found[/COLOR]

sudo reboot
[COLOR="DarkGreen"]Works![/COLOR]

Do you have another miracle solution? Thanks

---

### Post by luvr on 2006-08-31
> **Devil's Advocate said:**
> 1 SATA disk 120 Gb used 100% for WinXP Pro SP2. 1 IDE disk 80 Gb with 3 NTFS partitions. I prepared 1 15 Gb Linux3 partition and 1 Linux swap partition 2 Gb.
If I understand you correctly, then your WinXP system is installed on your SATA disk, right?

Perhaps the SATA disk is configured (in BIOS) to be the boot disk; in other words, the system reads the Master Boot Record from the SATA disk. Enter BIOS setup, and check for some kind of setting that talks about *"Boot Sequence"* or some such; you should be able to find which is the harddisk that will boot your system.

Now, if it's the SATA disk, then chances are, that Ubuntu will have written its (GRUB) Boot Loader Code to the *other* disk (I'm not entirely sure, though, since I have never actually tested this). If so, then change your boot sequence, so that your IDE disk becomes the boot disk instead of your SATA disk.

Or, depending on your BIOS, you may even be able to select your boot disk during startup - look for a message about hitting a specific function key to select the boot disk. That would allow you to test the boot sequence without having to save the new settings first.

---

### Post by whizbaby on 2006-08-31
Replace /WhereUbuntuHDisMounted by where ubuntu hd is actually mounted, this may be something similar to
/mnt/hdaX (where X is a number)
/mnt/sdaX (where X is a number)

if not shure type
mount
or 
less /etc/fstab
to determine

Then the miracle should occur

---

### Post by Devil's Advocate on 2006-08-31
> **luvr said:**
> If I understand you correctly, then your WinXP system is installed on your SATA disk, right?

Perhaps the SATA disk is configured (in BIOS) to be the boot disk; in other words, the system reads the Master Boot Record from the SATA disk. Enter BIOS setup, and check for some kind of setting that talks about *"Boot Sequence"* or some such; you should be able to find which is the harddisk that will boot your system.

Now, if it's the SATA disk, then chances are, that Ubuntu will have written its (GRUB) Boot Loader Code to the *other* disk (I'm not entirely sure, though, since I have never actually tested this). If so, then change your boot sequence, so that your IDE disk becomes the boot disk instead of your SATA disk.

Or, depending on your BIOS, you may even be able to select your boot disk during startup - look for a message about hitting a specific function key to select the boot disk. That would allow you to test the boot sequence without having to save the new settings first.

Thanks for the idea. The BIOS is not Award or any of the usual ones, but an Intel one. There are 3 possibilities for the booting: DVD-drive, SATA disk and floppy. I could see no way to change it from the SATA to the IDE, but, still in the Boot tab, both disks are listed, but not in the boot sequence.

I don't want to mess around with the SATA drive, as it has >100 Gb of data on it. If I can't boot Ubuntu for the reason you mention, then I'd be better to abandon it.

---

### Post by whizbaby on 2006-08-31
I'm not sure if this is the case. Grub is able to determine which hd is chosen by the bios and then installs into it's MBR. Please try what I said whith the correct pathnames to be certain that grub doesn't work. (I believe it does!! Never heard of having to change your bootsequence to be able to run linux)

---

### Post by Devil's Advocate on 2006-08-31
OK, sorry, I forgot to report this.

On SDA, it shows only the NTFS partitions, the C: partition being bootable

HDA is a bit of a mess, as the different trials have produced 5 LinxExt3 partitions and 2 Linux/Solaris Swap partitions. hda3 does have the boot flag set.

---

### Post by whizbaby on 2006-08-31
Here are my assumptions about your setup:
sda - only the dozer lurks there
hda - a conglomerate of partitions with ubuntu installed on EACH?

chose one ubuntu is installed to, lets say hda3 (I can't know), then do 

start from live-cd, open terminal.
verify where /dev/hda3 is mounted by typing

mount
this will reveal a mount point in the filesystem, lets assume it is /mnt/hda3

#ONLY if it isn't mounted at all do
#
#sudo mkdir /mnt/hda3
#sudo mount -t ext3 /dev/hda3 /mnt/hda3

then do

sudo mount --bind /dev /mnt/hda3/dev
sudo mount --bind /proc /mnt/hda3/proc

sudo chroot /mnt/hda3

sudo grubinstall

sudo reboot

where '/mnt/hda3' has to be replaced by the correct mount point and 'hda3' with the desired device.(sorry to confuse you with my not-copy-and-paste-safe posting)

---

### Post by whizbaby on 2006-08-31
> **whizbaby said:**
> 

#sudo mount -t ext3 /dev/hda3 /mnt/hda3


Hope you noticed I changed ext to ext3 (*%!§ typing errors!)
in line
sudo mkdir /mnt/hda3  
you are creating a directory which you want connected to a hardware device.
From the moment they are connected the directory is called the 'mount point' of the device. You could have called it '/sausage' and mount your hd on that but '/mnt/hda3' is a little more descriptive.

---

### Post by luvr on 2006-08-31
> **Devil's Advocate said:**
> If I can't boot Ubuntu for the reason you mention, then I'd be better to abandon it.
I'm pretty sure that you **can** get it to boot Ubuntu; it's really just a matter of setting up GRUB onto its Master Boot Record. Assuming that you have a way to boot Ubuntu (you probably have, since you can use the CD), you should be able to install GRUB where you need it.

However, whenever I attempt to install GRUB via Ubuntu, something bad appears to happen, and my harddisk becomes unbootable. Incidentally, during the Ubuntu install, it will complain about some kind of error in my GRUB partition (which I created via Slackware), even though I'm pretty sure there aren't any errors at all (and, after install, Ubuntu can access the partition perfectly fine); I even reformatted the partition in Ubuntu, and reinstalled, but the complaint keeps appearing. I will reinstall Slackware, and refresh my GRUB partition from there, then see what happens when I subsequently reinstall Ubuntu (next to the Slackware installation). Until I get a clearer picture of this issue, I'm a little hesitant to suggest manually installing GRUB, from Ubuntu, over a *working* Master Boot Record.

By the way, I have just discovered that the Ubuntu **Alternate** install disc allows you to select the location where the GRUB boot loader will get installed; that will allow you to install the boot loader onto your SATA disk, and boot Ubuntu from it.

---

### Post by luvr on 2006-09-01
> **whizbaby said:**
> Grub is able to determine which hd is chosen by the bios and then installs into it's MBR.
Yes, you're absolutely right, and it's what I would expect to happen.

However, the original poster **did** say that his computer keeps booting straight into Windows, without showing the GRUB boot menu first. That does suggest that GRUB did *not* get installed on the Master Boot Record of his boot disk.

Now, whether GRUB simply did not get installed at all (which could be the case, since apparently an error occurred during the install), or whether it did get installed, albeit onto the wrong disk, is not clear to me at this point. You would have to take a look at the contents of the Master Boot Record of the IDE disk in order to make sure; you could copy the MBR into a file (using, e.g., the **dd** data dump command), and check if it corresponds to the GRUB *stage1* loader, if you really wanted to do that.

---

### Post by whizbaby on 2006-09-01
> **luvr said:**
> 
However, the original poster **did** say that his computer keeps booting straight into Windows, without showing the GRUB boot menu first. That does suggest that GRUB did *not* get installed on the Master Boot Record of his boot disk.

That's why I suggested the steps above, to make sure that grub is installed correctly. (I don't think it has)
If it's still broken then there's the possibility to actually tell grub where to install with a command line tool (**grub-install**  **/dev/sda**, yes, now with a '-' in it, or just **grub-install** and then follow a special syntax)

---

### Post by Devil's Advocate on 2006-09-03
Thanks to everyone for their help. I give up!

1. I worked through the various suggestions. Whizbaby's seemed promising at first, as hda3 was not mounted. I followed everything through to the line
sudo chroot /mnt/hda3 
Up to here, everything was going swimmingly. Then came
sudo grubinstall (I also tried it with a hyphen!)
This elicited
sudo: unable to lookup ubuntu vis gethostbyname()
Merde alors!

Then I had the brilliant (?) idea to try and install it on a different computer, something I had avoided because this one has no Internet connection. This one is different from the first one in every way imaginable, CPU maker, chipset, motherboard, RAM type and it has only one HDD. I cleared a suitable amount of space on the HDD and confidently put in the CD. No problem, the live screen sprung to life and I played a game to show it was working. I double-clicked on Install. It crashed on screen 5/6 (you know, the Manual partitioning one). Second try, it got to the same place and I clicked Forward. It started churning away, but I couldn't see what was happening because screen 5/6 remained obstinately there and it possibly was obscuring the installation "thermometers". Anyway, after some minutes, the CD drive opened and I pressed enter and the thing rebooted - ***[SIZE="4"][COLOR="Red"]into Windows![/COLOR][/SIZE]***:mad: :frown: 

Deux fois, merde alors!

Now, thinks I, why hasn't Grub installed itself, when there is no way it could do so on the wrong HDD, because there was only one. I rechecked the CD on this computer and was informed there were no checksum errors and the iso file, from which I burnt it, was the right size.

Refusing to be beaten, I downloaded the alternate iso file and burnt it to a CD. Ah, sez me, now I can install it without a gigabyte of RAM being stolen. Great, everything proceeds as I would expect; that is until it had installed some of the apps. :(  Then the screen suddenly became black with two white rectangles on it. This appeared immediately after xserver.org was being copied or installed. As the hard disk and CD drive kept churning away, I thought, "Ah, it's wondering what graphics system drivers are needed and will revert to normal after a few seconds." Don't you believe it, it didn't. It stayed that way for perhaps 6 or 7 minutes, when all the activity stopped. I left it another minute or so of total inactivity. The CD drive wouldn't open, of course, and nothing I could do to the keyboard or mouse had any effect. Locked solid. OK, maybe it has finished a correct installation???
No way! A hard reboot, adroitly removing the CD ASAP, and what happens? Yes you've guessed it, it booted ***[SIZE="4"][COLOR="Red"]into Windows![/COLOR][/SIZE]***:mad: :frown: ](*,) ](*,) ](*,) 

Sorry, I've wasted an estimated 12 hours trying unsuccessfully to install it on two 'puters. Time to cut one's losses. [COLOR="Red"][SIZE="7"]Bye-bye, Ubuntu![/SIZE][/COLOR]

---

### Post by whizbaby on 2006-09-03
J'peut bien comprendre que la moutarde te monte au nez, mais ce qui t'es arrives n'est pas normal du tout (en plus sur deux ordinateurs rogntudju).

As far as I can see you didn't have a working install-cd so please don't judge the whole system. There seems to be an issue with getting the iso burned right (many people are complaining about a similar problem and I had to burn four cd's 'till it was working. My working cd didn't work on a friend's computer)

---

### Post by Brendt2 on 2006-09-03
> **Devil's Advocate said:**
> Then the screen suddenly became black with two white rectangles on it. This appeared immediately after xserver.org was being copied or installed.

This happened to me on one of the pc's that I was trying to install to... after i couldn't get it to work I just poped it into another computer.  No Problems...

If there is ever a easy solution to this problem I will go back and put it on the one that failed...

---

### Post by Devil's Advocate on 2006-09-03
> **whizbaby said:**
> J'peut bien comprendre que la moutarde te monte au nez, mais ce qui t'es arrives n'est pas normal du tout (en plus sur deux ordinateurs rogntudju).

As far as I can see you didn't have a working install-cd so please don't judge the whole system. There seems to be an issue with getting the iso burned right (many people are complaining about a similar problem and I had to burn four cd's 'till it was working. My working cd didn't work on a friend's computer)C'est plus que la moutarde, mais de l'acide chlorhydrique :twisted: 

I'm prepared to believe that burning an ISO file can be problematic, but why does the checksum checker not detect the problem? On the live CD, I used a different app from the non-graphics one to do the conversion and I slowed the burn, as high speeds can cause problems (I should mention that I burn ISO files on an almost daily basis, as I work on video stuff and ISO files are a convenient way of storing DVD layouts; never had a problem.)

Toutefois, I did order a CD a coupla weeks ago and I may give it a brief try when it arrives but, if I have the same problem(s), I won't waste any more time.

---

### Post by Devil's Advocate on 2006-09-10
OK, mission not accomplished.

I received the pressed CD-ROM yesterday (faster than anticipated!)

Identical results on both computers. Installation impossible. So it's nothing to do with the ISO image file or its burning.

I've always said that Linux can never become mainstream until it works "straight from the box". From what I've heard on the grapevine about Ubuntu, I had high hopes that this was it. I'm very disappointed and put down all the time wasted to experience.

I would point out that the hardware it won't work on is not, in any way, extraordinary. The main one is a P4 Prescott 3 GHz, 1 Gb SDRAM with 800 MHz FSB with an Intel m/b/chipset. The only non-Intel card in it is an extra Ethernet (incidentally, both networks were detected with the Alternate non-installation), sound, graphics and 1st Ethernet are all on-board. The other one is an AMD 1600 MHz, 512 Mb RAM, Via chipset, all functions except Ethernet on board.

Anyway, that's it. Fini, terminé, fertig, schluss! Sorry!

---

### Post by whizbaby on 2006-09-10
Out of 100 PCs I've personally experienced only one machine I couldn't by any means install it (just like you!). This machine was *hardware-identical* to 19 other's the ubuntu cd installed without a problem. Donc c'est le gros lot ...

---

### Post by Devil's Advocate on 2006-09-11
Intéressant ! Do I get double prize for not being able to install on 2/2 computers?

---

