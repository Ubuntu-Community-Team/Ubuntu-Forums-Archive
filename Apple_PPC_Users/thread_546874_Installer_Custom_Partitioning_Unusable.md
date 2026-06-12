---
title: "Installer Custom Partitioning Unusable"
date: 2007-09-09
forum: Apple PPC Users
---

### Post by Mike081 on 2007-09-09
I tried for an hour to get the installer to work with custom partitioning. The NewWorld boot block would always be set as having a mount point as "/" (root) so the installer would tell me I had to initialize it before I could install. There were also two NewWorld options in the list of formats (ext3, ext2, fat, etc.); neither of them worked. I tried blessing the NewWorld partition from terminal with yabootconfig, but that also failed with an error about not being able to find unionfs.

Before giving up I decided to try the guided installation, with no options. That worked fine. The problem is that I wanted some space on my spare drive for other purposes.

---

### Post by Auria on 2007-09-09
Hi,

how did you create your partitions? The easiest way is often considered to be using gparted (there's a gui for it in the menus somehwere, or you can use the terminal [http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)), parititon as you want, leave empty space (no partition) for Ubuntu, then tell the installer to use the largest available free space.

---

### Post by Mike081 on 2007-09-10
I partitioned it with Disk Utility first, leaving half free for Ubuntu, and the other half as an HFS+ backup. Then I ran the Ubuntu installer and selected "Custom" as my partitioning method so that I could divide up the free space for root, swap, and home; that didn't work. The Guided method works fine though, because it creates the NewWorld boot block.

---

