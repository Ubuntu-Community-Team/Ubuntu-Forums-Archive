---
title: "Get Windows"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by julio on 2005-10-01
I have tried everything to get Ubuntu working good on a computer. I've decided to give up, because Linux seems like it's more for advanced users. I'm not trying to offend anybody, but I've decided that i'm going to use Windows instead. Can anybody tell me how I can delete Linux and install Windows? (I have a full install Windows 98 disk)

---

### Post by mlomker on 2005-10-01
> Can anybody tell me how I can delete Linux and install Windows? (I have a full install Windows 98 disk)

Windows 98 is probably as hard to install as linux, actually.  You'll need to boot up on the floppy and run **format c: /s** to reformat your drive for DOS.  From there you change to the CD-ROM drive (probably drive D: but varies) and run setup there.

Afterward you'll spend quite a while figuring out how to get sound, networking, and other drivers installed.  Windows XP is a lot easier to deal with.

---

### Post by bambala2002 on 2005-10-01
Why windows 98? Go for windows 3.11 :D 

Seriously, the stoneage is over! Get XP if you've decided to switch to windows. Windows 98 is not supported by Microsoft anymore. That's one of many reasons not to use it.

---

### Post by xequence on 2005-10-01
Windows 98 is very hard to install, I couldent do it. I did get XP installed though... So, if your computer can run XP well, and you are sure you dont want linux, do it :P

> Seriously, the stoneage is over! Get XP if you've decided to switch to windows. Windows 98 is not supported by Microsoft anymore. That's one of many reasons not to use it.

And maybe their computer isnt new enough for XP...

---

### Post by blastus on 2005-10-01
Since you only have Windows 98 you might run into some problems getting rid of the Linux partitions you may have created. The fdisk program that ships with Windows 98 does not handle non-Windows partitions and may not be able to delete them.

So you may need to boot with the Ubuntu CD and go through the setup routine again but this time deleting any Linux partitions you may have created before. Also, I don't know how you installed Ubuntu, but if you installed GRUB (the Linux bootloader) to the MBR (master boot record) of your hard drive, you will need to boot with a Windows 98 floppy and enter...

```
fdisk /mbr
```

...to remove GRUB from the MBR and install the Windows 98 bootloader to it so that when you install Windows 98 it will boot.

These things have nothing to do with Ubuntu. They have to do with the fact that Windows 98 is extremely old and has problems deleting non-Windows partitions and reinstalling it's boot loader to the MBR. If you had a newer OS like Windows 2000 or XP, you could just boot with them and install them without having to jump through these hoops.

---

### Post by mlomker on 2005-10-01
> Since you only have Windows 98 you might run into some problems getting rid of the Linux partitions you may have created. The fdisk program that ships with Windows 98 does not handle non-Windows partitions and may not be able to delete them.

That's true with Win95 but the last time that I installed Win98 I was able to delete NTFS partitions using the OSR2 version's fdisk.  It might depend upon what version of Win98 that they have.

You are correct, though...they'd have to use FDISK to delete the partition and create a new one before using the Format command that I had mentioned to reformat the drive.  Boy, it has been a while since I've dealt with Win9x in any depth.

```

fdisk # delete partition and create a new one, exit and then reboot
fdisk /mbr
format c: /s

```

Then change to the CD-rom drive and run setup.

---

### Post by imagine on 2005-10-01
You could aswell find out the manufacturer of your harddisk, browse to its site and download a setup program which can be booted from a floppy-disk. Every manufacturer offers something like that.
When you have booted from the floppy-disk just select to overwrite the first sectors of your harddisk with zeros and your harddisk will appear to every OS including Win98 as empty, since the bootmanager and the partition information is gone.

---

### Post by blastus on 2005-10-01
[QUOTE=mlomker]That's true with Win95 but the last time that I installed Win98 I was able to delete NTFS partitions using the OSR2 version's fdisk.  It might depend upon what version of Win98 that they have.[/QUOTE]

I have Windows 98 SR1, that might explain it.

---

### Post by julio on 2005-10-01
My computer can get Windows XP. It's just I got a new copy of Windows 98 SE for free (it has a new product key) so i thought it would be cheaper if I installed windows 98 and then upgraded. Another thing, when I tried to delete the Linux partitions using "fdisk" it asked for the volume label and I don't know how to find it. Also, how can I get a Windows 98 floppy? Thanks for the help.

---

### Post by Omnios on 2005-10-01
If your switching back because or compiling software ignore this.

 But if its more window interface you might in the future try installing the KDE desk top (this can be dont in Ubuntu from synaptic). Its more GUI window like with just about everything customizable from graphical interfaces while also having the customization of Gnome. I just managed to to install a right click open as and run as root right menu thingy by downloading and moving the files to the apropriate file.

 Booting with Win 98 disk and  format C: is pretty straight forward Im very familuar with it lol. Even pretty familiar with win XP reinstalls also. 

 Anyways good luck with win I find when I have my XP running its either for games or just sits there.

---

