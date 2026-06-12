---
title: "Help with Win XP re-installation."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by Cyraxzz on 2006-06-29
I introduced my friend to Ubuntu Linux and the entire Open Source community, he loves it, and what's to switch immediately, but he want's to keep his XP partition only because of one game, that is not available on Linux nor can it run under wine. 

So, i am going to install Ubuntu for him, and he also want's to delete XP and reinstall it, I am planing to do that first, but i have one question:

During the XP installation, where do i chose my desired size of the Win partition?

When i used XP, and was going to install Ubuntu i could not keep both operating systems, simply because the Windows partition took all the space. And I could not re-size the XP partition for some reason, i tried, but it did not seem to finish it.  

And in the future where do switch between operating systems?

Any help is deeply appreciated.

---

### Post by Maggot on 2006-06-29
Install XP first. At the beginning it asks what disk, how much space you want to use.  After installing XP, install ubuntu. Do a manual partition when asked and allot the remaining space to ubuntu/swap or whatever you want.

Personally, I'd boot into ubuntu, fdisk my XP and linux partitions, then install XP followed by linux. I'm more comfortable with linux partitioning than windows though.

After installing Linux, the bootloader GRUB will allow you to choose between ubuntu and XP.

---

### Post by catlett on 2006-06-29
It's easiest to make your partitions ahead of time. Gparted live works great. It is a live cd with the partitioner application gparted on it. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Make 4 partitions. 1 for xp. Make that ntfs. 3 for ubuntu. 1 formatted as linux-swap, the other 2 as ext3.
XP can live on 5 gb. The install is around 2 to 2.5gb but that is just a base install. If he has a 80 to 100gb drive I would give XP 10gb. This will give him the ability to add whatever he wants and room for a dvd and games.
For ubuntu. swap rule of thumb is twice ram i.e. 256mb ram = 512mb swap./ The other 2 should be root and home. Root only needs 5gb. Home should be whatever is left. Root when there is a home partition will opnly hold the system files. Home will hold all your personal data etc. Of course you could make root biger but I never wente over 3.5gb.

So make the 4 partitions. Install XP. Then install ubuntu. Just choose to manually edit the partition table. It will give you the ability to label each partition. Just make the 512 swap. The 5gb make "/" root ( / is the label for root) and finally make the other one home.

---

