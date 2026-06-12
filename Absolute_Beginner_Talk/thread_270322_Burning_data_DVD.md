---
title: "Burning data DVD"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by karl-arthur on 2006-10-03
Hi,

I'm having some trouble burning a data DVD. When using the Nautilus CD/DVD Creator everything seems fine while it is "creating disc image", but when the actual burning is about to begin, I get an error message: "Error writing to Disc.  There was an error writing to the disc: Unhandled error, aborting." Very helpful indeed. 

I've tried in the terminal as well:
:~$ growisofs -Z /dev/scd0 -R -J ~/burn
Executing 'mkisofs -R -J /home/karl-arthur/burn | builtin_dd of=/dev/scd0 obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
/dev/scd0: "Current Write Speed" is 1.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-( media is not formatted or unsupported.
:-( write failed: Wrong medium type


However, when I first tried in Nautilus with too many files (4490 mb, disc is supposed to hold 4.7 gb, but as you know, that is generally a lie or creative marketing or wathever) I got error message: "Reload a rewritable or blank disc. Please replace the disc in the drive with a supported disc with at least 4490 MiB free. The following disc types are supported:
CD-R, CD-RW, DVD-RW, DVD+R, DVD+R DL, DVD+RW". Notice that the only unsupported disc is DVD-R, which is, of course, the kind I happened to buy.

So my questions are: Can my problem only be solved by buying new blank disc of any other format, or is there some way to work around this problem on the DVD-R discs? I have a feeling that they perhaps should be formated, but dvd+rw-format did not work. And if the discs are in fact unsupported, why would Nautilus only tell me so when I try to jam them whith to much data? 

Thanks in advance for help.

---

### Post by Drakkor on 2006-10-03
Maybe try K3b ?

---

### Post by karl-arthur on 2006-10-04
Thanks for the tip, seems like a nice program... Didn't solve my problem, though, so I guess it's back to the store...

---

### Post by think13 on 2006-10-04
It is most likely your CD/DVD drive that prevents you from burning that type of disk.  But I don't think CD burning programs check what disk you are using until you start burning, so I guess it wouldn't tell you that the disk is unsupported until you began burning.

---

### Post by mrdaryljones on 2006-11-11
i get the same error message in gnomebaker aswell when i try to burn a data DVD

INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
 
i know the DVD writer writes on this disk i used it in windows before

---

