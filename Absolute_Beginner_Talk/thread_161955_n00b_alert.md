---
title: "n00b alert"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by yota99 on 2006-04-18
I just installed ubuntu and it's the first time I've ever used linux. Im having a bit of trouble. How can I access the files on my windows partition? When it boots it fails the "mounting harddrive" step. When I click on drive hda1 and hda2 it says "could not display". And also, is there a way to play mp3's without downloading something? If not what should I download. I downloaded MP3 blaster how do I open it? It just says "could not open".  Oh and dial up is there a better way to use my dial up other than going to system/administration/networking?
Someone help please ](*,)

---

### Post by Sef on 2006-04-18
> How can I access the files on my windows partition?

You need to have a FAT32 or ext2 partition.  Windows and Linux can both read and write to them.

> And also, is there a way to play mp3's without downloading something? If not what should I download. I downloaded MP3 blaster how do I open it?

You need to install some codecs from Restricted Formats.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

Just read it from the top and all should be fine.

---

### Post by majstor on 2006-04-18
For  the mp3:

[https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970](https://wiki.ubuntu.com/RestrictedFormats#head-a57167a3ce442dc52d9b05e46a14503330d4e970)

For windows partitions:

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)


For modem:

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by peteremcc on 2006-04-18
i'm very new to Ubuntu as well but i've been working to get my windows NTFS partition working in Ubuntu.

i can access the NTFS partition while i am using root so there should be no reason it won't work (i just haven't figured out how to sort out the permissions yet.

---

### Post by majstor on 2006-04-18
[QUOTE=peteremcc]i'm very new to Ubuntu as well but i've been working to get my windows NTFS partition working in Ubuntu.

i can access the NTFS partition while i am using root so there should be no reason it won't work (i just haven't figured out how to sort out the permissions yet.[/QUOTE]

Try this:

Aplications>System Tools>File Browser (Root)

Find windows dir and right click and click Properties
Click Permission tab
Put dots for all Read and all Execute

---

### Post by carverj on 2006-04-18
I heard the latest kernel reads ntfs
For myself I have a seperate home partition, swap partition, Ubuntu partition and FAt 32 partition. I used the Ubuntu install CD partitioner to resize and configure the partitions. You have to install the GRUB program to the MBR (master boot record) of the disk.
Good luck learning Ubuntu.

---

### Post by peteremcc on 2006-04-18
yes i believe i tried this, though i can't test it at the moment... i'm having a few other problems at the moment (see other thread).

was mainly posting here to point out that it (should) be possible to access NTFS as well.

---

### Post by Kimm on 2006-04-18
> 
You need to have a FAT32 or **ext2** partition. **Windows** and Linux can both **read and write** to them.


Sure, both Windows and Linux can read/write to FAT32, but in what world can Windows read OR write to ext2???! ;) :p

---

### Post by majstor on 2006-04-18
[QUOTE=Kimm]Sure, both Windows and Linux can read/write to FAT32, but in what world can Windows read OR write to ext2???! ;) :p[/QUOTE]

In this one :D 

[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

---

### Post by lg3 on 2006-04-18
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

The above linked worked for me, granted it took about 30 mins of tinkering and also a handy reset Ubunut without rebooting is ctrl>alt>backspace. 

Use this after you remount. It is pretty easy to know if you followed the steps close enough. 

Good luck, I am a week into this and despite some frustrations much happier with Ubuntu than linux and a little satisfaction when I can fix a problem on my own with the help of Ubuntu forums.

---

### Post by macdo on 2006-04-18
As far as I know, Linux can read NTFS, but not write it without a big risk of data loss. FAT32, on the other hand, is well supported.

---

### Post by yota99 on 2006-04-18
hey thanks everyone for all the help. I got the windows partitions mounted now, but I still am a bit lost with the mp3 thing.

I went to the wiki page and tried to follow the instructions then when I typed the command into the terminal it said this 

> Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-mad: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
                    Depends: libmad0 (>= 0.15.1b) but it is not installable
E: Broken packages

Did I mess something up?

---

### Post by yota99 on 2006-04-19
oh yea and my clock seems to always get screwed up when I reboot. Whats with that?

---

### Post by nalmeth on 2006-04-19
It probably tries to connect to ntp.ubuntulinux.org or whatever to get the time, but since you don't have internet activated at startup, it just goes with some default. 
For your dependency problems, what are you trying to install here?
To fix dependency problems, usually this command in a terminal will clear it up:
sudo apt-get -f install
You should
sudo apt-get update 
and maybe 
sudo apt-get upgrade
before installing anything through apt

---

