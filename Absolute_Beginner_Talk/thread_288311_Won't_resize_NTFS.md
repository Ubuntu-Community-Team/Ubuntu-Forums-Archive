---
title: "Won't resize NTFS"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by carrie.peary on 2006-10-29
I tried everything for partitioning but nothing is working. It says that there is not enough room when I click the option for it to partition for me. 

I tried to do it manually but it will start to try and partition, but then an error comes up saying that it could not resize NTFS and quits the program. 

Here's some details:

-80GB HDD 
-Using 30GB

-Want 60GB for Windows, 20GB for Ubuntu
-2GB Swap
-8GB /
-10GB /home

so far, nothing is working. Any ideas why NTFS might not want to shrink? And it's defragmented as much as possible (huge chunck of white space at the end...about 1/4+ of total window.

Thanks for any help!

---

### Post by linuxhacker on 2006-10-29
You may just need to do a little maintenance. Try checking the NTFS for errors and definitely de-fragment the file system. Good luck. It hope this is helpful.

---

### Post by moshuptrail on 2006-10-29
It's very likely that you have bad blocks on your NTFS partition.  Gparted can't resize if there are bad blocks.  All is not lost, but you will have some studying to do:  The answer is a program called ntfsresize (oddly enough).  It's a command line program (also on the Gparted CD).  There are instructions available for how to do the resize.  It's actually pretty easy.  I've done it twice.  But it is scary!

---

### Post by carrie.peary on 2006-10-29
Thanks for the advice! I'll check into it tomorrow. But thankfully I have school so maybe one of my computer savy friends will figure something out...since I'm soo lost.

---

### Post by eriefisher on 2006-10-29
I've recently come across a utility called Partition Logic. It's claims to be able to resize NTFS and is a small iso download and burn. Might be worth a try. Good luck.

eriefisher

---

### Post by oracle5 on 2006-10-29
Go to [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) and download the iso, burn the iso, boot into the cd, and use qtparted. Its never failed to do what I've wanted it to do. You can install qtparted in Ubuntu but I think it is much safer to boot to this cd so you don't mount anything.

---

### Post by carrie.peary on 2006-10-31
So I download the file and just run it seperatley, right? I hope because for some reason Ubuntu will not find my wireless connection when I'm on the CD...so downloading it through that is not an option.

Oh, and thanks for the help guys! It's much appreciated!!

---

