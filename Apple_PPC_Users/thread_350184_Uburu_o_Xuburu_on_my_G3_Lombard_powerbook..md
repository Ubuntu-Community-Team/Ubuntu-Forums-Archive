---
title: "Uburu o Xuburu on my G3 Lombard powerbook."
date: 2007-01-31
forum: Apple PPC Users
---

### Post by nhylo on 2007-01-31
Hi:
my powerbook have 10.4.8 (OSX) install in a 37 GB harddrive with 26 GB free. I like to install uburu o xuburu have the live disc both work perfect. So you may ask what is the problem?. Well I don't want to lose or have reinstall OSX and when I try to install uburu/xuburu I have the feeling all will be destroy and I will lose my data. Is that correct and if is not correct (hope) how should do this and how you boot from each one when you want it?

Thank You 
nhylo

---

### Post by linear on 2007-01-31
You asked a fairly common question: how do I dual boot?

These are general instructions, your experience may vary depending on your Mac model:

[https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC)(for Breezy, but still valid).
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

0. Read up in the PPC forum on any model specific quirks.
1. Back up the OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition the disk. Make two partitions, leave the first as free space and use the second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---

### Post by samden on 2007-01-31
I am sure it can be done without reinstalling OSX, but it may be simplest in terms of disk partitioning to just reinstall OSX. This is how I did it and it was easy to find instructions - I ended up doing it a couple of times due to a mistake, and it might be easy to make a mistake and wreck your current OSX install anyway.

Even if you do find out how to do it without reinstalling OSX, it might be an idea to be prepared to reinstall it anyway - just in case something goes wrong.

Btw - make sure you make a shared partition, in hfs+ format - very handy. Plenty of instructions if you do a forum search.

---

### Post by nhylo on 2007-01-31
linear Thank you that about all i need i wish i could be as help full as you execellent responce  may be you could help me with another :
This one was posted by me few days ago I also have a minimac coreduo so with intel you can use parallels (very convenient) well my monitor resolution is 2048 x 1536 but i prefert for uburu 1920 x 1440 that fit a bet smaller than my desktop as my window is alowing me to send the page to the dock via yellow bottom instead of using the parallels full screan and rotation ( no my taste) so since saturday i have been reading a lot of post and wiki help and work on the console (mac/name) tiping all this sudo, sudo, sudo....
But i dedoct that the problen is a video car from intel Name       Intel GMA 950   that look like is not install or is not reconize and i will be very happy closing this case also as I have done with the installation thank to you and sanden so please if you can help me on that I will apreciate.

Once again thank you 

nhylo

---

