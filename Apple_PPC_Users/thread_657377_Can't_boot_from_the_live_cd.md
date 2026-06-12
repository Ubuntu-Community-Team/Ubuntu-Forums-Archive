---
title: "Can't boot from the live cd"
date: 2008-01-03
forum: Apple PPC Users
---

### Post by Vault of Thrones on 2008-01-03
Hi, I was trying to install Ubuntu 7.04 on my tibook, and when I try to boot from the desktop cd it just boots normally. I will hold down the C key as it starts up, but it doesn't do anything. If I hold the option key down it shows that the CD is in there, and has an os on it but when I select it and tell it to boot from there the screen goes black, then takes me back to the select volume screen, and the only difference is that now all of the icons are fuzzy. At this point if I try to boot from the normal OSX it goes to a gray screen and proceeds to do nothing.

Any ideas on how I could get my cd to work. I know that I burnt it correctly because it boots on other computers. And if there is no hope for booting off of the CD is there anyway to forego the cd and install without it? Maybe put the desktop cd as a different partition on the disk?

Thanks

---

### Post by anthonylane13 on 2008-01-03
I couldn't boot the live CD on my powerbook g4 either.  In the end I had to get the alternate install disk burned to a DVD as my poor old hardware isn't up to reading from CD anymore....
Good luck - it's worth it when you get it working!
[http://cdimage.ubuntu.com/ports/releases/feisty/release/]("http://cdimage.ubuntu.com/ports/releases/feisty/release/")
You can download here.

---

### Post by DariusJD on 2008-01-03
-Mistake-

---

### Post by Vault of Thrones on 2008-01-03
I downloaded the alternate install cd and burnt it to a DVD, and it still will not boot, does it have to be a DVD-R, because I used an RW. 

I get the same result as with the desktop CD. Both with holding C and choosing the boot volume.

The disk drive that I am using is a super-drive that I bought about a year ago to replace the combo drive that came with the computer so I don't think it has anything to do with the age of the computer has anything to do with it.

I am pretty sure that I should be able to boot from it because I also just replaced my HD and I had to boot from the Leopard disk to install it.

I think I'll try burning a DVD-R and try that.

---

### Post by anthonylane13 on 2008-01-03
is your replacement drive connected via USB or Firewire?
If it's connected by USB, I don't think your mac will allow you to boot from it - if it's firewire I think you can, but you may need to go into your system preferences and configure that?
That's all I can think of - hope someone with a bit more experience comes along soon :-)
Good luck

---

### Post by Vault of Thrones on 2008-01-03
It's an internal drive. I replaced it because the old one broke and this one has worked fine. The specs System Profiler gives me are: 

Udner the ATA section:
Model: MATSHITADVD-RAM UF-85JS
Revision: FWR7
Serial Number:                               (it doesn't put anything here)
Detachable Drive: No
Protocol: ATAPI
Unit Number: 1
Socket Type: Internal
Low Power Polling: No

and under the Disc Burning section:
Firmware Revision: FWR7
Interconnect: ATAPI
Burn Support: Yes (Generic Drive Support)
Profile Path: None
Cache: 2048 KB
Reads DVD: Yes
CD-Write: -R, _RW
DVD-Write: -R, -R DL, -RAM, -RW, +R, +R DL, +RW
Write Strategies: CD-TAO, CD-SAO, DVD-DAO
Media: Insert media and refreshto show available burn speeds

I looked under the Installing from the Alternate Install CD instructions and it said to do some stuff in terminal if holding 'c' isn't working. This did nothing when I rebooted the computer, so I had it boot in Single User mode, I typed the command it gave me and it told me that 'boot' was an unknown command.

I don't think that the drive should be a problem, but it could be. When I got the drive I had to install a patch to get it to support burning, maybe it's getting in the way of some other thing that lets it boot. I'm going to try to uninstall it and attempt to boot.

Thanks for all the help.

EDIT: Nevermind, I forgot that I installed a new HD when I was talking about the burning patch, Leopard supports the burner without it, and I didn't install in for my new HD.
When I try to boot from a disk, the disk drive makes sounds like its spinning, but only for about a second in little quick movements. Then it procceeds directly into OSX. I don't know why it won't boot, I was able to boot from the Leopard DVD when I replaces my Hard Drive. I don't see how this is any different.

---

### Post by Vault of Thrones on 2008-01-03
I think there may be a problem with my disk drive. After searching throught the other threads, I found one describing a similiar problem. The solution that was given was replace the drive, which is not an option for me.

The only other way that I can think of is to boot it on another computer, put my laptop in Target Disk mode and connect them. When I am choosing the install location I could choose my laptops HD. I can se plenty of problems with this method, and I don't want to go through the hassle. So if anyone knows of a different solution I am ready to try it.

I haven't tried using a DVD-R yet, because I am out of them, when I get some more I will try that.

I want to dual boot both Ubuntu and OSX and I should be able to get it to work if I can get the disk to load.
I am still going to try a non re-writable DVD but any other suggestions would be very helpful.

---

### Post by Vault of Thrones on 2008-01-04
Okay, I figured out that I was booting into the open firmware wrong. I did it properly now. But when I type [HTML]boot cd:,\\:tbxi[/HTML]
it tells me 'Can't Open CD'
What other options are there for getting this to boot?

---

### Post by Vault of Thrones on 2008-01-04
Okay, I have burnt a DVD of the Desktop CD, it still doesn't work.
Not with any boot method I know of, I altered the command in the openfirmware to:
boot dvd:,\\:tbxi
I actually get something of a result when I do this. Instead of saying 'Can't open CD, it takes me to a gray screen that had a cirlce with a line through it.

I am definately thinking that the problem is with my disk drive. I might take it to someone on Monday to see if they can't get it to do anything. In the meantime I'm taking a break.

---

### Post by Vault of Thrones on 2008-01-05
I think it is definately a problem with the disk drive, all of my disks boot just fine on other computers.
I am going to try to install by connecting my laptop to another computer via firewire tomorrow, will this work? The computer I booted my disks on has a firewire harddrive attached to it, and Ubuntu didn't recognize it, are there any special tricks to getting it to recognize an external disk?

---

### Post by Vault of Thrones on 2008-01-06
Well here's something funny, I went back and tried to boot from the Leopard install disk again, like I did when I installed my hard drive, it won't boot from it now, it would seem that for some reason my drive does not support booting. I would inaming that if I wiped my disk I could boot from the CD but I don't want to do that. I have yet to attempt putting my computer in Target disk mode and installing to it like that, but I think that I am  going to.

---

### Post by Vault of Thrones on 2008-01-10
Well, it still won't boot, I bet it would if I were to wipe my hd, I booted off the leopard DVD when I replaced my hd so I know that would work. I have tried some other things I've found: wiping the pram, the nvram. I have found that the disc will spin quite a bit when I hold down 'c', so something is happening.

I also tried putting it in target disc, but when I say to install it from the other computer it only lets me erase the drive then install, I don't want to do that. Is there any way to make the install location a firewire connected drive that you don't erase?

---

