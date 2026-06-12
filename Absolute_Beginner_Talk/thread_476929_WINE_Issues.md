---
title: "WINE Issues"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-06-17
Ok, I installed WINE, and I can run programs like Notepad, but when I try entering the path for games like Rise of Nations, it says that WINE cannot find the path specified.  For example, to run Rise of Nations, I will enter in the terminal:

```
wine "c:\program files\microsoft games\rise of nations\nations.exe"
```

Is that not how I'm supposed to run programs, or am I doing it wrong?

Thanks.

---

### Post by avik on 2007-06-17
The reason it's not working is that there's no concept of "C Drive" in Linux.  The best path is to reinstall the game using WINE from the very beginning.

If you really want to play games installed on your Windows Partition (I'm not sure that exactly possible, because it might not be able to find the supporting data), you'll have to be able to access the partition with Windows on it, then supply the path to the game as such:

```

wine /media/*<windows_partition_name>*/Program\ Files/Microsoft\ Games/Rise\ of\ Nations/nations.exe

```

Remember that Linux is case-sensitive and it does'nt recognize backslash (\) as a file path separator.

Your best bet is still to reinstall it.

---

### Post by Sonofmoog on 2007-06-17
Wine has made great strides in a very short time, but it does not run everything, and it can sometimes be risky to try.  

Couple things to try:

1) Install Rise of Nations using Wine
2) Linux does not recognize drive designations like C:  If your C: drive is mounted on /media/hda1, try modifying your path to "/media/hda1/program files/microsoft games/rise of nations/nations.exe"  Adjust your path accordingly ..

HTH

---

### Post by Yes on 2007-06-17
How would I install it using WINE?

---

### Post by Sonofmoog on 2007-06-17
> **Yes said:**
> How would I install it using WINE?

```
wine <mount point of CDROM>/setup.exe
```

---

### Post by Yes on 2007-06-17
Thanks.

---

### Post by Irti on 2007-06-18
how do i give the mount point of the cd rom..???.....what is the meaning of this mount point?? am new to linux... i know these are basics but i seriously still dont know the concept of this mount point...............

---

### Post by cooper6581 on 2007-06-18
a "mount point" is the directory in which your cd-rom, your ipod, any removable storage device or network storage device is mapped to.

Example:

mount /dev/cdrom /media/cdrom

/dev/cdrom is the physical device path to my cdrom drive, /media/cdrom is a directory on my hard drive so I can browse the cdroms contents.

---

### Post by gdoermann on 2007-06-20
I'm having issues installing some software... it is the Dell Printer software.  When I type 
```
sudo wine /media/cdrom1/setup.exe 
```
I get:
```
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:process:IsWow64Process (0xffffffff 0x33fb70) stub!
fixme:win:User32InitializeImmEntryTable (0x19650412): stub
fixme:actctx:CreateActCtxW 0x34f8e8 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x34f8b8
fixme:actctx:CreateActCtxW 0x34f048 00000008
fixme:advapi:CheckTokenMembership (0x78 0x16e900 0x34f274) stub!
fixme:actctx:ActivateActCtx 0xf00baa 0x34f4a0
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx (nil) 0x34fd38
fixme:actctx:ActivateActCtx 0xf00baa 0x34fd2c
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:module:LdrInitializeThunk "MPR.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"O:\\install\\x86\\instgui.exe" failed, status c0000142

```

I have no clue where to go from here and how to setup and work with wine!

Note: I ran the command as root to make sure it wasn't an issue of permissions...

---

### Post by Motoxrdude on 2007-06-20
Well, spaces don't work very well with linux. Instead of where there is a space, replace it with a ?.
So like C:/Program Files would be C:/Program?Files

---

### Post by gdoermann on 2007-06-20
> **Motoxrdude said:**
> Well, spaces don't work very well with linux. Instead of where there is a space, replace it with a ?.
So like C:/Program Files would be C:/Program?Files

You can also use a backslash as in:

/media/windows/Program\ Files/...

The easiest way is to type in a couple of letters, then hit tab to fill in the rest!

---

