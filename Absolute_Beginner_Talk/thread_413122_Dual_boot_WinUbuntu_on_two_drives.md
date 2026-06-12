---
title: "Dual boot Win/Ubuntu on two drives"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by kimosabe on 2007-04-18
Hello,
I have been trying to setup dual booting on my PC for two weeks now, using XP and Ubuntu(6.10.17), with no success.
This is what i have:    

80Gb Primary IDE, = 1 Partition containing Windows XP 

160 Gb SATA 1,     = SDA1=/boot, reiserfs
                                  SDA2=/, reiserfs
                                  SDA5=/usr, reiserfs
                                  SDA6=/var, reiserfs
                                  SDA7=/home, reiserfs
                                  SDA8=/temp, reiserfs
                                  SDA4=/swap,  Linux-swap

300Gb SATA 2.  = 1 Partition containing Data File

What i want to do is leave WinXP exactly as it is and use it's boot loader (NTLDR) to start Windows by default or boot into Ubuntu, without screwing around with the MBR. On my most recent install of Ubuntu, i set grub to be installed to (hd1) which i believe should be (want to be) the 160Gb SATA drive. The problem i have now is that Ubuntu is installed but i can't get to it. 
I've read countless examples of how to adjust grub to boot from  NTLDR, but either they refer to both OS's being installed on the same drive, or with windows on the second drive and fooled into thinking it's the primary, or, that you have access to your Ubuntu install. I even tried to use the live cd and mount my hard drive install but every time i try to chroot into it, it comes up with an error about group something or other.

Am i asking the impossible? Please help.

---

### Post by Razorback on 2007-04-18
Actually, you should boot to your linux drive.  Modify grub on that drive and add windows to its list.  You can modify the grub boot file menu.lst adding the windows drive.  I am doing what you are wanting to do.  I have windows on a SATA drive and ubuntu on an IDE drive.  I boot my IDE drive then use grub to select which one I want to boot to,

---

### Post by bodhi.zazen on 2007-04-18
> **kimosabe said:**
> Am i asking the impossible? Please help.

No, you are just choosing to make your life difficult.

IMO there is no reason NOT to install grub into your MBR.

An easy alternate it to boot the ubutnu CD and choose "c" at the initial grub screen.

Then use tab completion, but type :

root (hd1,1)
kernel /boot/vmilnuz <tab> and select kernel

continue with ... 

kernel /boot/vmlinuz-x.y.z root=/dev/sda2 ro splash quiet

initrd /boot/init <tab>

complete your initrd line to match your kernel

initrd /boot/initrd-x.y.z

boot

---

### Post by kittyhawk63 on 2007-04-18
I do this all the time.
I install Windows on one drive and after installation I then set it to slave.
I set the other drive to master and install Ubuntu. Ubuntu will automatically set to boot to either drive per your choice. 
Go to terminal and type:
[COLOR=Red] gksudo gedit /boot/grub/menu.lst[/COLOR]
and move Windows to the top of the list. It will then be the default OS to start. Use arrow key on keyboard to select Ubuntu.
Better yet, move Windows just above "Begin Automagic Kernels List."

kh

---

### Post by IndyBob on 2007-04-19
KittyHawk63

Question!  If you set the windows to slave, do you then use the (hdo) (hd1), etc after Windows so it knows what drive to boot to and fool windows amd then do your normal boot language in grub?

---

### Post by kittyhawk63 on 2007-04-19
> **IndyBob said:**
> KittyHawk63
Question!  If you set the windows to slave, do you then use the (hdo) (hd1), etc after Windows so it knows what drive to boot to and fool windows amd then do your normal boot language in grub?

You should not have to worry about this. It should set itself properly. I have not had to make any changes other than the ones I suggested.

Sorry for the long delay in my reply.
kh

---

### Post by kimosabe on 2007-04-19
> **IndyBob said:**
> KittyHawk63

Question!  If you set the windows to slave, do you then use the (hdo) (hd1), etc after Windows so it knows what drive to boot to and fool windows amd then do your normal boot language in grub?

Hey IndyBob,

I haven't changed the IDE drive to slave, I've left it as is (Primary IDE). I was hoping to be able to keep it this way, but from what i'm reading in this thread, it seems as though that's not going to happen.
Since i installed Ubuntu with Grub at (hd1), i haven't been able to boot into it at all. Windows is Ok, but i've lost access to Ubuntu. I know it's there, i just can't get to it. I can't even get grub to load.

BTW, I have an ASUS A7N8X-E Deluxe mainboard with one IDE hard drive and two (non-RAID) SATA drives. I can set the bios to load different HDD 's (eg. HD-0, HD-1,HD-2) in terms of boot device order, but i don't know if it's the same as setting a SATA drive as the primary

---

### Post by kimosabe on 2007-04-22
Hello all,

Just wanted to thank you all for your help. I tried everything that was suggested and still couldn't get it to work. I think it was my copy of Ubuntu Ultimate, that was the culprit. I decided to download 7.04 and got it working very quickly and easily with your input.

Thanks again all.

---

### Post by SuperTeece on 2007-04-22
> **kimosabe said:**
> Hey IndyBob,

I haven't changed the IDE drive to slave, I've left it as is (Primary IDE). I was hoping to be able to keep it this way, but from what i'm reading in this thread, it seems as though that's not going to happen.
Since i installed Ubuntu with Grub at (hd1), i haven't been able to boot into it at all. Windows is Ok, but i've lost access to Ubuntu. I know it's there, i just can't get to it. I can't even get grub to load.

BTW, I have an ASUS A7N8X-E Deluxe mainboard with one IDE hard drive and two (non-RAID) SATA drives. I can set the bios to load different HDD 's (eg. HD-0, HD-1,HD-2) in terms of boot device order, but i don't know if it's the same as setting a SATA drive as the primary


I had a similar problem when I had to reinstall Windows one time. My setup was windows on the first partition and Ubuntu on second of the same hdd. I found that to correct this I needed to boot to my live CD, open a terminal and type:
```
sudo grub

root (hd0,1)

setup (hd0)

quit
```

Pressing enter after each line.

I am by no means an expert so try to get a second opinion before trying this since your setup is different ;)

---

