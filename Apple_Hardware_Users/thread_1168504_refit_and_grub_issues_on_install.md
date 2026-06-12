---
title: "refit and grub issues on install"
date: 2009-05-24
forum: Apple Hardware Users
---

### Post by Brightbelt on 2009-05-24
Hi,
  Back here after a long absence -- I'm installing 9.04 on my intel iMac on its own partition.
Apparently refit didn't install correctly since I get no menu on the boot, and...

in the install, I failed to go to the 'advanced' button to get grub to install at sda3, so I got a 'Grub Failed to install - Fatal Error' at the end of my install.

Otherwise, I think Ubuntu installed fine, but....I have no access obviously.

I appreciate any help on this. Many Thanks,
Frank B.

---

### Post by Brightbelt on 2009-05-24
Okay ...I got refit installed correctly by doing it manually and I see it fine on the reboot menu now, but my Grub still gets an install error, even when I've tried installing Ubuntu from scratch. 

I also tried reinstalling Grub at the terminal with the liveCD doing this:
```

grub
root (hd0,3)
setup (hd3)
```

on ALL efforts with "root (hd0,3)" no matter which number I pick, I get a message 'This disk does not exist'.

So am I just locked out of getting Ubuntu installed?

I do appreciate any pointers...
Many Thanks, Frank B.

---

### Post by vinceshaw on 2009-05-24
Seems you have double problems: rEfit and grub. Try to solve the easier one: rEfit.
From Mac, open a terminal, go to your MacHD root then cd to efi/refit, confirm enble.sh and enalbe-always.sh files are there.
Type sudo ./enable-always.sh. That's it. it will give you rEfit boot menu next boot. Not sure you can boot your linux or not but at least it gives you a linux boot item to choose from, providing your linux is installed properly.

Good luck

Vince.

---

### Post by Brightbelt on 2009-05-24
Thanks Vince for your response. Not to sound ungrateful, but I already got Refit fixed - I mentioned this in my 2nd post.

Like you said, there's no clear solution to the other. I've read some threads thru google where this is a real tough problem for some folks.

I may try an Alternate Install CD. That seems to have had some success, but I'm not certain of it. We'll See.

Thanks Again, Frank B.

---

