---
title: "two ubuntu on one partition, deleting one?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by gagatz on 2006-11-01
Hello, I have the following situation: The primary master contains a windows partition the primary slave contains one ubuntu installation, that i want to use and a second ubuntu installation, that i want to delete. The problem is, that grub searches for the menu.lst in the second partition, such that if i delete this partition, i expect that ubuntu can no longer start, cos the boot manager will fail to find any boot menu. Am I wrong with this conclusions, and if not, what can i do to remove the second ubuntu installation securely and leaving the first as is?

Thanx, niko

---

### Post by adam.tropics on 2006-11-01
[This should sort you out!]("http://www.ubuntuforums.org/showthread.php?t=282855&highlight=restore+grub+live+cd")

---

### Post by matthewv on 2006-11-01
> **adam.tropics said:**
> [This should sort you out!]("http://www.ubuntuforums.org/showthread.php?t=282855&highlight=restore+grub+live+cd")
If you can still boot to both ubuntu partitions, it should be even easier. All you need to do is run 'sudo grub-install hd0' from the ubuntu install you wish to keep. This will rewrite the grub install in the boot sector with one that points to the partition of the ubuntu you wish to keep.

---

### Post by iammeagain on 2007-06-23
i have two ubuntu partitions, but what to keep both of them. One is Kubuntu the other is Ubuntu. I don't like mixing up my Gnome and KDE programs, so i just put them on seperate parititions. But I can only boot the one i installed first. Grub failed to install with the second system.

---

