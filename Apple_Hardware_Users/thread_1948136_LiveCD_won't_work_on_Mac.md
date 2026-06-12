---
title: "LiveCD won't work on Mac"
date: 2012-03-27
forum: Apple Hardware Users
---

### Post by Maecilla on 2012-03-27
Hey guys

I am at my wit's end here trying to make a Ubuntu 11.10/OSX 10.6.8 dual boot on my MacBook Pro.

I press C to boot from CD, then I get to the welcome screen. 
Whether I choose to test out Ubuntu or do an install,  the same message always comes up "Unable to find a medium containing a live file system".

I have tried making different partitions on my Mac HDD but to no avail. I even tried an old Ubuntu 9.1 CD I had lying around with the same issue arising.

I did install rEFIT but haven't used it so far since pressing C was enough to get me to the Ubuntu menu.

Documentation I have read relates this problem but mostly with PCs and doing stuff to the BIOS. So I am still looking for a solution! Any help?

---

### Post by ijumpship on 2012-03-27
never had any success with anything greater than 10.04

Try this
ubuntu-10.04.4-desktop-amd64bit version.A lot of things do not work though. like wifi.test it

---

### Post by Maecilla on 2012-03-28
> never had any success with anything greater than 10.04

what, seriously? I noticed the bug had been reported but thought it had been resolved by now.

As I said I tried using Ubuntu 9.10 as well with the exact same result.

Anyone got any ideas on how to solve this? :confused:

---

### Post by msarro on 2012-03-28
This worked for me 2 days ago with 11.10, amd64

You will need a USB stick with approximately 700M of free space.

Download the Ubuntu ISO.
Open system information and select the USB disk. Make note of what it says the disk number is (disk0 or disk1).

Open a terminal window and type:
dd if=/path/to/ubuntu.iso of=/dev/diskN bs=1M

Once that is done, reboot the mac (keeping the USB attached) and press/hold the C button to start booting off of the CD. You should no longer get the "unable to find live filesystem" error since it'll find the filesystem on the USB.

---

### Post by Kopkins on 2012-03-29
^^ This is what worked for me. 

I've done that for 11.10 and 11.04.

I've also installed 10.04. 

For all of them, however, my wireless (broadcom 4331) has not worked. There are some tutorials about how to install drivers to make it work, but for me they haven't worked entirely yet. In 11.10 and .04 ethernet cables work, and I can get it to recognize wireless networks, but it still can't connect to them. Just something to be aware of. Also, in 10.04 my computer wouldn't even recognize ethernet wire. 

Best of luck,
Kopkins

---

### Post by skylen on 2012-03-31
I have a 2009 MacBook Pro and found that two things are required to boot the Ubuntu CD (note I have not had the USB stick work well, so I use a real burned CD or DVD):

1. You must use the 'amd64+mac' ISO download.  Note the PLUS MAC on the end.

2. You must hit F6 at the ISOLINUX boot menu to bring up the boot options, arrow down to **nomodeset**, hit Enter to check the option, hit Esc to close the options menu, then Enter to boot.  Without the nomodeset option, my system hangs immediately when starting the Linux boot.

---

### Post by mode7 on 2012-04-02
Just to add, on my **Macbook Pro 8,1**, using the CD + pendrive combo works fine. (I burn the image to disc, then put it on the usb drive with unetbootin)

However, using the 64-bit Mac install image resulted in the filesystem error. Using normal Ubuntu ISOs allowed a proper boot and install, just in case anyone was confused why the Mac images may not have been working for them.

Also, I do not seem to need to change any boot options. Again, this is for *late 2011 MacBooks*.. use standard Ubuntu ISOs, and default boot options. I was also able to boot Xubuntu and Kubuntu images just fine with the CD+pendrive trick.

---

### Post by hughr2005 on 2012-04-04
I think I got 10.04 running once, on a 2008 MacBook Pro, 2.66Ghz processor. Unfortunately, there was some problem that meant I couldn't boot into OS X any more, so I had to wipe the hard drive and restore from backup. Since then I've just virtualised. I realise it won't give ubuntu all the power you might need, but for what I do (software development, hosting servers, and scripting mostly) VirtualBox has worked a treat. I do all the really processor heavy tasks in OS X.

---

