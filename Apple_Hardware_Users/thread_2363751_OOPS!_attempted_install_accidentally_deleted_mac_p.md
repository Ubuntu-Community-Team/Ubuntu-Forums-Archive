---
title: "OOPS! attempted install accidentally deleted mac partitions, need data recovery"
date: 2017-06-14
forum: Apple Hardware Users
---

### Post by teklife on 2017-06-14
hello, i was just trying to install ubuntu on a girl's macbook pro, something i've done literally hundreds of times. i recently did an lvm install with partitions on a VM and i was going to do that again. and this time by selecting lvm, completely erased was checked off, but i thought that in the next screen i could choose which partition to install to using lvm, but, when i clicked install now, i immediately clicked "go back" when it gave a warning saying that by continuing the partitions would be erased, but now none of the mac hd partitions are visible (when i checked on gparted) and the worst part is she had her recently dead mother's photos on there (only copy) and all of the files from her mac on the backup partition. 

she can't understand why she can't go back to her mac now, how did it all get wiped so fast, this all took place in a minute.

it seems as if it was all too fast to have actually written anything to the disks, so i should be able to recover her files yes?

please help, i'm sweating here.

---

### Post by QIII on 2017-06-14
Have you stopped using the machine and turned it off?

---

### Post by NoWayWin8 on 2017-06-14
> **teklife said:**
> how did it all get wiped so fast, this all took place in a minute.

It wouldn't have wiped it - it only deleted the partition table. You'll probably need to use a tool like [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover the partition table. The data should* all still be there.

*well, "might" all be there. A minute is enough time to have a small amount of data overwritten.

---

### Post by teklife on 2017-06-14
thanks for your speedy response. we did reboot and holding option key did bring up the mac recovery thing, which i just ran disk utility and saw again that there was no "HD2" which had been previously created for backing up her files. 

the lvm stuff seems a bit weird to me on gparted, the context menu showed an option to 'deactivate'. i don't understand enough about lvm to know what that means but i assumed it was like unmount, i did deactivate it, twice, i hope i didn't do more stupid stuff. 

needless to say, this girl that i convinced to use ubuntu on her macbook pro because the mac os was so slow is now hating me and ubuntu/linux in general because of this and is saying stuff like, forget it, i don't want this anymore, let's just go back to the mac, and i'm fumbling trying to explain why there is no mac no ubuntu and most importantly, no files of hers, especially the only copies of her mom's pics. 

i know it should have been backed up to an external HD, but i've done this so often (although only one lvm install) and never had any problems, so i was confident that within 15 minutes or so, we'd be rebooting to a vanilla ubuntu desktop. how wrong i was, and lesson learned, but still, hoping i can recover the files. 

i am trying to dd the disk now, and not do anything else on the computer. is it normal for the dd cloning to not show any sort of progress? i just see the command "[COLOR=#333333][FONT=UbuntuMono]dd if=/dev/sda of=/dev/sdb"[/FONT][/COLOR] after i entered it and nothing more, not sure how to tell if it's working.[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by teklife on 2017-06-14
> **NoWayWin8 said:**
> It wouldn't have wiped it - it only deleted the partition table. You'll probably need to use a tool like [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover the partition table. The data should* all still be there.

*well, "might" all be there. A minute is enough time to have a small amount of data overwritten.


your reply sounds very encouraging and comforting, boy am i worried. never ever have i ever lost anyone's data like this before. i remember my past experience with testdisk was confusing and there's not much info on recovering mac partitions (hfs+ i assume), and from an aborted lvm install?

---

### Post by NoWayWin8 on 2017-06-14
> **teklife said:**
> my past experience with testdisk was confusing and there's not much info on recovering mac partitions (hfs+ i assume), and from an aborted lvm install?

The documentation may be better now. The process for MacOSX looks fairly straightforward at [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) - Here's what I gleaned from it: run the TestDisk executable as Root, choose whether to create a log, select the hard disk, then partition type (Mac), then select "Analyse". It shows the current partition table.
Select "Quick Search" to look for missing/deleted partitions. The one that is of type HSF+ is probably the one you're trying to find. Highlight it and press "p" to list the files to be sure it's the one you're looking for. If it is, press Enter. Now when it shows the list of partitions on the disk, that one should be listed too.
if all the correct partitions are listed, highlight "Write" to create the new partition table. Then "Quit". If you're not sure, just "Quit" _without_ Write to not change anything at this time.

---

### Post by slickymaster on 2017-06-14
*Thread moved to **Apple Hardware Users**.*

---

### Post by kevin160 on 2017-06-14
Testdisk is an excellent tool.  

But why not just restore from the backup?  You did make sure there was a proper Time Machine backup of this girl's computer before you tried to install a second operating system onto it, right?

If not, then, I'm sorry to be rude, but you're not the person to fix this.  If there is important data missing,  find someone IRL who has more experience with mac partition tables, installing linux on macs, etc.  You're very likely to dig yourself deeper into a hole at this point.

---

### Post by teklife on 2017-06-14
last night she was so pissed off, but i was trying to reassure her that i was on the case, and did a dd of the mac hd to her 2tb external hd. 

this morning when i woke up and checked gparted, i was shocked and horrified to see that it didn't clone the mac hd to the free space on the drive, but completely formatted and OVERWROTE the whole hd. 

i didn't even know how to break this news to her, as she said, make sure nothing on that hd gets lost, that's 20 years of my stuff, "literally everything" she said. if she was pissed off last night, she was F'ing FURIOUS today. she's been cursing me out and saying, "i thought you knew what you were doing", and "how did i ever trust you?"

wow, i've never felt so much distress, i've never lost anyone's data before, and especially not TWICE! in a row!

i never read anything about dd needing a completely empty hd, or that it would overwrite whatever was on the drive.

so now, i got a dd'd mac hd which i accidentally deleted the partitions written over all of her files on her external hd.

i deserve to be called an idiot, i really f*cked this up, but that won't help fix this problem(and i'm getting enough much deserved verbal abuse here now), what is the likelyhood that the files under the dd'd mac hd to the external can be recovered?

---

### Post by QIII on 2017-06-14
dd is not called "disk destroyer" for nothing.  I would say that if you had never heard that then you were likely far more naive than you have claimed to be.

Before you volunteer to help out with something like this again, understand the tools you are using and consider the merits of thorough backups.

Unfortunately, if you dd'ed a drive you will need to find the talents of experts usually employed by countries -- if even they can do it.  dd comes with some very clear warnings about data being DESTROYED.  You have effectively done a US State Department level wipe.  Stop what you are doing.  See if you can find a data recovery company willing to take this on and pull your wallet out of your pocket.

---

### Post by NoWayWin8 on 2017-06-14
> **teklife said:**
> what is the likelyhood that the files under the dd'd mac hd to the external can be recovered?

dd? Wow, why did you do that? If it dd'd over anything you want to recover, the only chance is some sort of forensic data recovery service (which will require a professional, $$, and no guarantee of results).

I'd give TestDisk a try on the original HD with the photos before you give up that. But that external HD's data is probably a goner if it was overwritten with dd.

---

