---
title: "Messed up partitions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by 3dgimp on 2007-11-01
Hi all.

I didnt want to have to resort to a new post, as I know the answers are all available, but in trying to install ubuntu it's all gone horribly wrong.
Background:
I've built a new PC from scratch, and thought I'd give ubuntu a try. So I sot in my 320 gb hdd, put in the ubuntu livecd and start. I load up, install and everything seems to be fine. But the whole setup is sketchy and crashes every 5 minutes. I assumed this might've been because I used 64bit ubuntu. So i get the cd I ordered of 32bit, and try to install that. It fails to automatically create the partitions. So I try this myself. Again setup occurs, and upon rebooting there's no loader. I try to install acouple more times, and these both fail with ubuntu saying my disk is low on space/full.

Problem:
So now all I want to do is wipe my entire hard drive, to let me try to install ubuntu again. I'm looking in GParted and this is what I see.

Partition                        Filesystem          Size                  Used          Unused              Flags
/dev/sda2     (lock)       extended           298.09GB          ---              ---
  /dev/sda6                   ext3                   3.47GB              2.08GB      1.39gb
  /dev/sda10                 ext3                   2.04gb              2.04gb       0.00gb             boot
  unallocated                 unallocated         86.11gb            ---              ---
  /dev/sda11                 linux-swap         164.70mb          ---              ---                     
  /dev/sda8                   ext3                   2.04gb             2.04gb        0.00gb          
  /dev/sda9   (lock)       linux-swap          164.70mb        ---               ---
  /dev/sda7  (warning) unknown             192.78gb        ---                ---
  /dev/sda5   (lock)       linux-swap          11.33gb          ---                ---

Heres an image to better represent my hard drive:
[IMG]http://img215.imageshack.us/img215/2228/dsc01773in3.jpg[/IMG]

Yeh, so its pretty messy. I try to deleted any partition, and it just says unmount any partitions higher than it. I try to umount them in terminal, and it says unmounted once, and then if i view the partitions again in terminal, theyre not there.

I'm sorry if this is simple, but being a complete linux novice, I'm totally confused.

Also, in terminal, when i type "fdisk /dev/sda" i get the error "The number of cylinders for this disk is set to 38913. There is nothing wrong with that, but this is larger than 1024, and could cause problems with 1. sw that runs at boot time 2. booting and partitioning sw from other OSs"

That last warning is putting me off pluging into a windows machine and formatting.

Please please help me. Thanks so much in advance.

---

### Post by Duck2006 on 2007-11-01
Is the gparted on the live ubuntu cd or is gparted on the live gparted cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by 3dgimp on 2007-11-01
It's on the live ubuntu cd. I don't have any blank cds to hand at the moment. Is that a problem?

---

### Post by Jose Catre-Vandis on 2007-11-01
Best to download the Gparted Live Cd or the Parted Magic Live CD (better)  ([http://partedmagic.com/downloads.html](http://partedmagic.com/downloads.html)), burn it and boot up from there. in this way none of your partitions are mounted so you can then wipe your whole hard disk and start again :)

---

### Post by 3dgimp on 2007-11-01
I realised I was being a dunce. I had forgotten to write the new empty partition table. Done that now and all is well. Well, I've yet to install ubuntu...bt aut least my hard drive isnt all crazy.

Thanks for the advice tho.

Ed

---

