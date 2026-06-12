---
title: "new to ubuntu"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mikec73 on 2007-12-07
Tried installing ubuntu on old vista beta partition. After deleting all the partitions and recreating in the size I wanted i installed it. Of course at this point xp was gone but i was reinstalling anyways for problems.  Ubuntu installed and sucessfully booted but would not connect to internet.  this is where I run into problem #1
1.  eth1 not configured.  tried configuring setting in the gui to dhcp and auto using ip4.  doesnt connect. looked at help and used terminal to explore.  terminal says eth1 not configured but gui says it is. gui wants to get address using ip6 instead of ip4. which wont work.  internet is simple ethernet from router. connection is always on.  dns is automatic.  assigned by dhcp.

then i give up and move to installing windows (now i realize this was a mistake but anyways)  I discover that windows finds all sorts of unusable partitions. and installed  into the partition I had sized for it.  after install its on drive I not C and so software wont work properly.  A hard drive utility tells me that it finds a BIOS drive the size of my hard drive on an unidentified controller with ubuntu installed there.

2.  How to get rid of bios drive (odd mirror of hard disk) on unidentified controller. and get back to basic hd. why does ubuntu create a bios drive (kind of like a ram drive I guess.  I did a full reformat of the drive after this installs to get back to a blank new drive and this 80 GB BIOS drive 0x80 SN: N/A is still there
Seagate seatools lists its drive separate.

---

### Post by Dr Small on 2007-12-07
1.) After you have set everything up the way you want for eth1 to work, in GUI, then try running:
```
sudo /etc/init.d/networking restart
```

And see if that has any effect. Sometimes it does.

2.) I have no idea about.

---

### Post by crjackson on 2007-12-07
> **mikec73 said:**
> Tried installing ubuntu on old vista beta partition. After deleting all the partitions and recreating in the size I wanted i installed it. Of course at this point xp was gone but i was reinstalling anyways for problems.  Ubuntu installed and sucessfully booted but would not connect to internet.  this is where I run into problem #1
1.  eth1 not configured.  tried configuring setting in the gui to dhcp and auto using ip4.  doesnt connect. looked at help and used terminal to explore.  terminal says eth1 not configured but gui says it is. gui wants to get address using ip6 instead of ip4. which wont work.  internet is simple ethernet from router. connection is always on.  dns is automatic.  assigned by dhcp.

then i give up and move to installing windows (now i realize this was a mistake but anyways)  I discover that windows finds all sorts of unusable partitions. and installed  into the partition I had sized for it.  after install its on drive I not C and so software wont work properly.  A hard drive utility tells me that it finds a BIOS drive the size of my hard drive on an unidentified controller with ubuntu installed there.

