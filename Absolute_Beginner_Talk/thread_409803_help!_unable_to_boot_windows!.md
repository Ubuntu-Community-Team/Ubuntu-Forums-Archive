---
title: "help! unable to boot windows!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by franklinwho on 2007-04-15
I'm a complete noob to Ubuntu. I installed Ubuntu on a blank slave HD without realizing that I had to do something with grub to dual boot.
Now when I turn on the computer, the system directly boots Ubuntu.
Is there anyways I can get Windows back? or is everything lost?

---

### Post by CARB0N on 2007-04-15
if the linux is on a blank hd, and windows is on another hd (as i interpret your post), then you can try unplugging the slave hd that contains linux

---

### Post by franklinwho on 2007-04-15
I tried that, but nothing happens. After the COMPAQ sign flashes on teh screen for a second or two, it just goes black

---

### Post by seshomaru samma on 2007-04-15
The best way to solve this is:
put the Linux HDD back
Reinstall Grub - put it in the MBR - this way when the computer boots you will get a choice of either Windows or Linux
To reinstall grub - use the liveCD
instructions [here]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Tundro Walker on 2007-04-15
**Back to the Dark-Side...**

An alternate to getting GRUB re-installed is (*shudder*) using your Windows XP CD to reinstall Windows' boot loader on the Master Boot Record (MBR).  (If you're using Windows Vista, then this may or may not work, too).

1) Start up your computer, and DEL, F1, whatever you have to do to get into the BIOS

2) Set the BIOS so your CD-ROM takes priority over all other boot devices (make your HDD the 2nd boot device)

3) Put your Windows CD into the CD-ROM drive, and select "Save Settings and Exit" in your BIOS (usually F10) to reboot

4) Comp should boot from Windows XP CD

[COLOR=DarkGreen]*...Ok, the rest of this is what I gleaned from a bit of googling...*[/COLOR]

5) Press the **"R"** key in the setup in order to start the restoration console.

6) Select your windows XP installation from the list, and enter the administrator password.  NOTE: There may or may not be a bug where it prompts for a password that isn't needed.  Microsoft's knowledge base has an article on this...

[COLOR=Blue][http://support.microsoft.com/default.aspx?scid=kb;EN-US;308402](http://support.microsoft.com/default.aspx?scid=kb;EN-US;308402)[/COLOR]

7) Enter the command **"FIXMBR"** (without the quotes) at the input prompt and confirm the next question with a **"Y"** (without the quotes).

8) Use exit to restore the computer.

After that, you should be able to remove the CD, reboot, and Windows XP should boot up fine.  I'd only recommend this if you absolutely just want to go back to Windows, or if you can't get GRUB to reinstall (or find it too complicated to reinstall).   


**Dual-Boot Me, Big Daddy!**

If you want to dual-boot to Ubuntu, and are having troubles hassling with GRUB, I'd suggest just loading from Ubuntu LiveCD, and doing a new install of Ubuntu from it.   When the Ubuntu install wizard walks you through, just pick your slave HDD to wipe and do the full install of Ubuntu on, and you should be good to go.  Ubuntu does a good job of detecting your Windows version, and installing GRUB to take it into account.  

Granted, it makes Ubuntu/Linux the default bootup OS, so you'll need to manually select the Windows OS from the GRUB menu to boot from.  But, if you want to make Windows your main-stay default, you can change this in your GRUB boot up config file.

In an Ubuntu terminal, type (or copy/paste)...

```
sudo gedit /boot/grub/menu.lst
```If you're using Kubuntu, type...

```
sudo kate /boot/grub/menu.lst
```If you're using Xubuntu, type...

```
sudo mousepad /boot/grub/menu.lst
```Towards the top, you should see a line that says...

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**[COLOR=Red]default        0[/COLOR]**
```change the "0" to "saved" so it looks like...

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**[COLOR=Red]default        saved[/COLOR]**
```This sets GRUB to default to the OS that has the "savedefault" flag.  So, we need to change which one does...  

Head down to the bottom of the file, and look for the OS list GRUB manages...

```
## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro splash quiet vga=791
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
[COLOR=Red]**savedefault**[/COLOR]
boot

title        Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

(... more OS's here...)


```You want to delete the "savedefault" from the linux OS, and move it to your Windows OS.  This makes it the default going forward.  When you're finally ready to make Ubuntu the default, just switch it back to your linux OS.

