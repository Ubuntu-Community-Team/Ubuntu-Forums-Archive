---
title: "NTFS Partition labeled as Linux swap"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by robtudor on 2006-07-15
Hi,

I started the Ubuntu installation, but being completely new to Linux (always used Windows previously) I have screwed up the partitioning.  

I mistakenly chose an exisiting NTFS partition as the /SWAP partition and later the setup program failed.  The partition was not formatted, but it seems to have been labeled as the /SWAP partition by GPARTED.

When I boot into Windows, it labels it as an unknown partition but Partition Magic sees it as a Linux Swap - irrespective I am now unable to read that partition but I know the data is still there.

Does anyone have a suggestion as to how I might restored the labelling and access the partition?

Thanks in advance.

---

### Post by ovimunt on 2006-07-15
I'm sorry to tell you this but it looks like it's quite serious...

I've also screwed up my partitions recently and the only way I managed to fix it was by using a program called Partition Table Doctor 3.5. Bad news though is that I had to pay for it, 26 GBP (British Pounds). :-( I did try to get it through *other* sources but I couldn't find it...

In any case, your partition table might be screwed up beyond repair so before paying for this program, try downloading the demo version here [http://www.ptdd.com/ptddemo.zip]("http://www.ptdd.com/ptddemo.zip") It will let you scan for lost data and stuff and even browse the lost partitions it may find so it's quite a good tool to find out whether it's all lost or not. 

GOOD LUCK!

---

### Post by ovimunt on 2006-07-15
E-mail me and I'll give you more options which I can't write on the forum.

---

### Post by verbatim210 on 2006-07-15
if you got nothing to lose, try to revert the partition the same way you stuffed it up.  go back to gparted and "accidentally" change the swap back into ntfs.

just a thought backed by no experience or concrete knowledge.

---

### Post by robtudor on 2006-07-16
Thanks - I think I'll give both of those ideas a go and see what happens.

I did think it might be terminal but I am hoping I can try a few things first!

---

### Post by dermotti on 2006-07-16
Ewww...g'luck on this one.

---

### Post by ch_123 on 2008-02-02
I know this is an old thread, but I found this problem as I had the same problem, and as I managed to fix it, I thought I should chime in... Maybe I can help someone else who gets this problem.

I decided to try installing Debian on my PC. Somehow, it turned my C: drive into a linux swap partition. When I tried to run windows, It gave an error about not being able to find "autochk.exe" and rebooted. I tried a few things, but what fixed it was to back up all the contents of my C: drive using a linux live CD, then I reformatted the C: partition as NTFS, and copied all the files back. Worked perfectly. :)

---

