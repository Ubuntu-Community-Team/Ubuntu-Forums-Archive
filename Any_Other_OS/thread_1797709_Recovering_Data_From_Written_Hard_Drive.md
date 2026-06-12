---
title: "Recovering Data From Written Hard Drive"
date: 2011-07-05
forum: Any Other OS
---

### Post by Joel_Zimmerman on 2011-07-05
Hi there.

I'm new to the Ubuntu forums; please excuse me if some of my questions are no0b-ish :P

I am familiar with Ubuntu and Knoppix as I regularly use the operating systems on certain computers. However, my main notebook, an Acer Aspire 5942G with Windows 7 Home Premium 64-bit, contracted malware and so I downloaded a program called ComboFix to try and get rid of the infection. Turned out that the malware infected certain essential files that Windows needed to function properly and ComboFix blindly deleted these files. I was unable to start Windows, nor did I have an installation disc, so for the time being I am using good old Ubuntu 11.04.

Down to my question at hand: using Ubuntu, I accessed my C:\, highlighted the folders I wished to back up and transferred them onto a 1TB internal hard drive plugged in via USB. When the backup was complete, I set forward to install Ubuntu onto my hard disk, selecting to format my drive in the process. Once installed, I accessed the 1TB hard drive to have a look through my Documents and Settings folder which I copied from the now formatted drive. To my horror, it was a short cut file to which it accessed the REAL folder, which was now deleted an non-accessible.

Luckily for me, I had a lot of my things backed up, but I hadn't backed up a lot of my photo albums which are quite precious to me. Is there any way of even retrieving a few of these files? I understand that it's possible to recover all files from a formatted drive, as long as nothing else has been written onto it. This hard drive has had Ubuntu written onto it so I'm worried that they've already been overwritten. I have used PhotoRec to see if I can recover anything, but it shows up that my C:\ has 6 partitions on it and I don't know where to start looking. Here are what the partitions look like in the terminal:

[Intel  ] Intel/PC partition
[EFI GPT] EFI GPT partitino map (Mac i386, some x86_64...)
[Mac    ] Apple partition map
[None   ] Non partitioned media
[Sun    ] Sun Solaris partition
[Xbox   ] Xbox partition

Thanks for any help or advice on this matter!

---

### Post by handy on 2011-07-05
If you hadn't of installed anything on the drive you would be in much better shape. Having the formatted drive overwritten (in part at least) makes it a far more difficult proposition, which is somewhat dependent on how it was formatted & whether your images were overwritten or not. If they weren't overwritten then you have reasonable chance of recovering them.

The first thing I would do is use Clonezilla to make a backup of the partition in question, & then do any work on the backup, leaving the original untouched.

I've had no need to use such tools in the Linux or Apple worlds, as my experience in this regard was Windows based where I was faced with this problem more than once. I am 5.5 years away from those situations so I'm giving you the best I can come up with translated to Linux. :)

As far as tools to use are concerned the following look good, though whether or not you will get what you need from their free packages I don't know:

[https://www.e-fense.com/store/index.php?_a=viewProd&productId=11](https://www.e-fense.com/store/index.php?_a=viewProd&productId=11)

[http://download.cnet.com/EasyRecovery-Professional/3000-2242_4-37386.html](http://download.cnet.com/EasyRecovery-Professional/3000-2242_4-37386.html)

I've read on the Gentoo forums of someone using GetDataBack to recover data (images also) from an NTFS drive that was formatted with ext3.


I'll try to get this thread moved to the otherOS/distro talk sub-forum as there are a number of highly skilled people that consistently check in over there, you may possibly get a more appropriate answer, though no matter what anyone tells you, if you are going to attempt to recover your data, do it on a backup not your original.

---

### Post by mips on 2011-07-06
Don't do anything on that partition where you want to recover the data from.

Image the partition to a spare drive as handy suggested.

post the output of sudu fdisk -l here and tell us which partition it is that you need to recover data from.

You can use TestDisk to recover your files from the image.

---

### Post by handy on 2011-07-06
I knew there was a great GNU tool for the job but I couldn't for the life of me remember its name. :)

I just had a read on their website; TestDisk looks to be a terrific piece of software.

So I thought I'll install that, when I entered the command to download & install it I was told that I had already done so. :confused: 

Something else lost in the black hole of the past that was once my memory... :-k

[edit:] I just had a look on the Arch wiki & there is a list of good tools & some associated info', well worth the read:

[https://wiki.archlinux.org/index.php/File_Recovery](https://wiki.archlinux.org/index.php/File_Recovery)

---

### Post by mips on 2011-07-06
> **handy said:**
> I knew there was a great GNU tool for the job but I couldn't for the life of me remember its name. :)

I just had a read on their website; TestDisk looks to be a terrific piece of software.

So I thought I'll install that, when I entered the command to download & install it I was told that I had already done so. :confused: 

Something else lost in the black hole of the past that was once my memory... :-k[/url]

lol.

Test disk has saved some other peoples bacon before when they came crying to me.

If you are working a bad disc (bad sectors) GNU ddrescue is a gem!

This is also useful [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by handy on 2011-07-06
Thanks for that link, its now Bookmarked. :)

No wonder I usually carry ~1k of fairly well organised Bookmarks, they are to a large extent my online memory.

---

### Post by Joel_Zimmerman on 2011-07-22
Hey guys. Sorry for the extremely late reply, I have been up to my neck with work, but I'm done with it now. Thanks for the suggestions, I shall check them out swiftly.

Cheers.

---

### Post by mips on 2011-07-22
> **Joel_Zimmerman said:**
> Hey guys. Sorry for the extremely late reply, I have been up to my neck with work, but I'm done with it now. Thanks for the suggestions, I shall check them out swiftly.

Cheers.

Hence forth mount that drive as read only!

I suspect you will be ok in getting your data back but i could be wrong. Win7 has quite a large footprint on a HDD when you install it and your data usually only follows after the OS, assuming the the OS was installed at the beginning of the drive.
Ubuntu is much smaller in size when installed so I doubt it even got close to where your data is located.

Did you do a quick format or a complete format when you installed ubuntu? Full format takes a very long time so you would know if you performed one, by default ubuntu installer does a quick format.

You can also try a utility by Ontrack called Easy Recovery Professional that works very well.

---

### Post by Joel_Zimmerman on 2011-07-22
When I 'thought' I was sure I had everything, I decided to install Ubuntu. When the options to choose which partition to use came up, I remember selecting to clear all partitions, format completely and install Ubuntu.

Thanks.

---

### Post by mips on 2011-07-22
how big is the HDD an how long did it take to format roughly?

---

### Post by Joel_Zimmerman on 2011-07-25
The HDD is a 640GB SATA II and I had used up about 360GB including Windows and everything else. I have to say that I'm not entirely sure on how long the formatting took, but I do remember the slideshow of Ubuntu playing through its cycle twice.

---