**SIDE NOTE...**

If you update the linux kernel in Ubuntu, it re-writes the GRUB /boot/grub/menu.lst file to add the new linux kernel to it.  Unfortunately, it sometimes undoes your changes.  So, after a kernel upgrade, you may need to go back into that file, and change it to "default saved" and which OS has the "savedefault" flag on it.  While you're in there, you can also wipe out the old linux kernel's, too, since they start piling up after a bit.

Hope this helps!

---

### Post by carusoswi on 2007-04-15
> **Tundro Walker said:**
> **Back to the Dark-Side...**

If you update the linux kernel in Ubuntu, it re-writes the GRUB /boot/grub/menu.lst file to add the new linux kernel to it.  Unfortunately, it sometimes undoes your changes.  So, after a kernel upgrade, you may need to go back into that file, and change it to "default saved" and which OS has the "savedefault" flag on it.  While you're in there, you can also wipe out the old linux kernel's, too, since they start piling up after a bit.

Hope this helps!

I love stumbling around learning new stuff about computers - and sometimes, I luck out and learn things in the right order just in time.  I use Logmein to communicate to my office computer from home and home computer from the office.  The home computer has a habit of taking itself offline because WinXP runs automatic updates that cause it to reboot (and, when I'm not around, Ubuntu would be the default OS during a reboot).

Annoyed by this, I went browsing for a solution yesterday and came upon a thread that explained how to make a backup of GRUB, then, simply open the menu.1st (or is that menu.lst??) file to put the WinXP section ahead of the Ubuntu sections.  Worked like a charm, but, more importantly, familiarized me with the workings of the Grub file and forced me to make a backup.

Later in the day, during an Ubuntu update suggested as part of the routine to get VMware up and running, the update wiped out the WinXP reference in my Grub.  Had I not been aware of and working with the Grub earlier in the day, I no doubt would have assumed that I had screwed up my machine and would have painfully waded through a complete install of both OS's and all the applications for both.

Instead, I simply opened up the backup menu.lst, copied the windows reference, opened up my Grub and pasted back the XP text from my clipboard, saved, and I was back in business within a matter of minutes.

Sometimes, you just get lucky.

Caruso

---

### Post by Tundro Walker on 2007-04-15
Two recommendations when starting out with any Ubuntu installation (no matter which distro you do)...

**1) Backup /boot/grub/menu.lst**

Back it up somewhere you can access it if your computer won't boot up.  EG: on a flash stick that you can access after a LiveCD boot of Ubuntu.  This is more of a reference backup then a "I'm going to copy it back over because I borked up my original" backup.  This has helped me several times, the least of which was when I was originally dual-booting Ubuntu & WinXP, then decided to install Damn Small Linux (DSL) onto my HD just to play around with it.  DSL wasn't as kind as Ubuntu, and totally wiped out all other OS entries from my GRUB list (for shame!).  Fortunately, all I had to do was pull up my backup menu.lst file, copy/paste in the OS lines for Ubuntu and WinXP, and I was up and running again.

**2) Document all the stuff you do for an installation**

We're not talking about King James Bible version documentation here, just a quickie text file that lists all the tweaks, bug fixes, etc you had to do to get your distro running the way you like, and also list all the packages you installed that you absolutely can't imagine yourself living without.

For instance, when I installed Xubuntu on my old machine, I documented that it didn't have a GUI file search, so I installed gnome-utils to get one.  I also documented how I had to quick-fix the fonts to 96 DPI, otherwise they would keep shrinking until you couldn't read them.  I documented all the spiffy things I love to use that I had to install myself (EG: tilda quake-style console, brightside screen-edge mouse triggers, conky desktop sysmon, etc), and the tweaks I made to each.  For major tweaks, like conky's config file to get it to look "just right", I made a backup of that, too.  For the apps I installed, I turned it into a quick apt-get script that adds all of them, along with package cleanup and such.  So, if I ever have to reinstall (knock on wood), I can get up and running fast.

"Fortune favors the prepared"
"It's only a mistake if you don't learn from it"
"If you fail to prepare, you prepare to fail"

