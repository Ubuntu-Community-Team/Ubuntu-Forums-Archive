---
title: "2 Drives Ubutnu Winxp"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2006-11-15
Hello!
I just installed ubuntu in an old machine,on a 40 gig drive that i bought last week, everything was perfect.

The drive has the jumper settings as Cable select, and it is on auto on the bios settings, but it was on the Master connection wire.

Now , I decided to try it on a better computer, so I just plugged it in on the slave connector , and went to the bios and set it as primary boot device.

Now it doesnt boot it gets some mounting errors and..basically something like this..:

oot (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmliniz-2.6.17-10-386 root=uuid=9c4db707-6051-46b2-8dd6-3f7c7ae0fb95 ro quiet splash
  [Linux-bxImage, setup=0x1c00, size=0x17e851]
initrd /boot/initrd.img-2.6.17-10-386
  [Linux-initrd @ 0x1f976000, 0x6791c0 bytes]
savedefault
boot
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

/bin/sh cant access tty; job control turned off

I just copied this off another post, but its the same  that I wrote down.

I tried changing the grub like this..

root=/dev/hda1     to   show /dev/hda1

I even deleted the number 1 and left hda alone.. I tried hda2 also, but  anyway.

Ill change the connections to see if that helps...

I also updated the ubuntu in the old computer and it rebooted fine.

Thank you.

---

### Post by bulldog on 2006-11-15
To give you any answer you have to specify your new computer to us.
How many hard drives do you have?

If you set your drive as a master boot device I recommend to change the jumper setting to master and connect it to the master IDE port.
Your second drive should be set as a slave device with the jumper set on slave.

Hard disks are called (hd0) or (hd1) and so on in GRUB not hda,hdb or what ever.

---

### Post by gitano1 on 2006-11-15
It sounds to me as though you are attempting to retroactively set up a dual boot system. That is a more than dicey item. What you really need to do is start from scratch with the Ubuntu installation. You have added the 40GB drive to the already extant system. Reformat that drive and install Ubuntu onto it so it is recognized in the bios and sets up the proper Grub boot sequence on the original boot drive (C). My understanding is that when Ubuntu is installed as part of a dual boot system it creates a small partition on the C drive which initiates Grub and offers you two operating systems to choose from. You will likely save a lot of time and energy by simply reinstalling Ubuntu.

---

### Post by gigaferz on 2006-11-15
well..I changed the connection order.
And the windows drive is disconnected.
Ubuntu booted normally , but then..I got some system messages..

But I booted on command line.

It says failed to start X server. Its not set up corectly.
And then it shows me the server output to diagnose the problem.

[IMG]C:\Documents and Settings\CWR\My Documents[/IMG]

---

### Post by gigaferz on 2006-11-15
How do I set up somehting like this from the command prompt?

I just want a link id not, well Ill go back to my almighty pentium 700mhz....

---

### Post by Redache on 2006-11-15
Yeah you're trying to do something that's pretty hard on any computer. Grub is a bitchy thing and it doesn't like it when you change stuff around. Try reinstalling Grub on the newer computer and see if that solves the problem. As for your X trouble, what Video Card do you have?

---

### Post by gigaferz on 2006-11-15
Ok its working as expected!!

First I installed ubuntu on an old p3 with 200 mb ram etc... Ubutnu was installed on an used 40 gig hardrive, with the jumper settingd to cable select, on the master connector.

After a few days, I decided to remove the hard drive and put it on a better computer  a newer one. P4 2.4ghz 512 ram generic video card etc...

Anyway The first time I instaled it on the slave connector, and It was messing up, (read above).

Then I tried it on the Master connector and It worked but the X server was disabled , And I was booting at the command line.
 so I just reconfigured it with a command and it worked!

after a few tries I changed the jumper settings on both hard drives, winxp & ubuntu.

Ubuntu as master on the master connector, and I moved windows xp as slave with slave jumper settings on the (obvious) slave connector.

The thing that I have to do to reboot in windows is to bring up the bios and change the boot settings. And viceversa.

Other thing that I tried to do is to get Internet on a office, all the winxp machines had trouble with this LAN, the auto detect never worked, even with a 6month old dell!!!

Anyway..after researching the forums..I gave up and went to the web..and I found mii-tool.
First I pulled the info on my eth1 with ethtool
then  sudo mii-tool -F 10baseT-HD eth1  and ctrl+alt+Backspace after that. 
Now I got INternet.

Im posting this just in case if you know somebody with Internet problems in apartments or offices.

The last thing is that I would like to keep my connections settings as described above, because everytime I restart I have to run the terminal and change the duplex settings.

Thank you everybody

---

### Post by Redache on 2006-11-15
You've just hit on why Windows is a problem, It has to be the first Partition on the master drive or it starts causing problems and whining. I'm glad it finally worked!. As for your Network settings I'm not really good with network stuff so I wouldn't be much help.

Have fun with Ubuntu :D

---

### Post by gigaferz on 2006-11-16
Anybody knows how to keep the settings for the speed of the internet??

I am talking about full and half duplex and 10mbps or 100mbps..

Because I have to change it everytime...am im dumping windows for all the issues it has...I'd like to improve my ubuntu experience.
so far I managed to get trough dual booting with ZERO knowledge and the get the lan running so far...But I guess i was lucky...

Thank you..

---

### Post by gn2 on 2006-11-16
At boot time if you can access a "boot device selection menu" yby pressing F8 or whatever, you won't need to re-order the boot list to swap OS.

Dual boot on two drives: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Have you considered VMWare or Parallels as an alternative to dual-booting?

---

### Post by gigaferz on 2006-11-16
Actually i tried that already, but for some reason only the 1st boot drive is listed there with all the other options..anyway...It looks easier just to edit the grub, ill give it a try 
Thank you.

---

