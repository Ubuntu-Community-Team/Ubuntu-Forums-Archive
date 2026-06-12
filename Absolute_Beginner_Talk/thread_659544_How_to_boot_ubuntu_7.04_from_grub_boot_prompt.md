---
title: "How to boot ubuntu 7.04 from grub boot prompt"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by manmohanpv on 2008-01-05
Hi Frnds,

I have a Grub boot disk. I would like to boot my Dell Inspiron ubuntu 7.04 from the grub prompt.

$df

/dev/sda6            148910586   5544391 135799984   4% /
varrun                 1033280       224   1033056   1% /var/run
varlock                1033280         0   1033280   0% /var/lock
procbususb             1033280       120   1033160   1% /proc/bus/usb
udev                   1033280       120   1033160   1% /dev
devshm                 1033280         0   1033280   0% /dev/shm
/dev/sda3               197599     20945    166614  12% /boot

Please give me steps

thanks
manmohanpv

---

### Post by manmohanpv on 2008-01-06
I tried following commands at the grub prompt (system booted from a grub iso)

I have scsi hard  and two other partions OS (/dev/sda2) and DellUtility(/dev/sda1) already in it and /boot folder starts at /dev/sda3

1. Identify /boot

grub>find /vmlinuz

(hd0,1) 

but this is not going to help if we having other partiotion like OS and DellUtility, so type

grub >kernel (hd0,0)/ Tab Key

show all files under (hd0,0)...now type for next partition 

grub>kernel (hd0,1)/ Tab key

Like that you will able to view the files in all partitions and u will able to identify which is /boot and which is /

so i found (hd0,2) as /boot and (hd0,5) as / (verify from df command)

Now i need to boot the kernal from grub prompt Here i failed, i dont know why it gave me error message

>root (hd0,2)

>kernel (hd0,5)/vmlinuz-2.6.20-16-generic root=/dev/sda6

>boot

it booted, got stuck at some point. Any further help to identify the why it did not boot?

Am i using the correcting file names for booting?

-thanks
manmohan

---

### Post by manmohanpv on 2008-01-06
Update, i get following error message while i boot 

>root (hd0,2)
>kernel (hd0,5)/vmlinuz-2.6.20-16-generic root=/dev/sda6
>boot:


#############

VFS: Cannot open root device 'sda6" or unknown-block (0,0)

Please append a correct "root=" option

Kernel panic- not syncing: VFS: Unable to mount from unknown-block (0,0)

what is wrong with root=/dev/sda6 ? Please advice

-thanks
manmohan

---

### Post by manmohanpv on 2008-01-06
menu.lst file says >>>>>>>

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=f4ec8d38-47e6-44c0-abda-54f
58bc954cc ro quiet splash reboot=b
initrd          /initrd.img-2.6.20-16-generic
quiet
savedefault


why does it use root=UUID instead of root=/dev/sda6

any info?

-thanks
manmohan

---

### Post by manmohanpv on 2008-01-06
Guys, good news, i could able to boot dell inspiron 1420 ubuntu 7.04 from grub prompt

Here, the steps:-

>root (hd0,2)
>kernel (hd0,5)/vmlinuz-2.6.20-16-generic root=/dev/sda6
>initrd /initrd.img-2.6.20-16-generic
>boot

Make sure, /boot and / are pointing to the correct partitions, enjoy!!

-thanks
manmohanpv

---

### Post by logos34 on 2008-01-06
> **manmohanpv said:**
> Guys, good news, i could able to boot dell inspiron 1420 ubuntu 7.04 from grub prompt

Here, the steps:-

>root (hd0,2)
>kernel (hd0,5)/vmlinuz-2.6.20-16-generic root=/dev/sda6
>initrd /initrd.img-2.6.20-16-generic
>boot

Make sure, /boot and / are pointing to the correct partitions, enjoy!!

-thanks
manmohanpv

Just curious...Why ARE you booting from grub prompt? (and your entry doesn't seem like it should work.  but it does.  hmm)

---

### Post by manmohanpv on 2008-01-07
i was trying to learn the boot loader..so found grub, is a nice choice..

i could understand the partitions and how the booting of OS works...its all quite easy...

looking to have multiple OS in my system...so these information would be helpful..

also, if anything happens to my MBR, i would able to solve it easily now...

it works fine in dell inspiron ubuntu 7.04....why do u think it does not?

-thanks
manmohan

---

### Post by logos34 on 2008-01-07
ok, cool....the reason I ask is most people go out of their way to avoid doing anything manually--they want everything done/configured automatically for them, and they're not interested in HOW it works.  You're the curious type, admirable trait.

As for the grub direct boot commands you're using:

> Here, the steps:-

>root (hd0,2)
>kernel (hd0,5)/vmlinuz-2.6.20-16-generic root=/dev/sda6
>initrd /initrd.img-2.6.20-16-generic
>boot

the only thing that puzzles me is the '(hd0,5)/vmlinuz-...' -- you're telling it to look in the root (rather than boot) partition for vmlinuz, but on the root partition the path is **/boot/vmlinuz-**...i.e. it's inside the /boot directory.  I would have thought you wanted to use 'kernel (hd0,2)/vmlinuz-2.6.20-16-generic root=/dev/sda6'
or 'kernel (hd0,5)/boot/vmlinuz-2.6.20-16-generic root=/dev/sda6'

I haven't done it manually in a while (and I have only a separate grub, not separate /boot, partition), so I'm missing something obviously, since it works for you..

> why does it use root=UUID instead of root=/dev/sda6

Since the release of Edgy 6.10 grub and fstab use UUID's.  But you can use the '/dev/sda?' format just as well.  If you use UUIDs, however, remember they change if you ever format a partition.

blkid

ls -l /dev/disk/by-uuid

---

### Post by manmohanpv on 2008-01-08
oops you are right, i was just meddling with all crap, missed to concentrate

>root (hd0,2)
>kernel (hd0,2)/vmlinuz-2.6.20-16-generic root=/dev/sda6
>initrd /initrd.img-2.6.20-16-generic
>boot

OR

>root (hd0,2)
>kernel /vmlinuz-2.6.20-16-generic root=/dev/sda6
>initrd /initrd.img-2.6.20-16-generic
>boot


thanks logos34 for pointing out the mistake.

enjoy

manmohan

---

### Post by logos34 on 2008-01-08
> **manmohanpv said:**
> thanks logos34 for pointing out the mistake.

that's an oops for me too...it looks like I just made it more obvious by replicating it (shouldn't have put the 'hd0,2)' in

anyway, enjoy ubuntu

---

### Post by bodhi.zazen on 2008-01-08
I usually :

root (hd0,2)
kernel /boot/vmlin<tab> root=/dev/sda3 ro quiet splash
initrd /boot/init<tab>
boot

ie Tab completion works with grub too :twisted:

I keep my current Ubuntu install on a "super secret" partition, ie it does not appear on the grub boot screen, you have to boot it manually. 

1. Keeps our the riff-raff
2. Actually I just have not gotten around to re-configuring GRUB (uptime 33 days)

---

