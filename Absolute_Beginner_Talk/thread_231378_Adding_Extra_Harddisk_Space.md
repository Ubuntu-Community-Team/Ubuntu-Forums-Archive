---
title: "Adding Extra Harddisk Space"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-07
Is it possible to add some extra space from my windows partitions to my Ubuntu partition, when installing I gave Ubuntu 8GB but feel I could do with giving it a couple of extra GB so that i've got a bit of room to spare. I've got everything set up how I like it so I don't really want to reinstall and do it that way! Help much appreciated

Calv

---

### Post by djsroknrol on 2006-08-07
If you have a second HD, you could move your Ubuntu installation to it and shrink your other partition down and then move your Ubuntu partition back.

I did it using Partimage and it worked like a charm. Another poster on here, aysiu has a great site with a lot of info on Partimage or you could Google for it.

---

### Post by xpod on 2006-08-07
Im in the same position as you my friend although i put unbunto on a small 3.2g slave drive just to try out.

Now that im hooked i`d like to steal some of my xp space off my main hd

After defragging xp though it still had a big(relatively)block of blue data further down the disk so im hesitant to try.

I also have a couple of gigs of unallocated space on the end of the xp hd
but upon trying to format it to ext3 for unbunto to use and attempting to mount it(?) my xp would`nt come on (bsod)

I got it back by undoing what i`d done and choosing last good config in xp.

Not really using xp but the kids still all need it


Sorry for jumping on your bandwagon but i hope any info you get might help me.

---

### Post by kebes on 2006-08-07
As djsroknrol said, the easiest way to do all this is if you have an extra hard drive available. In that case, you can copy the partitions you want to save to the extra drive, reconfigure the main drive, and then copy the partitions back over. You could just copy the data, or use something like "partimage":
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
which lets you create and restore images of partitions (like Norton Ghost). There is a LiveCD called "System Rescue CD" that has a bunch of useful tools pre-installed, including partimage:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
However the partimage support for NTFS is still "experimental."

The Ubuntu install CD can also be used as a LiveCD to do similar things. Once booted into it, you can install partimage ("sudo aptitude install partimage"). Also if you start the installer, you'll notice that at the partitioning phase you have the option to resize and move partitions. You could use this to change the size of the XP partition and give more space to Ubuntu.

As far as I know, this will work even if the XP partition has data "at the end." The resizing will move the data and shrink up the empty space that you have left (defragging beforehand is a very good idea, however).

As always, note that resizing partitions is somewhat dangerous! There is always a chance that the partition becomes corrupted. Thus, be sure to BACK UP YOUR DATA before even thinking about trying this!!


Resizing partitions may break your bootloader (GRUB), so you may have to run something like "grub-install" from your LiveCD to fix that (and/or edit "/boot/grub/menu.lst").


So you can certainly try resizing the partition using System Rescue CD or your Ubuntu Install CD... however be sure to backup first.

---

### Post by xpod on 2006-08-07
the moving of partitions on a temporary basis might bo okay if you have a big enough one to move it to.

Unfortunately my xp hd is 40g and xp takes up about 1 third of it(including the separate data) With a 2.2g unallocated space on end.

My unbunto is on a mere 3.2g slave.

I should just be able to use the couple of gigs of UNallocated space thats on the end of xp hd should`nt i?

It`s not anything used by windows but i just cant seem to format it and mount it without it messing up xp booting.

What exactly would be the proper routine to have this small hd with unbunto see and use the unallocated space on the end of main hd WITHOUT it messing xp up.

I dont have xp cd other than a copy of 1386 directory(with xp setup)..
havent managed to make a bootable slipstreamed(with sp2)copy of my xp from it......yet!!

So im really flying by the seat of my pants BUT dont mind the risks.We dont really keeps stuff on the pc`s we have.

I only sat down on a pc a few months ago and the three we have are all mish mashes of bit`s n pieces that i slung together and somehow got working....Xp & ubunto...Kubunto...and win m.e (THAT`ll be linux soon)

