---
title: "Dual boot with XP Pro"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by golfmore on 2007-03-31
Installed 7.04 on my desktop. Did a dual boot. 
It asked if I wanted to install Grub to the MBR, said 'yes'.. On reboot, doesn't show choices, just goes to XP. What to do here? Thanks.

---

### Post by 67GTA on 2007-03-31
From the ubuntu terminal
Code:

sudo grub

You will get a grub> prompt. Enter
Code:

find /boot/grub/stage1

You should see two locations for the stage1 grub. ie. (hd0,0) and (hd0,1)

One will be your ubuntu grub and one will be your kubuntu grub. As long as you know which is which (Let's assume (hd0,0) for this example), just enter at the grub prompt
Code:

root (hd0,0)

You would of course enter the location for your specific stage1 location

then write the instructions to the MBR
Code:

setup (hd0)

type "quit" to exit grub and your rig should now be using your ubuntu grub loader.

---

### Post by golfmore on 2007-03-31
How do I get to the terminal? Do I hit the spacebar or e before it boots? It goes straight to XP now. (I am really new to Linux.) Thanks.

---

### Post by Shmook on 2007-03-31
You'll probably have to load from the LiveCD again; I just had a similar problem, [ this page]("http://www.ubuntuforums.org/showthread.php?t=224351") was helpful, especially post #6

---

### Post by 67GTA on 2007-03-31
Once the live cd is booted click  APPLICATIONS>ACCESSORIES>TERMINAL. You will be asking for root privileges when you type "sudo". You will have to use your password you gave at installation. You may have to mount your Ubuntu partition. Ask if you need anymore help.

---

### Post by YolaGP on 2007-03-31
Have you tried hitting Esc when entering grub? Maybe it's set not to show the grub options. If you hit Esc it will show you the hidden grub options.  (Sorry if I sound so ignorant. I'm new to Ubuntu, but I know this because it happened to me when I installed.)

---

