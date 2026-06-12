---
title: "Extraordinary Circumstances lead to desperate measures, Help.."
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by oucii on 2007-12-06
I am a beginner/n00b with Linux and in a somewhat anxious/no choice situation. To cut a long story short, there is a server (currently on Win2003) at a data centre, the local staff there cannot setup a dual boot with Linux/Windows, they JUST do not, period, no negotiations (:(). So stuck in a dilemma because both OS&#8217;s are needed urgently, but I only have remote desktop access, nothing else. YES it is not possible to dual boot Ubuntu if you installed it through VMware, this was stated in another topic, because it uses virtual hardware. BUT the server does not need to have all the hardware settings correct apart from network adapter, CPU,  and that&#8217;s it maybe? In desperation decided to give it a shot anyways and try and install it through VMware from within windows (remotely connected to it) obviously encountering many complicated challenges along the way. 

- How to dual boot with NO control over post BIOS OS selection menu.
- Connect to Ubuntu after installation would not be possible, must setup Network IP settings manually  (no DHCP there)

So after 3 hard days of researching about installations + VMware and learning about Ubuntu Linux while doing it, I yielded some questionable results :confused:.
Obviously I had to test this on a home platform first before even attempting such a wild thing on the remote computer. Here are the steps, which could be done if one was doing them remotely (no BIOS settings, no preinstall, no post BIOS menus)

1)	Partitioned the hard drive with Norton Partition Magic, to setup an ext3 and swap. 
2)	Installed WINGRUB aka GRUB4DOS, setup to look for Linux menu.lst automatically on all drives
3)	Downloaded VMware workstation + Linux Ubuntu LiveCD 7.04 (Also 7.10, alternate 7.04, fluxbuntu, Fedora)
4)	Fired up a virtual machine with VMware, with dual cpu setting, setup writing directly to partition (NOT virtual image) and booted LiveCD, installed into existing ext3 partition successfully.
5)	From VM, booted into installed Linux OS and edited menu.lst to remove &#8220;splash&#8221; and add &#8220;acpi=off&#8221; (somehow Linux doesn&#8217;t boot otherwise on my PC at all, even with normal installs) but it boots into VM.

And then I ran into the following problems&#8230; First I realized that with NTLDR and WINGRUB, when you restart your PC and have a choice of OS&#8217;s to boot, you cannot alter the menu so that it automatically chooses Ubuntu as first and then boots after x amount of time. See I thought you could do that, and just edit one line in the boot.ini, then restart and it would automatically start your desired OS after the timeout expired. Therefore allowing you to boot into either Ubuntu or Windows, just by editing one line. Although you CAN dual boot, except you have to select with arrows, which OS you want.. that won&#8217;t work, don&#8217;t have access to the server to select it. 

- First question, can I do that with GRUB? Edit it, to either select windows/Ubuntu.
Second problem. After choosing Ubuntu in the actual menu (not VMware) it started to boot! Then as was predicted by HymnToLife

> Re: Is it possible? VMWare + Dual Boot
In theory, it is possible to use a physical partition in VMWare but there will be a problem regarding your hardware. When you will run your windows "normall" (i.e. chosing it at boot time), it will install drivers for your real hardware and when you will boot it from your VM, it will have it's virtual hardware => problems. It's like installing windows on a computer then take he drive away and boot it in another. It may or may not work but not without problems.
__________________
Once upon a time, in a far, far away kingdom, lived an amazingly beautiful princess, who got a computer with Ubuntu for her sixteenth birthday. One night, an evil wizard came to her and told her that the rm command would give her everlasting life. Alas! the princess lost all the pictures of her prince charming as well as his Jabber address, and lived in sorrow ever after. The end.

Long story short, if someone tells you to rm -rf something, please don't do it 



The problem was that x server failed to start
&#8220;Module Loader present
Markers: (--) probed, (**) from config file, (= =) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(= =) Log file: &#8220;/var/log/Xorg.0.log&#8221;, Time: Thu Dec 06 22:08:50 2007 (= =) Using config file: &#8220;/etc/X11/xorg.conf&#8221;
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
No screens found&#8221;

Whether this is due to MY OWN hardware or due to installing it in VMware, probably the latter, don't know. But it does let me login, and it&#8217;s running :popcorn:. So the only option for any of this to work, is now to edit xorg.conf from within Ubuntu by accessing it through VMware, to somehow make it start on a real boot&#8230; maybe... I don&#8217;t know anymore, too late here, going to bed now, will work on this tomorrow.

