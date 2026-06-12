---
title: "Install to external drive"
date: 2007-02-25
forum: Apple Intel Users
---

### Post by neutrino15 on 2007-02-25
Hello,

I am a long time mac user, and a linux noob. I have ran many linux distros under parallels or vmware for quite some time, but recently, I have wanted to try beryl under ubuntu and parallels does not support 3d graphics!

I have a gigantic firewire external HD that would be perfect for my installation.

I use a C2D macbook.. So I will not have my external HD at all times. I want the installation to ONLY AFFECT THE EXTERNAL. I don't want it to touch my OSX installation. I read that I may need a different bootloader (reefit?). I would like to stay away from that if possible. The built in BootX seems to have support for many filesystems.. 


I partitioned the external into 2 parts:

200gb Extended Journaled (osx backup)
20gb Unix FIlesystem (linux)

When I ran the live cd for 6.10, I found that it could not understand the unix partition, so I formatted it to ext/3.

When I continued, it asked me to specify a root directory.. I didn't know which one to choose!!! I shut down the computer and am now back in osx with 20 dead gb..


I still want to put linux on my external. How should I do this? I really don't want reefit. And will reefit understand if I unplug the external hd? Will it still let me boot to OSX?





Thanks You!
-Jordan

---

### Post by cocoia on 2007-02-26
Hey Jordan,

I've been a longtime user of other OS'es on my external drive with my Macbook Pro. rEFIt, although it sounds very involved, is a very lightweight utility to work with your EFI, which in turn allows you to do some system-specific stuff like keeping your partitions in order. It's entirely upto you to decide if you want to use it. In this case, indeed, it is not a necessity.

In order to make BootX aware of the Linux partition, it must be flagged as bootable. You can use the Ubuntu Edgy installer for this, because I -believe- it sets your root parition  bootable. I am not sure about this. It did work for me when I split a similarly-sized partition on my disk between root and swap filesystems (something you also need to do, you can do it in the installer, be sure to format it as linux-swap). Otherwise, you can use parted, from the Terminal. In your live CD, you can go to programs > accesories > terminal and type parted. If you type help or something similar, it will show you what you can do, as it can easily set flags like bootable from there. Let me know if this helps.

---

### Post by neutrino15 on 2007-02-26
That helped a little (knowing that I can do it). I sucessfully partitioned a 20 gb chunk to ext/3. Then, I get lost. The next screen has 3 options. It wants me to set a mount point, and then a drop down menu that has somthing.. I forget. The first row is set to "/".. Isn't this the root volume? Or is this just the root of the partition I am looking at...

---

### Post by cocoia on 2007-02-26
Well, at that point you can press back to the partition table, and resize your ext3 partition. Make about 2 gig free after it, and make the new space into a partition. Choose Linux-Swap from the dropdown. Then proceed again, this time, select the ext3 drive as /, and the last partition, the linux-swap, as swap. You can let the rest as is, and make sure you don't mount two partitions twice. You can leave things empty as well, as long as you have your swap and root selected.

Hope this helps!

---

### Post by neutrino15 on 2007-02-26
That helps a ton! Thanks!

Ill be trying it shortly!

---

### Post by neutrino15 on 2007-02-26
I posted this in a rEFIt thread as well..

I installed ubuntu on the partition I created. However, GRUB failed on install.. And rEFIt does not see anything becides MacOSX...

(should I put grub somewhere else bescides HD0?)

-Jordan

---

### Post by cocoia on 2007-02-26
> **neutrino15 said:**
> I posted this in a rEFIt thread as well..

(should I put grub somewhere else bescides HD0?)

-Jordan


I'm sorry, I assumed you read the same howto's I did. A stupid train of thought from my side.  
  

Here, I followed this howto for Edgy.. [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook"). you need the edgy installer CD for this, as refit doesn't work on Dapper. Make sure you have internet, and start from the Live CD. 

Once booted, download this:
[http://ftp.debian.org/debian/pool/main/r/refit/refit_0.7-3_i386.deb]("http://ftp.debian.org/debian/pool/main/r/refit/refit_0.7-3_i386.deb")
package and install it.

type:
```
sudo gptsync /dev/sda && sudo sfdisk -c /dev/sda 3 83
``` (sda3 being the third partition, choose the number here that is your root disk).  and do not hit enter just yet.!!


Now, you can install as you did before, only, when setup reads 'Copying files" you should press enter and the rEFIt utility will sync your disk tables.

Make sure you have done this before it reaches 94%, or you will have the same problem.

Also, the howto recommends using rEFit (on OS X). I would suggest it as well. Installing isn't much of a hassle, just make sure to read the readme.

---

### Post by neutrino15 on 2007-02-26
GAHHH

Thanks alot for finding that. It seems very complex (not for tonite) especially since my router (with wired ethernet) is under the desk in the other room... I am starting to think that maybe this is not worth it...

Anyway, that probably will help, so if I ever do this again (and I probably will) I will use it..


0Neutrino

---

