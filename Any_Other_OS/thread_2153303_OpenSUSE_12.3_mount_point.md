---
title: "OpenSUSE 12.3 mount point?"
date: 2013-06-10
forum: Any Other OS
---

### Post by 3mutts on 2013-06-10
Alright, I'm installing OpenSUSE on a 2006 Dell Dimension E521 and I'm wondering what mount point I should use for the partition OpenSUSE will be installed on (NOT THE SWAP PARTITION!). On Ubuntu it is / but I don't see / in the options instead I see:

/home
/var
/opt
/boot
/srv
/tmp
/usr/local

I know it's not tmp as I assume that means temporary and /home is the home folder.

---

### Post by Lars Noodén on 2013-06-10
The mount points are arbitrarily assigned by each system to the devices you have prepared (/dev/sda1, etc).  You don't want to mix them between operating systems.  Each system should definitely use separate root, /usr, /bin, /etc and so on.  You might be able to share swap, /tmp and maybe /home between systems but everything else should be separate.  So pay attention to device names and write them down if you need to.

Also, if you're looking for an RPM-based distro you might turn to Fedora.  [Suse arrangements with MS](http://www.zdnet.com/blog/microsoft/microsoft-and-suse-extend-microsofts-controversial-novell-linux-pact/10164) have not been the wisest.  Nothing has changed for the better since the big [exodus back in 2006](https://news.samba.org/announcements/team_to_novell/).  Even [Jeremy Allison wrote ](http://linux.slashdot.org/story/06/12/21/167258/jeremy-allison-resigns-from-novell-in-protest) his own piece, too.  CentOS is also quite popular as an alternative.  Mageia might be an even better choice, since is it a good community distro.  Myself, I prefer the APT-based distros.

---

### Post by 3mutts on 2013-06-10
^ I'm not dual booting systems, Im over writing a old Windows XP installation which is on /dev/sda2 I want to make a main partition formatted as ext4 and a swap partition (I already know how to set that up) so / is ok? I can type points in I just want to make sure I don't end up with a unbootable system. Also, I don't want to use Fedora as it is a test bed and can be unstable at times. Also my mom will still be using this computer for printing things out so I don't want her coming into a black screen.

---

### Post by Lars Noodén on 2013-06-10
If you're replacing the Linux system, then you can just steamroll over the old partitions.  However, be very sure to mark them for formatting -- except for maybe /home.  

Another way to do it, is when editing the partitions erase all the Linux partitions and then create new ones.  Just be sure to leave the other system's partitions alone.

