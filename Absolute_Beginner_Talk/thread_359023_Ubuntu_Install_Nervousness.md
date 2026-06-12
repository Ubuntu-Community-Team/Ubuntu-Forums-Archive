---
title: "Ubuntu Install Nervousness"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by advil0 on 2007-02-11
I want to install Ubuntu Linux, I don't know anything about Linux, I have downloaded the ISO file, and I want to dual boot Windows XP MCE and Ubuntu to make it easier for me.  Can anyone help me calm my nervousness?
Thanks.

PS: I would really appreciate it if you guys would tell me how to dual boot easily.

---

### Post by mikewhatever on 2007-02-11
The easy part is kind of relative, since it depends on you lever of experience. If the LiveCD worked fine, and you've gained some background with the guides:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

you should be OK. Back up the most important files, and remember, that the worst thing that can happen, is you'd need to reinstall Windows.
No big deal at all.

---

### Post by advil0 on 2007-02-11
One question.  When I choose to use freed space on HD, will that delete anything on my pc?  IE programs on Windows, etc?  Because i'd like it if I went into Windows and have everything I had before I installed Ubuntu.

---

### Post by TwistesdTexan on 2007-02-11
Defrag your hard drive at least twice before installing. This will move all your windows files together so thy won't be bothered when you create new partitions. Don't skip this step. It might save you a lot of trouble later.

---

### Post by seth556 on 2007-02-11
I found the install really easy. I did the manual partion thing and left Windows some space on the Hard Drive. That was the hardest part but if you read the guide it's simple.

---

### Post by PartisanEntity on 2007-02-11
As a long time windows user I too found the installation very easy. When you tell the installer to use free space it will not delete any of your files, it will merely used unused space on your hard disk, it will not affect your windows xp mce installation and it will install a boot loader automatically so you can choose which OS to load at start-up.

I actually found installing my wifi card much much harder than the Ubuntu installation :) at the time.

---

### Post by glotz on 2007-02-11
The installation can be a bit scary but if you choose the right options, you'll end up losing nothing... :)

It will be dual booter automatically. At reboot you're presented with a choice to which OS to boot into.

And, besides this installation, always do backup what's dear to you. Once your harddisk crashes, you won't be happy...

Welcome to the tribe!

---

### Post by advil0 on 2007-02-11
What are my chances of having to install Windows again? Because I don't have a Windows CD.

---

### Post by advil0 on 2007-02-11
Anyone?  If there is a low chance, I will install it.

---

### Post by Netherspirit on 2007-02-11
Why not install Ubuntu on a virtual machine using VMWare? Its free and you will see how the install works without affecting your current Windows. Once you are confident that you know how it works, you can do the actual install to get a dual boot.

---

### Post by Henry Rayker on 2007-02-11
The likelyhood that you'll need to reinstall Windows will depend, for the most part, on how well you follow instructions. Additionally, it will depend on how full and/or fragmented your drives are. That 2x Defrag mentioned above is a VERY good idea.

However, if you ever get rid of Ubuntu, you may need a Windows disk to reformat the MBR, depending on how you do that installation.

---

### Post by annda on 2007-02-11
if you are careful (defragment your drive! and back up documents and any files that are important to you), you have nothing to fear. if you are still a bit anxious, print out the guides from the links above and consult them while installing.

i have done at least 20 linux installs on different computers, almost all of them in addition to windows and nothing has ever happened. some people report problems, but they can all be fixed without reinstalling windows - if you do not delete EVERYTHING on your disk during install.

by the way, if you don't have a windows install cd, read a lot before you REMOVE ubuntu (should you ever decide to do that).

---

### Post by Darklighter137 on 2007-02-11
I would personally recommend that you use the LiveCD for awhile and see if you even like Linux.  While the installer works well, there is no point installing Linux if you don't know even the first thing about it (namely, whether it is really for you or not).  That is why the LiveCD exists.

If you have free space on your hard drive (that is, space not occupied by your Windows partition), installation should be quite painless.  If you do not, you will need to repartition your hard drive manually, unless you have something like a recovery partition that you can delete.

The bottom line is, don't install Linux unless you are really committed to installing, learning, and using it.  If you are just testing the waters, use the LiveCD.

---

### Post by nickoli_02 on 2007-02-11
#1 thing to do: create a backup of any documents or files you want to be able to restore in case something goes wrong. 

#2: defragment the windows drive! Take notice of how much space you have left on your hard drive. You will probably want ~10GB for Ubuntu, but you can make do for less. Be sure to leave Windows some extra space to breathe as well.

#3: read up on the installation procedure. It is pretty straightforward. Make sure you understand how you're going to partition your hard drive, as this is where mistakes are usually made. Be very sure you understand it :)

#4: Pop in the installation CD, and go.

---

### Post by steve.horsley on 2007-02-11
Trying a live CD or running it in a virtual machine to see of you like it is an excellent idea. 

When you come to the real install, the chances of scrambling windows is very low, but it is an outside possibility, so back up your vital data first. Come to think of it, your vital data should be backed up anyway.

---

### Post by veloce on 2007-02-11
If you follow the vm or live CD "try before you buy", just remember that these will be SLOW compared to dual boot.

That said, I'm not a fan of dual boot systems.  The incentive is to continually boot the os you are most familiar with. I didn't really start learning and enjoying linux until it was the sole os on my system.  (except for windows virtual machines for particular work tasks).

windows vms under linux seem to perform much better than linux vmx under windows - go figure.

---

### Post by glotz on 2007-02-11
> **Henry Rayker said:**
> 
However, if you ever get rid of Ubuntu, you may need a Windows disk to reformat the MBR, depending on how you do that installation.
Why? (GRUB can boot windoze just fine. Is there something more to this?)

---

### Post by mikewhatever on 2007-02-11
> **advil0 said:**
> What are my chances of having to install Windows again? Because I don't have a Windows CD.

As I said earlier, this is the worst possible thing to happen, and the chances you'll run into it are extremely low. The only operation that can possibly harm Windows partition is resizing. Other then that, Ubuntu installer does nothing to Windows, in fact, it can not write to or delete anything from that partition, because Linux can't natively write to NTFS. So, you Windows partition will stay intact, and the only problems you may encounter after installation, GRUB boot loader related. To get ready for this, download [SUPER GRUB DISK]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"). It can help you to fix both GRUB and Windows boot loader if needed. Also, get a [BOOT DISK]("http://www.bootdisk.com/") for Windows boot loader only.
Finally, you can look for software to copy the entire Windows partition to have in backup. I'll get back later with some suggestions on that.

(Edit) Here are some links for software to backup a partition:
[http://www.drivesnapshot.de/en/down.htm](http://www.drivesnapshot.de/en/down.htm)
[http://www.acronis.com/mag/vnu-ati7](http://www.acronis.com/mag/vnu-ati7)
[http://www.habibbijan.com/?page_id=7](http://www.habibbijan.com/?page_id=7)
[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)
Please note, I haven't tried any of the programs, and can not speak for their integrity. Might be a good idea to search for reviews and user experience first.

---

### Post by nickoli_02 on 2007-02-11
No, linux can't natively write to NTFS, but there is the possibility that while partitioning the existing XP partition that something gets lost. This is why defragmenting is stressed. Also, like I said, make sure you understand what you're doing when it comes time to repartition the XP partition.

---

### Post by steve.horsley on 2007-02-12
> **glotz said:**
> Why? (GRUB can boot windoze just fine. Is there something more to this?)

Yes. Grub relies on some files that are located on /boot/grub on the Ubuntu partition. If you remove or format that partition, you kill GRUB. Best to replace it with a different bootlosder first.

---

