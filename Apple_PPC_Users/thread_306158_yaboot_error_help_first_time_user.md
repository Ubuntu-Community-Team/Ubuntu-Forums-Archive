---
title: "yaboot error help first time user"
date: 2006-11-24
forum: Apple PPC Users
---

### Post by JesseQ on 2006-11-24
I have been trying to install ubuntu on my g4 It has a 1 Ghz sonnet processor and 512 ram.

I can boot the live cd.  I choose install to the master HD with the full format option.  after the lengthy process I choose to restart into my fresh OS install.  I take out the live cd and get the "l" or "c" option for linux or CDROM. it defaults to "l" and the boot: prompt appears followed by:

Please wait, loading kernel...
/pci@f2000000/pci-bridge@d/mac-ic@7/ata-4@1f000/disk@0:3,/boot/vmlinux: Input/Output error

I have used both the Etch and the Dapper live CDs both return the same error.  I noticed a peculiarity while attempting an install of pure Debian Sarge PPC.  The disk partioner for Debian recognized a small (38.7 kb or something) partition #1 on the Master Drive.  I dont know how boot loaders work but MAYBE yaboot is pointing by default to the wrong partition and not finding any OS to load (read something about blessing partitions on the forums but I dont understand much).

more particulars
yaboot version 1.3. 13
dapper live cd for ppc
I am NOT trying to dual boot into OSX

---

### Post by Jimothey on 2006-11-24
Hi Jesse

---

### Post by Jimothey on 2006-11-24
Ooops sorry about that.

I'm also a first time user but havent been able to get as far - could you tell me (sorry to hihack your thread) when you boot fron the cd and you get the black screen with a prompt - what do you do - if i press enter it loads a strange buggy screen and crashes....

thanks in advance i hope you get sorted.

---

### Post by JesseQ on 2006-11-24
not sure what prompt you are talking about but i will assume it is the yaboot prompt.

steps ive taken so far:
download "powerpc" iso from ubuntu website
burn to disk using a prog capable of making disk images
insert in mac
boot while holding "C"
at boot: prompt press enter
let live cd load environment (gnome)
click install icon located on desktop
follow install program directions I chose to format the drive erasing all data and installing the necessary partitions to a "fresh" drive
reboot
remove disk
choose "l"
at boot: prompt press enter


Thats as far as I have gotten today

ch

---

### Post by Jimothey on 2006-11-25
Ah right. Thanks for that.

This bit 

"let live cd load environment (gnome)"

doesnt happen for me, I get a screen like ubuntu has tried to load but failed. There are 2 icons one looking like an install to hd option, but when I click on it the whole thing crashes.

Good luck though!

---

### Post by fcapria on 2007-02-26
Late to the thread, but if other G3 and older G4 Mac users are having this issue, check that your drive is the proper size for your IDE controller. Those Macs are limited to 128 GB drives. If you put in a larger drive and try to install Ubuntu onto, that's the exact error you'll get. 

Learned this the hard way. Wanted to preserve the original Mac OS X boot disk, so I replaced it with a 320 GB drive. Got the above error on install. Swapped out that drive for a 120 GB and all is good now.

---

### Post by herkamire on 2007-07-14
Thank you fcapria for that info. I'm guessing that is my problem. I wanted to provide further details about largedrives:

1) The drive works fine, once you're booted. ie I've been using it quite a bit for months. I think the problem is simply that you cannot boot off of it (ie OF won't read it)

2) Here's the info on exactly what macs are too old to boot from big drives (128GB or larger)

"The BootROM of Power Mac G4 (Mirrored Drive Doors), Xserve, Power Mac G5, and any other model introduced after June 2002 can accommodate these larger drives."

That's a quote from: [http://docs.info.apple.com/article.html?artnum=86178](http://docs.info.apple.com/article.html?artnum=86178)

Best,

        - Jason

---

### Post by herkamire on 2007-07-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/24867](https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/24867) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/24867](https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/24867) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				**Success!**

I got Ubuntu to boot, despide my large disk!

turns out that it can boot fine, so long as the boot partition doesn't extend past the 128GB mark.

So here's what I did:

1) installed Ubuntu on the whole disk (let the installer partition and all that)

(then I discovered it wouldn't boot)

2) boot from the liveCD installer disk again, and go to install again.

3) When you get to step 4, choose resize existing partition. The slider is for resizing the existing partition (the label "new partition size" can be misleading) set it to something less than 128GB and wait for it to resize the partition.

4) Quit out of the installer and reboot. It should work now.

5) OK, now presumably you want access to the rest of your disk. run the following to discover the device name of your hard drive:

```
mount | grep ' on = '
```

My output looked like this: ```
/dev/hdd3 on / type ext3 (rw,errors=remount-ro)
```

the characters up to the first number ("/dev/hdd" in the example above) is the device path to your hard drive. Use yours in place of /dev/XXX below

5) type the following (pressing return after each line):

```
sudo mac-fdisk /dev/XXX
p
```

6) You should see a table. the last line should start with /dev/XXX5 and say free space in the last column. If it's not than quit now by pressing q and then enter.

7) type the following (pressing return after each line):

```
c
5p
5p
w
y
q

sudo mkfs.ext3 /dev/XXX
sudo mkdir /mnt/huge
sudo mount -t ext3 /dev/XXX /mnt/huge
```

8) Now the rest of your disk should be available at /mnt/huge. Now you just need to add a line to /etc/fstab so it's automatically connected there when you turn your computer on. Guess the new line should look something like:

```
/dev/XXX5 /mnt/huge ext3 defaults 0 0
```

---