2.  How to get rid of bios drive (odd mirror of hard disk) on unidentified controller. and get back to basic hd. why does ubuntu create a bios drive (kind of like a ram drive I guess.  I did a full reformat of the drive after this installs to get back to a blank new drive and this 80 GB BIOS drive 0x80 SN: N/A is still there
Seagate seatools lists its drive separate.

Ubuntu didn't create a "BIOS DRIVE".  I don't know what type of computer you have, but some makers used to actually put your system advanced bios on a hidden partition of the C:\ drive.  Compaq used to do this on all of their systems.  The firmware BIOS only contained enough of a bootstrap loader to run the HD & Floppy.  The rest of the BIOS Settings were then loaded from the HD.  You could be dealing with this or an OEM maintenance partition.  Are you SURE it's not 8GB instead of 80? Have you ever installed backup software that stores a rescue image in a hidden partition?  Some MFG's also do this from the start.

---

### Post by mikec73 on 2007-12-07
thanks.  
#2 is the most irritating and perplexing problem. The system is not oem, I built it myself using a Seagate Harddrive, MSI K8NGM2 motherboard, NEC DVD burner.  Nothing super special in here  I called seagate and they have no clue how it happened.  searching this on the net is no help either but it was created by ubuntu.  I reformatted the HardDrive using the full format with seagates latest utility.  Its still there.  An older version of seatools shows it by a chart of the system bus. the newer seatools goes straight into the legitimate hd with no other option.  I am thinking this is a warning sign- stay far very far away from linux.  (tried solaris before this, it was a night mare too) after scratching that install and going back to windows then windows would not connect to internet, which is what got this ball rolling.  when I reinstalled xp its installer showed it by way of inaccessible partitions separate of the hd (which of coarse were not previously there) but it installed on a c drive partition this time!!!.  If a version of linux creates it then one of those linux partition softwares but be able to do something with it.  It is flashed onto something, I am thinking the hard drives bios rather than system bios.

---

### Post by AgentZ86 on 2007-12-09
> **mikec73 said:**
> thanks.  
#2 is the most irritating and perplexing problem. The system is not oem, I built it myself using a Seagate Harddrive, MSI K8NGM2 motherboard, NEC DVD burner.  Nothing super special in here  I called seagate and they have no clue how it happened.  searching this on the net is no help either but it was created by ubuntu.  I reformatted the HardDrive using the full format with seagates latest utility.  Its still there.  An older version of seatools shows it by a chart of the system bus. the newer seatools goes straight into the legitimate hd with no other option.  I am thinking this is a warning sign- stay far very far away from linux.  (tried solaris before this, it was a night mare too) after scratching that install and going back to windows then windows would not connect to internet, which is what got this ball rolling.  when I reinstalled xp its installer showed it by way of inaccessible partitions separate of the hd (which of coarse were not previously there) but it installed on a c drive partition this time!!!.  If a version of linux creates it then one of those linux partition softwares but be able to do something with it.  It is flashed onto something, I am thinking the hard drives bios rather than system bios.

Linux did not create this partition.I would suspect that your seagate partition program is causing this.
Since you had a windows problem connecting the the internet to begin with I would suggest this could be a virus problem.

Using Ubuntu Live CD or Gparted Live CD to create your partitions is the best way to install.

By the way I use Gparted for everything including boot partition viruses that don't let the computer boot at all. Gparted can usually boot and remove all partitions so that I have just unallocated partition space, I format to LInux ext3 then reboot and use Gparted from scratch or just boot to the windows CD and create a partition of my desired size and install windows.
Then install your desired Linux from there. My preferred is Ubuntu.

However if your not sure of how to create the partition this could be part of the problem as well.

If your planning on starting all from scratch and completely reinstalling everything then the best and simplest thing to do is create your partition like so:

1.NTFS partition
1.Ubunutu (and during install when asked for home directory select (/) for home that will put the home directory on your root Ubuntu partition simple and problem free.
1.swap

Most people do not have the problem your encounterin with Linux., It seems to be isolated problem.

If you want more paritions then create them as you desire, however NOTE: all OS's have a max of 4 primary partition limit. So if you want more then 4 then you need to create 1.extended partition then additional logical partitions withing the extended partition.

Anyhow once you create the partition then install Windows OS first not Ubuntu and select you drive (hda1) and select the partition that you created for your OS leave the others alone. you can use the windows to recreate this partition of the same size, then format and install etc.

Then move to install Ubuntu and install on hda2, or you might be able to selected guided and it will ask you about that partition as well.

Another way to do it is just to install windows forget all the partition stuff install windows as you normally would and simply use Ubuntu manual installation to resize the partitions and create your Ubuntu and swap partitions.

Also you could just create your windows partition as whatever size you want instead of using the whole drive size. during the windows installation process. Then the unallocated partition size can be used during the Ubuntu process. And be sure to write grub to partition root or hda1 so that you will have the dual boot capability.

This really a simple process and I'm quite sure it's something simple that your missing here. I'ts not windows but a similar process, and I understand that if you don't know it can be fustrating after years of learning things about windows many of the windows processes now seem simple, but thats only cause you know how to do those things already.

I recalled teaching my father how to use windows and I realized that many of the things I do on windows I take for granted that it took years of use to understand all the things I know about windows. I was fustrated a bit teaching him cause I thought people should just already know this. But even using a simple mouse is complicated to someone that never used a mouse before just remember that.

If your not familiar with the process if installation then it's more likely that it's a user problem and not a Linux problem here..

Not to sound like harping but it's just a simple fact. I would suggest patience.

Please post your computer specs. weather your HD is IDE, Sata, Scisi etc. 

Also what types of other drives if any are in the system such as any pen drives or ext. drives or tape drives etc. 

And finally if you are having a problem connecting with windows as well, then perhaps it's a hardware problem, either test cables, make sure drivers are properly installed on windows, and also the double check that the cables are not only partially pushed into the socket. I had a similar networking problem on my server I did everything possible and finally when I was considering taking the server offline and started to disconnect all the connections to actually install a new server, I noticed that one of the plugs was not clicked into the socket properly.
I have no idea how it could just happen I mean it's a server and I never go in the back of the computer. It just worked it's way out on it's own. It looked connected but it was not all the way pushed in. And after much diag. I basically was going to throw away the server and replace all due to a loose connection. 
This may not be the case in your case, but worth checking. 

Especially since you cannot connect with Ubuntu cause I've never had to configure anything on any of my Ubuntu systems it just plugs in and works every time.

Anyhow I hope this helps
Please post back so we can help you get this fixed.

---

### Post by mikec73 on 2007-12-13
system is MSI K8NGM2 with 768MB RAM.  Onboard NVidia Video, LAN Realtek HD audio. AMD Athlon 64 3400.  Seagate 80GB SATA HD.  NEC DVD burner.  Liteon CD burner.  3.5 floppy drive. external USB 11-1 card reader. 
Normally no cards in card reader or flash drives connected to usb.  Printer is HP 6110 (usb)
 
Windows xp has already been reinstalled as in last post.  It showed the bogus partitions then but did install as c: so that is good.  I then installed sun solaris 10 rather than ubuntu because of the issue.  I still believe ubuntu did it because it was not there till after installing ubuntu.  

The networking is partially solved.  It works with an exception.  If I load the other os  by warm restart it doesnt work if I do a cold restart (off for 30 sec then on) it works.  so somehow the initialization of the network port is getting confused.   When  not working, windows cannot uninstall and reinstall driver either, or am I able to disable the port that will cause the computer to be non responsive. 
As long as I dont mess with linux too much, windows is cool with that!!!:)

---

### Post by Shazaam on 2007-12-13
mikec73...
I don't know what the command in Solaris is but we need to have a look at what your disk geometry is. Pop the Ubuntu live cd in the drive, boot the pc with it then open a terminal (Applications>Accessories>Terminal), type in 
```
sudo fdisk -l
```
(small L)
This command will print out your drives and partitions. Please find a way to post the terminal output here.

---

### Post by AgentZ86 on 2007-12-22
> **mikec73 said:**
> system is MSI K8NGM2 with 768MB RAM.  Onboard NVidia Video, LAN Realtek HD audio. AMD Athlon 64 3400.  Seagate 80GB SATA HD.  NEC DVD burner.  Liteon CD burner.  3.5 floppy drive. external USB 11-1 card reader. 
Normally no cards in card reader or flash drives connected to usb.  Printer is HP 6110 (usb)
 
Windows xp has already been reinstalled as in last post.  It showed the bogus partitions then but did install as c: so that is good.  I then installed sun solaris 10 rather than ubuntu because of the issue.  I still believe ubuntu did it because it was not there till after installing ubuntu.  

The networking is partially solved.  It works with an exception.  If I load the other os  by warm restart it doesnt work if I do a cold restart (off for 30 sec then on) it works.  so somehow the initialization of the network port is getting confused.   When  not working, windows cannot uninstall and reinstall driver either, or am I able to disable the port that will cause the computer to be non responsive. 
As long as I dont mess with linux too much, windows is cool with that!!!:)


