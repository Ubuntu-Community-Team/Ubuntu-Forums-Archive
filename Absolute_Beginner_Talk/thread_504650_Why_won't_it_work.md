---
title: "Why won't it work?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by -=Viper=- on 2007-07-19
Ok i went full ubuntu thinking that i would not ever need windows ever again but now I see that i need it for some of the games that i play!  I tried to reboot with the windows disk i have in the drive  but it did not boot windows at all but it just went strait to grub.  Do i have to delete the ubuntu partisions and wipe the drive to get windows to work again or something else?  Please help me fix this.  Thanks everyone!

---

### Post by Seisen on 2007-07-19
You need to change your bios to boot off of the cd.

---

### Post by rillip on 2007-07-19
Yup, Seisen has it, grub/Linux has nothing to do with boot order.  Pop in your bios (usually delete, tab or F1 at point during startup) and set it to boot from CD.

---

### Post by -=Viper=- on 2007-07-19
it is set so it boots off CD first but it wont boot off it...

Edit:  Do you mean only boot of CD or set it first?

---

### Post by ubanchaos on 2007-07-19
what games ru trying to play just shoulda dual booted so u wont have to switch computers alot

---

### Post by crucis on 2007-07-19
You have to enter your bios, set your boot sequence such that the computer tries to boot the cdrom (windows xp cd) before the first hard disk (where grub resides in).

If you already have windows xp residing on the same hard disk as ubuntu, ensure that you did not delete the windows partition when you installed ubuntu.

Finally, i wonder if you tested out those games with wine? Some windows games actually work pretty well with it.

---

### Post by rillip on 2007-07-19
> **ubanchaos said:**
> what games ru trying to play just shoulda dual booted so u wont have to switch computers alot

Little late for that now... :roll:

Anyway, yes, it should be set to boot first.  If it's not booting the CD, then there's a problem with the CD.  Try it on another computer.  You can try boot only from CD, but I guarentee it will tell you boot disk failure, insert new boot disk and try again.

---

### Post by -=Viper=- on 2007-07-19
> **ubanchaos said:**
> what games ru trying to play just shoulda dual booted so u wont have to switch computers alot

I am Playing LFS but i cant use my wheel for the game in my house cept in my bedroom desk.  I need windows to play it smoothly and i cant get it to boot off the disk

---

### Post by -=Viper=- on 2007-07-19
> **rillip said:**
> Little late for that now... :roll:

Anyway, yes, it should be set to boot first.  If it's not booting the CD, then there's a problem with the CD.  Try it on another computer.  You can try boot only from CD, but I guarentee it will tell you boot disk failure, insert new boot disk and try again.

Tried the disk in another PC and it worked fine.  stupied f***n laptop.  had this problem installin ubuntu x_X  well now its time to fight with windows again :P

---

### Post by rillip on 2007-07-20
Good luck, sorry your cd drive sucks. :p

---

### Post by -=Viper=- on 2007-07-20
> **rillip said:**
> Good luck, sorry your cd drive sucks. :p


lol im backing up my HDD now to wipe the entire drive :P

---

### Post by Mornedhel on 2007-07-20
Also note that with the Linux-friendliness so characteristic of MS Windows, it may refuse to have something else than another install of Windows (or itself) on your primary hard drive (I had this issue with WinXP). And it will erase your MBR and replace it with its own bootloader, which will not see non-MS OSes. You may have to reinstall GRUB.

---

### Post by -=Viper=- on 2007-07-20
ok so you are saying that i should reinstall windows as my primary.  ok i can do that.

---

### Post by Mornedhel on 2007-07-20
Actually, I'm saying it may refuse to install otherwise. As in "I cannot be installed here. I need a Windows-friendly MBR, and that includes ignoring any non-MS OS."

---

### Post by ddrichardson on 2007-07-20
Some laptops cd/dvd work loose, try removing the drive cleaning out the contacter with compressed air  and reinserting the drive.

---

### Post by -=Viper=- on 2007-07-20
> **Mornedhel said:**
> Actually, I'm saying it may refuse to install otherwise. As in "I cannot be installed here. I need a Windows-friendly MBR, and that includes ignoring any non-MS OS."
ok well would wiping the drive let me reinstall windows?  If not then i'm in trouble...

---

### Post by Mornedhel on 2007-07-20
I must have worded this poorly.

If you wish to install Windows somewhere, you'll have to have another install of Windows on the primary partition. Having a single install of Windows is fine, as long as it is on the primary partition.

Installing any Windows anywhere will erase your MBR and rewrite it so you can only choose between booting a Windows version or another Windows version. Reinstalling GRUB fixes this and brings you back to the state where you can choose between booting any of your operating systems.

In other words, you do not have to wipe everything, except if your Linux install is on the primary partition. Then you're screwed, since you HAVE to install Windows there for it to work at all.

Please keep in mind two things :

1. I do not come from an English-speaking country.
2. My above statements may have been plain false. This is just something I deduced while trying to make a Fedora Core 2 and WinXP install coexist.

---

### Post by ddrichardson on 2007-07-20
Further to Mornedhel's last post, if you are going to format and reinstal a dual boot, do Windows XP first - it installs its own MBR without asking.

Then install Ubuntu and Grub will be written to the MBR, giving access to both OS's.

The partition numbers are largely irrelevant. Windows installs itself on the first visible partition - it wont care about anything other than Fat32 or NTFS. In any case Windows can be installed anywhere in the same way as Ubuntu (the boot.ini file defines where to find the NTLDR).

---

### Post by -=Viper=- on 2007-07-20
> **ddrichardson said:**
> Further to Mornedhel's last post, if you are going to format and reinstal a dual boot, do Windows XP first - it installs its own MBR without asking.

Then install Ubuntu and Grub will be written to the MBR, giving access to both OS's.

The partition numbers are largely irrelevant. Windows installs itself on the first visible partition - it wont care about anything other than Fat32 or NTFS. In any case Windows can be installed anywhere in the same way as Ubuntu (the boot.ini file defines where to find the NTLDR).

so i do have to reformat my entire drive then it will work....that is fine since the entire trice is copied onto another drive ( my external)  what a pain!  well whatever.  thanks everyone.

---

