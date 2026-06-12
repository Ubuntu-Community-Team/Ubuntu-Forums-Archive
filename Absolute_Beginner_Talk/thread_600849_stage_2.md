---
title: "stage 2"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by NavyRSt on 2007-11-02
Hey guys, I know that there are litterally tons of stage * issues on these boards. But, I can't seem to find one that matches mine and all the previous fixes aren't working for me. I'm hoping that there is someone more intelligent than I on here that figure this out, because it's driving me nuts. 

Here's the beginning: (I picked up the computer for free, so excuse the lack of knowledge)
It's a PIII 600MHz, 256mb ram, two IDE and one SCSI HDDs. And NO OS

There was 98 on it at one point in time, but that HDD went tits up a while back I guess.

After about a week of trying to figure out how to run the live CD at a halfway reliable rate (deleting quite splash and adding noacpi generally works well) I got Feisty installed successfully on the SCSI disk.

After installing I was able to have it boot up using the SUPERgrub CD (it was hanging up on stage 1.5). I had SUPERgrub "fix" the MBR and it loaded up ubuntu for it's second time. I was happy with the performance, so I installed all the updates (albeit going to gutsy) and had her restart.

Now SUPERgrub doesn't work and neither does GAG. 

I've done the find, root, setup dance a few times with no change or difference.

I would install on other HDDs but I was having issues before (error22 for instance). I might try it again, if suggested.

One of the things that has bothered me is that I've looked on gparted and it doesn't show any of the partitions. But, bringing up sudo fdisk shows this:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 17.2 GB, 17280442368 bytes
255 heads, 63 sectors/track, 2100 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2007    16121196   83  Linux
/dev/hda2            2008        2100      747022+   5  Extended
/dev/hda3            1025        1234     1686825    e  W95 FAT16 (LBA)
/dev/hda5            2008        2100      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 27.2 GB, 27226644480 bytes
16 heads, 63 sectors/track, 52755 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Any ideas, or suggestions would be greatly appreciated.

Thanks,
Brett

---

### Post by NavyRSt on 2007-11-03
TTT, bump for the day...

Any ideas?

---

### Post by meierfra on 2007-11-03
I  recommend using Xubuntu (256 MB of ram  is pretty low for Ubuntu)

---

### Post by NavyRSt on 2007-11-04
OK, well. I've installed FF on all 3 HDD's and nothing different.

Changes to GAG, nothing different.

Installed xubuntu GG, nothing different. But, the live CD performed better. So, I guess that's an improvment.

I'm still reading up, and trying to learn the code for terminal to find any hidden clues. But, I'd love to hear some suggestions.

Thanks,
Brett

funny thing, when I installed xGG it has the "previous user" menu. Nothing showed up.

---

### Post by NavyRSt on 2007-11-05
OK, I guess I'm asking the wrong questions here. So, I've come up with some new ones.

How long should I wait till I give up on "Loading Stage 2..."?

Is there anything that I can change in the Stage 2 file that would help alleviate issues?

Can I format the MBR from the Terminal program?

Do I need to format the MBR from a DOS/Win style boot disk?

Do I neet to format the MBR (remember, the computer restarts on it's own if I don't run SUPERgrub/GAG/ubuntu live CD)???

Thanks,
Brett

---

### Post by Pumalite on 2007-11-05
Maybe you need a smaller distro. You probably have integrated graphics eating up your RAM. Try: DSL or Puppy.(or stick to Feisty Xubuntu Alternate CD)

---

### Post by NavyRSt on 2007-11-05
gutsy Xubuntu was definitely a good jump in the right direction as far as speed goes. But, the thing that frustrates me is that the standard FF ubuntu WORKED twice in a row before I decided it was stable on the computer and move forward.

I'll try DSL and puppy (?... I'll have to look them up, I guess)

I'll also try the alt CD and see how that works.

Thanks,
Brett

---

### Post by Pumalite on 2007-11-05
You are welcome. Good luck.

---

### Post by NavyRSt on 2007-11-05
OK big edit on the RAM. It's 524mb. I don't know where the 256 came from, but yeah. I was watching the restart for the zillionth time and was kicking myself for giving bad info. 

So, there is another thing to ponder upon. If it's not RAM what would it be???

Also, I was able to completely clear out the MBR with GAG and have stage1 installed from scratch on the MBR (GG Xubuntu). But, it still performs the same. :(

---

### Post by Pumalite on 2007-11-05
Graphics?

---

### Post by NavyRSt on 2007-11-05
> **Pumalite said:**
> Graphics?

32 mb Nvidia :(

when FF was running the right way off the hard drive videos were painful at best.

But, a video card messing up boot loading? Surely the boot would be almost 100% independent of a graphics card, right?

Isn't there a way to change the boot so that there isn't any graphics to it, just like deleting the "quiet splash" on the live CD?  

BTW haven't had to do that with the Xubuntu CDs, which is nice and made me optimistic

Thanks for the ideas,
Brett

---

### Post by NavyRSt on 2007-11-10
I'm going to try to bring this up again.

The alt CD installed just fine. But, the loading sequence is all the same. If I don't run anything at all it just restarts on it's own, I can't even see if it's getting to stage1.5 or not.
If I run the liveCD and have it boot from the first disk I get this:
> Booting from local disk...
GRUB Loading stage1.5.

Grub loading, please wait...
_

If I run GAG or superGRUB:
> Loading Stage2...
_

I don't know how long I'm SUPPOSED to wait for, but I've had both of those sitting on my screen in exess of 30 minutes on more than one occasion waiting for something to happen. Sure, I've heard little ticks here and there, from the computer, for about the first 5 minutes on either startup. But, after that I get nothing, and no amount of *ctrl+alt+F1234567890* changes anything. In fact, I"ll get beeps after F10.

Any more ideas? I would really like to able to use some form of ubuntu.

Thanks,
Brett

---

### Post by NavyRSt on 2007-11-11
TTT...

Anyone?

Bueller?

---

