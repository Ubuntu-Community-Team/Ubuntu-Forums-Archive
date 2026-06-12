---
title: "Really thinking of running Ubuntu instead of XP, couple of questions"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-03-12
Ive heard so much good stuff about Ubuntu and Ive gotten kind of sick of some of the XP stuff and the only things Im running that are really Windows dependable are WoW and Space Empires 5.

So my questions to you is: How well is WoW running in Linux? I as a Ubuntu Wine thread about how to get it working and it seems it will run pretty well? 

I have questions about the following hardware:

Im using a Logitech MX1000 for WoW and Im have special shortcut keys (ctrl+alt+4 for example) for the buttons on it to. My second mouse is a Razer  Copperhead with special macros for the buttons. Im using a External DVD Burner, Writemaster. Im using my two 36GB Raptors in RAID 0 with the built-in Nvidia Forceware RAID controller. Im using the built-in Nvidia Forceware LAN. My soundcard is Creative X-FI Platinum. 

How will this hardware work in Ubuntu?

I also want to know if the Ubuntu install program can rezise my NTFS partitions on the RAID 0 and cant Ubuntu handle NTFS partitions safe these days so I can run games and stuff from the NTFS partitions? I also wonder if there is a program for the Windows Remote Desktop since I have a server running with Windows 2003 Server or is it easier to install some other Remote Desktop program on the server and my computer instead? All stuff I have is on the server, I only have the OS and games on my main computer.

I searched for some of the questions I asked but I felt it was safer to really ask for it since all ppl have different computers and stuff ;) I have been running Linux now and then a few years back but never really much.

---

### Post by xyz on 2007-03-12
Hi and Welcome!
The first thing you could do is to download the Desktop Live CD and boot from your CD-ROM. See how it works without installing it.
Good luck and let us know...
[download link]("http://espelhos.edugraf.ufsc.br/ubuntu-releases/edgy/")

---

### Post by hobs0n on 2007-03-12
Ok, Im doing it now :) Thanx for the welcome btw!

---

### Post by aberry5555 on 2007-03-12
Remote desktop won't work out of the box but a program called UltraVNC should work pretty well, go here to find it:

[http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/)

Also I know you were saying about games but you really have to check what games you want to play and how long you're willing to spend setting them up, as it involves alot of fiddling around per program to get it to work, games more often than not being the hardest things to set up. Also what GFX card are you running as this may affect how easy and how well your games will run.

---

### Post by xyz on 2007-03-12
> **hobs0n said:**
> Ok, Im doing it now :) Thanx for the welcome btw!

No problem!:) 

Sorry if you already know this but you'll need to burn your iso file once downloaded.
I'm assuming you're using Windows at the moment?
[CDBurnerXP Pro]("http://www.cdburnerxp.se/")
or
[ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm")
Don't forget to check the iso's integrity:
[winMd5Sum]("http://www.nullriver.com/index/products/winmd5sum")

---

### Post by Songwind on 2007-03-12
I got WoW running very smoothly under Wine with minimal setup.  The only issue I had was that you have to change your graphics config information in the Config.WTF file rather than with the GUI, but that's not really hard.

Your hardware will probably work fine.  I know the MX1000 will work fine because I do the same myself.  You can map keypresses to mouse buttons in X windows.

The partition resizing on the RAID *should* work, because when you have a separate RAID controller the operating system sees the logical volume as a single physical drive.  I haven't ever done it or known anyone who has, though, so YMMV.

There are remote desktop applications in both Ubuntu (Gnome desktop) and Kubuntu (KDE desktop).  I have used both to connect to my Windows 2000 domain controller and it worked great..

If you're really serious about doing a lot of gaming in Linux you might want to look into a subscription to [Cedega]("http://www.transgaming.com"), a Wine fork that is gaming focused.

---

### Post by hobs0n on 2007-03-12
Im using NERO and I always use "verify data" when I burn OS discs :)

Sorry forgot to say what more specific hardware I got, here it comes:

Gainward 7800GT
AMD San Diego 2.2@2.7GHZ
Epox 9NPA Nforce4
4x512MB Corsair Value PC3200 DDR

---

### Post by 3rdalbum on 2007-03-12
Don't quote me on this, but you can download a program for Ubuntu called Gnome Terminal Server client, that should be able to access Windows' remote desktop. I'm not entirely sure on that however, as I've never tried it between Linux and Windows.

```
sudo apt-get install tsclient
```

---