But after all this, I am feeling at getting to nowhere, and the possibility of remotely installing Ubuntu on the server is ever so fading away.
Any suggestions?
Please.

---

### Post by gn2 on 2007-12-06
Have you tried posting in a VMWare specific forum yet?

---

### Post by The Cog on 2007-12-06
I assume that you have remote desktop access to the Windows server? If so...

You could of course install vmware (or virtualbox?) and use the rdesktop to drive the vmware, and install Ubuntu in there. After that, your problem is getting IP access to the Ubuntu server - I assume they only let your server have one IP address, and that belongs to Windows. Perhaps install OpanVPN server on the Windows box and use OpenVPN to tunnel through to the inner Ubuntu server.

Exactly the reverse shoujdl also be possible, using Ubuntu as the host OS and Windows as the guest, but I'm not sure how easy it is to gain a remote GUI connection to a vmware server on Linux - see the vmware docs for that.

---

### Post by uidb4056 on 2007-12-06
If you install vmware you don't need dual boot simply get access to the server and start your virtual machine from vmware application, you can test it in your windows machine before using vmware workstation, later you can install on the server vmware workstation or server depending on your needs.

---

### Post by Slim Backwater on 2007-12-06
You want to setup a linux server at your datacenter, without wiping out the Server 2003 installation already there, and you don't have physical access, but you do have remote desktop access.  That's a neat trick.

* btw, if you were using an HP server with Integrated Lights-out (Advanced or Standard), you could do this easy as pie.  With iLo you could you access the server with a webbrowser, remote mount the ubuntu ISO in the virtual CD-ROM and reboot the server and run the installation.  I've done this, it's awesome.

Given a generic server, this is how I would try:

1. Install the ubuntu server on another computer, as similar to the server as possible.  Install to a small 4-10 GB partition, with no swap partition.
* Install Grub to the first sector of the /boot partition, not the MBR. (if you don't have grub already installed to the MBR, don't worry if the machine won't boot)

a. Boot that box with the live CD and make an image backup of the partition ( dd if=/dev/sda1 of=myimage.img bs=1M )  This will produce a file called myimage.img.  You could put the image onto another partition on the same hard drive, or a flash drive (8G flash could hold a 4G partition)

b. Make a backup of the grub bootloader:  dd if=/dev/sda1 of=linux.bin bs=512 count=1  This will produce a file called linux.bin.  Note that this is /dev/sda1 not /dev/sda (the latter would be a backup of the MBR not the first sector of the partition.)

2. If you don't have unallocated space on the server, make sure your disk is a Basic disk (nothing will work if it's been converted to a Dynamic disk - and you can convert a dynamic disk back to basic without data loss under some very specific circumstances, namely the disk was once a basic disk, and you have only 1 or 2 simple volumes on it) and shrink the disk to free up more than the size of your ubuntu partition.  Google that or search support.microsoft.com if you need to.

a. Create a simple volume (partition) in the resulting free space.

3. Copy the bootloader image and image backup to the server (they are just files at this point).  Copy the bootloader (linux.bin) to the root of the system drive (probably C: ) and do an image restore of the myimage.img to the NEW partition (maybe drive d: ?).

That is the hard part without BIOS level access to the server.  If you had BIOS level access you could boot a live CD and dd if=myimage.img of=/dev/sda2 bs=1M .  Norton Ghost might be able to do this, as might Acronis TrueImage, in fact you might even be able to use either of those to do the original backup!  There are probably windows programs that you could do this from the server, but I'm not up on all those. (maybe even cygwin could handle it?)

If the new partition has been restored successfully, and if it's the second partition on the drive, add a line to your boot.ini like this:
c:\linux.bin="Linux"

