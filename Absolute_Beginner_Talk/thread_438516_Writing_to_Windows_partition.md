---
title: "Writing to Windows partition"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by mastergunner on 2007-05-09
Guys I am trying to use DVDFab Decrypter in Wine to write into a windows partiton. When I have to tell the program where to write to it will not allow me to use my windows partiton. Why?I have downloaded the necessary linux program to be able to rad/write to my Windows partitons.

---

### Post by linux_kid on 2007-05-09
It's a simple as the following command:
```
sudo apt-get install ntfs-config
```This should work for Feisty, Edgy and possibly Dapper, not sure about others.

Then go to Applications->System Tools->NTFS Config

:popcorn:

If after installing this you still have trouble, come back :)

---

### Post by starcraft.man on 2007-05-09
First of all, why are you using a windows DVD ripping program, there are MANY for Ubuntu that will run native. They are also completely free, and offer nice GUI frontends :) Look [here]("http://linuxappfinder.com/multimedia/videodvdencoders") for options.

To write to your windows partition, it must first be mounted. If it is mounted, and its NTFS you will need the ntfs-3g driver (search forums it has enough posts on how to set it up). If you have both installed and still cannot see the windows drive, I can only assume it is a failing of the way it is being implemented (i didn't say emulated :p) by WINE. Your options then are either to rip it to your Ubuntu partition and then copy it over to the windows partition manually, or alternatively, try one of the alternate programs on linux app finder to do it which I am certain will have no difficulty finding the windows partition (assuming its mounted and you have drivers).

DVD::rip and Shrinkta are good I think, though I've never used em. I do encourage you to try native apps, we don't want you becoming a wine alcoholic, thats bad :p

---

### Post by mastergunner on 2007-05-09
I can delete and write to my windows partitions BUT with the ripper it will not allow me to select a Windows drive so I can rip to it. Why? As for the Linux apps from what I have heard cannot defeat the different encryption used by companies or am I wrong?

---

### Post by starcraft.man on 2007-05-09
> **mastergunner said:**
> I can delete and write to my windows partitions BUT with the ripper it will not allow me to select a Windows drive so I can rip to it. Why? As for the Linux apps from what I have heard cannot defeat the different encryption used by companies or am I wrong?

Uh, if this is a regular DVD (the same one thats been around for years and using CSS, NOT HD or Blu Ray) I don't see why it wouldn't or why you would think that. CSS is so broken its a joke they even put it on anymore. Any of those programs can rip a regular CSS DVD.

As for why you can't select the windows partition, like I said above, its likely a limitation on how WINE/DVDfab interact. WINE isn't a perfect emulator, its only designed to give essential functions and I assume you can still point it to the main Ubuntu desktop, thus basic function is accomplished. 

So, try one of the free programs, like I suggested above.

---

### Post by mastergunner on 2007-05-09
I just tried to download and use DVD Rip and it wont work. Man this sux. It shouldnt be this difficult. When I run DVD Rip from terminal this is what I get:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


What gives now?

---

### Post by starcraft.man on 2007-05-09
> **mastergunner said:**
> I just tried to download and use DVD Rip and it wont work. Man this sux. It shouldnt be this difficult. When I run DVD Rip from terminal this is what I get:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


What gives now?

Honestly, I don't know... I never rip any of my DVDs, can I suggest that you try another program... or wait for someone else to help ya with that, :)

I just remembered though, install K3b its my favorite burning program now, it also has a DVD video rip utility. When you install and open it up, the option is in Tools menu under Rip video DVD. 

Sorry, I forgot that program does it too :)

---

