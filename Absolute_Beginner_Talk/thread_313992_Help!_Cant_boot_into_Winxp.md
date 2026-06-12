---
title: "Help! Cant boot into Winxp"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2006-12-06
Hi,
This a.m. on starting up win xp, my dual boot xp-ubuntu laptop told me avg7.5 free  detected a trojan in winlogon.exe file, or something to that effect.  I clicked on "heal" and now I cant get back into windows!  I put win xp pro in the cd drive and selected f8 (as suggested on screen by Toshiba).  I was able to get into the screen that has Safe Mode,  but the machine cannot read the windoz cd.  I was trying to copy winlogon.exe from the WinCD to my C: drive as suggested below by the Wilders Security forum:

copy <D:>\i386\winlogon.ex_c:\windows\system32\winlogon.exe

Failed to do so, because when I selected Safe Mode and hit Enter nothing happened.  Is there any way to use Linux to get the laptop to read the Win XP Pro in the CD drive?

Thanks in advance for your help.
[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)
:(

---

### Post by moshuptrail on 2006-12-06
Well, the glib answer would be, "why would you want to?".

But seriously, there might be a way.  The problem is that Ubuntu can't write to a NTFS file system.  So you can't use Ubuntu to copy the winlogon file.  But wait.  I have seen mentioned in this forum some special drivers that you can install to allow writing to NTFS.  Do a search on NTFS and see what you come up with.  

Better yet, you need a bootable windows CD.  You might try to get your PC to boot from either a re-install disk, or an anti-virus program CD and see if that gets you into an XP environment.

You mentioned that you booted in safe mode but had no CD support.  There is another boot option for safe mode that includes CD support.  Did you try that?

---

### Post by jordanmthomas on 2006-12-06
to save you some searching...
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by LDRoamer on 2006-12-06
I think you need to boot into console mode with your windows cd. When you boot the CD you should get the option of a recovery console. I think you should be able to copy the file from there.

---

### Post by LDRoamer on 2006-12-06
Some stuff on the Winxp recovery console here:

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

I am sure a google will get you a bunch more.

---

### Post by pissedoffdude on 2006-12-06
I had a problem once where i couldn't boot into xp.  I put in the xp cd and went to the recovery console.  I dont remember the command because my brother did it for me.  The command was for a check disk.

---

### Post by seshomaru samma on 2006-12-06
What you need is [Knoppix]("http://www.knoppix.org/")

---

### Post by iClouseau88 on 2006-12-09
How can I use Knoppix?  I read a few forums and also googled, but no where did I see instructions on using Knoppix to boot into Windows.  In the mean time, this is what I have done:

1. Changed BIOS settings so that the box boots with floppy drive  first, then CD drive, then HD.

2. Copied 3 files boot.ini, NTLDR and NTdetect.com from another working XP machine into a floppy in order to make a boot disk.

3. Inserted boot disk into the floppy drive, noting that the Windows CD is already in the CDR drive.

4. Turned on the machine.  I could see Windows (Welcome?) Screen, then a blank screen,then for a split second or less I saw a blue screen but it disappeared too quickly for me to read the error message!  The machinecontinued to repeat the whole thing so I turned it off.

What should I do now to get the machine boot into Windows?
Folks, I am really in need of your advice. Thanks a lot.

---

