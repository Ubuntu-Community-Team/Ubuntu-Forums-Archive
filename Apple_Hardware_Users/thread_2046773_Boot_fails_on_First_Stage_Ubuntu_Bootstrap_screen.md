---
title: "Boot fails on First Stage Ubuntu Bootstrap screen"
date: 2012-08-23
forum: Apple Hardware Users
---

### Post by miguelbaines on 2012-08-23
Ok, I have a 2001 quicksilver G4 Ppc, 10.4.11, 867 mhz, 1.12 gb sdram, 61gb harddrive partitioned equally in two (os x 10.4.11 on one, free space on the other). Installed Lubuntu 12.04 alternate cd that i downloaded and burned. I had trouble getting yaboot installed, but I've finally figured it out and got it installed to dualboot.

Now, when I hold down the option key, select the linux icon, it takes me to the first stage bootstrap screen where I would select 'L' to launch ubuntu, instead, it kicks me back out to the dualboot screen. This happens with whichever option I choose L, X, O, C.

I googled, yahooed and binged, finally found someone who had the same problem, followed what he did to get it to boot, but it did not work for me. I was led to debian forums, ubuntu forums, tried everything in the faq, read through the known issues... and, well, here I am.

I see that everyone somehow posts their yaboot.conf file, I've no idea how to manage that although I did write it all down, so here's what my yaboot looks like now -

```

boot=/dev/sdb9
partition=11
ofboot=/dev/sdb9
root=/dev/sdb11
timeout=100
install=/usr/lib/yaboot/yaboot
enablecdboot
enableofboot
enablenetboot
macosx=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0
defaultos=macosx

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd,img
append='quet splash'

image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append='quiet splash'

```

I added the 'ofboot' from what the person who was able to boot did. He also commented out the device, which either way is not working for me. I just took out device all together. 

