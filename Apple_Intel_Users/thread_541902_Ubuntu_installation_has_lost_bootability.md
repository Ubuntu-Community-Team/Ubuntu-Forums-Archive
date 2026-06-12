---
title: "Ubuntu installation has lost bootability"
date: 2007-09-03
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-09-03
Oh boy, doesn't look like I'm ever going to get bored trying to multiboot several Linux OSes on my Macbook.
Now I have the exact same problem that karl_kashofer reported only an hour or two ago. in that I've lost Grub from my hitherto bootable Ubuntu installation due to getting GParted to create some further partitions.
However, his suggested solution (post #5 [here]("http://ubuntuforums.org/showthread.php?t=541108")) doesn't work for me.
I know I can resolve this if I re-install Ubuntu (leaving the /home partition untouched) but I hope somebody can guide me to a quicker solution.

Here's what's happened so far:

1) Used Boot Camp to create three additional partitions on Mac HD
2) Installed Ubuntu in these three (/, /home and swap)
3)Tried Boot Camp again in effort to create two further partitions, but it refused.
4) So, tried GParted Live CD and this worked fine to create two additional primary ext3 partitions
5) On reboot, however, rEFIt showed no Penguin for my Ubuntu installation.. Not even the "generic hdd symbol." that karl_kashofer reported was there -- just nothing.
6) In OSX, Partition Inspector shows that I now have 7 partitions (i.e. two more than the five I had earlier) BUT the MBR partition table no longer shows Grub in the boot code.
7) S0 I tried the solution outlined by karl_kashofer, using a Sidux Live CD, going into a terminal and trying "find /boot/grub/stage1" once I'm in grub in a terminal.
However, this just gives an error 15: File not found.

Anybody know how I can extricate myself from this (other than re-installing)?
Thanks
Paul

---

### Post by pxwpxw on 2007-09-03
You have to be risk tolerant.
See what the refit Partition (icon) tells you about MBR v/s GPT, one may be ok.

---

### Post by PaulFXH on 2007-09-03
Well, here's what the Partitioning tool says:

```

Current GPT partition table:
#          Start LBA             End LBA                     Type
1           40                        409639                       EFI System (FAT)
2            409640                237387815                Mac OS X HFS+
3            237392505          250726454                 Basic Data
4            250726455           270277559                Basic data
5             270282349          274510864                Linux Swap
6            274518720           293459354                Basic data
7            293459355           312576704                Basic Data

urrent MBR partition table:
# A          Start LBA            End LBA                   Type
1              1                         312581807                 EE  EFI  Protective

Status: MBR table must be updated.

Proposed new MBR partition table:

# A         Start LBA             End LBA                    Type
1             1                          409639                       EE  EFI Protcetive
2              409640                237387815                AF  Mac OS X HFS+
3   *         237392505           250726454                83  Linux
4              250726455          270277559                 83  Linux
```

(Note that this is all manually transcribed, so there may be errors)

---

### Post by PaulFXH on 2007-09-03
I should have mentioned that I did NOT accept the offer to re-write the MBR table as proposed (primarily as I didn't understand the consequences of doing this).

---

### Post by pxwpxw on 2007-09-03
Did you have grub on the MBR before?

---

### Post by PaulFXH on 2007-09-03
Yes, I had looked at the Partitioning Inspector earlier today (before this mess-up) and it had mentioned that the MBR had Grub as its Boot Code.
Now, it just says Boot Code: None.

However, if you are asking if the table I transribed had previously any mention of Grub, I'm almost certan that it did not.

---

### Post by pxwpxw on 2007-09-03
OK time for risk taking.

1. Let refit do the MBR update, that should make MBR intelligible to grub.

See what happens on restart. (probably nothing new)

2. In grub
```

grub> root (
then press TAB. it should list possibles like hd0
then TAB again, should list partitions
grub> root (hd0,2)
grub> find /
then TAB should list files in root, if thats where linux / exists.

```
When you find /boot/grub/

3. Then you are ready to put grub stage1 on the partition boot sector.
(to be continued)

Wait till i check this post for typos
OK

---

### Post by PaulFXH on 2007-09-03
I won't be able to get to your suggestion for about 2 hours. But I'll post when I've got it done.
Thanks
Paul

---

### Post by pxwpxw on 2007-09-03
OK, i might be asleep by then, I will check the morrow.

---

### Post by Mister.K on 2007-09-03
I've got the same problem but i've got a Santa Rosa MBP and i can't boot live cd. I must use alternate cd, it seems that the alternate shell havn't the same command that the standard shell... and i don't know how i can access parted to restor MBR.

---

### Post by PaulFXH on 2007-09-03
Well, I've got my Penguin back in the rEFIt boot menu and everything is fine once again.
It seems that using GParted to create partitions on the Macbook internal HDD caused two problems:

1) It essentially eliminated the MBR partition table and this now consisted of just one partition extending over the whole disk
2) It corrupted the Grub bootloader on the Linux root partition

However, resolving it wasn't that difficult. Here's what I did:

1) Boot into rEFIt's Partitioning Tool and here accept the offer to update the MBR partition table.
2) Now boot to a Linux Live CD (I used Sidux as I just happened to have it lying around). Open a terminal and type:

```
$ sudo grub
> find /boot/grub/stage1
```
Here I got "(hd0,2)" which corresponds to the third partition on the Macbook internal disk which is where I have put the Ubuntu / partition.
Now, I typed the following:
```
> root (hd0,2)
> setup (hd0,2)
```
and got the following output (transcribed so it may not be exactly word perfect:
```
checking if "/boot/grub/stage1" exists.....yes
checking if "/boot/grub/stage2" exists.....yes
checking if "/boot/grub/stage1_5" exists.....yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"...failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"...failed (this is not fatal)
Running "install /boot/grub/stage1 (hd0,2)  /boot/grub/stage2 p /boot/grub/menu.lst"
...............succeeded
Done
```
Then after a reboot, Ubuntu was bootable again on my Macbook.
I should mention also that after I created the new partitions with GParted, no icon whatsoever appeared in the rEFIt menu for Ubuntu.
However, after I accepted the Partitioning Tools offer to upgrade the MBR partition table, an icon of sorts (but not Tux) did appear for Ubuntu. However, clicking on this got no further than giving a "Missing operating system" message.
An awful lot of this had already been reported in this [thread]("http://ubuntuforums.org/showthread.php?t=541108") by karl_kashofer. So, thanks to him for smoothing the path for me.
Many thanks to pxwpxw for guiding me through this.

---

### Post by buschi on 2008-05-24
hey!

following this description gave me two entries in the rEFIt menu: "Boot Linux from HD" and "Boot Linux from Partition 4".

As I didn't like that, I reinstalled and went in the last tab of the installation procedure to "Advanced". There, I selected /dev/sda as where to install GRUB. on the first boot, I got the "no bootable device" message, but after running the rEFIt partitioning tool to fix the MBR, it just worked. No need to install GRUB manually!

Best,
Sebastian.

---

### Post by cyberdork33 on 2008-05-25
This issue has been addressed. Please go to the new Apple forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

