---
title: "[SOLVED] How install dual boot across two drives?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Astra on 2008-01-13
Hi Everyone,

Total newbie to Linux/Ubuntu and stuck on the install of Gusty. Scenario as follows:

Want an dual-boot system on IBM Thinkpad A31 XP/Ubuntu to experiment with.Have two 100GB hard-drives currently formatted as follows:

Drive 1
C: Boot (Win) 15 GB Primary
unlabelled: 22MB Primary (Intended for BootIT-NG as my boot manager).
Extended Partition as follows:
D: 1GB Logical
E: 4.10 GB Logical
F: 71 GB Logical
unlabelled 2.03 Logical (Intended as Linux Swap)

Drive 2
unlabelled: 22MB Primary (Intended for BootIT-NG as my boot manager).
S: 2.03 GB Primary (As Win Page File container).
Unlabelled: Unallocated 91.10 GB (Intended as install position for Linux by the following scheme):
10 GB for /
5 GB for /home
(Swap on drive 1 – as above.)
The remainder intend as NTFS format to share between the two OS's.

However, when I run the live CD as far the 'Manual' install for partitioning I run into problems. After I click the next for to start the partitioning set-up routine I get multiple 'warning' messages:

“No root file system is defined – Please correct this from the partitioning menu”

Eventually I get to the next stage.

Ubuntu does correctly identify drives and free space but if I highlight, say, the 91.10 GB unallocated space and then take 'Edit partition' I get a dialogue that seems not to want to take input. If select the top input field of the dialogue where I think I am meant to enter the files system (or something?) there is no dropdown scrollable list. If I try to use the bottom part of the dialogue and just enter '/' (meaning okay make this 'root') and then click 'OK' I get a warning that some app has crashed 'Ubiquity'.

Should add that prior to deciding on putting Linux on the second drive (apart from Swap) I did successful do a 'Manual' install with separate /, /home and swap all on the first drive only. I didn't boot into that as decided that would much rather have Ubuntu on the second drive.

