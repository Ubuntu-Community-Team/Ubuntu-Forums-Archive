---
title: "installing ubuntu...many questions!!"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by GI_Josh on 2007-01-17
ok, I have an HP pavilion dv8000 lappy with two 100 gig harddrives.  One drive is called "OS" and thats where XP is installed.  The other, Data, is used for storage, and I think I read somewhere not to install os stuff there.  I plan to ignore this and put ubuntu on that drive, in a partition.  Is that ok?  Also, can I even boot from that drive?  When I go into the menu to select to boot from a CD, I only have the option to boot to the CD drive or "Notebook hard drive."

Ok, moving on.  If I install ubuntu on a relatively small partition, can I access files and save files from outside that partition?

Finally, if I ever want to uninstall ubuntu and delete my partition, how hard would this be? 

Thanks for all the help.

---

### Post by spockrock on 2007-01-17
> **GI_Josh said:**
> ok, I have an HP pavilion dv8000 lappy with two 100 gig harddrives.  One drive is called "OS" and thats where XP is installed.  The other, Data, is used for storage, and I think I read somewhere not to install os stuff there.  I plan to ignore this and put ubuntu on that drive, in a partition.  Is that ok?  Also, can I even boot from that drive?  When I go into the menu to select to boot from a CD, I only have the option to boot to the CD drive or "Notebook hard drive."

Ok, moving on.  If I install ubuntu on a relatively small partition, can I access files and save files from outside that partition?

Finally, if I ever want to uninstall ubuntu and delete my partition, how hard would this be? 

Thanks for all the help.

Umm also long as that drive is an actual drive you can install to it, also when you install ubuntu you should be given the option to install grub, that will add a menu to your boot up process that allows you to pick which operating system you want to dual boot from.

yes if you want to uninstall just delete the partition and you may have to use the fixmbr command from the windows install disk.

---

### Post by rccharles on 2007-01-18
> **GI_Josh said:**
> ok, I have an HP pavilion dv8000 lappy with two 100 gig harddrives.  One drive is called "OS" and thats where XP is installed.  The other, Data, is used for storage, and I think I read somewhere not to install os stuff there.  I plan to ignore this and put ubuntu on that drive, in a partition.  Is that ok?  Also, can I even boot from that drive?  When I go into the menu to select to boot from a CD, I only have the option to boot to the CD drive or "Notebook hard drive."


You will need to look in you Bios configuration and see whether or not you can boot your data drive.  Is the menu you are talking about from your Bios?

I believe by default grub (at least a small portion of it) is installed on the first sector of the drive you install Ubuntu on (in your case the data drive).  This will mean you have to boot to your data drive.

If you cannot boot your data drive, you can install grub on your OS drive. Once installed and configured, Grub will let you run either Windows or ubuntu.


Another option, would be to use superGrub.  This has grub on a bootable CD.  In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)


> 

Ok, moving on.  If I install ubuntu on a relatively small partition, can I access files and save files from outside that partition?

Thanks for all the help.

This page answers a lot of questions.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

See the section on mounting windows.

Robert

---

### Post by GI_Josh on 2007-01-18
Yes that is the menu I was speaking of, the BIOS menu.  When I go in that, I only have the option to boot to the CD drive or Hard Drive, no option for data drive.  I should have been more specific about not installing OS files on the data drive.  When I bought my computer, there was a paper in with it warning against this.  It didn't say why.

If I install grubs on the OS drive, does it need to be partitioned in order to do this?

---

### Post by GI_Josh on 2007-01-18
Ok, I read up on Supergrub, but I'm still a tad lost.  Once I use it, is it then permanent, and I don't need the CD anymore to boot into ubuntu from my Data drive?

Also, i was thinking.  I found this program: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

It allows me to read and write to an ext2 file system from windows, which means I could just not partition my data drive, use the entire thing for ubuntu, and then still kinda use it like a data drive in windows with the space left over, right?  I think this should work.  Let me know If I've missed something.

---

### Post by GI_Josh on 2007-01-18
bump

---

