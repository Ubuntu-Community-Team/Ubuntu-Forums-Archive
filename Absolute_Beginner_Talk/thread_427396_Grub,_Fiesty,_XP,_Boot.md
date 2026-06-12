---
title: "Grub, Fiesty, XP, Boot"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by luke411 on 2007-04-29
I don't know what the deal is, I've done this in the past and had no issues. I installed Feisty as a dual boot on a current XP system and though the XP shows up on the boot menu, it won't boot. I get "starting up..." and then nothing.
   I have reinstalled grub, I have run "fixmbr" from the windows cd and nothing makes windows boot. All that happens when I run "fix mbr" is I can't boot into either. 
   The only thing strange is that when I look at my fdisk -l my devices are listed as "/dev/**s**da" instead of "/dev/**h**da1". I don't know if that has any bearing on the issue or not. My menu.lst file is standard dual boot "Windows (hd0,0)"

Any ideas?

---

### Post by Bigbluecat on 2007-04-29
Don't worry about the hda vs sda thing. Grub makes no distinction and just calls everything hdxx.

h and s were used to make a distinction between IDE and SATA drives.

Now, the first thing to do is to try an get a functioning system so that you can get working again.

I assume you have the windows recovery disk so lets try this:

fixboot
fixmbr
bootcfg /rebuild

I have in the past had fixmbr not do the whole job and needed the extra commands. 

If this does not work then there is another option from the recovery disk which is to start the install process - it then asks if you want to repair the existing installation. I would not go there yet in case there are other issues like missing partition tables etc. We will look for this later if needed. To do this you will need a LiveCD so keep one handy.

---

### Post by tom.clements on 2007-05-04
I have exactly the same problem.. the common thread appears to be SATA drives, but not sure where that leaves us with a fix!

---

### Post by Bigbluecat on 2007-05-04
I have two SATA drives and working OK. I don't think it is SATA.

---

### Post by Mr.Beast on 2007-05-04
More likely a specific chipset (ICH8R...etc)  that Ubuntu is not being discovered, or perhaps grub doesn't like very much.
If XP was working, and now isn't, then it's perhaps a Grub issue rather than a ubuntu problem.
not sure but maybe it does have something to do with grub getting it's hd,s and sd, in a twist?

---

### Post by Bigbluecat on 2007-05-05
I suspect that whatever the issue is it is beyond grub.

Grub works in a couple of main stages. 

1. The master boot record is essentially a pointer - it tells grub where to look for further instructions by pointing where to find your menu.lst.
2.The menu.lst has a few more instructions like where to find the kernel etc.

In the case the menu.lst points to the windows bootloader (see the bottom of your menu.lst file). There should be an instruction there that says "chainloader +1". This basically says that there is another bootloader following.

Once the windows bootloader takes over you are free and clear of grub and linux. There is no further interaction with linux.

Since you get the windows starting bar you are also past the windows bootloader.

Unfortunately it may be that something has become corrupted. The only way I know to fix this is with the windows recovery disk.

---

### Post by Herman on 2007-05-05
I agree with Bigbluecat,
If you are seeing "starting up..." that means Grub has already done its job of chainloading Windows and passing control to the Windows bootloader through Windows's bootsector. It is up to Windows now to boot itself if it is able to.

When Windows can't boot itself and you can't fix it with the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), the next thing to do is make yourself one of these great Windows boot floppy disks and boot Windows with that, here, [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/"). These are not just your ordinary Windows boot disk, these are heavy duty tools that will boot Windows almost no matter what! Even with the MBR and the bootsector corrupted, even with errors in boot.ini or of Windows partition number has been changed, and even if NTdetect.com or NTLDR itself is corrupt or even missing! :)

You will need access to a friend's Windows XP computer to format the floppy disk with and copy the healthy files from. You'll need a copy of boot.ini, Ntldr and Ntdetect.com either from your friend's computer or from a Windows CD. It is important to copy the links instructions on how to format the floppy disk exactly. Otherwise, once the floppy is formatted the files can even be copied to the disk from Linux. Try that, you should be able to boot with that and then hopefully run Windows apps from within Windows to find out what's wrong and fix it. :)

Also, (for others who may be interested), a good thing about using a floppy disk for this type of work is that the boot.ini file if necessary (in this case it shouldn't be), can be written to and edited from Linux. Even if you have Windows XP with NTFS, the floppy disk is FAT32, so you can edit the boot.ini in the floppy disk to boot Windows and if that was why Windows wouldn't boot then you can fix it from within Windows.

Here is a link to another very helpful website that gives you all kinds of extra information on this type of thing, such as what you can do if your computer has no floppy disk drive but you still want to do this, and all kinds of contigencies,  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")

Regards, Herman :)

---