BUT a lot of the stuff(windose)ive learned in the last few months is just mabey hampering my learning of this new wonder that is unbunto .

Again....sorry for hyjacking your thread my friend...HOPE you find room for me on here as well as finding room for YOUR unbunto....lol

Ps my xp is fat32..

---

### Post by kebes on 2006-08-07
xpod, from what you describe, you should be able to do the following:

1. Defrag your Windows partition.

2. Boot into the Ubuntu Install CD, and start the "install" process.

3. When you get to the partitioning section, you can resize the Windows partition a little bit, to make room for Ubuntu (as always, resizing a partition is always dangerous, so make sure you have anything important backed-up).

4. In the installer, allocate the remainder of the space for Ubuntu. Remember that you need to allocate space for a swap. So if you have only ~3Gb to play with, you should allocate ~2.5Gb for Ubuntu and ~500Mb for swap. If you have more space then you can make your swap bigger (depending how much RAM you have).

5. Format the new linux portion (which will be "ext3") and the swap, and finish the entire Ubuntu install. In addition to installing everything, it will install a bootloader (GRUB) which will add your windows partition and your linux partition as options during the boot process.


Like I already said, the "resizing" option in the installer is somewhat risky, but it's worth a shot. It should allow you to do what you need.

From your other post I take it that you already tried something like this but then XP wouldn't boot. Note that you have to finish the entire install (not just the partitioning) for GRUB to be installed, which will allow booting of the various operating systems. If you have problems booting XP afterwards (things like "hal.dll error") there are other threads in the forum explaining what to do.

I hope that helps.

---

### Post by djsroknrol on 2006-08-07
> **xpod said:**
> the moving of partitions on a temporary basis might bo okay if you have a big enough one to move it to.

Unfortunately my xp hd is 40g and xp takes up about 1 third of it(including the separate data) With a 2.2g unallocated space on end.

My unbunto is on a mere 3.2g slave.

I should just be able to use the couple of gigs of UNallocated space thats on the end of xp hd should`nt i?

It`s not anything used by windows but i just cant seem to format it and mount it without it messing up xp booting.

What exactly would be the proper routine to have this small hd with unbunto see and use the unallocated space on the end of main hd WITHOUT it messing xp up.

I dont have xp cd other than a copy of 1386 directory(with xp setup)..
havent managed to make a bootable slipstreamed(with sp2)copy of my xp from it......yet!!

So im really flying by the seat of my pants BUT dont mind the risks.We dont really keeps stuff on the pc`s we have.

I only sat down on a pc a few months ago and the three we have are all mish mashes of bit`s n pieces that i slung together and somehow got working....Xp & ubunto...Kubunto...and win m.e (THAT`ll be linux soon)

BUT a lot of the stuff(windose)ive learned in the last few months is just mabey hampering my learning of this new wonder that is unbunto .

Again....sorry for hyjacking your thread my friend...HOPE you find room for me on here as well as finding room for YOUR unbunto....lol

Ps my xp is fat32..

Your backup has to be equal to or greater than your original image. So you need to shrink your Win partition down, and free up some space before you do anything. I've found that equal, or as close as possible works the best with Partimage.

---

### Post by xpod on 2006-08-08
Sorry about delay....(work)

I dont know if im picking you up wrong kebes but i dont want to really touch my xp partition, i only want to use the unallocated space on the end of the drive xp`s on.
I already have unbunto working properly on the little slave drive but it dosent have much space to play with(i.e the constant updates etc)And it already dual boots fine with xp

ALL i want to do is format the 2g UNALLOCATED space on the end of xp hd to something that unbunto on THIS hd could use.

I dont need to take any images of hd`s to stick on other hd`s.

I just need to salvage the little bit of unused & unallocated space on one drive for use with unbunto on THIS drive......Surely i dont need to go through no install procedures just to do that....

Thats what it sounds like your advising but if im just reading it wrong then i apoligies

---