The step that he had that I am unable to get past, is where after he made those changes (the ofboot and #), he enters the following - sudo mkofboot -C /etc/yaboot.conf or sudo mkofboot -b /dev/sdb9 -C /etc/yaboot.conf, it then asks if you want to make /dev/sdb9 the HFS filesystem (or something like that) and i answer 'yes,' I get - mkofboot: aborted. In the man mkofboot, it says that will happen, so now I'm left wondering maybe that guy missed a step in his post??

Any insight would be welcomed.

Thanks!

---

### Post by rsavage on 2012-08-23
You don't say how you are running the mkofboot command?  Presumably you have managed to boot the system somehow?  If so, how?
 
Your ofboot value is wrong.  You are giving it a linux path not an openfirmware path.  You want something like this:
 
ofboot=hd:9
 
BUT, it probably won't be hd because you are using sdb so you must have 2 hard drives installed???  Or do you have some funky partitioning scheme?  I'm not sure how that will translate into openfirmware devaliases.  Some are described here [http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html#s9.2](http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch9.en.html#s9.2) 
 
The macosx openfirmware path also doesn't look right.  It is not specifying a partition, but looks more like a device.  
 
When you setup yaboot.conf you only need to run
 
sudo mkofboot -v

---

### Post by miguelbaines on 2012-08-23
Not sure what you mean when you wrote, 'you don't say how you're running the mkofboot command?' 

I'm using rescue off the cd and then shell in /dev/sdb11 to enter the commands

Yes I do have two hard drives, the second is my storage drive for the mac os, that one i believe is sda.

Yes I did enter the device for macosx, because I didn't know how else to enter it.

I'm going to make those changes and see what else I can come up with.

Thanks!

This is what i entered to install yaboot - 
```

ofboot=/dev/sdb11 ybin -v -b /dev/sdb9 -C /etc/yaboot.conf... and a penguin peed on it. ybin -v alone was not working, although it works now.


```

I'm going to make those changes and see what happens...

Thanks for your help! 

Changed ofboot to hd:9, still trying to crack macosx=...

---

### Post by rsavage on 2012-08-24
I haven't used the rescue option, not sure how that works.  
 
Can you run me through what happened on the install?  I don't really understand why you are going through this?  Did you get a message when installing that the bootloader stage had failed?  This is typically because it can't work out the openfirmware path of the partitions.
 
Before you make changes you need to work out what the openfirmware path of your partitions is.  Are you sure it is hd?  Since it is being identified as the second hard drive it is likely to be something else I think.  I'm speculating that the second hard drive is the source of your problems.
 
As a quick check follow the instructions in the FAQ.  Paraphrasing:
 
Run the cd to the yaboot prompt. Instead of entering 'install' or whatever use the openfirmware path to the kernel image. Type:
 
```

hd:11,/boot/vmlinux --no-log

```It should start loading something, and may even boot up fully.  If the command fails straightaway then hd is not your devalias.  Try ultra1, ide0, and ide1 instead of hd.
 
You may have to drop to openfirmware to work it out.  See the USB instructions.
 
If you still can't work it out then you can use as a temporary measure in your yaboot.conf 
 
```

ofboot=&device;:&partition;
nonvram

```This should allow you to boot via the option/alt key.

---

### Post by miguelbaines on 2012-08-26
My apologies for not responding straight away... I'm out of town until the first week of september. I do appreciate your help. I will continue when I'm back to get this thing working.

Cheers.

---

### Post by miguelbaines on 2012-09-20
Ok, I'm back. Took longer than I expected, but I'm back and wanting to get this thing going. 

The rescue option basically, as I understand, allows you to go back into the initial set-up to make changes to what has already been installed, to either reformat the partition, disk, wired/wireless setting, etc.

When I did the initial install, for whatever reason, it would not install yaboot. After researching I finally was able to get it to install, but now my problem is that ubuntu will not boot when I select L to launch linux in the dual boot screen.

I was however able to ascertain the path for macosx and am now trying to get the ofpath of the ofboot=/dev/sdb9 (my boot partition).

In shell, I type
```

ofpath /dev/sdb9

```
and I get
```

ofpath: SIIG-680-R1 (pata_sil680) is not supported.

```
So does that mean, because of my two harddrive set-up I won't be able to run linux/ubuntu or is there a way around that?

I ran the two codes you suggested - 

```

hd:11,/boot/vmlinux --no-log

ofboot=&device;:&partition;
nonvram

```
but I got nothing, both stating that it could not find device, hence my ofboot path??

Going to re-reread the FAQ to see what I may have missed.

Thanks.

---

### Post by miguelbaines on 2012-09-22
So now, I've found the ofpath, finally. I've edited my yaboot.conf... and the funny thing now is, on the dual boot screen, the icons have switched places. I used to have macosx on the right and linux on the left and now they've switched.

Still can't boot ubuntu though... it just kicks me back out to the dual boot screen.

---

### Post by miguelbaines on 2012-09-24
UPDATE

Looks like I finally got this thing to boot... i think. It goes through from the dual boot screen to the screen where I choose 'L' for linux, loads the kernal, loads what looks like the openfirmware screen, then it goes black, which I'm now going to guess has to do with my monitor.

I'm using a 32in Polaroid FLM HD tv as my monitor.

So, one problem solved, another created. Off to research I go...

---

### Post by miguelbaines on 2012-09-25
Still hoping someone will chime in...

After lots of reading, I finally got my machine to load some of the script after the boot loader screen - and it stops right at this line:

```

Begin: Running /scripts/init-bottom ... done

```

the screen flashes for a brief nano second and comes right back to the same spot where the last line above is... and that's it.


Lets recap what I've done - 

Re-re-re-re-edited my yaboot.conf file, so now it looks like this - 

```

boot=/dev/sdb9
partition=11
ofboot=pci/SIIG-680-R1@14/2:9
root=/dev/sdb11
timeout=100
install=/usr/lib/yaboot/yaboot
enablecdboot
enableofboot
enablenetboot
macosx=sdb10
defaultos=macosx

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="video=ofonly"

image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="video=ofonly"

```

Ran this tasty nugget - to update the kernel
```

sudo apt-get update
sudo apt-get dist-upgrade

```

Configured a new xorg.conf exactly as stated in the powerpcfaq section "How do I configure xorg?"


This was easier to load on my netbook from a usb flash drive!

---

### Post by miguelbaines on 2012-09-25
Added a "Modeline" to xorg.conf based on my cvt findings, and it still hangs in the same spot.

On the second boot screen, If I type in "Linux nouveau.modset=0," it boots all the way to the low graphics warning screen, i hit ok and then on the "what would you like to do?" page (next page where it gives you the option to continue or configure graphics) it hangs there.


... so close.

---

### Post by miguelbaines on 2012-09-25
You know that scene in Swingers, when the guys are driving through the night to get to Las Vegas, and that scene kinda drags to show just how far LA is from Vegas (it's at least 5 hours, if you were wondering), and at one point they can see Vegas in the distance... that's where I'm at with this.

Read more, made more adjustments to both yaboot and xorg. In yaboot I changed the 'append' value to read, "nosplash video=ofonly"

Found a thread where a guy added multiple 'modelines' to the xorg.conf in the monitor and screen section as well as adding 'Option "UseFBDev" "True" and Option "NoInt10" "True" under the device section...

and I got all the way to the 'ubuntu 12.04' with the four dots... and it hangs.

All I'm saying is, I expect to get my computer engineering degree when this thing is operational.

Alright.

---

### Post by miguelbaines on 2012-09-26
Update!

Success... sort of. I finally was able to get it to boot fully using the command line commands from the FAQ in regards to xorg, by downloading the nvidia driver as per the instructions and then using the following- 

wget [http://mac.linux.be/files/xorg/imac8.txt](http://mac.linux.be/files/xorg/imac8.txt)
sudo cp imac8.txt /etc/X11/xorg.conf
sudo reboot

I also made some additional changes because it was pointing to the wrong device id. I also did backup my previous xorg.conf file to be safe.

Now, one last item to fix... the screen size is actually bigger than my screen, so I only see pretty much the center of the desktop, the bottom edge of the menu bar and I don't see the apps at all on the left side.

Who needs Stanford or MIT when you have Google.

---

### Post by miguelbaines on 2012-09-27
Do you here them? The Angles... they're singing.

Coming to you live, from the ubuntu desktop! Finally!

I just played around with the display sizes and... voila!

Right off the bat had 249mb of updates and I still got a 'fatal internal error' already.

Anyway, I'll expect my degree in the mail.

Peace!

Somebody stamp a big *** SOLVED on this b****.

---

