---
title: "Can't boot into Grub from rEFIt, any help would be appreciated!"
date: 2013-06-11
forum: Apple Hardware Users
---

### Post by nknize on 2013-06-11
Hello Mactel experts!  I'm hoping you can help me out of a bind.

Here is the configuration:

OS: Ubuntu 12.04
Mac: MacBookPro8,3

Here is the situation:

1.  I've held off on installing any updates for the past month (this included kernel updates).  Today I decided, what the hell, I need to update.  After downloading and installing all of the updates (including the latest kernel) I was immediately presented with a message saying: /boot is almost full.  124MB remaining
2.  I proceeded to remove old kernel versions using the first answer on the following post [http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot](http://askubuntu.com/questions/89710/how-do-i-free-up-more-space-in-boot)   I was very cautious to triple check my actions and remove only the unused kernels that were **below** the currently loaded kernel version (which was obviously below the latest updated version).
3.  I rebooted the machine, selected Ubuntu from the rEFIt menu, and was presented with the dreaded blank screen with flashing cursor.  No GRUB love...

My guess is its trying to load the updated kernel version that failed to properly install because of low disk volume?? (not sure, just asking the experts)

The "good news" is, I've kept my partition organized such that everything is compartmentalized, e.g.:

/boot
/root
/opt
/home
/swap

My question is: What are my options?  How do I revert or reinstall the kernel so I can boot back into my working ubuntu?

Thanks so much in advance for all of the help!


[B]******* UPDATE ******
[/B]Conversation moved to: [http://ubuntuforums.org/showthread.php?t=2152378](http://ubuntuforums.org/showthread.php?t=2152378) 
*************************

---