Again, if Fedora is too experimental, you might look at Mageia.  By the way, Groklaw has dozens of articles on the Suse problem, like this one: [http://www.groklaw.net/article.php?story=20070930081040440&mode=nested](http://www.groklaw.net/article.php?story=20070930081040440&mode=nested)
And it's been covered elsewhere like in Techrights.

What about Kubuntu or Lubuntu instead of an RPM-based distro?

---

### Post by ajgreeny on 2013-06-10
If this is currently a windows only machine you will definitely need to format everything including any /home partition you make, in spite of Lars Nooden's comment above; /home can not be on a windows filesystem type, such as ntfs, as that will not enable the Linux permissions needed for /home.  A data partition can be ntfs if you wish, but not /home.

---

### Post by Lars Noodén on 2013-06-10
/home would already be in ext3 or ext4 format if it came from another Linux system.  So there would be no need to format it if there is a desire to keep the contents.  That would save restoring from backup.

---

### Post by ajgreeny on 2013-06-10
> **Lars Noodén said:**
> /home would already be in ext3 or ext4 format if it came from another Linux system.  So there would be no need to format it if there is a desire to keep the contents.  That would save restoring from backup.

Agreed, but I assumed, maybe wrongly, that the machine was Win XP only, therefore all ntfs, or maybe fat32 partitions.
@OP:  Sorry if that confused you.

---

### Post by 3mutts on 2013-06-10
> **ajgreeny said:**
> Agreed, but I assumed, maybe wrongly, that the machine was Win XP only, therefore all ntfs, or maybe fat32 partitions.
@OP:  Sorry if that confused you.

This machine is XP only. I know to reformat the Windows XP partition (/dev/sda2) and shrink the partition by 2GiB to make a SWAP partition, I'm just wondering what mount point the main install should be.

---

### Post by benerivo on 2013-06-10
Yeah, you need to decide on what partition you want for OpenSuse root -- maybe /dev/sda2 in your case if you're replacing XP. During the graphical install process you get to propose mount points for each part of the OpenSuse installation. The menu you mention, where it lists /home, /var, /tmp etc... should be fine to click inside and overtype. As with every linux install, you must have the new root partition as '/'. So select a partition and type '/' in to the mount point. Watch this video for one person going through it [http://www.youtube.com/watch?v=BroOMYPaY-c](http://www.youtube.com/watch?v=BroOMYPaY-c)

---

### Post by 3mutts on 2013-06-10
Alright, posting from the LiveCD. Anyways does this look ok to you guys?

[IMG]http://imageshack.us/a/img43/7495/snapshot3b.png[/IMG]
                                                                                       Original Set Up

[IMG]http://imageshack.us/a/img211/3045/snapshot5e.png[/IMG]

                                                                                        New Set Up

Also, after install, can I get rid of the two Dell partitions (I assume they are recovery partitions for Windows XP) and combine them with the new install?

---

### Post by benerivo on 2013-06-11
> **3mutts said:**
> Alright, posting from the LiveCD. Anyways does this look ok to you guys?...Also, after install, can I get rid of the two Dell partitions (I assume they are recovery partitions for Windows XP) and combine them with the new install?

Yes, it looks fine. Although it's possible to merge sda1 and sda3 with sda3 (root) after the install -- it's much easier to delete all three and create a single new partition in the empty space as part of the install process. It's probably done by either 'right clicking' on the drives on that screen you posted, or via the 'Configure...' button in the bottom right.

---

### Post by BigSilly on 2013-06-11
> **Lars Noodén said:**
> 
Also, if you're looking for an RPM-based distro you might turn to Fedora.  [Suse arrangements with MS](http://www.zdnet.com/blog/microsoft/microsoft-and-suse-extend-microsofts-controversial-novell-linux-pact/10164) have not been the wisest.  Nothing has changed for the better since the big [exodus back in 2006](https://news.samba.org/announcements/team_to_novell/).  Even [Jeremy Allison wrote ](http://linux.slashdot.org/story/06/12/21/167258/jeremy-allison-resigns-from-novell-in-protest) his own piece, too.  CentOS is also quite popular as an alternative.  Mageia might be an even better choice, since is it a good community distro.  Myself, I prefer the APT-based distros.

> **Lars Noodén said:**
> 
Again, if Fedora is too experimental, you might look at Mageia.  By the way, Groklaw has dozens of articles on the Suse problem, like this one: [http://www.groklaw.net/article.php?story=20070930081040440&mode=nested](http://www.groklaw.net/article.php?story=20070930081040440&mode=nested)
And it's been covered elsewhere like in Techrights.

What about Kubuntu or Lubuntu instead of an RPM-based distro?

OP, I wouldn't let any of this silliness put you off using openSUSE. It's a fine distro with a terrific pedigree.

If there's mudslinging to be done, I don't think it's fair to do it here and attempt to colour people's own judgement. And it's not like Canonical is exactly the saint, is it?

---

### Post by 3mutts on 2013-06-11
^ Yeah I really don't care about that, very similar things can be said about Canonical as well (the whole MIR argument). The point is that both are companies trying to make a profit off opensource systems and if that involves working with companies we don't like than so be it.  

Anyways, the installation went great but now I'm having issues with my Atheros AR5416 WIFI card, it was working on the live CD but it isn't working in the install, I assume this is a driver issue and that I need to find the Linux driver however with all the googling I did I can't seem to find it. If anyone can link me to the driver then that would be great.

---

### Post by BigSilly on 2013-06-11
If you have it installed then just do a reboot and the network should just work. It's a known bug with this release. Your Atheros should work fine. :)

---

### Post by 3mutts on 2013-06-11
^ Yes it is showing up it Yast IDK if its installed or not.

Edit: Got it working alright, now I'm installing updates (100 of them).

---

