---
title: "HELP! Need to save my data!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-02-12
I need to fix my hard drive, it won't boot into windows, but i'm putting ubuntu on my lappy anyways,** but i need my data first. **

so I run fdisk -l and I do not see anything, I want to run ntfsfix on something, but what? and how can I force mount something? in "Computer" I see filesystem and disk drive.

where is the stuff on my computer? I love running all in RAM by the way :]

thanks so much!



sv

---

### Post by kpkeerthi on 2008-02-12
**sudo** fdisk -l should get you the partitions. You should be able to mount the NTFS partitions and copy the files over.

---

### Post by Joeb454 on 2008-02-12
If you're running from the Live CD then you should be able to grab the data and put it onto an External Hard Drive :)

I've done that with my /home partition from Ubuntu before...it's still on my iPod just in case ;)

---

### Post by staticvoid on 2008-02-12
still nothing

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 

:( aaahhh..!

---

### Post by staticvoid on 2008-02-12
> **Joeb454 said:**
> If you're running from the Live CD then you should be able to grab the data and put it onto an External Hard Drive :)

I've done that with my /home partition from Ubuntu before...it's still on my iPod just in case ;)

Which is great, i got that, and yes i LOVE the live cd capabilities, saves my life!! but, not when the hard drive was not cleanly unmounted and i can't acess it to save my data : /

still yelling for help ;) and still in the live cd :(

sv

EDIT: by the way: AMAZING RESPONSE SPEED! these forums blow my mind... thank you a million times over :)

---

### Post by Joeb454 on 2008-02-12
Hmm... sudo fdisk -l (lower case L just to be clear) returns nothing?

What about opening up the Partition Editor from System>Administration?

---

### Post by staticvoid on 2008-02-12
woah! i did not know that was installed default!

lets see...
nope, nothing... this is so wierd, basically one day windows vista froze up and I had to hold down the power button, then it could not boot anymore after the forced shutdown, so i figured, well, i geuss it did not unount the hard drive...

so is there no other way to get to a HD?

sv

---

### Post by Joeb454 on 2008-02-12
Try searching Google for some Hard Drive recovery tools.

I can't think of any way to do it from the Live CD right now. I'll keep looking though :)

---

### Post by staticvoid on 2008-02-12
thank you so much!

ok

googling 'linux harddrive recovery'..

---

### Post by bigken on 2008-02-12
pull the hdd and hook it up to anther pc via usb or run the repair console with a vista cd

---

### Post by staticvoid on 2008-02-12
vista has a repair console? cool. i'll try that. now, how do I plug the HDD in as a USB? do i need to go buy an adapter?
thanks
sv

---

### Post by Joeb454 on 2008-02-12
Try the repair console first, it might work. It's helped me boot into Vista on this Laptop a few times (i.e. When GRUB decided to not let me ;))

---

### Post by bigken on 2008-02-12
ye you boot from the cd and it gives you the option to repair your system 
if you buy a usb adapter you probablys need a sata one check to see what type of hdd you have :)

---

### Post by aeiah on 2008-02-12
you could also see if the newest version of gparted livecd can see your ntfs partition, or partedmagic (both are small livecds). the recent partedmagic distros are about 40mb and have ntfsprogs, ntfs-3g and visparted.

its worth a go before spending money on a sata or ide to usb cable

---

### Post by staticvoid on 2008-02-12
ok, i'll try poping in the gateway windows vista 32 bit OS cd and look for a repair option. I don't think i'll disconect the hdd and buy a usb adapter till i'm desperate.

oky, btw, what is some good data recovery software for linux? i searched and search... i remember seeing some somewhere for recovering photos, and it worked for other types of files too... hmm


thanks sooo much!! how can i make it up to you guys? you have any unawnsered post i can help you with?

sv

---

### Post by staticvoid on 2008-02-12
> **aeiah said:**
> you could also see if the newest version of gparted livecd can see your ntfs partition, or partedmagic (both are small livecds). the recent partedmagic distros are about 40mb and have ntfsprogs, ntfs-3g and visparted.

its worth a go before spending money on a sata or ide to usb cable

oh yeah, good i dea, i think i have a gparted cd lieing arund... ok
vista recovery, if that don't work, then i'll go with gparted if that doesn't work... well...  :  /

sv

---

### Post by bigken on 2008-02-12
infact vista gives you the option to do a system restore

---

### Post by Joeb454 on 2008-02-12
I'll give Vista's install disc its due - It's helped me out quite a few times :) I've had grub decide to kill a part of the MBR, so Vista said it wouldn't/couldn't boot.

Put the disc in, choose repair automatically, get a drink, come back and then boot into whichever OS you like ;)

---

