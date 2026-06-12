---
title: "Ubuntu doesn't see CD-RW"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by ripleyscat on 2007-04-28
This computer has two optical drives, a DVD ROM and CDRW, both are Sony drives. I have recently installed  Ubuntu 7.04 and it's a brilliant OS. One little problem mars this beautiful picture though: the CDRW drive is not 'seen' by ubuntu 7.04 only the DVD ROM drive is available to use. Ubuntu 6.10 was installed on the same partition until recently and I had no such problem with the same optical drives.

I also have SuSE Linux 10.2 installed, and Windows XP,  both of them can access (and use) both the CDRW and DVD so this rules out hardware failure. My Ubuntu 7.04 fstab  below. I should add 'cdrom1' is the problem drive in this case.


/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Can someone throw some light on this, please? :confused:

---

### Post by steve.horsley on 2007-04-28
Perhaps the first step is to see if the drive is seen at the basic hardware level. Use the command :
**lshw | less**
and scroll up/down the list with up/down arrows, but typing this:
**/CD**
then Enter should take you right there. Type **q** to quit.

**ls /dev/cd***
might give you a clue as to whether the device driver has been installed.

---

### Post by ripleyscat on 2007-04-28
Thanks for the quick reply steve.horsley.  The output from the first command: lshw | less :shows only one entry for optical drive:: 


<snip>
  *-cdrom
                description: DVD reader
                product: DVD-ROM DDU1612
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DYS1
                capabilities: removable audio dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
<snip>


Output from command #2: ls /dev/cd*:  /dev/cdrom

So it looks like the OS can only see one drive, I have done some more research on the web and found this: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/79327](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/79327) I didn't upgrade Ubuntu 6.10, I did a clean install and my download was checked (md5sum) and the burned image checked with K3b (in SuSE 10.2 ).

---

### Post by steve.horsley on 2007-04-28
Actuall, I don't think that bug on launchpad is anything to do with your problem. If the drive is not listed in lshw then the low-level hardware is not being seen at all, so any discussion over its naming is moot. I really have no idea what to do about it i'm afraid, but I;m sure the missing entry in lshw is what you need to be addressing.

---

### Post by kenklay on 2007-04-28
I am having a similar problem with my CD-RW drive with 7.04 which I upgraded on top of 6.10.  It will recognize a music cd and play it, but not a data one.  When I put in a RW disk I get a one time sound from my speakers.  I get the same responses to the lshw and ls /dev/cd commands.

---

### Post by kenklay on 2008-01-16
I did a complete reinstall of 7.04 and the then CD-RW worked.

---

