---
title: "Running Ubuntu from CD"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by kcav45 on 2008-03-04
Hi,

I downloade Ubuntu 7.10 and burned it to a bootable CD. Then I booted from the CD, and have Ubuntu running.  :)  Eventually  I would like to reformat the hard drive and install Unbuntu but I don't want to lose my networking connections, my Address book, Favorites etc.  I would like to go step-by-step and get evrything running off the CD, then reformat the hard disk and install Ubuntu.  Is this possible?  

Could I set-up Chat wher I might discuss a custom installation?

KC

---

### Post by Tatty on 2008-03-04
You can install ubuntu as a second OS on your hard drive (i am assuming you have windows installed).

That way you can dual boot and select which OS you want to boot into each time you switch on your computer.

start here: [https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo")

This is much less wordy: [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by jan quark on 2008-03-04
as far as I know you cannot save the changes made during the usage of the Live CD

you can join the #ubuntuforums-beginners   freenode.net channel to discuss your installation with the beginners team

if you are using firefox install the plugin chatzilla
[https://addons.mozilla.org/en-US/firefox/addon/16](https://addons.mozilla.org/en-US/firefox/addon/16)

---

### Post by northern lights on 2008-03-04
What you're proposing theoretically works - question though: is your harddrive too small to accompany two OSs? Otherwise just dual boot for a while...

Forget the chat, I'd say - post your questions here - someone might encounter similar problems/questions in the future and thus find them answered already...

---

### Post by kcav45 on 2008-03-04
Tatty, Thank you for your reply,

Eventually I would like to dual boot, but not yet.  I will follow the links you provided.

Thank you very much for your reply. I am excited about oo-BOON-too. 

KC

---

### Post by kcav45 on 2008-03-04
Northern Lights, Thank you for your reply. 

I like your quote, I'm going to post here.

KC

---

### Post by kcav45 on 2008-03-05
I have a 60GB internal hard drive formatted for NTFS.  Should I reformat it for "Gutsy Gibbon" ? Should I use Ext2 or FAT32or continue to use NTFS? 

When new versions of Ubuntu are released, I want to uninstall &#8220;Gutzy Gibbon&#8221; and install the new version.  How should I partition my hard drive to facilitate this?  

KC

---

### Post by kcav45 on 2008-03-05
If I dual boot how can an external storage device be shared?

I have Windows XP installed on a notebook computer that has internal 60GB hard drive (formatted NTFS 55.78GB).  I also have 300GB eSATA hard drive that might be used as an external storage device. What if, Windows and Ubuntu shared the external storage space?  The external drive uses firmware to connect to the notebook.  There is no firmware available from the manufacturer to connect with a  Linux os.  The drive is formatted with FAT32. NTFS is available.  How can I createa dual boot system and share access to the eSATA drive?

KC

---

### Post by wheredidrealitygo on 2008-03-05
> I have a 60GB internal hard drive formatted for NTFS. Should I reformat it for "Gutzy Gibbon" ?ShouldIuse Ext2 or FAT32or continue to use NTFS?

When new versions of Ubuntu are released, I want to uninstall &#8220;Gutzy Gibbon&#8221; and install the new version. How should I partition my hard drive to facilitate this?

KC 

Ubuntu (Gutsy Gibbon) needs to be formatted to ext to work, whether you wish to use ext2 (older, comparable to fat32), or ext3 (newer, comparable to ntfs), the choice is yours.

You don't need to uninstall old versions to upgrade to newer versions, you can install a newer version simply by upgrading as you do with the update manager presently, at an appropriate time the update manager will inform you a new version is available, and if you wish to download it you can accept, it will download and install itself, restart, and you're in the new version.

> 
If I dual boot can external storage be shared?

I have Windows XP installed on a notebook computer that has internal 60GB hard drive (formatted NTFS 55.78GB). I also have 300GB eSATA hard drive that might be used as an external storage device. What if, Windows and Ubuntu shared the external storage space? The external drive uses firmware to connect to the notebook. There is no firmware available from the manufacturer to connect with a Linux os. The drive is formatted with FAT32. NTFS is available. How can I createa dual boot system and share access to the eSATA drive?

KC 

Yes, external storage can be shared. It's best to have it fat32, as both Ubuntu and Windows can read and write to it with no problems whatsoever, although if you need to have it in ntfs, Ubuntu supports read/write capacity for that as well, albeit not as developed as for fat32.

What kind of eSATA drive is it, if we know what model, we can look it up and see if anyone else has had luck with it.

---

### Post by kcav45 on 2008-03-05
Wheredidrealitygo asked, " What kind of eSATA drive is it?"  

I have a Seagate, ST3300601XS-RK, eSATA External Hard Drive,300GB,7200RPM,3GB/S,Cache 16MB buffer;  (Seagate, ST3500601XC-RK is 500GB model)  

I have connected the 300GB model to several PCs running Windows using USB cable.  The drive was immediately detected and files transffered efficiently. No drivers need be install.  The drive came formated with FAT32.

When connected using eSATA cable and adapterthe DTR is 3.0GB/S vs .45GB/s for USB using USB.

KC

















.

---

### Post by kcav45 on 2008-03-05
Dual Boot Systems

I can switch the 60GB hard drive with a 160GB hard drive installed in another notebook.  If I do my Dual Boot system specs will be:  Intel Pentium M 2Ghz CPU, 2GB RAM, 160GB storage. :)

When a system is powered-up the system loader reads the Master Boot Table stored in Sector 1 of Disk 0.  In a Dual Boot configuration I am asked which os do I want to run.  If  I choose Ubuntu the loader reads the Master Boot table to find the partition where Ubuntu is stored. If I rather run Windows it reads the MBT and finds the partition where Windows is stored. Then the system loader turns control over to the operating system's loader stored in the same partiton as the os. If I want to change from one os to another I need to reboot.  I can not hot key back-and-forth because the operating systems are not running simultaneously. This does not seem very useful. :(

I would like a Dual Boot system configuration that features a shared data repository, and where I could hot-key between OSs as if a KVM switch were employed.  As I explore ways to use Ubuntu I expect to find that drivers are abundant to connect Windows with peripheral devices, since 200,000 million issues of Windows XP are currently in use, and that these drivers provide robust connectivity.   I would like to create a desktop work environment where I could I/O to peripherals from Windows, and use the speed and flexibility of Ubuntu for the analytical and computationally demanding tasks.  How can I run Ubuntu in parallel with Windows. :confused:

KC

---

### Post by wheredidrealitygo on 2008-03-05
> **kcav45 said:**
> Dual Boot Systems

I can switch the 60GB hard drive with a 160GB hard drive installed in another notebook.  If I do my Dual Boot system specs will be:  Intel Pentium M 2Ghz CPU, 2GB RAM, 160GB storage. :)

When a system is powered-up the system loader reads the Master Boot Table stored in Sector 1 of Disk 0.  In a Dual Boot configuration I am asked which os do I want to run.  If  I choose Ubuntu the loader reads the Master Boot table to find the partition where Ubuntu is stored. If I rather run Windows it reads the MBT and finds the partition where Windows is stored. Then the system loader turns control over to the operating system's loader stored in the same partiton as the os. If I want to change from one os to another I need to reboot.  I can not hot key back-and-forth because the operating systems are not running simultaneously. This does not seem very useful. :(

I would like a Dual Boot system configuration that features a shared data repository, and where I could hot-key between OSs as if a KVM switch were employed.  As I explore ways to use Ubuntu I expect to find that drivers are abundant to connect Windows with peripheral devices, since 200,000 million issues of Windows XP are currently in use, and that these drivers provide robust connectivity.   I would like to create a desktop work environment where I could I/O to peripherals from Windows, and use the speed and flexibility of Ubuntu for the analytical and computationally demanding tasks.  How can I run Ubuntu in parallel with Windows. :confused:

KC

This is not possible. A dual-boot configuration in no way involves the capability to run both simultaneously unless one of them is in a virtual machine. You would need two separate computers (read: two separate machines, each with their own processor, motherboard, hard drive, etc) in order to run two operating systems at the same time. KVMs only work with multiple machines that share the same keyboard, not with one machine running multiple OS's.

Summary: Either boot from one, or the other, at the beginning, and restart to change them, or run one inside of a virtual machine inside of the other.

edit: your eSata drive should just work by plugging it in, same as in XP.

---

### Post by kcav45 on 2008-03-06
Thank you, Wheredidrealitygo

If  I plug the eSATA drive in when I bootUbuntu from CD willit work? I also have a Wacom Tablet, Blackberry Pearl, and Polycom Communicator  (microphone/speaker), will these work with Ubuntu? 

KC

---

### Post by wheredidrealitygo on 2008-03-06
I see no reason why your eSata drive wouldn't work directly from the livecd.

The wacom tablet is a 'probably', there are many threads on this forum about getting wacom tablets to work properly, including pressure sensitivity (which tends to be the main issue people have with them, as it tends not to work out of the box).

The Pearl and your mic/speaker, I'm not sure, you could always look them up.

I know that you can use bluetooth without a problem (if you have bluetooth on your computer) with the Blackberry though, from Ubuntu.

---

### Post by kcav45 on 2008-03-06
Thanks for your reply.  I can easiy try the peripherals with the Ubuntu LiveCD.  

KC

---

### Post by kcav45 on 2008-03-07
In order to determine connectivity between Ubuntu 7.10 and USB 2.0 peripheral devices,  I booted a notebook computer from Ubuntu LiveCD, connected 4-plug USB hub to USB port, and plugged two USB devices into the hub -  LGE. Super Multi CD/DVD burner, and Seagate, hard drive, model ST9481147-RK.  Both connections glowed blue indicating a live  connectionn.

On the Desktop I went to Places | Computer.  Four icons appeared. I did not see the external hard drive. Next, I went to System | Hardware and under USB 2.0 found the external hard drive.  Why wasn't the external hard drive visible under Computer| Places?   

KC

---

### Post by kcav45 on 2008-03-08
I  rebooted notebook from Ubuntu Live CD.  The external hard drive is visible on the desktop, while after the previous boot it was not.  However,  the external DVD burner is not visible on the Ubuntu desktop, the previous boot it was. I wonder what is causing this?

---