### Post by staticvoid on 2008-02-12
oh maan... it did not even find the OS  : / it also asked for the drivers to get into the hard disk.. huh?

looks like i'll need to go find a usb adapter, and if that does not work, i'll just forget about my data and do a fresh install of ubuntu... and... if the hard drive is physically screwed up... then... darn

: /

sv

---

### Post by az on 2008-02-12
First things first:

Does the hard disk show up in the BIOS when you boot?

If it doesn't, make sure that the power and data cables are properly connected.

Second:

If the disk is there, boot into the live cd and open a terminal.  Run

sudo lshw -C disk -short

and then

cat /proc/partitions

Post the output.

If the live cd can connect you to the internet, you don't need to download any other cd.  You can use the data recovery software in the repos.  But you may be able to mount your ntfs partition properly, so you probably don't need to data-carve.

---

### Post by staticvoid on 2008-02-12
my BIOS says:

[I]BIOS Version:  77.10

Main SATA:       None
Left-Bay PATA: Optiarc DVD RW AD-7530A-(PM)

CPU Type: ....
..[/I].

so i guess something is screwy. btw, i'm on a laptop, so its not a matter of jiggling some data cables : /


and when i hit arrow key right (to Advanced) it freezes up!

ok.. booting into the live cd to try those commands...

oh ok, i'm going to try "Boot from first HardDisk" and I get this error:

*isolinux: Disk error 01, AX = 0201, drive 80*

(same error here: [http://ubuntuforums.org/showthread.php?t=627443](http://ubuntuforums.org/showthread.php?t=627443))

and this means something is not connected right.. now.. how would I use TestDist or Rescuecd to test and repair it if possible?
**possibilities:**
   1.  Hard drive not setup properly in CMOS
   2. Hard disk drive not detected
   3. Hard disk drive not setup
   4. Bad hard disk drive

ok, booting in ubuntu to try those commands... i don't understand what they are doing...

yipes! it put me in a BusyBox terminal thing!! lets get outa here! its dark and scary!

ok..that was different...breathe... reboot...

again!!! aah!! its never done this before.. i'll get my xubuntu cd... sheesh

i'm getting all this

*[    107.152000]   ata1: COMRESET failed (errno=-16)*

stuff

humdinger..

sorryy... it was not doing this before

that was whopper of a post for nothing

sv

---

### Post by az on 2008-02-12
> **staticvoid said:**
> my BIOS says:

[I]BIOS Version:  77.10

Main SATA:       None
Left-Bay PATA: Optiarc DVD RW AD-7530A-(PM)

CPU Type: ....
..[/I].

so i guess something is screwy. btw, i'm on a laptop, so its not a matter of jiggling some data cables : /



So forget trying a software solution to fix a hardware problem.

Does your drive make any noise?


Bottom line, you need a new hard drive and you need to decide how much you want to spend on recovering the data from your faulty hard disk.

---

### Post by kpkeerthi on 2008-02-12
Just remove and re-attach the hard drive to the bay. And check again in BIOS. Worth a try.

---

### Post by staticvoid on 2008-02-12
okay i'll remove and re attach. hmm 

well it beeps, the motherboard that is, it sounds like a tiny ambulence driving around in there "wweee--oooo...weee---ooo"   : / then it does a few system beeps say that it can't find the hdd.

i'll need to get a new hdd then : / first lemme see if what kpkerrthi said works

---

### Post by staticvoid on 2008-02-12
quick! can I put in a hdd while the computer is in livecd???

thnx, gotta run,

SV

---

### Post by staticvoid on 2008-02-12
op i did it.

nothing still... a beeping...  "woo--aa, woo---aa" i have a gateway laptop btw

sv

hmm

---

### Post by Jimcanoa on 2008-02-12
It's weird, sudo fdisk -l should work, if it isn't working there might be sth wrong with the hardware. Did if fall or sth?

By the way, just to make sure, can you sudo? does "sudo -i" work?

---

### Post by staticvoid on 2008-02-12
yes yes... humdinger, it must be a hardware problem (i'm disected at this very moment)

it says a cable is loose o something.. it beeps... whines... : / i'll just have to use puppy linux for the rest of my life now that my hdd failed... HA  :)

sv

---

### Post by Joeb454 on 2008-02-12
Lol, you could always buy a new hdd? They aren't that expensive :)

---

### Post by bigken on 2008-02-12
you could also have solder creep on the motherboard try the hdd on another pc via usb before you buy a new hdd

---

### Post by staticvoid on 2008-02-12
so adapters a cheaper then hdds I take it.. ok, well i hope i can get my sisters data!!  :)

sv

---

### Post by bigken on 2008-02-12
about a tenner

---

