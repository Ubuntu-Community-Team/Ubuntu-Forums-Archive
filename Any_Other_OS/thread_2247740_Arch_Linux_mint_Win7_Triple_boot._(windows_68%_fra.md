---
title: "Arch Linux mint Win7 Triple boot. (windows 68% fragmented)"
date: 2014-10-10
forum: Any Other OS
---

### Post by Joseph_Simone on 2014-10-10
I have installed linux mint, arch, gentoo, windows 7, windows 8, fedora, windows vista, and kali linux based on debian before. (not all on the same computer.)
I have dualbooted linux mint with windows 7,
Accidentally deleted the C: drive on a windows 8 box when installing linux mint on a different computer. I then installed windows 7.
On a different windows 8 box, I Installed Kali Linux, but My mom couldn't figure out grub so I uninstalled Kali (with the help of boot-repair live) and fixed the windows 8 gpt.
On a 64 bit laptop, I wiped win 7 and installed gentoo with seperate etc, usr, home, and var using an initramfs. However, I forgot to graphically partition before installing arch, and neither cgdisk nor parted knows partition shrinking so I had to blow away my pretty gentoo. Installed arch by ssh in 2 hours, only spending 8 minutes typing, and the rest either waiting or pretending like I'm working.
On yet another laptop, I installed fedora alongside win 7.

Now I want to triple boot win7 arch and linux mint.

I have a x86 500GiB laptop. I like arch because of its flexibilty. I like linux mint for its ease of use and compatibitlity with debian packages. (Put steam and spotify on mint for leisure, and do work on arch. In the event that neither of those is compatible with software for my job, I don't want to hurt win 7. Unfortunately, my win 7's C: drive is 69% fragmented (ouch) and at the rate that my computer is shuffling away 80,402 files, it will take 33 solid days to get rid of all this. I don't think Gparted will let me shrink C while it is like this. Do I need to see this through?

When I do that, I want to save on partitions and minimise the chance of things going wrong, and I wanted to know which partitions can be shared and how.
I know how to perform a triple boot in theory, but I've never DONE it. I don't know what order to install. I do have a multiboot cd with gparted, dban if it comes to that, and bootrepair which has come to me in many a dark hour.
I don't know which bootloader I want.
I don't have SSDs or Efi so that shouldn't be a problem.
I'm going to use debian linux mint (which is rolling) so I don't have to worry about problems when upgrading (sudo apt-get dist-upgrade && sudo telinit 6, sudo pacman -Syu ; sudo telinit 6)
I have done complicated gentoo things so I'm okay with something difficult. The only reason that I'm not posting this on the arch bbs is that I can't get the right output for "date -u %V$(uname)|sha256sum|sed 's/\W//q'" And I haven't posted this to linux mint because registration is difficult.

If there is a link for something quite similar to what I'm doing, I'm ok if your response is _[un]("http://meta.stackexchange.com/questions/7515/why-is-linking-bad")- _[_he_]("http://meta.stackexchange.com/questions/225370/your-answer-is-in-another-castle-when-is-an-answer-not-an-answer")_[lp]("http://meta.stackexchange.com/questions/225370/your-answer-is-in-another-castle-when-is-an-answer-not-an-answer")-[ful]("http://web.archive.org/web/20140806015824/http://meta.stackexchange.com/questions/8231/are-answers-that-just-contain-links-elsewhere-really-good-answers")_.

---

### Post by Joseph_Simone on 2014-10-10
And I do have the laptop with arch Linux only on it, but I have no copy of windows 7 on it, nor one with the level of f:mad:d'upness that my win 7 has, so I can't know what to break and fix. The screen is a touch f:mad:d so I would prefer to do something where not being able to see the bottom left corner, 20 percent of the top, 12 percent of the bottom; of the screen. If possible, I'd like to be able to install by ssh or remote desk. I can setup network with bash, and I can manage partitions by text or graphically, I can compile software, and  I intend to use the kde software compilation, if that is of any help.

---

### Post by yancek on 2014-10-10
If you have Arch already, then you need to have some unallocated space on which to install windows 7 and Mint or create partitions in advance.  Can't help with the windows 7 except to let you know that your boot code in the mbr will be overwritten.  You need the Arch medium to reinstall its code to the mbr after the windows install to make sure they both boot before installing Mint.  I believe Arch also uses Grub2 as does Mint, so you can select to install the Mint Grub either to its partition or to the mbr.  To share, it would be simplest to create a separate ntfs partition on which to put data which could be accessed from all three systems as windows doesn't recognize Linux partitions.

I just read over your post again and am not sure what your setup is.  Do you have only windows 7 installed?  If that is the case and it is badly fragmented, I would expect problems.

---

### Post by oldfred on 2014-10-10
Moved to other OS since not Ubuntu.

If defrag is that slow in Windows, then you do not have enough space in the NTFS partition. Windows needs 30% free and at 10% free it becomes very slow especially with defrag. Houseclean Windows, defrag and leave 30% inside the NTFS partition as not used.

I believe both Arch & Mint use grub2. Whichever you install last will be the version that installs to MBR and is then first in grub menu. You can change that or reinstall the other install's copy of grub into the MBR to control system booting. Best to have repairCD or flash drive for current version of every system you have installed, particularly Windows as some Windows repairs cannot be done from Linux.

I would also create a shared NTFS data partition so all installs can use that and keep / or system partitions smaller.

---

### Post by Joseph_Simone on 2014-10-13
On separate Laptops:
Windows 7 only
Arch Only ;
I have no win 7 install disk.
I can use the Arch only laptop (2) to test solutions.
My end goal is to get Laptop 1 to have Win 7 Arch and Mint.
My current Win7 has ext2fsd so It can read from linux without writing. I do not want ntfs partitions, but I want to try to have Operating systems share files. If I share a /home , I don't have to copy all the important files from arch to mint and vice versa. (At least, that's what I think happens.) I've heard some people say that I have to create separate user accounts in home, while some disagree, I don't know why someone would separate /usr /var /boot /etc etc. I can probably get all this information using manuals, but I would prefer to get a condensed, clear version, and before I manage to screw anything up.

---

### Post by oldfred on 2014-10-13
A shared data partition is so you do not have to copy files from one install to another. I have many Ubuntu installs and link data into each from one data partition.
If using Windows then you need to use NTFS. 
If just Linux you probably should not use NTFS as you may need chkdsk occasionally and need Windows to run that, or at least a Windows repairCD or flash drive.

But if using a Linux formatted data partition you need to keep track of UID & GID. Ubuntu uses 1000 for first user. Not all versions of Linux use 1000 and that can create issues.

Those that do use a shared /home use different user ID so really separate inside one partition. The few that say it works with one user, do not have same gui/desktop or have virtually the same gui/desktop. Any attempt with similar but even different versions will lead to one install overwriting the other installs settings and if not totally identical versions conflict will cause issues. Even timing on updates can be an issue. Best to be seperate as different users or different partitions. So I prefer to keep /home inside my / (root) and have one data partition for every other install.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)


 Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

