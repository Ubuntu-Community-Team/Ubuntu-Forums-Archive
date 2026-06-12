---
title: "White Screen , Giving up!!!"
date: 2007-02-05
forum: Apple PPC Users
---

### Post by Myk0 on 2007-02-05
Hey All,

This is my last post here, becasue ive really been trying for 3 days to install ubuntu PPC edition but i have had no luck

I downloaded, ubuntu 6.10 PPC edgy, and alternate cd, burt the isos proper

When i restart they just hang in a white screen after the ding.... and stall. I have no idea what to do , have searched forever on the forums and cant come up with a solution... i think i might just be switching to debian PPC..... :( really wanted to try this out!!!

Tried booting from opensource didnt help. 

My comp: 15" powerbook 1.33 Ghz, 512 Ram, 2 years old :) Mobility Radeon 9700

Any suggestions

---

### Post by grazie on 2007-02-05
Sorry to hear about your problems. I don't know what step's you've talen to fix the problem, so listiing these would be good and keeping them on the same thread, makes helping you much easier. As you've been searching the forum already. I'm assuming you verfied you're downloads and you've burnt the disks slowly. 

Can you still boot your OS X install disk? If you boot to your OS X installation, can you read your Ubuntu CDs? Some people have problems with nvram settings, so clearing that may help. But first list the steps you've taken so far. Your system should cope well with both the Desktop (Live) and Alternate CDs.

Debian is notorious for being more tricky to install. Gentoo do a PPC minimal install disk and it's small, so it may be worth trying to boot your machine with that. It's a useful recovery disk to have in the future anyway.

---

### Post by Myk0 on 2007-02-05
ok to be more detailed:

downloaded the following isos

ubuntu 6.10 edgy desktop pc on cd & dvd
ubuntu 6.10 edgy alternate on dvd
ubuntu 6.06 drake desktop pc on dvd (note i downloaded the regular cd iso not dvd, but didnt htink it matters)

Burned all of them as iso. Tried each one individually

Turn off comp - > power on, cds in hold c, loads screen flickers as if loading to osx then flickers again and ends up at a white blank screen, on every iso i used.

Even tried reserting power management, PRAM, confirmed that it worked , didnt help the problem.

Osx cds work when using them on boot.

tried: sudo nvram=false? (i know its not the exact syntax but copied it from another forum) still didnt work!!! white screen!

Any more suggestions??? im really stumped.

---

### Post by grazie on 2007-02-05
Have you verified the md5sums of the all the ISO image you have downloaded? If so, did you burn the images to CD/DVD slowly? Boot OS X, insert the Ubuntu CD(s) and list the top level file contents on this thread (if you know how to take a snapshot in OS X, do that instead). 

I'm asking because most people that have booting problems have not followed these steps or burnt the image incorrectly.

---

### Post by Myk0 on 2007-02-05
put in the cd, Ubuntu_PowerPC_dapper

all the files look fine 704 mb. burn the iso with toast using a right click on the image, and toast it, image burn. havnt checked the latest MD5 i downloaded, but it still seems to have the same problem... i think its the computer rather than the software, i dont quiet know what the issue is but it freezes it up 

Burned it semi slow, although ive been reading alot of threads saying burning speed does not make a difference, but i burned all 3 cds at different speeds no difference....

By the way: i already have osx installed on the HD .. if this makes any differnece

---

### Post by grazie on 2007-02-06
If you don't check what you've downloaded before burning, you could be just creating coasters. Checking the generated md5sum is easy. In an OS X terminal
```
$ md5 <image.iso>
```
Replacing <image.iso> with the name of the image file. What speed you burn the image to disk can make a difference. Most people have OS X and/or OS9 installed (and keep it) before trying Ubuntu.

---

### Post by Myk0 on 2007-02-06
ubuntu-6.06.1-desktop-powerpc.iso

MD5: 502911770ad173dbe82c698379ed7d11

Where can i check proper md5's to compare, and i truely dont believe this is software related.

---

### Post by casaschi on 2007-02-06
Dont know anything about the PPC version, but I solved a similar problem with my laptop by adding "vga=791" at the "boot:" prompt (when the CD starts the boot process you should have the "boot:" text prompt for few seconds, then booting starts unless you type something)

You can either try that parameter (does your PPC system have a VGA or VGA like graphic card?) or looking at the boot options for your system.

---

### Post by Keith Hedger on 2007-02-06
Hi I use a powerbookk to and I have been using ubunto for some time but i found a lot of problems with edgy(6.10) but dapper(6.06) works fine some of the downloaded isos seem to get corrupted(I use a 56k dialup so it takes foreever!) so I use the pucker CDs from shipit which install perfect try one of them before givving up

---

### Post by Myk0 on 2007-02-06
keith i got the md5 from terminal now what do i compare it to , to make sure its not corrupted?????

---

### Post by grazie on 2007-02-06
Myk0,

That md5sum is good. On the page where you download the iso there should always be a file called MD5SUMS which for example contain the following

b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
2ccc1ec608040e6aac8913a016c31bed  ubuntu-6.06.1-server-sparc.iso

It wouild now be good to try and boot from OpenFirmware. I'll see if I can dig up some links. In the meantime I'd suggest downloading the [Gennto 2006.1 Minimal CD]("http://bouncer.gentoo.org/?product=gentoo-2006.1-minimal&os=ppc") and try booting from that. It's only 55M and it's a useful tool to have anyway.

Incidently, we're using Dapper (6.06) here.

---

### Post by Myk0 on 2007-02-06
Tried to boot previously from open firm ware and i get this

error: cannot open \install\yaboot

tried boot --live cd
boot cd
boot cd:, \install\yaboot
and boot cd:,\\:tbxi

im downloading gentoo now, whats another alternate easy to use linux system for PPC ?? and how hard is it to install debian?

---

### Post by Myk0 on 2007-02-06
Update:

I downloaded the gentoo net installer disk and debian net install disk

both end up at this damn white screen. I am pretty confident now that its not a software related issue ( i now own 6 cds of ubuntu) :p any ideas???

Something must be blocking yaboot or any linux installer off the cd @ the opensource...

---

### Post by grazie on 2007-02-06
The good news is that you have eliminated a lot of common problems. The bad news is that some Macs do seem to simply refuse to boot Linux.

If you've not lost heart yet, booting from OpenFirmware is the next step. However, OpenFirmware uses nightmare device names and just about every machine is different. So what works on one machine will not necessarily work on yours. 

I've not had to solve your particular problem myself, so I'll see if I can find some useful resources.

For information only, the only other sizable ppc distro is Yellow Dog, but I'm sure you'll not have any more success with that, but there may be something useful on their forums.

---

### Post by Myk0 on 2007-02-06
grazie thanks for your help, was one step ahead of you

used openfirmware,

boot cd:,\\:tbxi 
and boot cd:,\\install\yaboot

no luck

used 

reset-nvram
reset-all

then proceeded to reset PRAM (power management) 5 chimes later, reset

went back to openfirmware 

tried to boot --livecd

opens a gray windwo saw, a quick flash of wiritng then a circle with a line going through it diagnolly, like a do not pass sign.

---

### Post by aboz on 2007-02-06
I just ran into a similar problem on a dual 2.0 g5 powermac.  Below is the fix. Not sure if this is your problem or not.

The yaboot that's shipping with 6.10 has a [bug]("http://ozlabs.org/pipermail/yaboot-users/2006-June/000029.html") in ofpath

boot up a live cd and mount the "/" partition that you just installed onto (the one that didn't boot ;)

```

mount /dev/sda3 /mnt

```

check out /mnt/etc/yaboot.conf.  If your device line says something similar to:
```

device=/disk@0:

```

Then this is probably your problem.

I downloaded the current yaboot and replaced the ofpath scripts on my system.

```

sudo chroot /mnt
apt-get install git-core
git clone git://ozlabs.org/srv/projects/yaboot/yaboot.git

```

In another shell (don't chroot), do
```
http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2113632
cp /mnt/yaboot/ybin/ofpath /usr/sbin/ofpath
cp /mnt/yaboot/ybin/ofpath /mnt/usr/sbin/ofpath

```

I had problems with running ybin from the chroot directory.  I ended up doing the following, but in the end I ran 'yabootconfig -t /mnt' without a chroot.  Mileage may vary.

From the chrooted environment:
```

sudo chroot /mnt
mknod /dev/sda b 8 0
mknod /dev/sda1 b 8 1 
mknod /dev/sda2 b 8 2 
...
mknod /dev/nvram c 10 144
mount /proc

```

---

### Post by Myk0 on 2007-02-07
aboz: im still new to the linux enviornment so im going to need your help redefining these instructions...

"boot up a live cd and mount the "/" partition that you just installed onto (the one that didn't boot"

How exactly do i boot up a live cd that doesnt boot?!?!?!? :P or you mean in OSX?

Here is a copy of my yaboot.conf off my edgy cd , in osx, went into the cd into /etc/yaboot.conf

didnt see any device line at all??

----------------------------------------------------------------------------------------
## This yaboot.conf is for CD booting only, do not use as reference.
## Ubuntu PowerPC (edgy)

default=live
timeout=300

message=/install/boot.msg

# PowerPC subarch 
image=/casper/powerpc/vmlinux
    label=live
    alias=live-powerpc
    initrd=/casper/powerpc/initrd.gz
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --"
    initrd-size=1048576
    read-only

image=/casper/powerpc/vmlinux
    label=live-nosplash
    alias=live-nosplash-powerpc
    initrd=/casper/powerpc/initrd.gz
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet --"
    initrd-size=1048576
    read-only

# PowerPC64 subarch
image[macrisc4]=/casper/powerpc64/vmlinux
    label=live
    initrd=/casper/powerpc64/initrd.gz
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --"
    initrd-size=1048576
    read-only

image[macrisc4]=/casper/powerpc64/vmlinux
    label=live-nosplash
    initrd=/casper/powerpc64/initrd.gz
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet --"
    initrd-size=1048576
    read-only

image=/casper/powerpc64/vmlinux
    label=live-powerpc64
    initrd=/casper/powerpc64/initrd.gz
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --"
    initrd-size=1048576
    read-only

image=/casper/powerpc64/vmlinux
    label=live-nosplash-powerpc64
    initrd=/casper/powerpc64/initrd.gz
    append="file=/cdrom/preseed/ubuntu.seed boot=casper quiet --"
    initrd-size=1048576
    read-only

# PowerPC subarch
image=/casper/powerpc/vmlinux
    label=check
    alias=check-powerpc
    initrd=/casper/powerpc/initrd.gz
    append="boot=casper integrity-check quiet splash --"
    initrd-size=1048576
    read-only

# PowerPC64 subarch
image[macrisc4]=/casper/powerpc64/vmlinux
    label=check
    initrd=/casper/powerpc64/initrd.gz
    append="boot=casper integrity-check quiet splash --"
    initrd-size=1048576
    read-only

image=/casper/powerpc64/vmlinux
    label=check-powerpc64
    initrd=/casper/powerpc64/initrd.gz
    append="boot=casper integrity-check quiet splash --"
    initrd-size=1048576
    read-only
-------------------------------------------------------------------------------------



Did not cd any device id??? im very confused right now ....

---

### Post by aboz on 2007-02-07
Sorry, I misunderstood your problem.  When you said it crashes after reboot, I thought this was *after* you went through with the installation ( this is what happened to me ).

After reading through this thread again, the only thing I can suggest is to burn the cds with hdiutil

```

hdiutil burn <image.iso>

```

If that doesn't work, you can try doing something crazy like installing via debootstrap from osx.  

I really wish Ubuntu ( and GNU/Linux  in general ) had better support for these machines.

Good luck.

---

### Post by Myk0 on 2007-02-07
really, im out of options, gentoo , debian , and ubuntu do not work , no version of linux works on this comp, its terrible!

could it be because i havnt setup a linux partition, i currentlly have my hd partitioned for osx.?

---

### Post by Myk0 on 2007-02-08
Well after 5 days of searching i have figured out my problem.

I replaced my Apple cdrom drive with a Pioneer DVDR/CDR - DVR-k06 which is a very suitable affoardable replacement. Updated the firmware of the dvdrom and everything worked fine.

HOWEVER

The old apple cdrom drive was set as master on this computer and the new DVDR is set to slave, causing boot cd issues and the 'c' key not to work. I read about pin fixes on the IDE boards, but have no decided what i want to do yet.

For those getting the white screen of death, that are using the dvr-k06, this is why.

P.S Master is for powerbook users and slave should be set for cube users.

Thanks for your help guys!

---

### Post by grazie on 2007-02-08
I'm glad you found a solution. What made you decide to try another CD/DVD ROM?

However, the solution you found is a solution for your particular machine. It would be good to have a sticky or a wiki page containng a table of known Mac booting problems.

Something to bear in mind for the future is that if you cross or multiple post, you are far less likely to get advice from others, as it's regarded as spamming. And when someone offers advice, read what's been written as it may not always apply to the problem in hand. Finally, headless chicken mode rarely solves any problems.

---

### Post by Myk0 on 2007-02-08
Price was about 1/3 and pioneer dvr-k06 seems to be a perfect solution for the apple optical drive. 

By the way: the slave to master fix is done by joining pins 43-45 ground to pin 47.... you can use a soldering iron or use a conductive pen :)

---

### Post by gurnemanz on 2007-02-09
> **Myk0 said:**
> Price was about 1/3 and pioneer dvr-k06 seems to be a perfect solution for the apple optical drive. 

By the way: the slave to master fix is done by joining pins 43-45 ground to pin 47.... you can use a soldering iron or use a conductive pen :)


Myk0, do you have a link to an illustration of this fix? I suspect I have the same problem, since I have bought the same optical drive to solve the same issue.

And where does one find a conductive pen?

Thanks -

g.

---

### Post by Myk0 on 2007-02-09
[http://www.xlr8yourmac.com/](http://www.xlr8yourmac.com/)

in the data base article sections, im researching more into this subject and will perform the fix in the next week or so, i can give you some detailed explainations once it works.... apparently there have been a lot of sucsess grounding these pins, you can buy a conductive pen online, in a hardware or electronic shop, i personally think the best bet is to bring your computer to a electricion and get him to perform it , since the pins are packed tight, but its up to you...

~M

---

### Post by gurnemanz on 2007-02-09
> **Myk0 said:**
> [http://www.xlr8yourmac.com/](http://www.xlr8yourmac.com/)

in the data base article sections, im researching more into this subject and will perform the fix in the next week or so, i can give you some detailed explainations once it works.... apparently there have been a lot of sucsess grounding these pins
~M


Lucky for me you didn't give up after all!

I'll probably pull out the old soldering pencil and practice leading a bead before I try the pins.

Thank you, Myk0.

g.

---

### Post by Myk0 on 2007-02-09
funny enough (you guys will laugh) but it came to me in a dream that it might be the dvr...so at 5 am i got on my laptop and checked some stuff out, and i was right.... sometimes getting away from the problem lets your sub-consious worker better. :)

I am considering writting up a full wiki for this issue.

Ps. check out  -  forum.rpc-1.com/ in specific a search on the thread dvr-k06, lots of good info, firmware updates, etc. Gotta love the open source community and hackers :P 


~M

---

### Post by grazie on 2007-02-09
I'm still curious to know why you thought changing the CD/DVD ROM would solve your problem? Laptop devices are usually pretty tricky to change and are usually quite pricey. I'm sure many people wouild like to know how tricky you found it.

Booting Linux with an alternative CD/DVD ROM is rarely a problem, but Apple build their devices with modifiedl firnware, so using any old CD/DVD ROM will not boot MacOS without additional firmware updates/patches/hacks.

Also, as you have a solution or at a least partial solution it's very helpful to others if you mark your post as resolved. (EDIT > Go Advanced > Tick "Check box if your thread **IS** resolved.")

---

### Post by Myk0 on 2007-02-10
grazie you dont seem to have read what i wrote earlier on. I changed the optical drive, due to failure not because i wanted to install linux :P

It seemed as if its a great solution for a much faster and 1/3 price dvr for apple optical drives.

The pioneer dvr-k06 happens to ship with 2 different types of firmware settings, master and defualt, in the US they ship usually as master but there are times that they have made mistakes which they clearly outlined in thier response email to me.

Software like patchburn allows for non apple drives to be read as 'burnable' however does not address the slave/master issue.

Apple does not write firmware in order to address these IDE issues... unfortunately. However i am aware that on 10.4.4 they have address these non-apple drives as burnable, not requireing one to install patchburn.

---

### Post by grazie on 2007-02-10
[QUOTE=Myk0]grazie you dont seem to have read what i wrote earlier on. I changed the optical drive, due to failure not because i wanted to install linux :P[/QUOTE]

I can't see where? All I can see is this

[QUOTE=Myk0]Well after 5 days of searching i have figured out my problem.

I replaced my Apple cdrom drive with a Pioneer DVDR/CDR - DVR-k06 which is a very suitable affoardable replacement. Updated the firmware of the dvdrom and everything worked fine.[/QUOTE]

And about CD/DVD ROMS

[QUOTE=Myk0]Apple does not write firmware in order to address these IDE issues... unfortunately. However i am aware that on 10.4.4 they have address these non-apple drives as burnable, not requireing one to install patchburn.[/QUOTE]

No, Apple modify them (or at least they use to) so that you can't go out and replace with a cheaper alternative when they fail!

---

### Post by jaaron7 on 2007-03-15
hey, I'm running into this problem too, but it wasn't fixed by switching around CD drives (tried that already - I've got a pioneer DVD rw from NewEgg and I've still got the DVD-RAM that came with the computer (450MHz G4 Sawtooth))

when booting with C held down it flashes and ends up stuck on a white screen. When booting with Option held down to bring up the boot selection screen, if I select the Ubuntu disk, it'll flash for a second, and end up right back at the Option menu, but with some of the colors inverted.

I've tried this with a new Kubuntu disk (6.10), and with my Ubuntu (6.10?) and YDL (3.01) disks. The Ubuntu and YDL disks have worked in the past (Ran YDL a few years back, was able to boot off the Ubuntu disk just a few months ago)

attempting to boot from the CD in Open Firmware gives the error "can't OPEN: cd:,\install\yaboot" ... gives something along those lines for all yaboot CDs I try (I currently don't have a hard drive with yaboot that I can try to boot from)

My OSX cd still boots, so it appears to be something about OF rejecting yaBoot

I've tried reducing my computer down to the bare minimum hardware. Wouldn't even boot with the only disk drive being the DVD-RAM that came with the computer. I've fiddled with master/slave combinations, different drive combinations, unhooked my KVM, unhooked everything from my USB2 card (which has been in there for a couple years and didn't stop Ubuntu from booting before).

I've run out of ideas. Anyone else have any?

---

### Post by jaaron7 on 2007-03-16
I finally tracked down the cause of the problem. For me, somehow the aliases hd and cd got mixed up (and no amount of PRAM resetting fixed it..) and so "boot cd:,\install\yaboot" actually pointed to the master hard drive instead of to the cd drive, so I typed in "boot hd:,\install\yaboot" and it booted off the cd.

so, to anyone else with this problem, go to Open Firmware, and check "dir cd:\" and make sure it actually prints out the directory of the cd. If not, then you'll have to use its actual name.

I was able to install Ubuntu and get it working with just the hard drive I wanted it installed on hooked up. Now that I've got both of my drives in though, I'm running into the same problem. ...at least now I know what's going on though.

**update**
It all makes sense now. OF didn't just randomly get cd and hd confused - I did. I wanted two internal cd drives, so I moved my Mac into a PC case and when I did, for some reason, connected the CD drives to where Apple had had the hard drives, and visa versa. I'm sure I had some reason for this, but i can't remember it now

I now have Kubuntu running with the option to boot OSX off my second hard drive

---

