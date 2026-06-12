---
title: "Boot Issues"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by kyleriege on 2010-01-28
When I hold option or if I boot through refit I am given two options: Mac OSX and Legacy OS. When I choose Legacy OS I am taken to a black screen that says: Missing Operating System.

I have played around with dual and triple booting and would like to return to single booting with Mac OSX.

How do I get rid of this Legacy OS Option? Please be detailed in the explanation?
Thanks in advance

Below I've posted a partition report.




*** Report for internal hard disk ***

Current GPT partition table:
# Start LBA End LBA Type
1 40 409639 EFI System (FAT)
2 409640 488134983 Mac OS X HFS+

Current MBR partition table:
# A Start LBA End LBA Type
1 1 409639 ee EFI Protective
2 * 409640 488134983 af Mac OS X HFS+

MBR contents:
Boot Code: Unknown, but bootable

Partition at LBA 40:
Boot Code: None (Non-system disk message)
File System: FAT32
Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
Boot Code: None
File System: HFS Extended (HFS+)
Listed in GPT as partition 2, type Mac OS X HFS+
Listed in MBR as partition 2, type af Mac OS X HFS+, active

---

### Post by linuxopjemac on 2010-01-28
can't you just remove refit ? Your mac should be able to boot by itself then I guess.

---

### Post by kyleriege on 2010-01-28
booting into mac is not an issue.
The issue is the Legacy OS that refit thinks is there. 
If I remove refit and hold option while booting, an option to boot into windows exists, however this goes to the same screen that says: missing operating system.
Im hoping to remove the cause of the bootloader thinking an operating system is there when it isn't

---

### Post by linuxopjemac on 2010-01-28
try to ask [here]("http://www.insanelymac.com/forum/index.php?showforum=63"), and report us, if it worked, how you did it.

---

### Post by linuxopjemac on 2010-01-28
[http://ubuntuforums.org/showthread.php?t=1198613](http://ubuntuforums.org/showthread.php?t=1198613)

Tell us if it worked...

---

### Post by kyleriege on 2010-01-29
The second thread worked.
I had to boot from the ubuntu cd.
In the terminal I typed 
sudo dd if=/dev/zero of=/dev/sda bs=440 count=1
I restarted and legacy was gone
thanks for the help!

---

