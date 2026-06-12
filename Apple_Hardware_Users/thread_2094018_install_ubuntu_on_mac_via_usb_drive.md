---
title: "install ubuntu on mac via usb drive"
date: 2012-12-12
forum: Apple Hardware Users
---

### Post by mideast on 2012-12-12
Oh, woe is me. Because it can't be that hard, and I'm not normally this dumb, but its 4hrs and my head is hurting. 

I've a 2009 Mac, currently running Mountain Lion, 10.8.2. My CD drive has long not been part of this world. I've already downloaded Ubuntu iso, partitioned my disk and installed rEFIt, but I can't seem to make a bootable USB image. I've been through the detailed instructions here:

[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

but they don't work for me. And I'm no slouch with Bash or the command line. Still can't get any joy. 
Every step of the procedure completes fine, but all I get when rebooting is 'missing operating system'.

Ah huh. I've already been down the sync partition tables route. Several times.

There must be loads of people that've been through this? The searches just keep taking me to the same useless pages, the one above and this one:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

They don't help. Oh woe is me.... :frown:

---

### Post by mideast on 2012-12-13
no advice?

---

### Post by coffeecat on 2012-12-13
*Thread moved to **Apple Users**.*

> **mideast said:**
> no advice?

I've moved this to where it is more likely to be seen by people running Ubuntu on Apple hardware and able to help you. If you don't get a response, it's OK to bump your thread, but not more than once per 24 hours, please.

Just a thought, and I know it doesn't answer your question, but have you considered running Ubuntu in a virtual machine such as VirtualBox within MacOS? This is what I did for a time with my 2006-era Mac Mini running Leopard/Snow Leopard. It was leisurely but usable and your 2009 Mac will be much more capable than my Mini.

Good luck!

---

### Post by pindar on 2012-12-13
OK, before someone jumps in and complains that your post is long on whining ("woe is me") and telling us how awesome you are ("no slouch with Bash or the command line"), but short on useful information (2009 Mac: which model?), I would suggest you try the following two methods:

[LIST=1]
[*]The one method that I have found pretty reliable for most of my Mac hardware is described here: [http://www.devslashzero.com/node/160]("http://www.devslashzero.com/node/160"). Steps are fairly easy to follow; this has worked for me most (but not all) of the time.
[*]Another method would be booting from a Ubuntu iso file which you copy to a USB disk or USB stick. Since you say you know your way around on the command line, here's a very brief rundown:[LIST]
[*]Partition your USB drive or stick in OS X. Give it ONE partition, formatted as FAT. Choose GPT partition table. This will actually create two partitions: a small (~200 MB) system partition + the rest of the disk in FAT as data partition.
[*] Next step will need a computer running linux: install grub-efi to the small system partition and set the "boot" flag.
[*] Copy the ubuntu iso file of your choice to the data partition. 
[*] Boot your Mac up and hold the "option" key. You should be able to boot from your USB disk. At the grub prompt, drop to a command line and boot the iso via the "loopback" command (google is your friend here).
[/LIST]
[/LIST]
I've successfully used both methods. HTH!

---

### Post by dmuos on 2012-12-17
Hope your problem is solved by now.

If not, would you care to ellaborate on

1-which ubuntu version (edition and bits) you are trying to install use as Ubuntu Live

2-whether it is the iso downloaded from ubuntu.com

3-the 2009 Mac model (About This Mac > More Info... for example)

I have used the instuctions suggested in ubuntu website (identical to last option of your first link), and have had no problems creating bootable USB in different Ubuntu editions with 2007 Mac Mini or 2009 Mbook Pro.

---