Really stumped with this. Any ideas how I get the above arrangement installe?. (Please remember, I'm beginner with Linux.)

---

### Post by gn2 on 2008-01-13
You have a complex set-up.

Things could be easier for you if you put [S: 2.03 GB Primary (As Win Page File container)] on Drive 1 and delete the Linux swap partition on Drive 1.

Next, delete [unlabelled: 22MB Primary (Intended for BootIT-NG as my boot manager)] and read up on GRUB, you will get much better support on here with any issues you may have with GRUB, whereas help with BootIT-NG will probably be difficult.

You'll possibly find it easier to install into unallocated space on Drive 2 using the "Manual" partitioning option to create /, /home and swap, and install GRUB in the MBR of the drive that's first in the BIOS boot list.

For lots of useful info, check out the Hermanzone link in my sig.

---

### Post by Astra on 2008-01-13
Many thanks for response and suggestions.    Have tried many times now to install by the 'Manual' route without success - I keep running into a 'ubiquity' has crashed error message and I seem not to get beyond that; I mean I think that is the reason why I can't really even attempt to define the partitions myself.    Think for just now I'll have delay the attempt at install of Ubuntu until the techs get the crashing Ubiquity out of the way on Manual installs.    Could, though, probably will, look for another popular distro and see if I fair any better there.    Thanks again.

---

### Post by gn2 on 2008-01-13
This might help: [http://ubuntuforums.org/showpost.php?p=1606469&postcount=1](http://ubuntuforums.org/showpost.php?p=1606469&postcount=1)

---

### Post by louieb on 2008-01-13
I use manual partitioning all the time. 1st I'll use a Live CD with GParted  on it ([SystemRescueCd]("http://www.sysresccd.org/Main_Page")) is my favorite.  Use it to partition and format the disk just the way I want it.  
When thats done I put in the install CD and when I get to the partition part of the install I choose manual. You select the partition you want for /  choose edit and select / for the mount point. Do the same for /home.

Noticed your going to use Bootit. So after answering all the install questions you will see an advanced button. You are going to want to put the GRUB pointer in the **boot sector **of the root partition. 
Then you can have your boot loader chainload the / partition. Works great.

---

### Post by Astra on 2008-01-13
Hi Gu2 and Louieb,

So there might be hope after all, great!

I'm not sure if my bios supports the feature that is talked about in the other thread but I'll look into. Also I am using a laptop and the second drive just kind of slots in (hope that makes sense) without any need for jumpers - don't even know if the drives for this are pinned for using jumpers, mmm...? Something else to check out.

However, if I could go the 'bios route' I'm wondering how I would get /swap to the first hard-drive after doing a full install to what would revert back to being the second hdd, after the install. In principle, is it possible to move partitions around, maybe even move and resize them, after doing an initial install of Linux?

For Louieb's suggestion. Yes, when I got the email of the response I had just finished reading elsewhere about Grub being needed in root (or /boot) as Linux can't be launched without it. Had to adjust my thinking on what I was intending to try when I read that.

For the suggestion of trying the rescue cd to set-up and pre-format the partitions I'll give that a whirl in the next few days.

However, I suspect I might still be stumped as I can't 'edit the partitions' - tell Ubuntu installer what partition I want what 'directory', pardon my Windowese, to be installed on. The *@~#!!!!! 'Ubiquity' seems to crash and make any attempt at input in the dialogues impossible. At least I think that is the effect the crash is having on my attempts to manually assign paritions.

What does Ubiquity do anyway? Maybe I can just turn it off in the 'live' environment before initiating the install routine?

Will report back on success or fail.

Many thanks again, greatly appreciated.

---

### Post by louieb on 2008-01-14
Hello Astra,
> **Astra said:**
> Hi Gu2 and Louieb,

...I'm wondering how I would get /swap to the first hard-drive
...is it possible to move partitions around, maybe even move and resize them, after doing an initial install of Linux?

...still be stumped as I can't 'edit the partitions' - tell Ubuntu installer what partition I want what 'directory',..Ubiquity' seems to crash and make any attempt at input in the
... What does Ubiquity do anyway? Maybe I can just turn it off in the 

Gparted to the rescue - its pretty intuitive just create a swap partition before starting the install. The installer will automatically pick it up and use it.

Its possible to move and resize partitions around after the install. But because Ubuntu uses UUID to identify which partition is for what. It a pain in the as to do it afterward. Reason being the UUID can change during the resize. I recommend  all partition work be done before the install. 

The live installer (Ubiquity) is a work in progress should be really good someday. But the alternate CD uses the Debian text based installer - its rock solid, been around for years, a lot of distros use it. My 1st choice. Not any harder to use. Same questions and options. Just different and IMHO better.

---

### Post by gn2 on 2008-01-14
If it was me.....

Drive 1, which I presume is the drive that the BIOS boots from first?

30gb C:
10-15gb / ext3 bootable flag on
1gb swap
remainder /home ext3 bootable flag off
Grub in MBR of Drive 1

Drive 2

D: MyDocuments NTFS

I would put all the Windows system stuff on Drive 1 and leave unallocated space on Drive 1.
I would remove the boot utility that you have.

Then run  the Ubuntu Alternate CD installer, select manual and create the /,swap and /home partitions in the unallocated space, specifying the mount points and boot flags.
Once it's installed you will be able to read/write to the D: My Docs partition from Ubuntu.

---

### Post by Astra on 2008-01-14
Many thanks Louieb and Gn2,

I managed to get it installed (have seen it up and running, though still to configure and so on) and got the partitions according to my planned scheme. Good advice to go down the SystemRescue CD route, it's a nice piece of kit that disk. 

From there the 'alternative' CD' Manual' install was far steadier than the standard route for a Manual install. So much so that I ended up thinking that I might well have managed the partitioning without recourse to the SystemRescue CD, doubtless I'll mess around with a reinstall some day while I experiment with things so I'll give that a go next time.

Might be beginner's folly but my impression is very much that the Manual partition install of the 'Ubuntu Alternative CD' is way better than the partitioning routine offered by the Ubuntu Live CD.

For any other newbie wanting to give it whirl it's here:

 [CENTER][http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)
[/CENTER]

SystemRescue CD here:

 [CENTER][http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)[/CENTER]


 [LEFT]That said I did have one bit of hesitation (and a final difficulty) over the 'Make (partition) bootable' for my root partition, really because I don't yet really understand the relationship between GRUB and a partition being bootable. Took a guess and assumed that GRUB would have to be installed to a bootable partition &#8211; please correct if I have that wrong.

For future reference would you please tell me if, for example, I had decided to make a separate /boot partition (which I assume GRUB would have to be installed to) would it be the case that that /boot partition would have to be made the 'bootable' one (and not the root partition)?

Only other difficulty I had was in getting GRUB installed to the root partition &#8211; got several fails. Though, even with the heart-stopping warning **'This is a fatal error'**, the 'Go back' option gracefully allowed for going back and trying again &#8211; until I got it right.

Then it dawned on me that I was probably misunderstanding the numbering scheme for partitions within the (alternative) installer partitioner. Physically I thought of the partitions as being 'what I would be able to see if looked at an 'ordinary disk 'map' of them' &#8211; so reckoned the root to be partition 3 but, it turned out, the installer partitioner saw it as 4. Would I be correct in thinking, then, that the partitioner counts the MBR as partition 1? Or have I got that wrong?

In ordinary-disk-map-speak my partitions (up to root) would have been:[/LEFT]
 [LIST=1] 
[*] [LEFT]My swap partition for Windows.[/LEFT]
[*] [LEFT]Very small partition for Boot-IT.[/LEFT]
[*] [LEFT]Root partition (as the first partition/volume inside an extended partition)[/LEFT]
[/LIST] [LEFT]But the installer partitioner saw '3' as being '4'. Why? MBR = 1? Or, MBR = 0 and the extended partition itself = 3 and, so, the first volume (partition) in it is therefore = 4? Arggh...!!!  This way lies madness!

In any case, Ubuntu is up and running now. 

Gn2's suggestions I think I will give a try out at a later date just to see how that would have worked out. But I'll wait till get a bit more experience with configuring Ubuntu and a little more understanding of GRUB. As things stand I have a bit of experience with Boot-IT from toying around with dual booting Windows so don't expect to get wildly stuck with it.

One last question, off topic, but I think I need an answer fast; any recommendation on the best linux firewall?

Thanks again.[/LEFT]

---

### Post by gn2 on 2008-01-14
> **Astra said:**
> 

One last question, off topic, but I think I need an answer fast; any recommendation on the best linux firewall?


It's already installed and active by default running in the background.
It's called IP Tables, there is a handy GUI configuration tool for adjusting the settings called Firestarter.
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

Glad you're sorted, enjoy :D

---

### Post by Astra on 2008-01-14
Gripes that fast. 

Tafurthelink, Gn2.

You seem to be a night owl as well.

Many thanks.

---

### Post by louieb on 2008-01-14
You'll get use to it. GRUB begins its numbering with zero.
So the 1st  drive is (hd0) the first partition in the first drive is (hd0,0) so on and so forth. Look at /boot/grub/device.map to see how GRUB sees your  partitions. 

The separate partition for /boot is only useful if your installing on an older PC and get Grub ERROR 18. 
Linux and GRUB do not care if the boot flag is set or not. Set it if you want - I alway forget.

---

### Post by Astra on 2008-01-15
Thanks again Louieb. Happy I didn't have to abandon Ubuntu. :)

I saw somewhere else threads are meant to be marked as 'solved' if solved so I'll mark this one if have the permissions and can find the buttton. - not sure who is meant to do the marking.

Doubtless I'll be back though.

---

