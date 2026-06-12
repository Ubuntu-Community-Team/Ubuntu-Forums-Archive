---
title: "usb flash drive not mounting automatically"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by pelletan on 2006-10-28
Hello,

Whenever I plug my 250mb flash drive in my pc it doesnt mount automatically anymore. I have to go to System / Administration / Disks and it shows there as a 250mb hard drive. I can click on it, and go to the partitions tab and if I click on enable, it mounts it to /media/sda1 and it also puts an icon on the desktop. But if I unplug it from the pc or reboot, I have to repeat the process again. Is there anyway I can fix this problem?

Thanks :)

---

### Post by pelletan on 2006-10-28
i forgot to mention im runing daper in case it makes a difference

---

### Post by pelletan on 2006-10-28
can anyone help? please!

---

### Post by dbott67 on 2006-10-28
Take a look at this thread:

[http://www.ubuntuforums.org/showpost.php?p=553568&postcount=8](http://www.ubuntuforums.org/showpost.php?p=553568&postcount=8)

> **firenurse4 said:**
> \\:D/

[COLOR="Blue"]**Solution Found!!!**[/COLOR]

Well the last thing I thought to try worked. The problem was with Gnome-volume-manger.  This is the daemon that apprently is supposed to auto mount drives.  What I did was first to uninstall that program.  I rebooted (proably not necessary step in Linux) and the drives were showing up in the Disk Mount Applete.  Still has to mount them but this was progress. Also, the Card reader worked like it should.  I reinstalled the daemon (gnome-volume-manager) and now the system works as it should.

I have no idea what was messed up or how it happened, but I did get it fixed.

---

### Post by pelletan on 2006-10-28
just tried that and it didnt work for me

---

### Post by pelletan on 2006-10-28
i just discovered another problem...because of this when i mount manually, i can only read stuff on my drive, and write stuff new stuff on it
but if i want to delete a file or change a file i have to do it as root...it wasnt like that yesterday :(

---

### Post by Judicata on 2006-10-28
Pop it in, and do a "sudo mount -a" and see if that works.  The -a mounts things as they appear in your /etc/fstab (someone correct me if I'm wrong).  If that doesn't work, post your /etc/fstab.

---

### Post by pelletan on 2006-10-28
well that works to mount the usb drive and i can write to it and stuff
so as long as that works im happy.

but if i take it out of the pc and plug it back in, it doesnt redetect it automatically. that would be a nice bonus if i can get that to work again

---

### Post by Judicata on 2006-10-28
I found this in a search for your problem.  It isn't a solution, but maybe it gets you in the right direction (i.e., see if you're having the same problem). This was in edgy, but it could be the same for you.

[http://www.ubuntuforums.org/showthread.php?t=263919&highlight=usb+automount](http://www.ubuntuforums.org/showthread.php?t=263919&highlight=usb+automount)

---

### Post by pelletan on 2006-10-30
i tried everything i could, still experiencing the problem...whats weird is i tried a friend's usb flash drive and his automount just fine on my box. i dont really get it, mine used to automount just fine 2 days ago! if someone else can help that would be greatly apreciated :)

---

### Post by pelletan on 2006-10-30
bump

---

### Post by drs305 on 2007-02-20
This post just showed up on my computer but now I see a posting date of Oct 30. Strange ...

Since you 'bumped' and are still looking for an answer, posting your fstab might give the experts that watch this forum a clue as to what is happening. I know I have messed with fstab as a newbie and am still learning. I also know that I have altered some of my fstab settings - some USB drives mount automatically and some don't. It depends on what I have written for their fstab setting.

All USB devices do not show up as the same device, even if they are plugged into the same USB port and are the same type of advice. That's one reason why one may automount and another won't, and why it would help if you posted your fstab file (/etc/fstab). Posting the fstab will also allow them to view your permissions and might explain why you are having read/write difficulties.

---

### Post by glabouni on 2007-02-20
USB devices should automount with the correct permissions without having anything to do with fstab. 

atm I'm experiencing the same kind of behaviour. Had a USB external disk FAT32 formatted I've been using for a couple weeks without a single difficulty. Just decided to reformat the drive to ext3 and now it is no more automounted with the correct permissions. 
only root can write to it.

seems this is a known but unresolved problem: [https://answers.launchpad.net/ubuntu/+ticket/2436](https://answers.launchpad.net/ubuntu/+ticket/2436)

---

### Post by Psquared on 2007-03-03
What's the gui frontend to gnome-volume-manager or the cli command to run it?

I'm having this same problem. I'm thinking about using ivman, but it requires some scripts. Not sure I want to try that. I am running a fresh install of fiesty with all current updates. Nothing unusual to my setup except maybe my mobo is rather old. (4 years) The mobo will not support a USB keyboard or mouse, but my printer is connected via USB and works fine. I have not tried my camera, but it worked fine under Dapper and was detected as USB device when I plugged it in. 

[B][U]So.... why does Fiesty not recognize my Memorex Flash Drive? (256 mb)
[/U][/B]
My fstab is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=b652d602-ff7b-4609-81fe-d52ef59acf22 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=c1f6c487-30aa-4030-8923-5149cc7625c1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Interestingly, there's no mention of hda1 or 2 in fstab, but they are automounted. CDrom works fine.

In /dev there is no usb device. There is a folder called /dev/bus/usb/001/001, 002/002, and 003/003 and I do have 3 USB ports on my pc. I tried mounting manually using vfat to a mount point in /media and /mnt and its a no go. I get a message saying that these entries in /dev/bus/usb/.... are NOT block devices.

I'm playing with pmount now, but if someone has solved this for dapper or edgy it will probably work in Fiesty so please post any info.

Thanks in advance.

---

### Post by Psquared on 2007-03-05
Well, it turned out I have a bad USB port. I plugged my Flash Drive into a different port and it was recognized right away and opened a window for me to browse the contents and let me drag and drop. I need to open my case and find out why the port went bad. There are 4 on the back and 2 work and 2 don't.

---

### Post by z987k on 2007-04-27
I'm also having a problem with mounting my usb drive.  It worked great in dapper and edgy but now in fiesty, no luck.  In fact it used to automount.  Now I can't even manually mount it.  Says /dev/sdc1 doesn't exist.  I have tried all 6 usb ports on my computer also.

---

### Post by dentaku65 on 2007-04-27
I really think that there is something really odd with hal and usb.... I've a similar problem with my extrenal usb drives (and sometimes with wintv usb card too....); I've filled a bug in launchpad
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110555](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/110555)
I hope that someone post specific issue/fix there...

---

