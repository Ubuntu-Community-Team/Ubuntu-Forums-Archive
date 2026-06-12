---
title: "Can't get the Ubuntu live CD to install on my PowerBook G4 (OSX10.4.6) hard drive"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by Nels on 2006-07-05
I've repartitioned my PowerBook's internal hard drive so that there is 70G for OSX and 10G for Ubuntu; both are formatted MacOSX extended (journaled). When I double click to install from the booted live CD (made from the downloaded iso), I'm OK until the step that gives me the three choices: erase 80G drive completely, install on the largest unused partition, or manually selecting the partition. I select to manually install, and select the 10G partition I've already prepared. The next window talks about picking the mount point and mentions the 70G partition that the OSX is on. Here, no matter how I arrange it when I push the install button I get an error message: "no root file system." Each time I try a new arrangement I dread pushing the install button for fear of messing up the partition with the OSX. I've even tried the option to install on the largest unallocated space. The installer is not very explicit as to what exactly it's requesting  and exactly what will happen. Could someone walk me through this portion of the install? What I'd like to end up with is a laptop that will boot into OSX except when I use alt/option upon start up and select Ubuntu as the start up disk.

---

### Post by legacycn on 2006-07-05
there must be 3 patitions at least, in your situation, my suggestion is:
9G for /,
1G for swap,
the rest for /boot

---

### Post by linear on 2006-07-05
The problem is that your 10GB partition isn't "unallocated"; it's formatted for Mac OS. If you erase it completely (afraid I can't provide a walkthrough) you should be able to tell the installer to use unallocated space and proceed from there.
 
Here's a useful link on dual booting: [http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")
 
The following was written for Breezy but may be helpful: [https://help.ubuntu.com/community/Installation/PowerPC]("https://help.ubuntu.com/community/Installation/PowerPC")

---

### Post by Nels on 2006-07-05
I read in another thread that Linux does not play well with a disk that is Journaled formatted, so using Disk Utility I erased and over wrote the partition with zeros leaving it just MacOS extended. These were the only two options given in Disk Utility there wasn't one for unformatted/unallocated. I rebooted using the live CD and went thru the install process, but had the same error message: no root file system.
I've read the two links but things are no clearer for me. As for creating three partitions, I'm not sure I'd care to do that unless that could be done within the larger 10G space already created. Actually I thought that the installer would create these partitions as needed. If I do have to do that manually, would I allocate them in the mount point section of the install?
Thanks for your help.

---

### Post by Ptero-4 on 2006-07-05
Nels. Linux sometimes can fail when reading from a HFS+ journaled partition. But removing such type of partition doesn't cause problems.

---

### Post by Nels on 2006-07-06
[QUOTE=Ptero-4]Nels. Linux sometimes can fail when reading from a HFS+ journaled partition. But removing such type of partition doesn't cause problems.[/QUOTE]
Have been trying to get this to work. Tried creating suggested partitons within the 10g space, but still no luck. Ptero-4 are you saying there is an option to partition without this MacOS formatting? Would I need to erase the drive again and reinstall OSX? Would I make all the suggested partitions manually with Disk Utility? If I do wouldn't there wind up being a whole bunch of hard drive icons cluttering the desktop? I'd prefer to just have one for OSX and one for Ubuntu.
I'm starting to think I should install this on an external firewire hard drive. Would that be any easier? Suggestions?

---

### Post by tidris on 2006-07-06
Do not create any partitions for ubunutu by hand. Instead, create free space in the disk and then let the ubuntu installer automatically create all the partitions it needs using the free space in the disk.

---

### Post by Nels on 2006-07-07
Tidris thanks for the advice. I again erased the hard drive on the PowerBook and repartitioned into two, a 70G for the OSX and 10G (not journaled) for Ubuntu. I've reinstalled OSX and rebooted from the live CD, but can't get past step 5 of the installation procedure. If I select "use largest unused space", with the hope it will install on the 10G space, it says it can't partition. When I reselect and choose "manually allocate" it goes to the next window. I select the 10G space (hda5). It continues to the next window of selections and there regardless of my choices I wind up with the error message:"no root file system". I'm just stumped. I guess I can't figure out what is wanted. But it's got to work somehow. Ubuntu looks great as a live CD so I can't wait to install it.

---

### Post by tidris on 2006-07-07
> **Nels said:**
> Tidris thanks for the advice. I again erased the hard drive on the PowerBook and repartitioned into two, a 70G for the OSX and 10G (not journaled) for Ubuntu. I've reinstalled OSX and rebooted from the live CD, but can't get past step 5 of the installation procedure. If I select "use largest unused space", with the hope it will install on the 10G space, it says it can't partition. When I reselect and choose "manually allocate" it goes to the next window. I select the 10G space (hda5). It continues to the next window of selections and there regardless of my choices I wind up with the error message:"no root file system". I'm just stumped. I guess I can't figure out what is wanted. But it's got to work somehow. Ubuntu looks great as a live CD so I can't wait to install it.

The problem is that you haven't created any free space in the disk yet. That 10 GB partition needs to be formated as "Free Space" in DiskUtility, or it has to be deleted while booted from the ubuntu live CD.

---

### Post by Nels on 2006-07-07
Tidris, that last hint finally opened my eyes. I get it!, free space is not the same as "Free Space." I'd been creating free space by partitioning as I normally would on a hard drive. I did not realize that with Disk Utility I could create "Free Space" at the time the drive is erased and partitioned. Clicking on the 10G space before partitioning showed me that option and I saw it for the first time. But it is also the last time that option is available, so it must be done then. (I do have to say, coming at this from a new user point of view, the phrases: free space, "Free Space", unallocated space, partitioned space, get used interchangeably though they can mean different things, which can be confusing. Actually, it seems that the "Free Space" is not really even a partition as such.)

During the Ubuntu installation I followed your advice to choose at step 5, "use largest continuous free space" option. And as you said all other needed partitions were created by the installer. Everything installed and booted fine with all things working: track pad, screen, clock, keyboard (excepting, though, the built in wireless Airport). My only wish is that the PowerBook would by default boot into OSX upon start up and Ubuntu as an option only when starting up holding the option/alt key. Now it shows a command line window at start up to choose between the two. I'll search the forum for an answer. Thanks again and all the best.

P.S.   I just reread Linear's link above which may be my answer to dual booting.

---

