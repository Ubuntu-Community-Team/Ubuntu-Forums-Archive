---
title: "[SOLVED] What is recognized"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by jcats on 2008-03-02
I recently transfered my dual boot(XP & Ubuntu) stuff into a new case. I also got rid of my CD ROM and put in a DVD/CD ROM. I also got rid of my floppy.
Now, neither one of my DVD's (I have a DVD/CD burner also) will open. When I look at "computer", the floppy and the CD ROM are still being recognized. 
How do I get Ubuntu to update the hardware?
Any body know why they won't open? There is nothing in either DVD. They will open with a paperclip.
Thanks for your time.
jcats

---

### Post by logos34 on 2008-03-02
Are the jumpers set correctly? (you'd be surprised how many people overlook that part)

Do they show up in hardware scan?
[B]
sudo lshw -C disk[/B]

---

### Post by jcats on 2008-03-02
Thanks logos34 for the reply.
Yes, the jumpers are correctly set (I did go check them, just to be sure)
I pasted your code into terminal and after password, it says:

PCI (sysfs)    this shows just for a second, it disappears, then it says:
IDE     with the cursor blinking on the I,

I have no idea what this means.
Thanks again;
jcats

edit:
I just checked the bios, both DVD's are recognized on the right IDE channel correctly, so I'm thinking it's a  OS problem.

---

### Post by jerksire on 2008-03-02
Check out your jumpers and you should fix them the exact way they were fixed in the previous cd rom if the Cd Rom was working ok before you changed them and put in the DVD Drive.

---

### Post by logos34 on 2008-03-02
> **jcats said:**
> I pasted your code into terminal and after password, it says:

PCI (sysfs)    this shows just for a second, it disappears, then it says:
IDE     with the cursor blinking on the I,

ok, try just

**sudo lshw**

anything?

---

### Post by jcats on 2008-03-02
logos34; I tried your new code and got the same response as before:

PCI (sysfs) this shows just for a second, it disappears, then it says:
IDE with the cursor blinking on the I,

thanks for trying, you keep sending me stuff, I'll try it
jcats

---

### Post by paydaydaddy on 2008-03-02
I'm sure you have already checked, but you may need to reconfigure your bios after having made changes in hardware. Probably not the problem since it lets you boot, but may be worth a look. I have had situations where I had to clear CMOS before new hardware was detected properly.

---

### Post by logos34 on 2008-03-02
> **paydaydaddy said:**
> I'm sure you have already checked, but you may need to reconfigure your bios after having made changes in hardware.

yeah, check if the bios is detecting the optical drives

although that's odd you can't get a response from lshw

---

### Post by jcats on 2008-03-02
yup, the drives are correctly recognized in the bios

---

### Post by jcats on 2008-03-02
I just ran "sudo lshw" again. This time, it sat at IDE for a second, then showed (next line) SCSI, then  listed my computer. Below is the part about my DVD's

                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom:0
                   description: DVD writer
                   product: LITE-ON DVDRW SHW-160P6S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: PS0A
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                   configuration: status=open
              *-cdrom:1
                   description: DVD reader
                   product: ATAPI DVD D DH16D2P
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   version: HP57
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd


So if I read this correctly, it is only seeing my original DVD burner, and not seeing my DVD ROM. And there is no mention of the floppy. 
There is no code to type in Terminal that will make Ubuntu update it's hardware listing?

Anyone?
Thanks;
jcats

---

### Post by logos34 on 2008-03-02
Bingo.  So it least we know ubuntu recognizes the hardware.  

Your -rom is this entry:
> *-cdrom:1
description:** DVD reader**
product: ATAPI DVD D DH16D2P
physical id: 1
bus info: ide@1.1
logical name: /dev/hdd

Fstab may need to be edited.  

gksudo gedit /etc/fstab

Change optical drive entry:
> 
/dev/**hdc** /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

Or do you have that already?  (I was thinking maybe the previous drive used /dev/scd0).

Now see if your dvd-burner (on secondary master, channel ide0) works.

One step at a time.  We'll worry about the dvdrom second.

Oh, and post 

ls -l /media

ls -l /dev | grep dvd

---

### Post by jcats on 2008-03-02
Thanks logos34 for hanging in with me.
the fstab was already set, as you posted

the -l /media is as follows:

total 12
lrwxrwxrwx 1 root root    6 2007-11-24 10:43 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-11-24 10:43 cdrom0
drwxr-xr-x 2 root root 4096 2007-11-24 10:43 cdrom1
lrwxrwxrwx 1 root root    7 2007-11-24 10:43 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-11-24 10:43 floppy0

ls -l /dev | grep dvd is as follows:

lrwxrwxrwx 1 root   root           3 2008-03-02 15:07 dvd -> hdc
lrwxrwxrwx 1 root   root           3 2008-03-02 15:07 dvdrw -> hdc

So, this definitly doesn't see the changes. Logos, I really appreciate your help
thanks;
jcats

---

### Post by logos34 on 2008-03-02
> **jcats said:**
> Thanks logos34 for hanging in with me.
the fstab was already set, as you posted

the -l /media is as follows:

total 12
lrwxrwxrwx 1 root root    6 2007-11-24 10:43 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-11-24 10:43 cdrom0
drwxr-xr-x 2 root root 4096 2007-11-24 10:43 cdrom1
lrwxrwxrwx 1 root root    7 2007-11-24 10:43 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2007-11-24 10:43 floppy0

ls -l /dev | grep dvd is as follows:

lrwxrwxrwx 1 root   root           3 2008-03-02 15:07 dvd -> hdc
lrwxrwxrwx 1 root   root           3 2008-03-02 15:07 dvdrw -> hdc

So, this definitly doesn't see the changes. Logos, I really appreciate your help
thanks;
jcats

Actually as far as the dvd burner goes it should work with those links--you're just substituting a new drive into the old /media and /dev symlinks.  There's even a cdrom1 mountpoint.

Can you manually mount a data cd in the dvd burner?
[B]
sudo mount -t iso9660 /dev/hdc /media/cdrom0[/B]

or

sudo mount -t iso9660 /dev/cdrom /media/cdrom0

---

### Post by jcats on 2008-03-02
ok, my inexperience is showing.

sudo mount -t iso9660 /dev/hdc /media/cdrom0

or

sudo mount -t iso9660 /dev/cdrom /media/cdrom0

are these to edit the fstab? Does it matter which 1 of these lines I use?

I did try to mount both drives, both could not be mounted

Thanks;
jcats

---

### Post by logos34 on 2008-03-02
no, run those commands in a terminal to manually mount a CD data disc (not blank) in the drive.

Normally you can also just click on the cd drive in the nautilus file browser side pane to mount a disc

Do you have automount set in prefs?

System>Prefs>Removable Drives and media>stoarge tab> enable 'mount removable media when inserted'

---

### Post by jcats on 2008-03-02
I have the 'mount removable media when inserted' checked in pref.

I can't get the DVD drawers to open, either by pushing the button or using the eject disc. I did paper clip one of the drawers open, inserted a disc and used the auto mount code you gave me. I got back- no media found.
The bios see both DVD's correctly, just Ubuntu doesn't

Logos34, I really appreciate all your efforts
thanks;
jcats

---

### Post by logos34 on 2008-03-03
can you toggle the tray open/close with command

eject -t

or 

sudo eject

(you may need to install pkg of same name)

For drive info try

eject -n -v

cdrecord -scanbus

Not sure why it's not responding, despite being detected by lshw

---

### Post by jcats on 2008-03-03
I tried eject -t and sudo eject and in both cases it just returned to the start (not sure what it's called)
When I typed in eject -n -v and cdrecord -scanbus I got the following:

jcats@PurpleUbuntu:~$ eject -n -v
eject: using default device `cdrom'
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hdc'
eject: `/dev/hdc' is not mounted
eject: `/dev/hdc' is not a mount point
eject: device is `/dev/hdc'
eject: exiting due to -n/--noop option
jcats@PurpleUbuntu:~$ cdrecord -scanbus
The program 'cdrecord' is currently not installed.  You can install it by typing:
sudo apt-get install cdrecord
bash: cdrecord: command not found

Any thoughts on this?
Thanks;
jcats

---

### Post by logos34 on 2008-03-03
that's what I get for eject -n -v, so it's normal...It sees the links ok.  But why it won't actually eject the tray beats me.

You can install cdrecord.  Here's what the output should look like this:

> $ cdrecord -scanbus
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (x86_64-unknown-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
scsibus1001:
        1001,0,0 100100) 'ASUS    ' 'DRW-1608P2      ' '1.41' Removable CD-ROM
        1001,1,0 100101) *
        1001,2,0 100102) *
        1001,3,0 100103) *
        1001,4,0 100104) *
        1001,5,0 100105) *
        1001,6,0 100106) *
        1001,7,0 100107) *

I'm out of ideas.  Hopefully someone else will come along with the answer.

Other things to try (just brainstorming):

unplug the slave dvdrom

try changing jumper settings from master and slave to both as 'cable select' or vice-versa

---

### Post by jcats on 2008-03-03
OK, thanks logos34. I really do appreciate all your efforts. I'll keep plugging at it, and if I find an answer, I'll post here.
Again; thanks for everything you did.
jcats

---

### Post by jcats on 2008-03-05
Hey Logos-Just an FYI- I got it solved...at least 99% of it.

And in the "who would have thought it category", it turned out to be a bad power wire:oops: The first of the 3 connectors works fine, but the next 2 (which were on the DVD's), had no power at the yellow wire.
I switched power leads, the computer recognized both DVD's and they work fine.

And despite the fact that I told the bios not to look for a floppy, and there is no floppy or cable hooked to the motherboard, it insists that there is one. But I can certainly live with that.

Thank you for all your efforts
jcats

---

### Post by logos34 on 2008-03-05
hmm..so I guess that explains why the Bios and lshw detected them (through the data cable) but the tray didn't respond (no juice).  I just hope your power supply is still good. 

That's bizarre about the floppy...like an amputee that still feels its missing limb!

---