### Post by golfmore on 2007-03-31
I have a 6.1 that is live. My 7.04b is not. Did I download the incorrect 7.04b? I may install the 6.1 again and do this step.    (I'm too paranoid.) Thanks. I will do that.

---

### Post by 67GTA on 2007-03-31
Any Ubuntu live cd will work. Don't be paranoid, this is easy. Just boot your live cd and follow the instructions in my first post. Type each code in one at a time(hitting enter after each one) and you should be able to boot from the grub menu that will list all the operating systems available on your hard drive. If XP is not on the grub menu post back and we can help you get it there.

---

### Post by confused57 on 2007-03-31
> **golfmore said:**
> I have a 6.1 that is live. My 7.04b is not. Did I download the incorrect 7.04b? I may install the 6.1 again and do this step.    (I'm too paranoid.) Thanks. I will do that.
Do what was suggested earlier about pressing "Esc" when prompted during boot of your pc,  this will tell you if grub is installed to your mbr or not.  If this doesn't work, then do the following:

Boot up the 6.10 live cd, open a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

this will show your partition tables...

You can use the 6.1 live cd(or any live cd) to reinstall grub for your 7.04 Feisty install.

See the first link in my signature for installing with the alternate cd, which is probably what your Feisty install cd is.

---

### Post by golfmore on 2007-03-31
67GTA, or anyone, I am using live CD now. Still no grub. I did what you suggested in post regarding the terminal. I installed 7.04 and am using 6.1 live now. When I get to the grub>  prompt, i do the "find/boot/grub/stage1"  and it keeps telling me 'unrecognized command.'  

Am lost again. Thanks.

---

### Post by Maestro23 on 2007-03-31
> **golfmore said:**
> 67GTA, or anyone, I am using live CD now. Still no grub. I did what you suggested in post regarding the terminal. I installed 7.04 and am using 6.1 live now. When I get to the grub>  prompt, i do the "find/boot/grub/stage1"  and it keeps telling me 'unrecognized command.'  

Am lost again. Thanks.

Need a space:

> find (space) /boot/grub/stage1

---

### Post by confused57 on 2007-03-31
> **golfmore said:**
> 67GTA, or anyone, I am using live CD now. Still no grub. I did what you suggested in post regarding the terminal. I installed 7.04 and am using 6.1 live now. When I get to the grub>  prompt, i do the "find/boot/grub/stage1"  and it keeps telling me 'unrecognized command.'  

Am lost again. Thanks.
You're missing a space:
find<space>/boot/grub/stage1

Do you have 2 separate hard drives, one for Windows & one for Ubuntu?  If you do, don't do anything yet about reinstalling grub...post the output of "sudo fdisk -l".  If you only have one hard drive, go ahead and reinstall grub as 67GTA suggested...he's given you some good advice and it's usually better to copy & paste commands rather than trying to type them in a terminal...it's hard to tell where spaces are, the difference between 1 & small L, etc.

---

### Post by golfmore on 2007-03-31
Only have 1 HDD.  I did get to the 'root (hd0,0)' thing..    It shows (hd0,1)   and  (hd1,1)  tried to setup. Did 'setup (hd0,1)  and it said ;couldn't mount.......'                      Good grief... Thanks.

---

### Post by 67GTA on 2007-03-31
You need a space between "find" and" /boot". It should look like find /boot/grub/stage1 and not find/boot/grub/stage1.

---

### Post by 67GTA on 2007-03-31
Hey, conufesed57 is on it. I didn't see the second page. Just ignore me.

---

### Post by 67GTA on 2007-03-31
Don't mean to hijack the thread but man this is annoying. I went over on my ISP FAP limit, and went from 1.5 megs to 56K until it drops back down. By the time I see someone has posted there are several posts made between me viewing the last post and posting a reply. I had forgotten how slow dial up was.:evil:  I guess that'll teach me.

---

### Post by Thisbetom on 2007-03-31
> **67GTA said:**
> Any Ubuntu live cd will work. Don't be paranoid, this is easy. Just boot your live cd and follow the instructions in my first post. Type each code in one at a time(hitting enter after each one) and you should be able to boot from the grub menu that will list all the operating systems available on your hard drive. If XP is not on the grub menu post back and we can help you get it there.

Hey,

I recently made the switch to Ubuntu.  I installed it on 3 partitions with a fourth ntfs partition of 20gigs for Windows b/c I work with Microsoft Visual Studio in my MIS classes.

After I got Ubuntu configured, I put the windows cd in and installed it (it prompted me to reformat the fourth partition of 20gigs and I did).

After the install I found windows had hijacked my machine and found this thread.  I followed the instructions and I now boot directly to Ubuntu... Maybe im missing the concept of dual boot, but am I supposed to be prompted on startup?

I guess my question is, how do I get it to ask if I want to start in Ubuntu or Windows.

Thanks,
-Tom

(update: I found the escape key thing on boot at the 3 second countdown... but I still don't see Window's showing up.  It shows the following:

Ubuntu, kernel 2.6.17-11-generic
Ubuntu, kernel 2.6.17-11-generic (recovery mode)
Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
)

Ill keep looking and post if I find anything, but if you already know the answer as the end of your previous post eludes I would appreciate a quick HOWTO

THANKS AGAIN,
-Tom

---

### Post by 3rr0r on 2007-03-31
Tom

open a terminal and type
```

cd /boot/grub/
```

then type:
```

sudo cp menu.lst.backup

```

now:
```

sudo nano menu.lst

```

You want to set tell grub where your windows xp hard drive is.
Scroll down towards the bottom.  You should begin to see stuff like

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title           Back|Track (on /dev/sda2)
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/sda2
savedefault

```

Also, you can set the 3 secs to 30, how I have it in this menu.lst  Look for this

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         30

```

---

### Post by 67GTA on 2007-03-31
Tom, run fdisk -l in a terminal and post the output. We need to know where windows is located.

---

### Post by 3rr0r on 2007-03-31
> **67GTA said:**
> Tom, run fdisk -l in a terminal and post the output. We need to know where windows is located.

I just tried that and it gave me nothing.  THen I tried fdisk -L and it said wrong input.  For some reason fdisk -l gives me no output.   Odd...

EDIT: it worked when I did it w/sudo.  You need sudo to run fdisk ?

---

### Post by 67GTA on 2007-03-31
Sorry, sudo fdisk -l.

---

### Post by Thisbetom on 2007-03-31
> **67GTA said:**
> Sorry, sudo fdisk -l.

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671   83  Linux
/dev/hda2             638         768     1052257+  82  Linux swap / Solaris
/dev/hda3             769        9611    71031397+  83  Linux
/dev/hda4   *        9612       12161    20482875    7  HPFS/NTFSm
tom@tom-laptop:~$ 

Am I right in thinking I just follow 3rr0r's guide and change the Windows Xp Home edition entry to (hd0,3)?

-Tom

---

### Post by Thisbetom on 2007-03-31
> **3rr0r said:**
> Tom
then type:
```

sudo cp menu.lst.backup

```

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Home Edition
root           ** (hd0,3)**
savedefault
makeactive
chainloader     +1

```

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         30

```

Made a copy of the menu.lst and pasted your the info from the bottom of yours with the hd0,3 change for my partition... 5 second wait time... booted up, hit escape, selected windows... IT WORKS!!!

I dont know if I should be happy or sad (that I can actually use windows again 8-) )... next project is vmware so that I can just stay linux all the time. 

Thanks again for the help,
-Tom

---

### Post by Thisbetom on 2007-03-31
Ohh, one more thing... If I delete "savedefault" from the windows option does that mean i will boot in Ubuntu everytime if I miss that 5 second window to hit the esc key for grub?

-Tom

---

### Post by 3rr0r on 2007-03-31
Let me get the part out of the menu for you ... one sec

Alright, its in the menu.lst (at least this is how I set my default in case I miss the timer).

Look around here:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         3

```

My default is 3... You have to count your entries in your menu.lst file.  For each Ubuntu, and Ubuntu (recovery).  Then the "Other OS's" counts, then the actual other OS.  Let me show you with mine:

0 Ubuntu 
1 Ubuntu (recovery)
2 Other's OS's below this break
3 Windows XP Home Edition
4 Backtrack

So, if I miss the time out of 30 secs, mine will go to Win XP Home by default.  I had it set to 2, which after the timer, does nothing.  That way you have the convenience of picking yourself.  Let me know if that was confusing and glad it worked out!

EDIT: If you don't want to have to count all those other versions (older versions) of the Kernel with Ubuntu showing up like3 or 4 times plus the recovery mode for each kernel, just comment out the older ones.  You can do that by putting a "#" sign at the beginning of the line.  Without the quotes though.  Just  # like so:

```

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

#title          Ubuntu, kernel 2.6.15-27-386
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.15-27-386
#savedefault
#boot

#title          Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
#initrd         /boot/initrd.img-2.6.15-27-386
#boot

```

Notice my newest one is uncommented, then the previous one is commented out.

---

### Post by 3rr0r on 2007-03-31
Basically, everywhere "Title" is uncommented (no # in front) it counts up, starting from 0.

---

### Post by 67GTA on 2007-03-31
You should be able to use the info you have now for Windows and copy it to your Ubuntu /boot/grub/menu.lst and be able to choose wich OS to boot at the grub splash screen instead of hitting escape to boot to Windows. Check out 3rr0r's example of the grub menu.lst he posted earlier.

---

### Post by golfmore on 2007-04-01
Now I get "no OS found"    Going to do a complete new install of 7.04. Will get back to you.

---