### Post by Brightbelt on 2009-05-24
I tried the alternate install disk and no luck there either. :(

---

### Post by cyberdork33 on 2009-05-26
Post the content of the report in /Applications/Utilities/Partition Inspector (This is part of rEFIt's tools).

---

### Post by Brightbelt on 2009-05-26
Thanks Cyber, how ya doin? I was hoping you'd come in and save the day as usual. 

Many Thanks and Here's my report:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640   2866954279  Mac OS X HFS+
 3     2866954280   2927577326  Basic Data
 4     2927577327   2930277134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640   2866954279  af  Mac OS X HFS+
 3     2866954280   2927577326  83  Linux
 4     2927577327   2930277134  82  Linux swap / Solaris

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 2866954280:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 2927577327:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris
```

---

### Post by Brightbelt on 2009-05-28
Anyone, Anything?

Thanks.

---

### Post by sahabcse on 2009-05-28
For fixing the grub follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by volanin on 2009-05-28
You have linux installed on /dev/sda3.
In grub this is (hd0,2) since grub starts counting from zero!

So do as you already did, with a few corrections:

```
grub
root (hd0,2)
setup (hd0,2)
```

---

### Post by Brightbelt on 2009-05-28
Thanks to you both!! That's very Helpful Information.

---

### Post by Brightbelt on 2009-05-28
Okay guys, either way, I get nowhere. 

- If I do the root (hd0,2) thing, I get an error that says "This disk does not exist". 

- If I go for the "find /boot/grub/stage1" thing, I get 'Error 15: File Not Found'. 

So there is something really basic that is wrong and I don't know what it is. 

I Appreciate any further help on this....
Thanks, Frank B.

---

### Post by sahabcse on 2009-05-29
If you installed a /boot on seperate partition means, run

grub> find /grub/stage1

---

### Post by volanin on 2009-05-29
> So there is something really basic that is wrong and I don't know what it is. 

You are right!
You are not running GRUB as the root user!
Perform these steps. Do not skip any of them:


**1.** Run the liveCD.

**2.** Open the terminal.

**3.** Run GRUB as the root user:
```
$ sudo grub
```
**4.** Inside GRUB, select the linux partition:
```
root (hd0,2)
```
**5.** Check if GRUB files are correctly available in the linux partition:
```
find /boot/grub/stage1
```
**6.** Install the GRUB BOOT LOADER to the linux partition:
```
setup (hd0,2)
```
**7.** If everything went ok, reboot.

**8.** The linux partition should show up in the refit menu!

---

### Post by Brightbelt on 2009-05-30
Many Thanks for your help Volanin, but maybe I haven't been clear. 
I've run ALL OF THAT. and I either get Error 15 'file not found' or error 21 'This disk does not exist'. 

So I don't know what's wrong. I have successfully installed Ubuntu on this computer before, BUT I have since changed one thing in the meantime: I changed to a 1.5 terrabyte Seagate hard drive (called Barrocoda sp?) and I suspect that there's possibly a compatibility problem between this hard drive and Ubuntu.

This is all I can imagine at this point.

I appreciate all your help and everyone's help so far,.
Frank B.

---

### Post by cyberdork33 on 2009-05-30
sorry i didn't get back sooner. You seem to have a very odd situation, and it may very well be due to that new drive you have. your partition table info looks good, I don't understand why the instruction posted is not working...

can you boot the live cd and mount your linux partition, verifying that /boot/grub/stage1 exists?

Maybe you could try grub-efi? (see faq)

---

### Post by Brightbelt on 2009-05-31
Thanks Cyber for checking in. I've looked at Grub-Efi and it all looks rather vague to me. I'm not sure it's worth my trouble to be truthful. 

Ubuntu is mostly for play for me, and I'd rather forfeit the 30 gb I partitioned for now than get in over my head with grub-efi. 

Thanks, Frank B.

---

### Post by Brightbelt on 2009-05-31
This might be an eye-opener, especially considering I'm using a Barracuda drive myself...

[http://www.linux-magazine.com/online/news/seagate_promises_firmware_update_for_barracuda_drives](http://www.linux-magazine.com/online/news/seagate_promises_firmware_update_for_barracuda_drives)

For the record, I've also tried installing both PCLOS Gnome-2009, and Mandriva Spring 2009-Gnome and both OS's "seem" to install okay and grub even seems to install, but I get no grub menu on the restart, nor do I have any way of accessing the OS or that partition.

---

### Post by cyberdork33 on 2009-06-01
> **Brightbelt said:**
> This might be an eye-opener, especially considering I'm using a Barracuda drive myself...

[http://www.linux-magazine.com/online/news/seagate_promises_firmware_update_for_barracuda_drives](http://www.linux-magazine.com/online/news/seagate_promises_firmware_update_for_barracuda_drives)

For the record, I've also tried installing both PCLOS Gnome-2009, and Mandriva Spring 2009-Gnome and both OS's "seem" to install okay and grub even seems to install, but I get no grub menu on the restart, nor do I have any way of accessing the OS or that partition.
ah, yes... that. Well, if you search around, I bet you can find the firmware they have been giving to people.

EDIT:
Try here. I talked with an IT friend of mine, and he seems to think that you do not have the issue mentioned (as the drive wouldn't respond at all...). Anyway, the firmware updates are [here]("http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951&Hilite=") if you want to try it.

---

### Post by Brightbelt on 2009-06-01
Thanks Cyber - you're thorough as usual. I did however go to the Seagate site last night and on the first pass (which is the model number check) they say I *might* have a hard drive that has issues...

But then on the specific serial number check, their automated system concluded that my hard drive was not affected by the recent issues. 

Cyber, I haven't looked at your link yet, but after completing such a specific check on their website with their automated system, I would be wary of trying to install any firmware updates. 

As usual, Many Thanks for all your efforts...
Of course, this particular post may come out differently once I check out your link...:D
Frank B.

---

### Post by PhysMeistro on 2009-07-18
Seems like a good discussion for me to join.

I'm having the exact same problems as Frank B.  I recently upgraded to a new Barracuda 1.5 TB drive (but I don't think that would be the problem since hard drive failure seems to be their most commonly reported flaw).

I got the grub fatal error upon installation as well (trying to install to sda3).  Booting from live CD, I type
```
sudo grub
root (hd0,2)
```
I get ```
Error 18: Selected cylinder exceeds maximum supported by BIOS
```
Then I try ```
find /boot/grub/stage1
``` and get ```
Error 15: File not found
```

Any help would be appreciated.  And cyberdork, just so you know, you saved me when I triple booted this machine last December.  I'm hoping you can work your magic here, too.  Thanks.

-Zac

---

### Post by Brightbelt on 2009-08-03
Hi,
This thread is slightly dated, so I thought I'd *Bump* this in case there is any new news or new developments that may have come along to help this issue. 

Many Thanks, Frank B.

---

### Post by pxwpxw on 2009-08-03
If you have nothing to lose, it could be worth installing karmic amd64 alpha3 using the Desktop CD, to get the default grub2 (grub-pc) install, which should be smarter about drives than old grub1 you seem to have.

Daily build Desktop CD (or the Alternate)
[http://cdimages.ubuntu.com/releases/karmic/alpha-3/](http://cdimages.ubuntu.com/releases/karmic/alpha-3/)

[http://cdimages.ubuntu.com/releases/karmic/alpha-3/karmic-desktop-amd64.iso](http://cdimages.ubuntu.com/releases/karmic/alpha-3/karmic-desktop-amd64.iso)

I have just now installed using the karmic Desktop CD on IMAC81 but with single  HD. I am using it now after restart. The alpha3 comes with some bugs, but should be enough to show if grub2 is the answer. Need to use the Custom/Manual partitioning.

---

### Post by Brightbelt on 2009-08-05
Thanks PXWPXW, is the karmic amd64 CD you're talking about an Ubuntu CD?

---

### Post by pxwpxw on 2009-08-05
Yes, ubuntu 910.

---