However, "All the skill in the world won't help you when an angel pee's in the touch-hole of your musket", so a little luck is always nice..LOL!

---

### Post by franklinwho on 2007-04-15
Thanks everyone.
I changed the menu.lst file and now windows is booted up.

Would it be safe to wipe the drive with ubuntu on it? or is there a better way to go about it?

---

### Post by Tundro Walker on 2007-04-15
>  Would it be safe to wipe the drive with ubuntu on it? or is there a better way to go about it?Ooh...you don't want to do that!  Once Ubuntu is on a drive, it's pretty much usless trying to get it off.  See, Ubuntu permeates itself into the core of the drive in such a way that any reformatting will destroy the HDD.  Didn't you read the pop-up message that said this before installing!?

(dramatic pause...)

Just kidding...hehe...

You can wipe the disk however you like.  You should be able to use Windows (DOS command-line) FDISK to reformat the drive (which takes a while letting it reformat it all), or just destroy the Ubuntu/Linux partitions (which is faster, but doesn't clean up any bad sectors or such).

If you're uncomfortable using Win/DOS command-line FDISK, you can boot up an Ubuntu live CD, and type the following in a terminal window...

```
sudo gparted
```That will start the Gnome Partition Editor.  There, you can select and destroy the  Ubuntu/Linux partitions on the drive, and replace it all with a FAT32 partition which will let the drive "format" for good slave use in Windows (or Linux).  Again, it's not the same as doing a total HDD reformat...IE: any bad sectors and such will stil be there since you're just wiping out the partition table.

When you boot up Windows XP (Vista, too I assume) with the FAT32 partitioned drive as a slave or secondary master, Windows should detect it, and you should be able to right-click on it in "My Computer".  Scope out the drive options applet to upgrade it to NTFS format if you so choose.

**With that said...**

You may have gotten off to a rocky start, but I personally, I wouldn't give up on Ubuntu so easy.  It was a little culture shock when I first started with it, and, like others, I started by dual-booting with WinXP.  But everything I was doing on WinXP was a hassle..having to verify licenses and such just to d/l Microsoft's development environments, having to spend afternoons "cleaning" the computer.   It was the routine I was used to, and there was a bit of a learning curve with Ubuntu (especially learning to use the command-line more, which is really useful and powerful).  So, I never really gave Ubuntu a full go.

But, WinXP made the choice for me by permanantly destroying itself one afternoon when I used "Disk Cleanup", and chose to delete off the old Win98 installation files.  Seemed logical...I was using WinXP, so no sense in keeping old Win98 installation files around.  

WinXP cleaned the disk all right...I wasn't able to boot WinXP after it was done.  6 hours later using the Windows XP CD and recovery console, I realized it had wiped out tons of critical boot files, and basically needed a  fresh install.  Well, I couldn't fresh install, because the one I was using was a 2nd copy of my roommates, and he had since used it to install WinXP on his mother's laptop.  Microsoft had just recently tightened the validation of WinXP keys, so if I were to reinstall using that copy, I wouldn't make it pass key validation, because his mother's computer would already be registered as using that key.

This forced me to go to Ubuntu full-time.  With a little help from the NTFS-3G package, I was able to finally mount the Windows drive.  I was going to salvage some mp3's off it before re-partitioning for slave use under Ubuntu.  After mounting, I surfed around on it, and realized of 8GB worth of stuff on it, WinXP had wiped out almost everything except ~250MB worth of stuff...so, not only did it wipe boot files, it wiped my mp3's and other stuff I wanted to keep.

The irony is, I never used the Disk Cleanup utility before until that one day.  I preferred to manually wipe out things, or use some DOS batch files to clean up exactly what I wanted to, because it gave me a chance to "walk the garden" and spot any odd "weeds" that may have cropped up.  So, the one time I decided to use Disk Cleanup (on the off chance it may find more stuff to purge then what I already was purging myself) it totally wiped itself off the disk.

I guess the joke to this is, when Microsoft says "Disk Cleanup" they really mean "DISK CLEANUP!"  It's so thurough it even cleans ITSELF off the disk!

So, while there was a learning to Ubuntu and Linux, and a few growing pains, I'm really glad all that happened, because I'm happier now using Ubuntu.

---