### Post by maniacmusician on 2007-03-12
> **hobs0n said:**
> Ive heard so much good stuff about Ubuntu and Ive gotten kind of sick of some of the XP stuff and the only things Im running that are really Windows dependable are WoW and Space Empires 5.

So my questions to you is: How well is WoW running in Linux? I as a Ubuntu Wine thread about how to get it working and it seems it will run pretty well? 

I have questions about the following hardware:

Im using a Logitech MX1000 for WoW and Im have special shortcut keys (ctrl+alt+4 for example) for the buttons on it to. My second mouse is a Razer  Copperhead with special macros for the buttons. Im using a External DVD Burner, Writemaster. Im using my two 36GB Raptors in RAID 0 with the built-in Nvidia Forceware RAID controller. Im using the built-in Nvidia Forceware LAN. My soundcard is Creative X-FI Platinum. 

How will this hardware work in Ubuntu?

I also want to know if the Ubuntu install program can rezise my NTFS partitions on the RAID 0 and cant Ubuntu handle NTFS partitions safe these days so I can run games and stuff from the NTFS partitions? I also wonder if there is a program for the Windows Remote Desktop since I have a server running with Windows 2003 Server or is it easier to install some other Remote Desktop program on the server and my computer instead? All stuff I have is on the server, I only have the OS and games on my main computer.

I searched for some of the questions I asked but I felt it was safer to really ask for it since all ppl have different computers and stuff ;) I have been running Linux now and then a few years back but never really much.
WoW runs great under WINE.

For your mouse (mice), you'll probably have to map the keys yourself. I don't know how easy that is, I've never tried.

Ubuntu can handle NTFS paritions fine, but ext3 is still easier. you can't run .exe's like you do in Windows, because Linux uses different methods  of packaging and installation. If I were you, I would copy those games over to your Linux parition then install them using Wine.

For your RAID setup; no idea. Try out the live cd (that's the Desktop CD)

---

### Post by hobs0n on 2007-03-12
> **3rdalbum said:**
> Don't quote me on this, but you can download a program for Ubuntu called Gnome Terminal Server client, that should be able to access Windows' remote desktop. I'm not entirely sure on that however, as I've never tried it between Linux and Windows.

```
sudo apt-get install tsclient
```

Ok, Ill try that when I get it installed :)

BTW, I tried installing it now and it couldnt see the RAID, it only saw the two discs. What can I do to make it see it?

---

### Post by Songwind on 2007-03-12
Did you create the RAID in Windows rather than the RAID controller BIOS or something?

---

### Post by hobs0n on 2007-03-12
> **Songwind said:**
> Did you create the RAID in Windows rather than the RAID controller BIOS or something?

Created in the RAID bios. On a note, Windows doesnt support RAID off the box I so I have to use [Nlite](http://www.nliteos.com/) to add the Nvidia RAID drivers to the ISO of windows. Might have to do the same with Ubuntu?

---

### Post by kakalaky on 2007-03-12
You will have to use dmraid for it to see the raid array, which doesn't work properly (at least for me) unless you use the version from feisty.  The install can be done, but it isn't easy if you are new to linux.  If you wan't to try,  check to see if your raid controller is compatible here:  [http://people.redhat.com/~heinzm/sw/dmraid/readme]("http://people.redhat.com/~heinzm/sw/dmraid/readme") If it is, let me know what Ubuntu release you are using and I can help you get it done.

---

### Post by hobs0n on 2007-03-12
> **kakalaky said:**
> You will have to use dmraid for it to see the raid array, which doesn't work properly (at least for me) unless you use the version from feisty.  The install can be done, but it isn't easy if you are new to linux.  If you wan't to try,  check to see if your raid controller is compatible here:  [http://people.redhat.com/~heinzm/sw/dmraid/readme]("http://people.redhat.com/~heinzm/sw/dmraid/readme") If it is, let me know what Ubuntu release you are using and I can help you get it done.

Ah ok, checked the link and it said NVidia Nforce was supported so my Nforce4 is probably supported then :)

It would be really nice if you could help me getting this dmraid driver thingy to work in Ubuntu :)

---

### Post by Songwind on 2007-03-12
Maybe.  We're out of my depth here.  My RAID experience is on the two extremes - either server level solutions that present the OS with single drive, or software-only.

*continues to watch with unfeigned interest*

Oh, btw, did you read this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by hobs0n on 2007-03-12
Ok hehe no I didnt read that one ;) Seems really easy and pretty usual problem. Ill try booting the CD again and trying to install the DMRAID thingy :)

