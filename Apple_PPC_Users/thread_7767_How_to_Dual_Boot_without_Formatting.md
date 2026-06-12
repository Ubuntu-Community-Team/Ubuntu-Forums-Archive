---
title: "How to Dual Boot without Formatting"
date: 2004-12-10
forum: Apple PPC Users
---

### Post by Khuffie on 2004-12-10
Yes! It works! I just installed Ubuntu on my Powerbook G4, got it to dual boot with OS X without reformatting. You will need to resize the partition of your computer, unless you have an extra drive (not possible in a Powerbook), in which case you can just install Ubuntu.

Don't worry. It's pretty easy. I'm not much of a Linux geek (in fact, I'm a n00b) and I got it to work perfectly. Here's how, step by step:

1. **Backup your data!** Resizing partitions is a risky process and you could lose to risk all your files. With that said, I did it just now and it worked fine! Also, make sure you have some free space on your hard-drive for the Ubuntu partition.
2. Get your hands on a copy of iPartition.[iPartition](http://www.coriolis-systems.com/iPartition.php) 
3. Follow the instructions in the Help file about how to create a BootCD. Make sure you follow them closely, as you need to authorize iPartition to read your boot disc first. This takes a while.
4. Pop the CD into your tray, hold the C button and reboot your machine.
5. Eventually (it takes a while to load) you'll see a Finder window. Load up iPartition, and select your default hard drive where OS X is installed. Click on Partitions.
6. You should see a pie chart showing the partitions on your hard-drive. Click on the main partition (assuming its the only one you have). It should move away slightly, and you'll see two arrows, one of which has a small white dot next to it. Grab that dot, and resize the partition. Note the free space info on the side. I left a 20 gig partition for Ubuntu (although you can probably go for a smaller one). When you're done, click on commit. 
7. Restart into your normal OS X (just to check if its still working :)). Put in your Ubuntu CD, and restart, again holding C.
8. A bit into the installation process, it'll ask you about partitioning. Hit 'manually edit partition table' (something to that effect :)).
9. Select the partition that says FREE SPACE next to it (sometimes there's a small 100 meg one, ignore that, make sure you select the one that you just freed up). Hit enter
10. In this set of options, select "automatically configure partition" (or something to that effect. Accept the next couple of screens.
11. Watch as the installation goes by. Grab a coffee or something :).

Once the installation is complete, Ubuntu will be your default boot. However, before it boots, you have a short timeframe in a menu where you can hit L to boot into Ubuntu, hit X to boot into OS X or hit C to boot from CD.

Enjoy! Hope this helps...if you have any trouble, let me know.

Now, to figure out this whole Linux thing (as I said...I'm a n00b ;)).

---

### Post by dkitty on 2004-12-11
8) Schw33t.

---

