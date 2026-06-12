---
title: "[SOLVED] apt-get install to a different partition"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by DBrocks on 2008-04-19
Hey guys. I have ubuntu SE installed on a Dell P3 (runs like a champ). However, it is only a 4 GB HDD. I've expereminted, and decided I want to run it as an FTP/File sharing server. I only have about 2GBs left on HDD1, and everything is configured perfectly. I am planning to pick up a 250 gb HDD. I want to add the 250 in as a Slave, because I already have all my stuff (samba, proftpd, etc) set up exactly the way I need to, and don't want to loose all my configs. However, after a while, I may run out of room on HDD1 using Apt-get install. So, my question is: How can I make Apt-get install to a different partition, rather then just "/". Is that possible? Or would it be easier to back up all my configs, and scrap the 4GB HDD? Thanks in advance! 

~Dan

---

### Post by zvacet on 2008-04-19
> How can I make Apt-get install to a different partition, rather then just "/".

I don´t think it is possible,because everything you install with apt-get or synaptic goes to the **var/cache/apt/archives **and that is on root partition.Backing up is easier option.

---

### Post by erlyrisa on 2008-04-19
fusermount

but it's not for the light hearted ....

I would test on a system you don't care about.

---

### Post by hyper_ch on 2008-04-19
you will have to copy different parts of the filesystem to the new harddisk and then mount it accordingly... BUT system-wide config files are stored in /etc.... so, unplug your current drive, nstall ubuntu on the new drive, plug the old drive back in and copy the /home folder and (parts) of your etc folder... to the new harddisk...

---

### Post by conscious on 2008-04-19
The bulk of installed software goes to /usr. So the solution to your problem seems to be to create a partition on the 250GB drive, move everything from your current /usr there and then mount that partition as /usr.

---

### Post by p_quarles on 2008-04-19
> **conscious said:**
> The bulk of installed software goes to /usr. So the solution to your problem seems to be to create a partition on the 250GB drive, move everything from your current /usr there and then mount that partition as /usr.
Yes, that method would be my best guess at a solution as well. As mentioned earlier, packages are placed in /var prior to installation, so you may want a separate partition (on the new drive) for that as well. A separate partition for /etc would likely be pointless. It stoes configuration files for virtually every aspect of the system, but these are small. My / partition (which includes everything but /home) has eaten up 5.2 GB, but /etc is only responsible for 16 MB of that.

---

### Post by stchman on 2008-04-19
> **DBrocks said:**
> Hey guys. I have ubuntu SE installed on a Dell P3 (runs like a champ). However, it is only a 4 GB HDD. I've expereminted, and decided I want to run it as an FTP/File sharing server. I only have about 2GBs left on HDD1, and everything is configured perfectly. I am planning to pick up a 250 gb HDD. I want to add the 250 in as a Slave, because I already have all my stuff (samba, proftpd, etc) set up exactly the way I need to, and don't want to loose all my configs. However, after a while, I may run out of room on HDD1 using Apt-get install. So, my question is: How can I make Apt-get install to a different partition, rather then just "/". Is that possible? Or would it be easier to back up all my configs, and scrap the 4GB HDD? Thanks in advance! 

~Dan

Use the LiveCD to make your Ubuntu partition bigger vie gparted.

---

### Post by p_quarles on 2008-04-19
> **stchman said:**
> Use the LiveCD to make your Ubuntu partition bigger vie gparted.
I don't think it's possible to make a partition larger than the hard drive on which it resides. ;)

---

### Post by DBrocks on 2008-04-19
Okay. Thanks SO much for all the help guys. I figured it would be easier to back up my config files, re-run apt-get, and restore my config files. So thanks for checking this out. It was a great help!

---

