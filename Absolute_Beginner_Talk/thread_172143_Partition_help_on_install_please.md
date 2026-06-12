---
title: "Partition help on install please"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Pelham123 on 2006-05-08
Hi

I've read a few guides about partition setup on install and I'd like experienced users to say what they use....

1)If you use just a '/' and swap partition are there any advantages etc? Or..
2)What are the benefits of having separate partitions for usr, home, var, tmp etc?

Just getting kindof confused

---

### Post by aysiu on 2006-05-08
[QUOTE=Pelham123]
1)If you use just a '/' and swap partition are there any advantages etc? Or..[/quote] No real advantage that I can think of. > 
2)What are the benefits of having separate partitions for usr, home, var, tmp etc? It's always a good idea to have a separate /home (or at least a separate data partition--if you don't mind redoing your settings), but having separate /usr, /var, /tmp and other partitions may chop up your hard drive too much.

If you have something like a 20 GB hard drive, having five partitions for various folders may give you too many size limitations (Uh oh. I ran out of space in my /usr folder. Now I have to resize it.).

The advantage of having a separate /home or data partition is the ability to reinstall Ubuntu or do a fresh install of a newer version of Ubuntu and retain your data and settings.

---

### Post by Sef on 2006-05-08
> 1)If you use just a '/' and swap partition are there any advantages etc? Or..
2)What are the benefits of having separate partitions for usr, home, var, tmp etc?

A single Gnu/Linux system should have 3 partitions:  / (root), /home, and swap.   The home partition is handy to have in case your operating system fails for some reason, (e.g., dist-upgrade, something gets messed up.)  Also if you do a clean install, you can keep your home partition and thus your documents instact without having to reinstall them.

---

### Post by Pelham123 on 2006-05-08
Thank you both for the replies...its pretty much what I thought but it's always good to have it in black and white.

Many Thanks!

---

### Post by Herman on 2006-05-08
Hello, Pelham123, 
Here's my opinion, I prefer just a swap area and / for several reasons.

Directories (folders) can expand and contract exactly as required from moment to moment and there's no space wasted. 
Partitions are more or less rigid and fixed in size. For a multiple partition install you need to be able to plan ahead and guess how much room you'll need for each partition and allow a little extra spare room for future growth. This means some space must be wasted, or you risk running into space limitation problems down the track. Even though we do have new software now that can handle it, it's still a chore to resize a partition that's too big or too small when your needs change or you realise you made a mistake during your install.
 Single partition installs are nice and neat and tidy, and simple. If You decide to multiple boot later on, there will be far less confusion about which partition belongs to which operating system.
When you have a single partition install, it's simple to make a copy of the whole partition, (resized smaller temporarily), and paste it to the end of your hard-disk as a back-up copy (complete with added software, tweaks and settings, but without too many files). This makes the idea of a seperate /home partition almost redundant.
Modern journalled file systems like ext3 are more stable than the older systems so it's highly unlikely you'll ever loose data for a filesystem problem, so that reason for multiple partition installs is now gone by the wayside.

A single partition install is all the average desktop home user or business person needs. Multiple partition installs might be necessary for special purposes. The majority of people attracted to multiple partition installs probably do it for an experiment, for the novelty value and to impress freinds, not for practical reasons. It's okay to experiment and have fun with Ubuntu if you want, but I think you'll eventually find the single partition (and swap) install will serve you well. 
At least that's what I think.  Good luck with your install.   :D Regards, Herman

Edit: Hello, Aysiu and Sef, I'm awfully sorry to be contradicting you two good fellows. No disrespect intended. This would make a great subject for a debate wouldn't it?

---

