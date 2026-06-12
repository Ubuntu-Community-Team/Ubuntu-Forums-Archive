---
title: "Ubuntu dual boot with puppy linux"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-29
How can i dual boot ubuntu and puppy?

---

### Post by marko_4454 on 2007-04-29
As far as I know, you can dualboot with anything. You just have to have different partitions and a boot loader, it doesnt matter what OS'es you have there ;)
Hope this helps

---

### Post by mojo123 on 2007-04-29
ok just to say i dont see the install option on puppy linux liv cd

---

### Post by N1N31NCHN41L5 on 2008-05-02
I have been trying to do this and always end up with both puppy and ubuntu unbootable : (

---

### Post by NightwishFan on 2008-05-02
There is something called the puppy universal installer in the menu somewhere. Use a pre-existing ext2 partition to do a puppy full install. You can use its grub but it ends up letting Windows/Puppy boot but not Ubuntu, a good bet is to find a way to restore Ubuntu's grub after you install puppy.

---

### Post by N1N31NCHN41L5 on 2008-05-04
> **NightwishFan said:**
> There is something called the puppy universal installer in the menu somewhere. Use a pre-existing ext2 partition to do a puppy full install. You can use its grub but it ends up letting Windows/Puppy boot but not Ubuntu, a good bet is to find a way to restore Ubuntu's grub after you install puppy.

The machine im trying to dual boot on does NOT have ANY M$ I had a tutorial from the forums that said to take the 3 base puppy files an put them in a folder called boot on a clean partition and then to just add ................
but even though i save the link its gone and i cant find it :( want to add puppy to ubuntu's menu.lst so it shows up at startup.

---

### Post by trucker33377 on 2008-05-04
> **mojo123 said:**
> ok just to say i dont see the install option on puppy linux liv cd

Hi if it were me Id make a new partition with the gparted on the puppy live cd. i use the new puppy dingo 4 gparted is under the system drop down tab after thats done then use the puppy universal installer.its under the setup tab.  that should allow you to put the puppy on the partition you made. after you do that you need to go to system tab and run the grub bootloader conf. Hope this works for you Im new to both OP sys myself so you may want to check more but that worked for me

---

### Post by NightwishFan on 2008-05-04
It is there, its called puppy universal installer, and install it like a normal os, on your drive. It needs a preexisting empty partition but there is a partitioner on the live cd. Trust me I have done it. Do the full install.

---

### Post by flyingtiger on 2008-05-05
> **NightwishFan said:**
> It is there, its called puppy universal installer, and install it like a normal os, on your drive. It needs a preexisting empty partition but there is a partitioner on the live cd. Trust me I have done it. Do the full install.

Yes, he's right. You might use gparted in the Admin menu to make a partition for your Puppy Linux install, then open the Universal Installer to install Puppy Linux on the new partition.

---

### Post by Puptentacle on 2008-06-15
Here is what I did. Hope this helps someone. 

I already have Ubuntu Hardy on this machine and didn't want to lose it but also wanted to be able to boot into Puppy 4. Installing Puppy (full install) onto another partition was giving me only the option to boot into Puppy (by writing a new boot sector) or an unbootable machine (using "update existing grub" in Puppy Universal Installer). I couldn't seem to get the Ubuntu grub to recognize the Puppy boot information for whatever reason so here is what I did. 

[LIST]
[*]Installed Puppy to the new partition, allowing it to write a new boot sector
[*]Rebooted the machine to the Puppy Live CD
[*]Went to the boot folder and opened the Puppy menu.lst
[*]Mounted the Ubuntu partition and opened the Ubuntu boot folder's menu.lst
[*]Copied the boot information from Ubuntu and pasted it into the corresponding section (sda1) in the Puppy menu.lst
[*]Rebooted and got both options in the Puppy Grub.
[/LIST]

The Grub that comes with Puppy gives a boot option for every partition that you have on the disk as well as (in my case) an option to boot to Windows if it finds an NTFS or fat* partition. It does this whether those partitions are flagged for boot or not. I just removed those references I didn't need in the Puppy menu.lst. This worked fine for me. If anyone needs any more information just ask.

---

### Post by OmniCloud on 2008-06-18
I was gonna try puppy...but is there anyone who can confirm this over at the puppy forums? 

[http://distrowatch.com/weekly.php?issue=20070625](http://distrowatch.com/weekly.php?issue=20070625)

Very disturbing, Don't know if I wanna give this distro a try after reading that man...

---