You can choose to boot Linux (without changing the default= line in the boot.ini) by going into System Properties (Win+Pause/Break->Advanced or Right-Click 'My Computer' -> Properties or Control Panel -> Classic View -> System, etc.) Advanced, Startup & Recovery (Sorry, I'm a bit unclear on this myself)

this should work, I'd be really interested in hearing what/where it broke if it didn't.  The destination partition needs to be larger that the partition that was backed up.  It MUST be larger, and you must have a partition, not just free space.  The larger partition is not terribly abnormal, and is exactly the situation when you are resizing a partition, although you probably won't be able to grow the filesystem to fill the partition, so don't make it too big.  Why not?  Because the filesystem will be mounted, and resize2fs won't work on a mount filesystem, although resierfs, jfs and xfs can grow a mounted partition.  Maybe you could choose one of those (reiserfs, jfs, xfs) for your root partition during the Ubuntu installation.

You boot process will then be, DOS MBR (boots the active partition) ntldr (reads boot.ini) C:\linux.bin (which is grub) which finds /boot on the second partition and reads /boot/grub/menu.lst (or grub.conf, I'm not clear on that either).

Another way to choose which O/S to boot, because this will be using the DOS MBR, is to make the second partition active with FDISK (does that still work in XP?) and make the dos partition active with FDisk in linux.  That might be even cooler.  In that case you don't need to edit your boot.ini nor put the linux.bin file on it.  Actually that's really cool and should work really good as long as there's a windows way of changing the boot flag on the partition. (Don't know if Logical Disk Manager can do that).

All in all, that should work well.  If you have Norton Ghost or Acronix True Image (both support image backups regardless of file system) use that to do your backup and restore on your server.

I know this is getting long, but that would make it easy:
1. Install Windows XP to a small partition on a computer you have access to.
2. Install Ubuntu to a second partition, do not write grub to the MBR.
3. Test changing the "Active" partition to the second one to see if Linux boots.  switch it back with fdisk in linux.
4. Boot Windows XP and run Acronis or Ghost and backup the second partition.
5. Copy the backup to the server
6. Shrink the server's partition to free up more than enough space for the linux partition.
7. Create a new partition in the free space
8. Use Arconis/Ghost to restore the backup.
9. Change the active partition to the linux parttion, reboot.

Also, for a server, you probably don't even want X.  Use the Ubuntu Server CD (which doesn't install X) or even consider a more "server"-ish distro such as CentOS or Debian (I run both Ubuntu and CentOS servers, there isn't much difference as far as a server goes)

I HTH.  Let us know how it goes.

._.

(posted in the Absolute Beginner forum, lol)

---

### Post by oucii on 2007-12-07
Ok I think people misunderstood my first post, and only Slim Backwater managed to understand what part of the problem was. So here is a reply, will try and make it short as possible.

I am trying to install a Linux distro (Ubuntu) on a remote 1U Rack Server, but ONLY have RDP (remote desktop) access to Windows.

To clarify… the following is already done.

On a test machine (simulating that I have only remote access) I have already installed Ubuntu onto a partition using VMware. I have configured the IP static settings and RDS (remote desktop) server IN Ubuntu already, (by just booting it from VMware) Now I am faced with 2 challenges…

1)	*SOLVED* How to actually boot the installed and configured Ubuntu without access to POST bios OS choice utility…*UPDATE* SOLVED!! As stated before, I downloaded and installed WINGRUB, which is very simple and effective. I just could not get Ubuntu to be default option, this was due to a mistake in syntax, corrected the error… It now works!! This is what the boot.ini looks like, which loads GRUB4DOS grldr, which in turn finds and loads the Linux kernel automatically.

> [boot loader]
timeout=2
default=C:\GRLDR
[operating systems]
C:\GRLDR="Ubuntu" 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

Now, by changing the value after “default” it is possible to boot either systems. Boot.ini could be modified from Ubuntu or Windows (with remote access). Which makes this perfect and easiest solution to boot either.
> 
[boot loader]
timeout=2
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\GRLDR="Ubuntu"
This alternative would load windows as default.

2)	*NEED HELP HERE* Second problem, Ubuntu REAL boots but with x not finding any screens. Probably because it was configured by VMware virtual hardware during installation. I need Ubuntu with graphics, because there is a lot that needs to be done once it’s running. Doing all through command line will be pain and hours of time which I don’t have. So I have access to Ubuntu, through VMware in Windows and able to configure any files, install any drivers manually. Question here now, is not about VMware, or booting, but specifically how to make the graphics work in this situation. What should be done to reconfigure xorg.conf in order for it to boot and work? Any suggestions there?

> The problem was that x server failed to start
“Module Loader present
Markers: (--) probed, (**) from config file, (= =) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(= =) Log file: “/var/log/Xorg.0.log”, Time: Thu Dec 06 22:08:50 2007 (= =) Using config file: “/etc/X11/xorg.conf”
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
No screens found”


