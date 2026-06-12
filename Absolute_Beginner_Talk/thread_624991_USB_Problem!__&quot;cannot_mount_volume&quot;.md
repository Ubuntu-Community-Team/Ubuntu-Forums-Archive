---
title: "USB Problem!  &quot;cannot mount volume&quot;"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by vlaklak on 2007-11-27
[B]Hi Everyone,

I have a problem about USB.  I have an External Box and 80GB harddisk in it.  

It was working well, but today when I used it, Ubuntu gave me an error message!  I can not reach important files!

Can you help me please?
[/B]

---

### Post by FuturePilot on 2007-11-27
Do you still have Windows on that computer or at least access to a Windows computer? I would try doing what the first option says. Plug it into a Windows computer and then use the Safely Remove Hardware feature before unplugging it. Most likely it got disconnected improperly at some point.

---

### Post by lespaul_rentals on 2007-11-27
This is obviously an NTFS device.  See, NTFS is based on file permissions, so your NTFS drivers in Linux cannot work very well if the device was removed or shutdown inproperly.  In fact, the NTFS table can be corrupted through normal use, no matter how much TLC you give it.

Try this:

```
sudo apt-get install ntfs-3g ntfs-config
```

Install both of those if you do not have them already.

Then, plug in the device, and figure out which device name it is given.  My USB devices are usually labed "sde1" or something similar, but yours could be totally different.  You'll need to create a mount point for the device:

```
sudo mkdir /mnt/ntfs
```

Then try to mount it:

```
ntfs-3g /dev/device_name /mnt/ntfs
```

It might give you an error message, such as "cannot mount device" or "NTFS table is dirty."  If so, add the force tag:

```
ntfs-3g -o force /dev/device_name /mnt/ntfs
```

> **FuturePilot said:**
> Do you still have Windows on that computer or at least access to a Windows computer? I would try doing what the first option says. Plug it into a Windows computer and then use the Safely Remove Hardware feature before unplugging it. Most likely it got disconnected improperly at some point.

Actually, while this is quite possible, NTFS sucks horribly at maintaining a clean table.  I take great care of my flash drives, USB hard drives, etc. and this stuff still happens.  I can Safely Remove the device every single time and I run into problems left and right.

If you do have access to a Windows computer, run "chkdsk /f" on the device and Windows will try to repair its piece of crap file system.  Usually, this will make things better for a while, although once I had to run chkdsk *three times* before I could get ntfs-3g to mount it without the force tag.  Man, whenever I hear people say things like "FORMAT UR PARTITION NTFS CUZ GUTSY RECOGNIZES IT PERFECT," it just really makes me mad.  It's a gigantic Microsoft headache!

---

### Post by vlaklak on 2007-11-27
I don't have Windows!
I only use Ubuntu 7.10

sudo apt-get install nfts-3g ntfs-config
But when I write it in terminal this shows up: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nfts-3g


The problem did'nt fix at all.   

I don't understand!  Does it mean that I can not use Usb all the time?!?  Or can it fix itself after a while without doing something? :)

---

### Post by lespaul_rentals on 2007-11-27
I feel like an idiot!  I meant NTFS config, not NFTS!  Sorry!  Please copy and paste this command instead:

```
sudo apt-get install ntfs-3g ntfs-config
```

And no, it does not mean you cannot use USB.  You **can** use USB, it's just that NTFS sucks and has corrupted your drive, in a sense.  It will not fix itself after a while, it's just a flaw of NTFS.

---

### Post by Ken Jannot on 2008-02-25
I'm getting the same error message, and I too had no luck with the suggested fix. I get this message with every single usb-connected drive I have--FAT32, flash, the card readers on my printer--same thing on every one.

The weird thing (well, one weird thing) is that this only occurs with kernel 2.6.20-16. In kernel 2.6.22-14, I haven't had that problem. (But I've had other problems with that kernel, like freezing up or not starting at all, so I've been bypassing that kernel altogether.)

Please help--this is quite frustrating, and the combination of both these problems has rendered my Ubuntu all but useless.

---

### Post by Ken Jannot on 2008-02-28
Where's the much-vaunted Ubuntu help from the much touted Ubuntu community? Why the silence?

---

### Post by bumanie on 2008-02-28
As far as I can see, the answer to your question is within the error dialogue box. I would read choice 2 again, seeing you don't have windows. You need to do a forced mount as choice 2 describes.

---

### Post by Ken Jannot on 2008-02-28
I do have Windows--but I've tried both choice 1 and choice 2. I also tried the suggestion made by lespaul above. Nothing helps. Also, as I've mentioned, this happens for every single drive I plug into the computer, not just one that may have been uninstalled improperly.

---

