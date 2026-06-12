---
title: "Removing Partitions on a Mac"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by drohl on 2008-11-05
I tried to install 8.04 but with no luck.  I'm no longer interested in installing Ubuntu.

Now, I have 2 extra partitions on my HD (3 and 4) that I'd like to get rid of.  Since Ubuntu did its own thing to create the partitions, Boot Camp will no longer remove them.  How can I get rid of these partitions and regain space on my HD?

---

### Post by cyberdork33 on 2008-11-05
> **drohl said:**
> I tried to install 8.04 but with no luck.  I'm no longer interested in installing Ubuntu.

Now, I have 2 extra partitions on my HD (3 and 4) that I'd like to get rid of.  Since Ubuntu did its own thing to create the partitions, Boot Camp will no longer remove them.  How can I get rid of these partitions and regain space on my HD?
Use DiskUtility

---

### Post by drohl on 2008-11-05
> **cyberdork33 said:**
> Use DiskUtility

What exactly do I need to do with it?

I get the following window when I open Disk Utility.  The two grayed out volumes at the left are the ones I'd like to delete.

[IMG]http://drohl.files.wordpress.com/2008/11/picture-1.jpeg[/IMG]

How exactly do I go about deleting them?

---

### Post by cyberdork33 on 2008-11-05
select the disk (not the partition) and on the partition tab, click the partition you want to delete and click the minus sign.

You could also use gparted on the Ubuntu LiveCD.

---

### Post by drohl on 2008-11-06
Well, I ended up using Disk Utility from the Leopard install CD to erase the entire hard drive and basically start my computer from scratch since nothing else seemed to work.

I then restored from a Time Machine backup that I had previously created and now I have my extra 30 or so GBs back.

Just posting this in case anyone's wondering what is the easiest way to get things to actually work.

---

### Post by Tommmyboy on 2009-05-05
PREFACE: [COLOR="Red"]*Any modification to a disk's partitions or partitioning scheme/map should be done with extreme caution as there is a risk of data loss. If you're not already backing up regularly, start now, before you do any partition work;*[/COLOR] in fact, it can't hurt to have a redundant set of back ups in case one becomes corrupt and fails (I've started to make two back ups of everything because I've read a couple of really sad, sad stories of authors, musicians, students... people who are really connected to their Macs because it's like their virtual store house... who thought they were really good doing their back ups on a schedule that suited them, who didn't freak out when they had a disk failure because of course they had backed up... but were devastated when attempts to restore showed the back up file to be corrupted and they lost everything.)

I know this is an old topic but I just wanted to add my experience with partitioning using Leopard's Disk Utility and gParted. In a nutshell, to avoid having to go through what could be an annoying time consuming task of completely erasing your Mac disk and then restoring a back up because Disk Utility fools you into thinking there's no way to delete or resize or otherwise manipulate partitions of ANY file system (even the HFS+ which is Apple's own file system) on your disk, **[COLOR="Red"]once you get Ubuntu up and running, I'd recommend sticking to gParted almost exclusively for all future partition creation, deletion, and resizing, be it for Mac or Linux partitions; post Ubuntu install, Disk Utility has only been reliably useful for formatting an already mapped but unformatted partition for Mac as HFS+ or enlarging (using unallocated space created in gParted) or shrinking a Mac HFS+ partition [/COLOR]** 

gParted has that shrinking and enlarging functionality even though the app doesn't officially support HFS+, but - and I guess this might have to do with disk fragmentation - gParted indicates that resizing also involves actually moving data around during the process, a scary proposition seeing as gParted doesn't officially support HFS+ and therefore doesn't error check. If Disk Utility moves data around when you shrink or enlarge a Mac HFS+ partition, at least they don't tell you about it! But in any case, if you shrink a Mac partition with gParted, it'll mess with the bitmap of your disk so either use Disk Utility or run a verify/repair disk after using gParted to fix the Mac partition bitmap.

Disk Utility just seems to go whack - it seemingly randomly creates the visualization of the partition map in a way that neither coincides with the order in which the partitions were created, nor their assigned partition numbers.  I have a triple boot box via reFIt with Intrepid (well, it's Jaunty now), and two different flavors of OS X, so I booted up the other version of OS X on the disk, and Disk Utility there presented a random visualization of the partition map as well, and even though it was the same damn program, the two visualizations were different! I was a little worried because I had spent months tinkering to get my set up to work and wondered if it was just all a mess that Disk Utility was making it look like. 

I popped in a live CD and opened up gParted, which showed everything visually correct in terms of the order in which partition is actually on the disk. So all was good. I'm beginning to have less and less faith in Mac products and more and more trust in opensource stuff so I was confident things were fine.

A couple weeks ago, one of my OS X partitions melted down because I installed some hideous app it didn't like. Well, total no brainer to fix as I back up entire partitions to bootable disk images religiously so I opened up Disk Utility from my OS X partition that wasn't broken and tried to make adjustments and erase the partition, delete it just to be on the safe side, and then recreate it so I could just restore the back up to the partition; I've done it about 3 or 4 times in the past successfully, but before installing Ubuntu. Well, it let me erase it. But I couldn't delete it, it kept saying "Media Kit says partition does not exist." Now mind you, this is an OS X partition we are talking about, not a Linux partition which Mac barely recognizes to begin with. I had to pull out a live CD again and delete the partition in gParted, map out the partition as free space, and then only was I successful in going back to Disk Utility to do a restore of my back up DMG to the partition that got messed up. 

[I][COLOR="Red"]So the moral of the story is, if you find Disk Utility making your partition map look all messed up and acting all crazy, don't panic; just pop gParted in to take care of the hard work and leave Disk Utility to wrap up the loose ends gParted doesn't support.
[/COLOR][/I]

drohl, the original poster, had an amazingly good attitude about having to erase his entire drive and then restore from Time Machine... amazingly good luck as well... Time Machine can be a little sketchy to do entire system restores from... sometimes it works and sometimes it doesn't. It's excellent as an automated solution for backing up anything outside of the System and the Library folders though - like application documents and what not. But because there is never a time when every element in the System or Library is not in use, it's a crap shoot getting an accurate back up of some of those files, and throw off one little tiny file and you could possibly end up with a kernal panic and an unbootable OS X. The most reliable back ups that are ten times speedier than trying to restore from an iffy Time Machine are... ta da... Disk Utility's "DMG" files, which are just basically clones of a disk or a partition. To make one, you have to log out of the partition you're currently using, then either open another partition that OS X and Disk Utility on it (rare, I think I am the only one, lol) or slide in your OS X install disk and open Disk Utility there, make sure you have some sort of adequate back up medium, Firewire drives are good, unmount the partition you want to back up, and choose File, New Image, From Disk, and let it roll. Should you need to restore your back up if your disk fails, you simply drag and drop within Disk Utility and away it goes!

---