Slim Backwater:
Thank you for the dedicating time for a good exlpanation! About the imaging/backup-restore solution, I thought of this too, unfortunately don’t have a PC that resembles the servers spec. But nevertheless, taking this route would still present the problem of how to dual boot without POST (which is now solved), and how to reconfigure settings in Ubuntu without access to it through VMware.   

Server is 1U Rack, single 250GB HDD, AMD 5600 X2. Onboard VIA Chrome9 HC IGP graphics card, Onboard VIA Rhine II Fast Ethernet adapter. Nothing else.

Yes this is somewhat not a beginner question anymore lol, but being a complete Linux newb, don't know where else to ask.

---

### Post by uidb4056 on 2007-12-07
From the terminal you can try to run:

dpkg-reconfigure xserver-xorg

Then choose as a graphics card vga, if it runs at least you will have graphics environment, later you can try to find the right drivers for your card.

---

### Post by oucii on 2007-12-07
Well graphics became least of the worries now. Another complication exists, because Ubuntu was installed from VMware, it added a virtual ethernet card with it's own MAC address. When I real boot Ubuntu it finds the real/actual ethernet card, with a different MAC address, and the settings for the IP, Gateway, DNS are not configured. There is no DHCP where it's going to be installed. I need to have the internet working for the first real boot of Ubuntu, otherwise it's over.
So the next question, is there anyway to setup add an ethernet controller in Ubuntu, before it is discovered ?

---

### Post by popch on 2007-12-07
It appears that there is a fundamental misunderstanding here.

A dual boot system allows you to select one of several operation systems each time you start the computer. With a system which has been installed that way, you can run Windows Server 2003 on monday, wednesday and friday and - say - Ubuntu linux all other days. 

With this kind of setup, there might be times when no OS is running, i.e. when the computer is turned off. There is no way to run more than one of those OSs ***at the same time***. You have to shut down your computer to start another one.

In a dual boot system, each of the operating systems you can start the system with requires one or more partition on a fixed disk. 

Since your data centers refuses to even discuss installing a dual  boot system, we will not follow this track further.

To explain what running a virtual machine might involve, I take an approach which might seem a bit oblique at first. 

We start with your server running Windows Server 2003. You are remotely logged in from your desktop computer, and your Windows session covers all of your display.

You run several programs in your session on the Windows Server, say Solitaire, Mine Sweeper and MS Excel. (Excel is a program which lets you perform calculations on numbers).

Running a 'virtual' machine involves a fourth window besides those with Solitaire, MineSweep and Excel. This fourth window runs a very special kind of program, let's say VMWare. (There are other fine programs which can do what we describe here, but let's stick with VMWare for the moment).

The window holding the VMWare program allows you to 'simulate' a computer. It can load an operating system into its part of the RAM. What you see in the Window controlled by VMWare is exactly what you would see if that operating system ran in another server on which you had a remote session.

That's the 'virtual' bit of the Virtual Machine. 'Virtual' means that you see something which is not there at all. In that case, you apparently see an OS running in an apparently existing computer, or a 'virtual computer'.

As you have observed, the VMWare program pretends to the OS within the virtual machine that there was some RAM, a (virtual) network card and some other virtual devices.

Now comes a very crucial part of the whole technology: the disk used by your virtual computer.

While it would be perfectly possible to 'attach' a partition of your real disks to your virtual machine, that is very rarely done. In fact, the people at VMWare advise against doing so.

Most commonly, you let VMWare create a file within the NTFS partition of your server. VMWare handles whatever your virtual machine wants written to and read from its virtual disk and redirects those operations to that disk file.

If you have read this explanation up to this point, you might realize that you could have done too much work. 

Once VMWare is installed on your server, you create a new virtual machine, state how large a file you want to attach to the machine in place of a partition. Then you boot your virtual machine either from the liveCD with Ubuntu or (after a few simple preparations) even from the ISO image of that CD. Installation done.

---

### Post by oucii on 2007-12-07
> 
It appears that there is a fundamental misunderstanding here................
........................................................................................... Then you boot your virtual machine either from the liveCD with Ubuntu or (after a few simple preparations) even from the ISO image of that CD. Installation done.
__________________
Popch 

