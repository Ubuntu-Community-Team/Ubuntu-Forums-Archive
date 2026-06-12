---
title: "MacBook 2,1 Partitioning"
date: 2010-10-03
forum: Apple Hardware Users
---

### Post by jackhe22 on 2010-10-03
Hey Linux Guys!,

I recently did up my MacBook with a new hard drive and some extra RAM, and thought it might be a nice idea to dual-boot with Ubuntu.... sadly I put it off and ended up using BootCamp to install XP; However, I recently installed rEFIt and realized that you could do a tri-boot. I've watched loads of tutorials on YouTube about tri-booting, but none of them solve my problem:

Because I installed Windows with Bootcamp, not manually, disk utility tells me that modifying the partition map may cause Windows to stop booting....  :(


HELP!



Jack.

---

### Post by srs5694 on 2010-10-03
In principle, it's possible to overcome such problems by re-creating the [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) after you've repartitioned. That said, this does seem to be a tricky issue, both because hybrid MBRs are flaky and because of boot loader issues. I can help with the former, but I'm not an expert on Mac/EFI boot loaders, so I can't help much with the latter.

---

### Post by jackhe22 on 2010-10-03
Heck No! That looks way too complicated. Thanks anyway, but is there anything else I can do?

---

### Post by jackhe22 on 2010-10-03
Bump!

---

### Post by srs5694 on 2010-10-03
If you're dual-booting an Intel-based Mac with Windows, you *already* have a hybrid MBR! Your "way too complicated" reaction just means that you'll be up to your neck if/when the hybrid MBR bites you, as such configurations seem to do far too often. (Blame Microsoft for not better supporting GPT and Apple for deciding to use the flaky hybrid MBR method to work around Microsoft's poor GPT support.)

A solution that doesn't involve further changes to your partitions is to install Linux in a virtual machine. Several are available for both Windows and OS X.

---

### Post by jackhe22 on 2010-10-04
Hmm, sounds okay. Its just I do remember once a long time ago when I had a BootCamp, I messed it up when I added a partition. I might try it, at least if it turns unbootable I can still access the partition for my data.
Virtual Machines are NOT an option.

---

### Post by jackhe22 on 2010-10-06
Bump!

---

### Post by jwhendy on 2010-10-07
I have a MacBook 2,1 and don't think this should be all that tough. Can you just backup, try resizing and see what happens? Honestly, if you want to tri-boot, I think you should just bit the bullet, think through your partition scheme and start from scratch. Hate to break that news, but I think it's easiest.

I've not used the "boot camp method." Instead I use OS X's gpt command line tool from my Leopard install disk to do it all. It generally would work like this (for dual boot):

- backup
- boot from OS X install disk
- install OS X
- reboot, set up OS X
- reboot into install disk again
- use Disk Utility to resize OS X partition and add another partition; at this point:
--- disk0s1 = GUID table
--- disk0s2 = OS X
--- disk0s3 = free space/spare partition
- use gpt to remove partition #3
--- "sudo gpt remove -i 3 disk0" should do it
- now add partitions for Linux and possibly swap
--- sudo gpt show disk0 (note start/size of partition #2)
--- sudo gpt add -b [end of partition #2 + x] -i 3 -s [size] -t linux disk0
--- repeat for swap on partition #4 if desired

Anyway, that's the gist of the process. It's been a while since I did it, but once that's done, you can use rEFIt to sync the GUID table to the MBR, reboot into a Linux CD, install it to partition #3. When you're done, I think you need to sync the tables one more time, though I'm not positive.

Sorry for the vagueness; it's been a while. I would modify the steps above, ditching swap and using the spare primary partition for Windows. I think you might have to go:

- disk0s1 = GUID
- disk0s2 = Win
- disk0s3 = OS X
- disk0s4 = Linux

I think Windows is sensitive about being first for some reason.

In any case, I really do think it's best to backup everything you want, roll up the sleeves and just start over. Sorry to say it, but it's actually quite a bit cleaner in my opinion.

Also, you can install OS X without the install disk. Sometimes you'll reboot into the OS X install disk and it will complain about your drive because it wants to be the only OS on it. I *just* reinstalled Leopard two weekends ago and have always [i]had[i/] to wipe my Linux partition as well, install OS X to a freshly formatted disk and go through the steps above. Not so this time! Here's what I did:

- plug in my 5th gen iPod (30gb white video)
- format it with 1 partition and a GUID partition table
- install OS X to the iPod
- reboot into the iPod (hold down the Option key when rebooting)
- set up OS X
- reboot into the install disk
- use Disk Utility to clone the iPod image to my hard drive partition
- whammy -- done!

It was great. No more having to wipe everything. If I do that again, I'm going to try and make room on a drive (even an 8gb USB stick) and install to that. Then any time I want to start over, I can backup, wipe the drive, and reinstall from the fresh image.

Hope this jumbled mess of crap helps even a little...!

---

### Post by jackhe22 on 2010-10-09
Thanks for the reply. I have decided to abandon running Linux on my MacBook. Instead, I will be installing Ubuntu on a spare laptop I was recently given.

Jack

---

### Post by jwhendy on 2010-10-09
Hope whatever you do works out for you! Good luck.

---