---

### Post by kakalaky on 2007-03-12
First, download the alternate install cd and get these packages (assuming you are using i386).  You will also need a flash drive (or some kind of removable storage to hold the packages):

dmraid - [http://librarian.launchpad.net/5347776/dmraid_1.0.0.rc13-2ubuntu1_i386.deb]("http://librarian.launchpad.net/5347776/dmraid_1.0.0.rc13-2ubuntu1_i386.deb")

libsepol1 - [http://librarian.launchpad.net/6637466/libsepol1_1.14-2build1_i386.deb]("http://librarian.launchpad.net/6637466/libsepol1_1.14-2build1_i386.deb")

libselinux1 - [http://librarian.launchpad.net/6456979/libselinux1_1.32-3ubuntu1_i386.deb]("http://librarian.launchpad.net/6456979/libselinux1_1.32-3ubuntu1_i386.deb")

libc6 - [http://librarian.launchpad.net/6393129/libc6_2.5-0ubuntu11_i386.deb]("http://librarian.launchpad.net/6393129/libc6_2.5-0ubuntu11_i386.deb")

libdevmapper - [http://librarian.launchpad.net/6443101/libdevmapper1.02_1.02.08-1ubuntu5_i386.deb]("http://librarian.launchpad.net/6443101/libdevmapper1.02_1.02.08-1ubuntu5_i386.deb")

Burn the alternate install cd and put all the .deb files on a flash drive.  Boot the alternate install cd and start the install in text mode.  When it gets to partiitioning, press Ctrl-Alt-F2, press enter to activate the terminal, and type bash and press enter to get a nice shell.

run this to find out what you flash drive is under /dev so you can mount it:
```
dmesg | tail
```

In my case it was /dev/sdc1, so I mounted it like this:
```
mount /dev/sdc1 /mnt
```

now you need to install the necessary packages to get the array recognized:
```
cd /mnt
udpkg -i libsepol1*
udpkg -i libselinux1*
udpkg -i libdevmapper*
udpkg -i dmraid*
modprobe dm-mod
dmraid -ay
ls /dev/mapper
```

the output of the last command should be somehting like nvidia_abfcacai (everything after the underscore will be different).  If you get this your array is now visible.  More to come shortly.

---

### Post by kakalaky on 2007-03-12
I'm back, start where we left off.

press Ctrl-Alt-F1 to return to the install menu, and select back, then select the option to detect drives to restart the partitioner. This time the raid array should show up as nvidia_abfcacai or whatever yours was named.  Select the one that has no number after (such as nvidia_abfcacai1, nvidia_abfcacai2, etc)  and select manually partition.  Select any empty space and partition as you would like.  Continue the installation until it fails at installing a bootloader.  Press Ctrl-Alt-F2 to return to the terminal.  More to come soon.

Back again.  Now we need to copy all the debs from the flash drive to the new install, this time including libc6.
```
cp /mnt/(name of .deb) /target/root
```

Now chroot
```
mount --bind /dev /target/dev
mount -t proc proc /target/proc
mount -t sysfs sysfs /target/sys
chroot /target
```

Now install the .debs
```
dpkg -i libc6*
dpkg -i libsepol1*
dpkg -i libselinux1*
dpkg -i libdevmapper*
dpkg -i dmraid*
```

These packages will cause dependency problems if you don't do this and agree to remove libc6 and ubuntu-minimal
```
apt-get -f install
```

Now we need to install a bootloader.  You might need to change this if your disk and partition setup is different.  For me, I only had the two drives that are in the raid array, so hd0 works here.  I have Windows on the first partition followed by boot, root and swap partitions for linux.  These devices would be named nvidia_abfcacai1 for the windows partition, nvidia_abfcacai2 for boot, nvidia_abfcacai3 for root and nvidia_abfcacai4 for swap.  For grub the windows partition is (hd0,0), boot is (hd0,1), root is (hd0,2) and swap is (hd0,3).  The staging files mention below are e2fs_stage1_5 for ext2 and ext3, reiserfs_stage1_5 for reiserfs, xfs_stage1_5 for xfs, etc.
```

sudo apt-get istall grub
mkdir /boot/grub
cp /lib/grub/i386-pc/stage1 /boot/grub/
cp /lib/grub/i386-pc/stage2 /boot/grub/
cp /lib/grub/i386-pc/(the staging file for your boot partitions filesystem) /boot/grub/
grub
device (hd0) /dev/mapper/nvidia_abfcacai
root (hd0,1)
setup (hd0)
quit
update-grub
nano /boot/grub/menu.lst
```

At this point you should have an automatically made menu.lst open for editing.  Make sure kopt line uses /dev/mapper/nvidia_abfcacai# where # is corresponds to the root partition.  Make sure groot is (hd0,#) where # corresponds to your boot partition.   Now find the section where there are 3 uncommend groups that begin with title.  Make sure they point to the correct partitions and remove the /boot part before each line if you have separate root and boot partitions. You will also need to remove the savedefault line.  It will look something like this:

```
# kopt=root=/dev/mapper/nvidia_ceejdgda3 ro
# groot=(hd0,1)

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		vmlinuz-2.6.17-11-generic root=/dev/mapper/nvidia_ceejdgda2 ro quiet splash noapic
initrd		initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		vmlinuz-2.6.17-11-generic root=/dev/mapper/nvidia_ceejdgda2 ro single
initrd		initrd.img-2.6.17-11-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		memtest86+.bin
boot
```

Press Ctrl-X, then y to save the file.  If you have windows, you can add it under "End Debian automagic kernels list" part.  It would look like this if it is the first partition:
```
title Windows XP
  rootnoverify (hd0,0)
  chainloader +1
```

Now press Ctrl-Alt-F1 to go back to the installer menu.  Choose to continue without installing bootloader.  Thats it.  When you reboot you should have Ubuntu Edgy on fakeraid.

---

### Post by hobs0n on 2007-03-12
> **kakalaky said:**
> First, download the alternate install cd and get these packages (assuming you are using i386).  You will also need a flash drive (or some kind of removable storage to hold the packages):

dmraid - [http://librarian.launchpad.net/5347776/dmraid_1.0.0.rc13-2ubuntu1_i386.deb]("http://librarian.launchpad.net/5347776/dmraid_1.0.0.rc13-2ubuntu1_i386.deb")

libsepol1 - [http://librarian.launchpad.net/6637466/libsepol1_1.14-2build1_i386.deb]("http://librarian.launchpad.net/6637466/libsepol1_1.14-2build1_i386.deb")

libselinux1 - [http://librarian.launchpad.net/6456979/libselinux1_1.32-3ubuntu1_i386.deb]("http://librarian.launchpad.net/6456979/libselinux1_1.32-3ubuntu1_i386.deb")

libc6 - [http://librarian.launchpad.net/6393129/libc6_2.5-0ubuntu11_i386.deb]("http://librarian.launchpad.net/6393129/libc6_2.5-0ubuntu11_i386.deb")

libdevmapper - [http://librarian.launchpad.net/6443101/libdevmapper1.02_1.02.08-1ubuntu5_i386.deb]("http://librarian.launchpad.net/6443101/libdevmapper1.02_1.02.08-1ubuntu5_i386.deb")

Burn the alternate install cd and put all the .deb files on a flash drive.  Boot the alternate install cd and start the install in text mode.  When it gets to partiitioning, press Ctrl-Alt-F2, press enter to activate the terminal, and type bash and press enter to get a nice shell.

run this to find out what you flash drive is under /dev so you can mount it:
```
dmesg | tail
```

In my case it was /dev/sdc1, so I mounted it like this:
```
mount /dev/sdc1 /mnt
```

now you need to install the necessary packages to get the array recognized:
```
cd /mnt
udpkg -i libsepol1*
udpkg -i libselinux1*
udpkg -i libdevmapper*
udpkg -i dmraid*
modprobe dm-mod
dmraid -ay
ls /dev/mapper
```

the output of the last command should be somehting like nvidia_abfcacai (everything after the underscore will be different).  If you get this your array is now visible.  More to come shortly.

First of all I wanna say WOW and w00t!! Im running Firefox from the Ubuntu install and obviously Ubuntu has drivers for the Nforce4! 

Im tryin the guide that Songwind linked, hopefully Ill get it working, Otherwise Ill look at your post. I dont have a flash drive, closest I have is a HDD MP3 player auto detects as a HDD in Windows. Might that work?

EDIT: installing just dmraid didnt work ;) I tried connecting my MP3 player and Ubuntu detected it anyway. Trying your guide now :)

---

### Post by Normlaure0 on 2007-03-12
I have just installed the ubuntu programme from a provided cd - and no problems so far BUT, the system refuses to accept my wanadoo installation disc provided by my server.  What do I do about this?

I am using my laptop at the moment and the installation disc is with thePC (and not working).

I am an OAP and definitely a non-techie, so simple answers if possible please.

Norm

---

### Post by hobs0n on 2007-03-12
Ok thanx again for helping. 

A newb question, since I can the the command prompts up now when Im running the normal install program, cant I add the drivers and programs for the RAID from there? Copied them to the MP3 player. A stupid question,, how do I write | key? Cant really find it and I think Ive tried all keys in various combinations ;) Im know how to make that key before..

EDIT: Im going to shop some f00d with my GF now so Ill let this Ubuntu installation running and check on this thread in a couple of hours :) Im so impressed by the Ubuntu install..

---

### Post by lamalex on 2007-03-12
for your games, free wine works ok, don't use cedega, if you really want your games to work well and dont mind paying, use crossover office. I've played wow, cs, cs:s, hl2 with it and have had almost no problems. cedega was terrible when I tried it. cxoffice is the way to go for linux gaming.

---

### Post by Big_Croc7 on 2007-03-12
| = AltGr + `
:-)
press and hold altGr; the other key is in the top left (at least on my keyboard), it has ` and ¬ and | on it :-)

PS. it's the only use I know of for AltGr!!! (except in Doom... or was it Castle Wolfenstein?)

---

### Post by kakalaky on 2007-03-12
Alright, back from lunch.  The mp3 player should work fine instead of a flash drive.  I'm going back to edit my previous post to finish the instructions.

Edit:  You can't use the livecd to install on fakeraid because the installer on it will not properly recognize the array even with dmraid.  Well, technically you can, but you basically have to install the whole system manually.

Edit again:  If you can wait until the next release (feisty) this should be much easier since it has a working dmraid.  All my instructions really do is get the dmraid from feisty working in edgy.

---

### Post by hobs0n on 2007-03-12
> **Big_Croc7 said:**
> | = AltGr + `
:-)
press and hold altGr; the other key is in the top left (at least on my keyboard), it has ` and ¬ and | on it :-)

PS. it's the only use I know of for AltGr!!! (except in Doom... or was it Castle Wolfenstein?)

You mean the button left of the backspace button? Ive tried all kind of keys but I cant get the  |  key!! Thing is, since Im from Sweden I have a swedish keyboard and in the uhm desktop of the Ubuntu install I got the swedish keyboard to work but if I enter a command line (ctr+alt+x) I dont have a swedish keyboard anymore. Since the default is US, how do I get the  |  sign with a US keyboard?

> **kakalaky said:**
> Alright, back from lunch.  The mp3 player should work fine instead of a flash drive.  I'm going back to edit my previous post to finish the instructions.

Edit:  You can't use the livecd to install on fakeraid because the installer on it will not properly recognize the array even with dmraid.  Well, technically you can, but you basically have to install the whole system manually.

Edit again:  If you can wait until the next release (feisty) this should be much easier since it has a working dmraid.  All my instructions really do is get the dmraid from feisty working in edgy.

Ok, your description doesnt seem so hard, its the damn  |  sign that makes trouble for me ;) When is Feisty released?

---

### Post by kakalaky on 2007-03-12
The | key is below the backspace key on US layout  Shift + \  does it.  Feisty is scheduled for release on April 19th.

---

### Post by hobs0n on 2007-03-12
> **Iamalex said:**
> for your games, free wine works ok, don't use cedega, if you really want your games to work well and dont mind paying, use crossover office. I've played wow, cs, cs:s, hl2 with it and have had almost no problems. cedega was terrible when I tried it. cxoffice is the way to go for linux gaming.

Ok, Im checking it out now. Sounds like a good program to use when running windows apps, I might get Space Empires 5 to work even! =)

---

### Post by hobs0n on 2007-03-12
> **kakalaky said:**
> The | key is below the backspace key on US layout  Shift + \  does it.  Feisty is scheduled for release on April 19th.

Ive just read through your total  explanation and the [guide](https://wiki.ubuntu.com/FakeRaidEdgy)  and it really seems like a big pain in the **** to get this working so I think Im gonna practice my patience and wait for Feisty instead ;) 

I really really thank you for spending so much time helping me tho, very very nice!

EDIT: Since HDDs are so cheap these days Im just gonna buy a cheapo Samsung 250GB disk and install Ubuntu on that on instead, better and safer if windows gets it RAID all alone :D

---

### Post by hobs0n on 2007-03-12
Just to say another thing I was impressed by the Ubuntu install was that the remote desktop program supported Windows Remote Desktop so I could connect to my server without no problem :up:

---

