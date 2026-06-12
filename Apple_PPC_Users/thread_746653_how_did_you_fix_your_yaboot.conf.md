---
title: "how did you fix your yaboot.conf??"
date: 2008-04-05
forum: Apple PPC Users
---

### Post by eruckus on 2008-04-05
Hey everyone!

I've got an older G5 (single 1.8, 512M, single 160G SATA) and i was looking at updating the OS, so i looked to linux. I downloaded and installed 7.04 server hoping to use it as a LAMP box, but like so many before me when i restarted the system after installation i got that stupid little mac face/question mark icon.

From other posts ive seen on this forum and around the net it looks like my yaboot.conf needs some manual editing to get my machine to boot, but i haven't found anything in any thread that can help me out yet. ive been messing around with different configurations of the file, but i wanted to know who has got a G5 to boot with ubuntu (and ive seen your sigs, i know you're out there...) and could you post what you had to change to get everything working.

Ive been tooling around with this for almost a week now so ANY feedback would be GREATLY APPRECIATED!!! 
Many thanks in advance!!:):)

---

### Post by Gen2ly on 2008-04-06
Of course, we'd be glad to help.

I'll post my "yaboot.conf" first because I do better learning by example:

```
# yaboot.conf 
# see man yaboot.conf for more details.


# Global Variables
# boot      = bootstrap partition
# ofboot    = defines the OpenFirmware device path to the boot-strap partition
# device    = Open Firmware device path where the kernel is located.
# partition	= partition number where the kernel images are located
# root      = Globally identified root partition
# magicboot = Specifies the path to an OpenFirmware CHRP script
# defaultos = Defines the default OS the first stage loads - default is linux
# delay     = Time at the OS boot menu before loading the default OS (seconds)
# timeout   = Time at the boot menu before loading the default kernel image (tenths of a second)
# fgcolor   = foreground color.  Values include: black, blue, light-blue, green,
              light-green, cyan, light-cyan, red, light-red, purple, 
              light-purple, brown, light-gray, dark-gray, yellow, and white.
# bgcolor   = background color.  Values same as above.
#
# For dual booting use:
# bsd=/dev/hdaX
# macos=/dev/hdaY
# macosx=/dev/hdaZ

# To add a password in plaintext (chmod 600 /etc/yaboot.conf) & md5 hash

#password=secret
#password=$1$saltstrg$HnJ/gcM3oKhNbnzUPgXTD/


boot=/dev/hda8
ofboot=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:8
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
macos=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:11
partition=9
root=/dev/hda9
delay=3
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
defaultos=Linux
enablecdboot
bgcolor=black
fgcolor=light-gray


# --- Kernel image section begins here ---
# Specify the filesystem path to the kernel image, symlinks are OK
# label line cannot have spaces
# first image is default

image=/boot/vmlinuz
    label=Linux/Gentoo
    read-only
    sysmap=/boot/System.map

image=/boot/vmlinuz.old
    label=Linux/Gentoo-old
    read-only
    sysmap=/boot/System.map

# Run "ybin -v" for changes to take effect.
```