### Post by seshomaru samma on 2007-01-18
What format is your data drive?
if its FAT32 Linux can access it easily ,can read and write
if its NTFS then it will be more difficult - you will be able to read but writing would be difficult and perhaps not possibe with Ubuntu (though I know other Linux distros can )
> Ok, I read up on Supergrub, but I'm still a tad lost. Once I use it, is it then permanent, and I don't need the CD anymore to boot into ubuntu from my Data drive?
its permanent ,but you dont need the supergrub , Ubuntu will install Grub for you , you will then get a boot screen which will allow you to choose Linux or Windows.
I suggest you resize one of your partitions and create a special partition for Ubuntu.
I'm sorry but I dont think I quite understand your set up.
If you boot from an Ubuntu live CD , open a terminal (Applications &#8594; Accessories &#8594; Terminal) and paste this command :
```
sudo fdisk -l
```
and paste the output here 
(it will show you how linux sees your drives ) then we can help you further....


EDIT: it seems like the next post understands your set up better....

---

### Post by rccharles on 2007-01-19
> **GI_Josh said:**
> Ok, I read up on Supergrub, but I'm still a tad lost.  Once I use it, is it then permanent, and I don't need the CD anymore to boot into ubuntu from my Data drive?


SuperGrub boots your Ubuntu/data drive just once. I have only used it to boot a partition without a boot loader in it.  I have gone through most but not all superGrub options.  I could not find a way to install grub from scratch onto a partition.  SuperGrub would restore the master boot record (MBR).

Things get a little more complicated because you will have Ubuntu on your second drive.  You can install grub in a windows partition, but the partition must be vfat.  I did not see were grub supports ntfs.

This means that you will:
1)  have to create another partition on your first harddrive to place the grub support files. The mbr is a small amount of space.  To get more room, grub places some files on the disk which it uses.
2) use superGrub for all Ubuntu boots.
3) swap you os and data drives.  Use grub to boot windows and Ubuntu

I do not know for sure that superGrub will be able to boot your data drive.  There could be some bios code to prevent a boot.  I think superGrub will boot your data drive.  ( I am being overly cautious here. )

Here are some links:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=3)
[http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q10)

Be sure to backup your critical windows files.

> 


Also, i was thinking.  I found this program: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

It allows me to read and write to an ext2 file system from windows, which means I could just not partition my data drive, use the entire thing for ubuntu, and then still kinda use it like a data drive in windows with the space left over, right?  I think this should work.  Let me know If I've missed something.

This should work.  

Robert

---

### Post by rccharles on 2007-01-19
> **GI_Josh said:**
> Ok, I read up on Supergrub, but I'm still a tad lost.  Once I use it, is it then permanent, and I don't need the CD anymore to boot into ubuntu from my Data drive?


While this link is about a USB drive, your situation seems similar to me.  Link:
[https://help.ubuntu.com/community/BootFromUSB?highlight=%28](https://help.ubuntu.com/community/BootFromUSB?highlight=%28)

Robert

---

### Post by GI_Josh on 2007-01-19
Thanks for all the help, and I'm sorry I wasn't clear enough.  I read many more guides on the 'net, and I decided to go for it.  I installed ubuntu on my second hard drive (I chose the erase drive option) and it installed just fine.  Grub (which was autoinstalled, I didn't use supergrub) lets me choose whether to boot ubunut or XP every time I turn it on.  Finally, I used that program in windows which made windows recognize my linux drive as a drive letter, and even  lets me drag and drop files onto it.  I think that my situation is currently solved, except for a few slight issues (namely, hibernation).

Now to get to learning about ubuntu!!

---

### Post by rccharles on 2007-01-20
> **GI_Josh said:**
> Thanks for all the help, and I'm sorry I wasn't clear enough.  I read many more guides on the 'net, and I decided to go for it.  I installed ubuntu on my second hard drive (I chose the erase drive option) and it installed just fine.  Grub (which was autoinstalled, I didn't use supergrub) lets me choose whether to boot ubunut or XP every time I turn it on.  Finally, I used that program in windows which made windows recognize my linux drive as a drive letter, and even  lets me drag and drop files onto it.  I think that my situation is currently solved, except for a few slight issues (namely, hibernation).

Now to get to learning about ubuntu!!

That's great!

Where did grub get installed?  

Robert

---

### Post by GI_Josh on 2007-01-20
Ummm.....I'm actually not sure, since it all happened automatically.  The installer looked for other os'es, and then it said installing grub, and voila.

---

### Post by rccharles on 2007-01-20
> **seshomaru samma said:**
>  Ubuntu will install Grub for you , you will then get a boot screen which will allow you to choose Linux or Windows.


Seems like you were onto the situation.

Robert

---

