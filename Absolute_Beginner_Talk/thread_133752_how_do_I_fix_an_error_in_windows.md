---
title: "how do I fix an error in windows"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by hottrodd95 on 2006-02-20
while installing Ubuntu some error happend and I can not get windows xp up and running in the dual boot mode. When I try to go in Windows xp it gets to the loading page and it reboots, It gave me a message "The header checksum does not match the computed checksum" with these numbers "C0000227", "rpcrt4.dll" I researched in Microsoft website and it says that I need to extract some files to fix the problems but I can not reach the command prompt to extract. I always get to "grub>" and I can not do anything. How can I fix this problem while using linux?. Thanks in advance!!!!

---

### Post by paxmaster on 2006-02-20
well how about boot in you window xp, and I am sure there an option to restore your window xp 
and that don't work download the dll file to your floppy disk and restore it, you need to know ms dos to fix your dll

---

### Post by pdc303 on 2006-02-20
It sounds like rpcrt4.dll has become corrupted.

See this thread:
[http://forums.devshed.com/computer-hardware-103/stop-c0000221-bad-image-checksum-the-image-rpcrt4-dll-is-108442.html](http://forums.devshed.com/computer-hardware-103/stop-c0000221-bad-image-checksum-the-image-rpcrt4-dll-is-108442.html)

You could try replacing the .dll file.
You could boot from your Windows disk if it's XP and use the 'Automatic Recovery' thing which checks and replaces a whole load of .dll and system files.

I really don't see how the Ubuntu installer could have caused this. The last thing it would do is touch your Windows files.

---

### Post by hottrodd95 on 2006-02-20
thanks alot, I will try it. But if I download the .dll how can I get it to the windows xp side of the HDD?

---

### Post by qferret on 2006-02-20
Best bet is to boot from the XP CD.

If the automatic recovery fails, you can go into recovery console and pull the file in from a prompt.

---

### Post by hottrodd95 on 2006-02-21
how do you talk to command prompt from "grub>"?

---

### Post by mustang on 2006-02-21
[QUOTE=hottrodd95]how do you talk to command prompt from "grub>"?[/QUOTE]

I believe he meant from the recovery command prompt from booting from a XP CD.

---

