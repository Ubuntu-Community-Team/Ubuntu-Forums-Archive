---
title: "GRUB Blinking _ (On a triple boot machine)"
date: 2012-08-08
forum: Apple Hardware Users
---

### Post by Zerum on 2012-08-08
Hello, recently I updated Ubuntu and when I restarted my computer both my windows and linux partitions were greeted with a flashing _ (My Mac partition works just fine) 
I've searched around for solutions but none have worked, in the attached is a copy of my RESULTS.txt. 
What should I do to fix this problem?

When I run ```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```I get this error. I've already mounted into sda3 (this is where Linux is installed.) ```
/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```

---

### Post by drs305 on 2012-08-08
Zerum,

Welcome to the Ubuntu Forums!

I see you've run the boot info script. Did you do it from the Boot Repair app and did you try using the "Recommended repair" option? 

I don't know if Boot Repair can work with GPT partitions or not, but unfortunately I do know that I can't provide much help with this issue.

I could add "GPT" to the thread title for you, which might get you someone more knowledgeable about it.

There is a link to Boot Repair in my signature line.

---

### Post by Zerum on 2012-08-08
> **drs305 said:**
> Zerum,

Welcome to the Ubuntu Forums!

I see you've run the boot info script. Did you do it from the Boot Repair app and did you try using the "Recommended repair" option? 

I don't know if Boot Repair can work with GPT partitions or not, but unfortunately I do know that I can't provide much help with this issue.

I could add "GPT" to the thread title for you, which might get you someone more knowledgeable about it.

There is a link to Boot Repair in my signature line.
Hello, and thank you! Yes, I've tried running the boot repair app but unfortunately it says "Scanning devices" but it never finishes. It just goes on forever. Any ideas on what to do? 
I would appreciate it if you did. :)

---

### Post by oldfred on 2012-08-08
Moved to Apple sub-forum.

Some older instructions may discuss grub stage 1, 1.5 or 2. Those are obsolete and refer to grub legacy. And normal instructions for standard PCs or even dual boot with Windows do not apply as Macs are different. 

I do not know Macs either but a couple of links:
[https://help.ubuntu.com/community/ubuntupreciseon2011imac](https://help.ubuntu.com/community/ubuntupreciseon2011imac)
 [B] 	[SOLVED] Triple Boot MacbookPro (Lion, Win7, Ubuntu)  
[/B][http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)

---

