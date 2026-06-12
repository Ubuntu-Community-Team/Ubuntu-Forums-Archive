---
title: "Hard Drive issues for an intermediate user"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by travist120 on 2007-04-03
Hi! I have been having a problem with my hard drive and I am done trying to solo my way through it and actually ask for some help. 

My friend gave me a desktop computer with an 80GB harddrive and 512MB of RAM, I'm not going to get into details, but all I know is that the copy of windows that was on the computer was an illegal copy cause I can't upgrade to SP2. I'm totally fine with that, it's just the hard drive that concerns me. I am a semi-noob to linux, I have the general gist of everything that linux is, it's just that I am so used to windows, that when I wanted to learn linux I had problems. Well I decided to take the soft easy route and try Ubuntu. Boy, did it hurt. When I try to install Ubuntu it gives me an error saying that there is a bad sector on my hard drive. It told me to reboot into windows and run CHKDSK to fix it. I tried, it said no errors. I downloaded and burned and checked another copy of ubuntu, same deal. (I can't put another hard drive in because the power supply on my computer is funky and won't power a secondary harddrive) I then took matters into my own hands and found GNOME Partition Editor within the applications of Ubuntu. I ran a test on a USB exerternal harddrive and found that it can partition hard drives, its just that one hard drive that does it. I found the commands that GNOME Partition Editor (ntfsresize) was using and ran them in the Terminal. I used the no error option(is that right?) and tried to free up 20 GBs of space. When it finished, I looked back in GParted and lo' and behold! THE AMOUNT USED IN THE NTFS PARTITION DOUBLED AND DID NOT SHRINK! So now I am stuck. Hoping and praying that I can do this. (I'm really stubborn) (It is necessary that I have a windows and that I have all of my files.) So now I come to you and ask for your help.

---

### Post by confused57 on 2007-04-03
I'm sure you're aware that resizing partitions "can" be a dangerous operation to perform and could possibly render Windows unbootable.  With this being said, you could try downloading the gparted live cd(30 mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it has a newer version of gparted than the Ubuntu live cd and reportedly does a better job resizing NTFS partitions.

Make sure to defrag your Window's partition before trying to resize it.

I'm no expert on computer hardware, never had to repair a bad sector on a hd, so I can't help you there.

---