### Post by blastus on 2005-10-01
[QUOTE=julio]My computer can get Windows XP. It's just I got a new copy of Windows 98 SE for free (it has a new product key) so i thought it would be cheaper if I installed windows 98 and then upgraded. Another thing, when I tried to delete the Linux partitions using "fdisk" it asked for the volume label and I don't know how to find it. Also, how can I get a Windows 98 floppy? Thanks for the help.[/QUOTE]

As mentioned earlier, Windows 98 has difficulty with non-Windows partitions--even just to delete them. Another option you can use is [DBAN](http://dban.sourceforge.net/) to erase everything on your hard drive. DBAN will whack the MBR (which includes the boot loader and the partition table) along with the entire drive.

You should have gotten a Windows 98 boot floppy with Windows 98. If not then you need access to a machine that is running Windows 98 to create one. There are ways to do it without but I don't remember. It's also a pain in the ass because you have to make sure the CD-ROM driver is on the floppy and loads properly so you can access the CD and install Windows.

---

### Post by patrick295767 on 2005-10-01
[QUOTE=julio]I have tried everything to get Ubuntu working good on a computer. I've decided to give up, because Linux seems like it's more for advanced users. I'm not trying to offend anybody, but I've decided that i'm going to use Windows instead. Can anybody tell me how I can delete Linux and install Windows? (I have a full install Windows 98 disk)[/QUOTE]


For desesperated with linux, I tried to add all my progress in this post 
cos i started with linux one-2weeks ago
[http://www.ubuntuforums.org/showthread.php?t=64557&page=1](http://www.ubuntuforums.org/showthread.php?t=64557&page=1)

Every single details of installations are written there... 
Maybe u can have a look ...

---

### Post by aysiu on 2005-10-01
Microsoft has some official documentation on this as well:

[http://support.microsoft.com/default.aspx?scid=kb;EN-US;q247804](http://support.microsoft.com/default.aspx?scid=kb;EN-US;q247804)

---

### Post by Drakx on 2005-10-01
[QUOTE=xequence]Windows 98 is very hard to install[/QUOTE]

You must be joking right ? :confused:  whats hard about a win 98 install ? damn ive had that installed on satas with an ati x850 all with no problems, how ever xp is better though i prefer (if i must choose one win 2k) :)

---

### Post by nitricacid on 2005-10-01
[QUOTE=julio]I have tried everything to get Ubuntu working good on a computer. I've decided to give up, because Linux seems like it's more for advanced users. I'm not trying to offend anybody, but I've decided that i'm going to use Windows instead. Can anybody tell me how I can delete Linux and install Windows? (I have a full install Windows 98 disk)[/QUOTE]


Maybe you should try a windows based forum

---

### Post by MetalMusicAddict on 2005-10-01
I just wonder why people need to announce their leaving? Seems they just want attention. Dont like Linux/Ubuntu. Sorry to hear that but just leave. :???:

---

### Post by Hobgoblin on 2005-10-01
[QUOTE=julio]My computer can get Windows XP. It's just I got a new copy of Windows 98 SE for free (it has a new product key) so i thought it would be cheaper if I installed windows 98 and then upgraded. [/QUOTE]

Then don't bother installing Win98 at all, just install the XP "upgrade" and input the '98 CD key.

---

### Post by MetalMusicAddict on 2005-10-01
[QUOTE=Hobgoblin]Then don't bother installing Win98 at all, just install the XP "upgrade" and input the '98 CD key.[/QUOTE]
He would have to install it (98) 1st. XP (upgrade) looks for a past installation. Then he would still need a XP key.

---

### Post by nitricacid on 2005-10-01
Why are we still talking about Windows on a Linux Forum?

BTW. you install WIndBlows the same way you installed Linux, just follow the EZ step by step install.
As for serial key just copy one from a computer at your school.
They are on the side of the tower in a little sticker, they all have them.

---

### Post by phen on 2005-10-02
i remember the good times back when you had to tweak your autoexec.bat and config.sys files on the floppy to enable your cdrom. that was so annoying :-)

maybe there are images of bootdisks available on the net, that allready include this stuff...

---

### Post by mlomker on 2005-10-02
> it asked for the volume label and I don't know how to find it. Also, how can I get a Windows 98 floppy?

The volume label is the 'name' of the partition.  That should be visible when you look at the partitions within fdisk.  I can't remember how to get to the screens...I don't have a copy of it around anymore.

---

### Post by mlomker on 2005-10-02
> had to tweak your autoexec.bat and config.sys files on the floppy to enable your cdrom. 

All of the later editions have that done for you.

---

### Post by Error_Msg on 2005-10-02
[QUOTE=julio]I have tried everything to get Ubuntu working good on a computer. I've decided to give up, because Linux seems like it's more for advanced users. I'm not trying to offend anybody, but I've decided that i'm going to use Windows instead. Can anybody tell me how I can delete Linux and install Windows? (I have a full install Windows 98 disk)[/QUOTE]

Oh c'mon, Julio!
You can do it!
Give it another shot, Ubuntu will recognize most everything and then all you need to do is to come back here for advice on fine tunning.

E_M

---

