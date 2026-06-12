---
title: "Partition issues"
date: 2014-05-04
forum: Any Other OS
---

### Post by alexjezuit on 2014-05-04
First off I'd like to say this is a bit unrelated to Ubuntu. I am here because this forum seems to be pretty active and helpful.

I have a Windows (C partition, the 100MB recovery partition, and a Steam partition (for games)

What I had was a dual boot with Windows 8.1 and Linux Mint 16. I had issues with Mint overheating and fans and stuff, so I decided to remove it and install Elementary OS.
I opened the Windows disk manager and deleted the first partition (it was blank) that related to Linux. It deleted all 3 of the blank ones (root, swap, and home?) or at least it shows it deleted them.
Now I have a green Free space 50gb box that doesn't let me create anything new in it.

I booted up my eOS live boot and opened up gParted, and it doesn't let me delete from there either.

I think it might be because my Steam partition is under dev/sda3 but I really don't know. I'm pretty new to partitioning things.
[IMG]http://i.imgur.com/2crjCBk.png[/IMG]
What did I do wrong? I want to keep my Windows, Steam, and 100mb recovery partition and dual boot eOS with it, just like I did with Mint. I am having trouble removing mint though.

Here's a picture in case it helps describe what my partition setup looks like

---

### Post by oldfred on 2014-05-04
Moved to other OS since not Ubuntu.

Post this.
sudo parted -l

Logical partitions must start with sda5.

Do not use Windows to modify partitions except for shrinking a NTFS partition. It does not show Linux partitions correctly, usually rewrites partition table without Linux partitions that are logical and may convert to dynamic partitions which do not work with any Linux and even some Windows repair tools.

---

