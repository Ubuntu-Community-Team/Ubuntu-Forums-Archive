---
title: "Dual boot.  Two HDDs.  Ubuntu on slave?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2006-06-11
Hello.  I have no experience what so ever with Linux but would like to give Ubuntu 6.06 Desktop a whirl on my PC.   

My computer has hdda 120G master and hddb 40G slave.  The plan so far has been to follow this tutorial by Jason Faulkner and keep Ubuntu and XP on separate drives.  
[http://www.pcmech.com/show/os/903/]("http://www.pcmech.com/show/os/903/")
I was all set to follow this tutorial but then things changed.  The install menu on the 6.06 LiveCD has GParted instead of the text based installer.  Having never partitioned in any OS, and now that it looks different to the tutorial, I’m not sure I’m capable of doing this unassisted.  

What kind of result would I get if I was to select install on hdb and then select “Erase entire disk: IDE1 slave (hdb) -40.0 GB”  and let Ubuntu installer do the rest?  
Would I get dual boot without interfering with my XP install?  

My other option I suppose might be to download the alternate install CD.  Does this version of  the CD have the same installer as the tutorial?  

I hope my questions are basic and easy to answer.

Robert.

---

### Post by _simon_ on 2006-06-11
as long as you select the drive WITHOUT XP on to install then you should be fine..

---

### Post by glotz on 2006-06-11
Well, that'd obviously wipe your slave and install onto it. The default install makes 2 partitions, / and SWAP if I remember correctly. That should result in working double boot with zero extra effort, and should something go wrong, you can always get back to windows by "repairing" mbr (crudely overwiting grub with windoze booter resulting always in working windoze and non-working anything else)

Don't bother d/ling another cd if you've got one allready. Dunno if it would have a command line interface installer.

Try it, there's nothing you can lose.

---

### Post by Drakkor on 2006-06-11
Just did it on my 2nd drive and it works fine,grub gives you a selection on boot so you can either select Ubuntu or Windows XP.

---

### Post by confused57 on 2006-06-11
This may be an option for you:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)

See these sites for dualbooting screenshots:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=Dualboot)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by alphaomega on 2006-06-11
I am running Dapper on a 20GB Slave with winblows on my 40GB master. Breezy installed fine and Dapper well, was way easier. Install Grub and there are no worries. 

Just pick the slave drive when installing, install grub and off you go.

---

### Post by Gyrotwister on 2006-06-11
Thanks for the fast replies.  

There has been no mention of grub in the install process so far.  I’m using the most recent LiveCD, not the Dapper beta.  
I'm expecting dual boot to happen automagically.  Please stop me if there is something I need to know about this before proceeding.  

After dipping my toes in the water again I have another query.   
Chose to erase my entire hdb, then this message came up.

The following partitions are going to be formatted:
partition #1 of /dev/hdb as ext3
partition #5 of /dev/hdb as swap

Is this ok?
What about partitions 2, 3 and 4?

---

### Post by confused57 on 2006-06-11
[QUOTE=Gyrotwister]Thanks for the fast replies.  

There has been no mention of grub in the install process so far.  I’m using the most recent LiveCD, not the Dapper beta.  
I'm expecting dual boot to happen automagically.  Please stop me if there is something I need to know about this before proceeding.  

After dipping my toes in the water again I have another query.   
Chose to erase my entire hdb, then this message came up.

The following partitions are going to be formatted:
partition #1 of /dev/hdb as ext3
partition #5 of /dev/hdb as swap

Is this ok?
What about partitions 2, 3 and 4?[/QUOTE]

Partition #1 is a primary partition, you can have up to 4 primary partitions.  The swap partition #5 is a logical partition...this is normal.  Grub will automatically be added to the Windows mbr, where you can select which OS to boot during startup.

---

### Post by Gyrotwister on 2006-06-11
It worked!:p  

I can boot to Ubuntu on hdb or XP on hda.  

Thanks for the support.

---

