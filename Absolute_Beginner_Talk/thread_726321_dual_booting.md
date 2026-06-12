---
title: "dual booting"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by RyviusRan on 2008-03-16
I have installed ubuntu first but decided to have windows xp media center 2005 installed. When I put in the cd for windows to boot from it loads up perfectly and asks to write a new registry. 

I type yes for it and so it reboots but just goes back to saying the same thing without any progress. One the command prompt one of the lines i noticed said error invalid parameter.

does anyone have a tutorial of dual booting, but with windows after ubuntu?

---

### Post by tommcd on 2008-03-16
Unless you have a primary partition reserved for Windows you will likely have to wipe the disk clean and start over. Boot up the Windows install CD, delete the existing linux partitions, and create a partition for Windows at the beginning of the disk and install Windows to that. This should leave enough unallocated space for linux partitions.Then boot up your Ubuntu CD and create partitions for Ubuntu in the unallocated space and install Ubuntu on that. Windows should be installed first in a dual boot set up like that.

---

### Post by Patrick-Ruff on 2008-03-16
you could always back up and try resizing your existing windows partition, there's a good chance it wont kill all your files, but if it does you have a backup ;)

---

### Post by drubin on 2008-03-16
There are TONS.. TONS. 
Here is one.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Shouldn't be a problem. I do have one question though, You said you have Windows Media Center installed? Is there a reason for that, If there is you might want to take a look at 
[MythBuntu]("http://mythbuntu.org/") Might be more what you are looking for.

---

### Post by tommcd on 2008-03-16
> **RyviusRan said:**
> I have installed ubuntu first but decided to have windows xp media center 2005 installed. When I put in the cd for windows to boot from it loads up perfectly and asks to write a new registry. 

I type yes for it and so it reboots but just goes back to saying the same thing without any progress. One the command prompt one of the lines i noticed said error invalid parameter.

does anyone have a tutorial of dual booting, but with windows after ubuntu?

Do you already have Windows installed or are you trying to install it? When I read your post I thought you were trying to install Windows after Ubuntu. Sorry if I misread your post.

---

### Post by alzie on 2008-03-16
You can try here :  [http://everything2.com/index.pl?node_id=1261544](http://everything2.com/index.pl?node_id=1261544)

Its the only instruction I could find to add a Windows OS to an existing Linux OS.  I'd be sure to back up everything first though.

I hope this helps

---

### Post by jan quark on 2008-03-16
or try this site:

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by RyviusRan on 2008-03-16
well I have ubuntu already installed and I was reading a tutorial with installing windows xp when you already have a linux OS installed. 

I created another partition and did everything it said up until it said install windows xp

link here:  [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

and I also noticed when booting the windows xp installer up and get to the command prompt right before it asks for to rewrite registry key it says    C:/ not ready

I think this tutorial says it will use windows under F:/ which could be the problem. I was wonder if there was a way to make it so it notices the F:/  instead.

---

### Post by TLDigital on 2008-03-16
Try Super Grub.  

[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

I am a nood also, but I used it to repair my Grub to duel boot Unbutu and Vista.

---

### Post by RyviusRan on 2008-03-16
i think when I made another partition I somehow did something wrong becuase it isn;t recognized when i reboot...but this tutorial seems acurate.

oh and I already have a grub disk but thanks I will look at this one too

---

### Post by bumanie on 2008-03-16
If you read this site, it may help (there is a lot to read though)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It has heaps of info. on grub and dual booting etc.

---

### Post by RyviusRan on 2008-03-16
the problem I see is that when I get to the menu where it shows my OS it shows 

ubuntu and recovery mode and a memtest

I have partitioned an extra part for windows and it is not recognizing it.

I am asking if any knows how to make the new partitioned space recognized, I already have it in the right for mat ntfs for windows. But it is not showing up on the boot menu.

---

### Post by jken146 on 2008-03-16
First, you need to install Windows.  Then you should restore GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by RyviusRan on 2008-03-16
When I go to boot the windows installer cd it will ask to rewrite the registry key

I select yes

but it says cannot find the specified registry key or value.

anyone know what that means?

---

### Post by RyviusRan on 2008-03-16
bump

---

### Post by RyviusRan on 2008-03-16
bump

---

### Post by tommcd on 2008-03-16
You won't be using grub to boot the ntfs partition until after Windows is installed. I have reinstalled Windows after installing Ubuntu. (In my case I deleted all the partitions and started over).  Set you computer's BIOS to boot from CDROM drive. Boot up the Windows install disk and proceed through the install. When you get to the partitioning part choose to install Windows on the ntfs partition you have reserved for it. Then reinstall grub to the MBR after Windows is installed.
Is the ntfs partition you have reserved for Windows a primary partition? Windows needs to be on a primary partition.
If you are having problems then the easiest thing in the long run might be to delete all partitions with the Windows install CD. Install Windows first. Then install Ubuntu. This will take a couple hours at most. If you have a separate home you could probably leave that partition alone so your data won't be lost.

---

### Post by RyviusRan on 2008-03-16
ok I have windows running and ubuntu running but inorder for one to run I have to boot up the grub cd and switch to boot the partition that the OS is on.

is there a way I can have them both show up in the boot screen when I load the computer?

---

### Post by RyviusRan on 2008-03-16
I tried using 

sudo gedit /boot/grub/menu.lst

and I entered

title                         Windows XP
root                        (hd0,1)
makeactive
chainloader             +1

it shows up now in the boot screen, but when I select it, it says something like incorrect path.

any idea how to have them work both on the same boot screen?

---

### Post by tommcd on 2008-03-18
If you installed Windows first, then Ubuntu, you would not have this problem. When the grub menu comes up you should be able to boot Windows or Ubuntu. If this is not the case, then the easiest thing to do is reinstall grub like this:
Boot up the Ubuntu live CD. open a terminal and do:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
EDIT: Is windows on the first partition on the drive? If so the grub entry should probably be (hd0,0).

---