It's usually better to specify UUID of devices.  I'm not going to get in to all the details but its pretty easy.  Also there's yabootconfig that may be able to do it automagically.  I've wrote about both before [here](http://gentoo-wiki.com/HOWTO_Install_Gentoo_-_From_Stage1_on_an_iBook_G3#BootLoader_Setup).

Hope this helps.

---

### Post by stream303 on 2008-04-06
I'm surprised that Ubuntu didn't finish the install on that G5 single, however I've read about other G5 tower owners having problems.  Hopefully an owner can jump in, since I don't have one.

Did the install dump you out back to a main menu after it tried to write the yaboot boot-loader to disk, and if so did you just finish up the install anyway?

Can you post your /etc/yaboot.conf such as it is, and also your /etc/fstab from a rescue-boot, or live-cd session?

Dirk is right on about checking the UUID.  I just use

```
sudo blkid
```

I also have my suspicions about /etc/fstab, and making sure that the UUID there is also accurate.  Something about the G5 towers either single or dual with their dual-hd controllers....

Here's a quick peek at my G5 imac yaboot.conf

```
boot=/dev/sda2
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="nosplash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="nosplash"
```

---

### Post by eruckus on 2008-04-06
hey guys, thanks for the replies!

Dirk:
ive tried installing different a few versions of ubuntu and (on seemingly sucessful installs) i kept getting that mac face/question mark. when that happened i booted an alternative cd in rescue mode and ran yabootconfig hoping it would resolve the issue, but unfortunately it never did. 

What ive never done is specify the UUID of devices (mainly cause i am very new to linux and honestly have no idea what a UUID is). Im doing a google search as we speak (or really as i type...ok, well ill really run it in a sec.) to see how to specify my specific devices with a UUID. Could this be the key?

Stream:
Like i said above, ive done numerous installs but most of them look like completed successful installs, including my most current one. /etc/fstab is something else i have little (ok, no) knowledge about. How does it interact with yaboot and my machine at start up?


My yaboot.conf is exactly what the yaboot installer spit out. i figured i would leave it unchanged untill i figured out a little more about what i was doing.
```
## yaboot.conf genreated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes untill you have!
## see also: /usr/share/doc/yaboot/examples for example configurations
##
## for a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/disk@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
     label=Linux
     read-only
     initrd=/boot/initrd.img
     append="quiet splash"
     
image=/boot/vmlinux.old
     lable=old
     read-only
     initrd=/boot/initrd.img.old
     append="quiet splash"
```

I just ran /etc/fstab and this is what it gave me
```
#/etc/fstab: static file system information.
#
#<file system> <mount point>   <type>  <options>       <dumb>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda3
UUID=295a92dc-83f1-4681-aabd-fdf0f18ba8d3 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4
UUID=cc406fa1-643b-4015-930f-8baa2b0599d5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

thanks so much for your help!!

---

### Post by Gen2ly on 2008-04-06
hmm, looks like the installer didn't discover UUID.  That's OK.  Sometime it isn't needed.

```
boot=/dev/sda2
device=/disk@0:
```

Try discovering the UUID from the LiveCD and enter it manually into the yaboot configuration file (/etc/yaboot.conf).  Except for that it looks ok and Linux (I mean Ubuntu :) ) should now boot.  If it doesn't work, please post the partition table:

```
sudo mac-fdisk -l
```

---

### Post by stream303 on 2008-04-07
```
boot=/dev/sda2
**device=/disk@0:**
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
```

Ah, I think we just need to find your Openfirmware device path.  Try:

```
ofpath  /dev/sda
```

and now with the info, change the device line. (sudo nano -w /etc/yaboot.conf) and save.  Mine looks like this when I run ofpath /dev/sda
**/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:**

So the line would look like this (on my machine):
device=/ht@0,f2000000/pci@3/k2-sata-root@c/k2-sata@0/disk@0:

Now make the system aware of the change, but to be doubly sure we're going to run mkofboot first.  Their syntax looks very similar.  Note the capital C.

```
sudo mkofboot -v -C /etc/yaboot.conf
```

then

```
sudo ybin -v -C /etc/yaboot.conf
```

and reboot!

I'm hoping that there won't be any /etc/fstab problems so let's see how this goes.

---

### Post by stream303 on 2008-04-07
You got me playing with yaboot myself and learned something interesting.  I don't know if it will work in your case but here it is...

Even though my yaboot.conf has a very detailed device= line, I found that you can just use a shorthand which stands for the the first hard drive that is found by the system:

```
device=hd:
```

Wow.  Just did a ybin -v -C /etc/yaboot.conf with this change, and the G5 iMac had no troubles booting.

I'm wondering though, that if the yaboot installer couldn't automatically determine the ofpath in your case, if this shorthand would work for it either.  Maybe.  Guess you'd have to try it...  

Weird!

---

### Post by eruckus on 2008-04-07
alright, so i found my UUID and edited the "device" line of yaboot.conf accordingly. then i ran mkboot and ybin and rebooted and was visited by the mac face/question mark again.

i was looking in other threads ([here](http://ubuntuforums.org/showthread.php?t=439629&page=2)) and some other users had ofboot=sd0:2, or similar variations in their yaboot's (see post 19, among others) but i noticed you guys didnt. I tried throwing a "ofboot=sd0:2" into my yaboot.conf but it didnt help. Does anyone know what the numbers correspond to? if i knew this i could make ofboot specific to my machine

Thanks!!
:)

---

### Post by stream303 on 2008-04-07
I'd try setting the device back to the openfirmware path you found, do the ybin, but this time, when booting, hold down the ALT / Option key, and see if it allows you to set the startup drive.  Wait for the gui clock to timeout before selecting.

Perhaps change the delay to 100 instead of 50.

I'm kind of shooting in the dark here, since there could be many variables that I don't see on that tower.  Is that tower capable of handling two hard drives?  If so, there may be something funky with a dual-hd controller, a strange fstab etc.

Here's a good link for firewire that goes into a little more detail about the major / minor device numbers, and it may help on your internal hd situation.
[http://hansmi.ch/articles/boot-linux-from-firewire#ofpath](http://hansmi.ch/articles/boot-linux-from-firewire#ofpath)

We're getting into a common problem that was seen with dual-hd installs into towers that had us pulling out hair trying to get yaboot.conf correct, and possibly fstab.

I'll do more research, and hopefully the yaboot guru's can jump in...

---

### Post by eruckus on 2008-04-08
SUCCESS!!!

so finally, things are looking up. After about a week or so of tinkering with installs and yaboots i finally got ubuntu to boot! i decided to try all of the tricks ive learned thus far:

i used the apple install disk to write the drive to zero's
i installed ubuntu 7.04 server ppc
i popped in a gentoo live cd, mounted /dev/sda3, proc and /dev
chrooted to the hard drive
edited yaboot.conf (see the bottom of the post)
ran mkboot then ybin
rebooted the system and cleared the PRAM

and then when it finally came around i was greeted with the ubuntu prompt! a much more attractive greeting than that stupid mac face/question mark. i logged in an poked around; everything looks normal. Thanks you guys for all your help, knowledge and incite!

Now on to my next task, to turn my shiny G5 ubuntu machine into a LAMP and DNS server!! Wish me luck!

Thanks sooo much again everyone!:-D:-D

---

### Post by Gen2ly on 2008-04-08
Congrats!  I hope (and believe) that Ubuntu will provide a good server.  I think once a good linux setup is made that many users begin to like linux.  Any more problems, grips, testimonials, I'd like to here them.

---

### Post by eruckus on 2008-04-09
well my next mountain to climb is webmin. everyone is telling me if im going to run a server, i should do it through webmin. ive already download and (i think?) installed it correctly. Have you used webmin or are you familiar with it? any tips?

thanks!

---

