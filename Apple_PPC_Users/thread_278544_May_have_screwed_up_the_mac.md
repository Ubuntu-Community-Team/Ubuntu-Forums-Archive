---
title: "May have screwed up the mac"
date: 2006-10-16
forum: Apple PPC Users
---

### Post by PlatinunMOTO on 2006-10-16
I have an old powermac 5500 I wanted to install Windows on it because I thought you could I don't know much about macs. So I finally got os 8.6 to boot and I tried to startup from a knoppix cd so I could wipe the hd didn't work.

so I connected the hd to my pc and wiped the drive and formatted it with FAT.  Now it does't boot at all obviously.  I just want to run knoppix or linux on it.  I have yellow dog linux but it's like it will not allow me to to boot from cd. I keep getting a disk with a ? mark on it.

Any ideas?

---

### Post by GregB on 2006-10-16
I'm not familiar with Mac's, but is the bios set to boot from the cdrom?

Also, have you tried the [Mac (PowerPC) desktop CD version of Ubuntu]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-powerpc.iso")?

---

### Post by taurus on 2006-10-16
Will move this post over to the Mac section too...

---

### Post by miked06 on 2006-10-16
You can't install windows on an old power pc mac, the cpu architechture is power pc not i386, but you can install linux just make sure that you find a distro that supports the old power pc architechture

---

### Post by PlatinunMOTO on 2006-10-16
I found that out later which sucks but I like linux too I have YDL 2.3 and I'm burning it to a cd to use on the mac but does there need to be a mac partition because there isn't one.

---

### Post by PlatinunMOTO on 2006-10-16
I don't know how to make it boot from the cd, I've tried cmd+opt+shift+delete I've tried holding c and none of them work.

It's like it doesn't see the cd rom at all it shows a floppy disk with a ?

---

### Post by oswaldkelso on 2006-10-16
First you need mac os on the machine. This is because its a older processor and you need to install a linux boot loader (yaboot)in control panels in the system folder. Then when you boot you can choose one OS or the other.(or if memory serves me right auto boot just one os)

[http://penguinppc.org/bootloaders/quik/](http://penguinppc.org/bootloaders/quik/) this boot loader does not require mac os but is buggy and not for noobs imho.

[http://penguinppc.org/bootloaders/yaboot/this](http://penguinppc.org/bootloaders/yaboot/this) is the boot loader you require

heres the instructions
[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml#contents](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml#contents)

---

### Post by PlatinunMOTO on 2006-10-16
I don't have a MAC OS cd is there a way I can get one? I'm not going to use mac anyway I just want linux.

---

### Post by PlatinunMOTO on 2006-10-16
Now I have another problem the mac doesn't turn on at all I turn the switch on the back on and nothing hit the button on the keyboard and nothing what happened?

It was working fine a minute ago and then I shut it off because I had no mac os.

---

### Post by PlatinunMOTO on 2006-10-16
It seems the power supply is shot although I'm not certain but it won't even turn on does anybody know where the power supply is located in a powermac 5500?

---

### Post by 3rdalbum on 2006-10-17
Your Powermac requires the BootX bootloader (look on penguinpcc.org). BootX is a Mac program. **You need to keep Mac OS to boot up Linux on a beige Mac.**

Also, I'm not surprised Knoppix didn't work - it's an x86 distribution, not a ppc one.

---

### Post by oswaldkelso on 2006-10-17
> **PlatinunMOTO said:**
> I don't have a MAC OS cd is there a way I can get one? I'm not going to use mac anyway I just want linux.

[http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/System_7.5.3_Info.txt](http://download.info.apple.com/Apple_Support_Area/Apple_Software_Updates/English-North_American/Macintosh/System/Older_System/System_7.5_Version_7.5.3/System_7.5.3_Info.txt)

This is the last free version of mac os. It may or may not load on your 5500 worth a shot but  it a lot of floppys. Your mac should read pc formated floppys plus you may not need them all because you only need to get it to boot the system. good luck!!

---