Popch
No no no, you got me all wrong. Or maybe I just explained bad. Here we go again... in detail now.

The people at the datacenter only offer Fedora or Win 2003, not both on separate partitions. You can have one, but not the other. So they state they do not setup dual OS's, partly because it takes up them more time + they don't want to do it, since not enough demand for it. I need both Win and Linux, since we have certain server applets running on Windows, which don't have Linux binaries out yet, eventually we'll want migrate fully, but in time. I also would like Ubuntu, as a beginner in Linux it is an attractive solution. So left with NO help from datacenter beaurocrats I have only one solution for now, try and install Linux, while having an intact Win OS, and be able to boot ONE or the OTHER just by modifying the boot.ini (with WINGRUB you can use boot.ini and set a default OS to boot, which is already tested and done). So that is what I meant by dual boot. 

How to install it if you only have RDP (remote desktop) access, with no POST BIOS. You can't! The only possible solution which MAY or MAY not work is installing through VMware directly to a partition. And it is possible, and I did that already. The actual problem I am facing now is, that when installing Ubuntu it configured itself with the virtual hardware... I now need to reconfigure 2 things vital for the operation of the OS in real (not in VMware). First x server, which I know how to do now. Second, IP + DNS + Gateway + Netmask settings... because after the installation from VMware, as soon as it's REAL booted from BIOS, it will detect the real ethernet card (not virtual assigned by VMware) and I would not be able to connect to the server with either SSH, or VNC because they don't use DHCP there... so somehow by editing conf files, I need to have those setting configured. Perhaps if there was a method of assigning static IP + DNS + Gateway to all ethernet cards, even if they are newly discovered on boot by Ubuntu.

---

### Post by popch on 2007-12-08
OK, now I get what you want to do.

You want to modify the server run by your data center so that you can run it either under Windows (as supplied) or under Ubuntu Linux.

You also profess to having little experience at running a Linux server.

My first advice: don't do it.

My second advice: if you have to have a Linux server for some testing purposes, why don't you set it up in a virtual machine on your desktop computer?

My third advice: Once you 'hijack' the server provided by your data center, it should have exactly the same IP address as it does when running Windows. Otherwise, no other computer in your network would be able to find it unless you also hijacked the network and added another IP address.

My fourth advice: Be prepared for some interesting discussions with your data center when your server needs some attention and they find out about the modifications you have made to its setup.

Not having much experience with data centers and little with Windows servers, I hope that those words have been helpful to you. I can not take you any further.

---

### Post by oucii on 2007-12-09
Popch
Thank you for spending your time on the advice.
But the situation is of a radically different nature. 

1)  Why not do it? I am trying to explore and discover. I like Linux and want to learn how to use it, while also being able to have it on our server.

2)  In the beginning of this post, I stated that it&#8217;s going to be tested ("simulated") on a local machine first! 

3) Server is ours, it is completely allowed, no hijacking here. The only negative side effect, is that if it all goes wrong, I pay £15 (British Pounds) for the cost of one of the staff at the data centre physically going near our server, inserting a Windows 2003 CD, and reinstalling it. In fact not sure where you from, it's called colocation in here, we pay for it. [http://en.wikipedia.org/wiki/Colocation](http://en.wikipedia.org/wiki/Colocation)

4) The data center simply doesn&#8217;t provide a "service" where they install 2 OS'es for you. They don't have such expertise, they purely provide colocation services, BUT for big companies who need that kind of customization on their servers, their own engineers go to the data centre, and set things up. Anyone can do that, but atm I am nowhere near the data center, which is located in London, UK. (Won&#8217;t be for a long while either)

Concerning the actual success of this thing. Well I have installed on actual partitions and configured Ubuntu, both from VMware. Challenging part was to assign a static IP + DNS + Gateway to all ethernet cards. Other things included settingp up ssh, WINGRUB, and vnc server. It took a while, because I am a complete Linux newbie, but with the help of people in these forums and &#8220;guides/tutorials/how tos&#8221; got there eventually. Thanks to all of those who helped. Final test is now to do it on the server machine, or else&#8230;£15 quid! :)

---

### Post by mips on 2007-12-09
Edit: Ignore, missed the part about not being in the UK.

Let us know how it goes. If you come right then you know that you will have to write a guide and post it in the Tips & tricks section ;)

---

