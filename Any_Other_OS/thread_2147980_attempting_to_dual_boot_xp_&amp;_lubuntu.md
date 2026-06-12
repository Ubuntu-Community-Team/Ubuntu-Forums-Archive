---
title: "attempting to dual boot xp &amp; lubuntu"
date: 2013-05-23
forum: Any Other OS
---

### Post by aeymxq on 2013-05-23
hello all,

i have lubuntu 10.04 (iirc; it's the latest version with a non-pae kernel) installed on my thinkpad t42p laptop. i am trying to install windows xp.

i use gparted to format the usb to ntfs, then use tuxboot to burn the iso to the usb. all works fine. i reboot, press f12, boot from usb, and get bootmgr missing, press ctrl alt del to reboot.

i've gone through this process like 10 times, sometimes using unetbootin or the dd command in terminal. sometimes the error varies, but i can't get xp to start.

there's nothing wrong with the usb or the computer's ability to boot from usb.

my partition scheme looks like this:

/dev/sda1 ext4 (lubuntu)
/dev/sda3 ext4 (empty: i am planning on installing arch here)
/dev/sda4 ntfs (this is the partition i was planning on putting windows on)
/dev/sda2 extended
/dev/sda5 linux-swap

in writing this post, it occurs to me that maybe the ntfs partition needs to be first? idk if this is the case, though: i assumed the xp installer would be able to select the partition, and the order wouldn't matter cuz the comp is booting from the usb.

anyway, plz halp! ):P

---

### Post by ohnonot on 2013-05-23
i think there's about a million places on the linux interwebs where it says, if you want to install both windows and linux, windows has to be first. and yes, on the first partition of the first hd. fyi, it's because windows is stupid.

---

### Post by aeymxq on 2013-05-23
ugh, used live gparted to reorder the partitions but am still getting this error.

---

### Post by Megaptera on 2013-05-24
I don't think re-ordering the partitions is enough. I suggest you backup all your important docs, pics, tunes etc to external media. Then install XP and then install Lubuntu. The Lubuntu install will set up Grub to over-write the Windows mbr and should then give you the option at bootup to choose between Windows and Lubuntu.

---

### Post by ohnonot on 2013-05-24
that's what i meant!> **Megaptera said:**
> I don't think re-ordering the partitions is enough. I suggest you backup all your important docs, pics, tunes etc to external media.at this point i would also partition the hd to your needs, maybe with gparted from a live cd.> Then install XP and then install Lubuntu. The Lubuntu install will set up Grub to over-write the Windows mbr and should then give you the option at bootup to choose between Windows and Lubuntu.
ps: reading about new hardware, there seems to be other ways, sth about efi, but since i am using old hardware, as are you, op, this solution is 100% what you need to do!!!

pps: you are still able to boot normally into (l)ubuntu???

---

### Post by Megaptera on 2013-05-24
> **ohnonot said:**
>  ... that's what i meant!.... 

Sorry, I didn't mean to imply I was contradicting you, I was hoping to expand a bit on your reply ... apologies :)

---

### Post by ohnonot on 2013-05-24
(searching for a rat-with-sunglasses-smiley)...
dude, i didn't mean that you meant to contradict me!
it's always better to say things in different ways, because understanding what someone else is saying is the most difficult thing in the world and beyond!

---

### Post by deadflowr on 2013-05-24
> **aeymxq said:**
> 
in writing this post, it occurs to me that maybe the ntfs partition needs to be first? idk if this is the case, though: i assumed the xp installer would be able to select the partition, and the order wouldn't matter cuz the comp is booting from the usb.

anyway, plz halp! ):P

Windows boot needs to be in a primary partition, whether the first partition or the fourth, doesn't matter. As long as it's a primary and not logical.

If your having problems booting XP, then post the grub.cfg file so we could have a looksy.
(Use the code tags if you do{# symbol in the reply box toolbar})

This is assuming that lubuntu still boots.
Otherwise, +10 for backing up and starting over.

---

### Post by aeymxq on 2013-05-24
what i am going to try out is running xp via virtualbox. if this meets my needs i may stick with that, but yeah i realize that i might have to reformat the hdd. it's a new install so it isn't really too big a deal.

question, though: is it possible to partition a usb to have multiple live OSs? my usb is quite large, but i would really hate to write xp, format hdd, still get the same error, and then have to go to a net cafe or something to get lubuntu.

---

### Post by ohnonot on 2013-05-24
basically, a usb drive is just another hard drive. so, yes, you can. does it work? will it boot? i don't know. try it!

---

### Post by Megaptera on 2013-05-24
This may help [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)  (quote) " It can be used to create a Multiboot USB Flash Drive containing multiple operating systems, antivirus utilities, disc cloning, diagnostic tools, and more. "

---