Well, Windows will typically read the linux partitions as unallocated partitions, but will not read the linux partitions, and the seagate installation disk should do similar unless it has the ability to read and/or write to linux partitions. 

In anycase linux would not create bogus partitions unless you did it manuall, linux does not even have the ability to do anything like what your talking about.

Linux will create a swap partition which typically is not formated to anything it's just empty space that is used for when your computer starts using too much memory, and then in this case it will use the swap space to become more efficient. Windows uses swap on the same partition, but linux create a new swap, but it's only very small space and windows will recognize it as unallocated space as well.

Typically the Windows installation disk might see the partitions, but should easily remove / delete them right from the tools on the Windows installation disk I do this all the time there is never any problems here.

I still think this sounds like some type of virus in my opinion.

When something is written to the disk and you can write or create new partitions or remove the partitions something is wrong. And when in doubt you can always boot up to the Gparted Live CD and this I use to fix all kinds of windows problems and kill boot viruses etc. 

I've had windows computers that would not allow me to boot to the CD it would only boot to the windows OS and no matter what I did I could not boot to the windows reinstallation CD, 

I put in the old Gparted live and off we went , I booted up fine and removed the windows partitions and created a linux partition.

I then went back and rebooted from the Windows CD and boom I'm booting up. And now I can use the Windows to create my windows partitions. But now windows only sees the unallocated partition spaces which I now delete and create my own with windows etc. 

I also sometimes use Gparted to create my partitions and then only delete the ntfs partitions with Windows installer and then create another of equal size with the installer, this way my linux partitions remain entact. The I install windows, then I later install all my other OS's I use to have Octiple (8) boot system just for kicks. But got bored with it, now I just use dual boot Windows/Ubuntu.

Anyhow again Ubuntu / Linux would not have caused this this is strange that the seagate tool is not letting your remove these things, however I'm quite sure the Gparted live CD will do everything you want.

Once in Ubuntu you will have problems using the partition tools if you try to download and run them while booted up. Gparted live boot to the live CD and runs from there that way you don't have to unmount etc. 

I'm currently experimenting with Gparted and Qtparted while booted to my Ubuntu system. Appearantly people are not aware of this subject and need help with using the tool from within Ubuntu Hard drive boot.

I'm working on that next.

Anyhow I hope this helps and can confirm this subject. Since you find nothing on the net also that could be partial confirmation that Linux did not cause this as this would be a known issue with linux and would most likely get solved as fast as it becomes apparant. 

Happy hacking.
:)

---

