---
title: "Dual Boot Win/Mint10 - Mint 14 won't overwrite Mint 10"
date: 2013-02-22
forum: Any Other OS
---

### Post by Malfini on 2013-02-22
Hi All,

My HP desktop currently has dual boot setup Win7 and Mint 10
I want to replace 10 with Mint 14. When I try a custom install I see the partitions below and attempt to select sda5 to place the new OS.

When I click install I get an error "No root file system is defined." 

When I try "install next to existing operating system"  It asks me to split an existing 100GB partition. ( I can't tell which one - both current win 7 and mint 10 partitions are the same size.)

Is there an option to completely overwrite the mint 10 partition?
Should I re-format the mint partition sda5 from windows?

Thanks for any suggestions

---

### Post by Mark Phelps on 2013-02-22
Since this is a Mint install, did you try asking in the Mint forums first?  [http://forums.linuxmint.com/]("http://forums.linuxmint.com/")

---

### Post by oldfred on 2013-02-22
With the manual install you cannot just click on the ext4 partition but also have to tell the system it will be used as / (root) and what format or ext4. 

If you want swap you can repartition to add it by shrinking sda5 by 2GB and then select that as swap. Swap has no format.

---

### Post by grahammechanical on 2013-02-22
You select sda5 and click Change. Then you select a file system from the drop down menu - Ext4. Then you select mount point / then you select to format. You can also change the size of the partition of you want.

Regards.

---

### Post by Malfini on 2013-02-23
Thanks all for your replies.

**Grahammechanical** : I followed your instructions, and then got a message that "you have not selected any partitions for use as swap space.......you may experience installation problems if you do not have enough physical memory....If you do not go back and and assign a swap partition, the installation will continue without swap space"

**I have 3.6 GiB physical memory, Should I be worried about this?**

Do I need to create a 5th partition on this drive? And how to set a partition as swap space?

Thanks for your help.

---

### Post by varunendra on 2013-02-23
*Thread moved to **Other OS/Distro Talk**.*

-------------------------

> **Malfini said:**
> **I have 3.6 GiB physical memory, Should I be worried about this?**
Usually not, at least not during the installation pahse - 3.6 GiB is more than plenty for that. But for regular usage, it is a good idea to have a 1 or 2 GiB swap (partition or file).

> Do I need to create a 5th partition on this drive? And how to set a partition as swap space?
By your screenshot, it looks like the EXT4 partition is an extended one. As such, just do what oldfred suggested -
> **oldfred said:**
> If you want swap you can repartition to add it by shrinking sda5 by 2GB and then select that as swap. Swap has no format.

To elaborate, do it as following -
[LIST=1]
[*]Boot with Mint live cd
[*]Run Gparted (I hope it is on the current Mint live cd)
[*]Right-click on the EXT4 partition, and select "Resize/Move"
[*]In the resize box, type 1024 (for 1 GiB) or 2048 (for 2 GiB) in the "Free Space Following.." field, then press 'Enter' (you can also just click & drag the right border of the partition to do so).
[*]Click "Resize" button, then click the green tick mark to apply changes.
[*]Next, in the newly formed space, right-click > select new.
[*]In the "File System" select "linux-swap" > click "Add"
[*]Again, click the green tick mark to apply the changes.
[*]Close Gparted
[*]Start installation
[*]In the manual partitioning screen, select the EXT4 partition > click "Change" > make it as a moumt point for '/'. Also choose to "Format" it to completely overwrite the current Mint installation.
[*]Proceed with installation and let us know the good news! :)
[/LIST]

Hope you understand that formatting will completely remove all the files on the EXT4 partition. Backup your important files if you have any on it.

Hope it helps.

---

### Post by Malfini on 2013-02-23
**Oh No!**

I was apparently successful at creating a 2GiB swap partition, and the installation appeared to go without a hitch.

unfortunately, upon restart I got:

[B]no file found
grub rescue>[/B]

](*,)Any suggestions?

---

### Post by Malfini on 2013-02-23
This is what Gparted says:

---

### Post by varunendra on 2013-02-23
Yes.

Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") on a live session. If it cant fix the issue, it will create a boot-info file or pastebin link to it. Post it here so we can see what went wrong.

---

### Post by varunendra on 2013-02-23
> **Malfini said:**
> This is what Gparted says:

Did you try to encrypt your home while installation? If not, it should be safe to reformat the 2GB partition as swap.

---

### Post by Malfini on 2013-02-23
Wow, you're fast!

Actually I did elect to encrypt home. I'll try boot repair.

---

### Post by Malfini on 2013-02-23
MUCH THANKS TO ALL, I am now booting successfully! \\:D/

It took me a while to figure out how to install boot-repair. After a few unsuccessful tries, this page was the charm: 

 [http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

---

### Post by varunendra on 2013-02-24
Glad you got it all sorted.

Usually, regardless of whose directions you are following, just ask here if you are stuck at some point, and most often someone would be able to pick it up and answer you.

Enjoy your OS!
:popcorn:

---

