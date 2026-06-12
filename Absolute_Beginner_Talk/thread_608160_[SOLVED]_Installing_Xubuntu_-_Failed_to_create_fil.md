---
title: "[SOLVED] Installing Xubuntu - Failed to create file system"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by cincinnatus on 2007-11-09
I have Ubuntu installed on my computer, and I want to install Xubuntu because it's an older computer and I want to conserve resources. But when I tried to install from the Live CD, it gives me this error message:

"The ext3 file system creation in partition #1 of IDE master (hda) failed."

What do I need to do?

---

### Post by overdrank on 2007-11-09
> **cincinnatus said:**
> I have Ubuntu installed on my computer, and I want to install Xubuntu because it's an older computer and I want to conserve resources. But when I tried to install from the Live CD, it gives me this error message:

"The ext3 file system creation in partition #1 of IDE master (hda) failed."

What do I need to do?

HI I know from my experience that xubuntu will mount the partition that it is trying to format. If you have ubuntu installed already then just install the xubuntu desktop and you will have the same thing. In the terminal just use the command ```
sudo apt-get install xubuntu-dektop
``` then when complete log out and when you login in select the xfce session from the lower left hand corner and your there. Good luck! :KS

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by oilchangeguy on 2007-11-09
> **cincinnatus said:**
> I have Ubuntu installed on my computer, and I want to install Xubuntu because it's an older computer and I want to conserve resources. But when I tried to install from the Live CD, it gives me this error message:

"The ext3 file system creation in partition #1 of IDE master (hda) failed."

What do I need to do?

an easy way. do you have a 98 boot floppy laying around? if not head over to [www.bootdisk.com](www.bootdisk.com) and create one. then boot from the floppy, at the a:> prompt type fdisk. and follow the prompts to delete the partition. then try your xubuntu cd.

---

### Post by cincinnatus on 2007-11-13
Okay, with the computer I'm using, I have to lug it upstairs whenever I want to connect it to the internet, so I decided to use fdisk to delete the partitions. Now I messed everything up. (don't worry, though, I didn't have anything important on that computer anyway. It's the computer I can do anything I want with).

I deleted the primary partition, but when I tried to delete the Extended Partition, it says "Cannot delete Extended DOS Partition while logical drives exist." When I try to delete the logical drives, it says "No logical drives defined".

Hoping that deleting one partition would be good enough, I tried booting with the Xubuntu CD. It got to the startup screen okay, but when it tried to load up Xubuntu, I got a bunch of error messages. Now when I try to boot from the Xubuntu or the Ubuntu live CDs, it fails to load anything and spits the CD back out.

And of course, since I deleted the partition, the hard drive won't boot. There was a trace of GRUB left though. It said GRUB loading, please wait... then gave me "Error 22"

Then I typed "fdisk /mbr" in at the Win98 disk prompt (I got the idea [here]("http://www.neowin.net/forum/index.php?showtopic=292614"), but whether or not it was necessary I don't know). It got rid of grub, but the computer still spits CDs back out at me.

Since the CD wouldn't boot, I tried SmartBootManager, but all it gives me is "SBMK Bad!"

Please tell me if you have any suggestions for what to try next.

Thanks.

---

### Post by cincinnatus on 2007-11-21
Okay, it works now. I ran DBAN to completely wipe the hard drive, then ran the Xubuntu CD, and it installed.

---