### Post by bumanie on 2008-02-28
In that case I don't have any suggestions other than wondering whether the usb ports are still functioing. Check all your leads and ensure they are connected properly and making proper contact. Logic would dictate that if no external devices works, there is either something terminal with your OS, your mobo has developed a problem or there is no connectivity to the usb port.  Having said that, I just noticed the problem you mentioned with kernels. Unfortunately some kernels don't suit all hardware configurations, in this case, as far as I know, all you can do is boot with a different kernel as you've been doing. Have you tried the drive in windows? May be the ntfs file system has corrupted somehow. Try it in windows, if it is recognized, do a check disk on it and see what that says. It could also be that the disk has bad sectors etc. [Sorry did not realise you were new poster within this post. You really should have started a new post]. Can you boot into a kernel prior to 2.6.20-16? I'm on windows at present due to getting a new computer that seems to have an ethernet port/driver problem (it's getting diagnostics done on it to confirm whether the mobo is bad or not), so I can't see ubuntu, but I think I had a kernel 2.6.20.15, but then again I still use feisty fawn as gutsy was too hard to configure with this old computer I'm now using. Not a great option, but if you're using gutsy and things are difficult to get working properly, you could try 7.04 instead and see how it is. In fact that reminds me that the last kernel upgrade in feisty made my computervirtually unusable, so I disabled it in synaptic.
Hope some part of this helps you.

---

### Post by Ken Jannot on 2008-02-28
It's definitely not a problem with the usb ports, since they work in Windows and with different Gutsy kernels. Would it make sense simply to reinstall Gutsy? And if so, what's the best way to do that?

---

### Post by bumanie on 2008-02-28
You could do that, but it depends how your system is set up as to whether you risk losing saved data or not. If you don't have a separate /home partition, you will lose your saved data unless you make a new opartition. It depends how computer savvy you are. If you don't have a separate /home you could make one by using gparted to make a new ext3 partition and copy the files in home there. If you did that you then have to ensure that you do a manual partition at the partitioning stage and make a separate / for you system files. You should be able to able to copy files back to the new / and new /home within /, but I am not an expert on this aspect of linux, but there are tutorials if you are prepared to read and search through the forum and/or google.
The thing is, if it is a kernel issue, you will end up with the same kernels and quite likely, the same problems being repeated. I personally would consider 7.04 istead, but you still risk losing data as described above. I would try what I've suggested myself, but I always save anything important on other media, therefore if I stuff something up it doesn't matter. What ever you do, carries some risk and as you can't use ubuntu at present and can't backup via usb device, the only other option you have is to save data to a cd/dvd before going ahead with anything. If you want to use ubuntu and can't burn data to a cd/dvd, realise you potentially risk losing everything presently saved on ubuntu. 
If you do happen to have a separate / and /home (as well as swap, of course), do a manual partition and only choose to format / and all should be fine regarding your data.
This is a choice only you can make.
PS: Just remembered there is a program for windows that allows read/write to ext3. If you google that and install that in windows, you could possibly save your data that way.
Whatever you decide to do, good luck!

---

### Post by SosinPL on 2008-05-28
<SOLVED>
I'm experiencing the same problem after installing 8.0.4 instead 7.10. It was OK when I used 7.10. I'm sure that ports are OK and my USB keyboard and printers work normally. But neither USB flash disk nor camera can't be accessed. lsusb and lshw see all USB devices. But /proc/bus/usb is empty and looks like washed out.
For usb normal mount check /etc/fstab and add the following line if missed:
/dev/sda1 /media/usb auto user,rw 0 0
For camera detection refer:
yigal.weinstein
January 27th, 2007, 02:30 AM
There is a bug. I just got a beautiful Kodak z710 digital camera today an hour ago and it is working perfectly now though.
The bug is not really a bug but simply giving proper permissions to gThumb to mount/download your photos.

1. In a terminal please do the following:
lsusb

2. find the line of the output that contains Kodak in it and copy "copy:this:" see bellow,
Bus 0ab Device 0cd: ID copy:this Kodak Co.
for example my beautiful Z710 has the following line:
Bus 001 Device 012: ID 040a:05b3 Kodak Co.
so I would copy "040a:05b3" for the next step.

3. sudo vim /etc/udev/rules.d/45-libgphoto2.rules

I use vim but you can use what ever you are comfortable with, I suggest gedit if you are a Linux newbie.

4. on a new line copy "copy:this" this way:

SYSFS{idVendor}=="copy", SYSFS{idProduct}=="this", MODE="0660", GROUP="plugdev"

for example my camera entry looks like,
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05b3", MODE="0660", GROUP="plugdev"

you must now restart udev in order for it to take notice of the changes you made. So type,
sudo /etc/init.d/udev restart

5. You should now be able to import what you want - I can :D . If you have problems I have subscribed to this message so don't hesitate to reply.

I have a screenshot of something similar to what you should see after you reattach your camera after the above steps ( - I have already decided to use one of my pictures as a desktop background - at least for today).

Note, this "problem" has already been reported as a bug,
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

---

