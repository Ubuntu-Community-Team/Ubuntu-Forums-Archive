---
title: "How to create partitions"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-02-23
Well, I'm very new to this linux thing, and I need to know how to create partitions for a multi boot. I do know how much space to allocate, but how to actually create the partition is what I do not know.

Thanks for your help.

---

### Post by nickoli_02 on 2007-02-23
You can create all sorts of partitions with the partitioner that comes with the Ubuntu installation CD. The desktop CD uses GParted, and the alternate CD uses a text based tool. Either way you'll be able to create all the partitions you need :D

---

### Post by floke on 2007-02-23
If the LiveCD works for you then these are the steps to do it all...

(1) Boot into Windows. BACKUP ALL YOUR IMPORTANT DATA (Nothing has ever gone wrong for me and I've done this more than a dozen times - but you can't be sure...). Then defrag hard drive and run a disc scan for errors.
(2) Check C drive to see how much space left you have on it - you will need around 5Gs at least for Ubuntu (it can run on less but you'll need space for your docs etc.) - i.e. work out how much space you want to give to Ubuntu.
(3) Reboot LiveCD - open GParted - System/Admin/Gparted
(4) Select shrink partition option - and enter the values that you want to shrink your windows drive to - e.g. you might have a 60G HDD, and might want to have 30G for Windows and 30G for Ubuntu.
(5) Click apply - and then (and this is now the point of no return) - click the option (I think its called this) for 'perform actions' (though it might be apply again...)
(6) GParted will then shrink windows. Exit GPARted
(7) Click the Install icon on the desktop
(8) Follow instructions on screen (location , name etc.) - and when asked, select the option for 'install on largest amount of available free space'.
(9) Wait for Ubuntu to install.
(10) Reboot and enjoy!

Any problems then just post back.

Good luck.

---

### Post by Luk0r on 2007-02-23
nickoli_02 is right, just ensure you run a 'chkdsk /f' in Windows before you do anything, or you can mess things up.

---

### Post by antoz on 2007-02-23
Provided there is enough free space and you defrag the drive first the installer will shrink your patition if you select the second option "use largest free space" I think it makes it about 50-50 but you can use the slider to change that. I have done that the first time I tried to install and accidently made my windows partition too small ( I aborted the instalation because I got cold feet) No harm came to my computer I just used the live Cd again to resize the partition and it all worked out OK. 
Other then that I am a greenhorn too as far as Ubuntu is concerned, so I don't want to give you any more advice.

---

### Post by Aurora Borealis on 2007-02-23
Thank you all for your posts. I know how to save regular word processing files; is there a way to save all my bookmarks and everything else, too? Also, what does it mean to defrag the hard drive, and how do I accomplish this?

---

### Post by floke on 2007-02-23
Not sure about bookmarks etc.
To defrag means to defragment - you have to, in Windows, go to system tools (I think)  and select a utility called something like 'defragment' - if you use XP you then have to scan the drive and defragment it. Basically the windows file system (NTFS for XP) splits files up around the hard drive - i.e. fragments them (something that the Linux filesystem, ext3, is extremely resistant to). You should defrag your HDD every 6-8 weeks normally in windows to clear up space and improve efficiency.

---

### Post by Aurora Borealis on 2007-02-24
Awesome-thanks!

---

