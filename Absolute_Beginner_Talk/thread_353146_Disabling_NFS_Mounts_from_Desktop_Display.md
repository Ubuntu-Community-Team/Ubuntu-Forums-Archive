---
title: "Disabling NFS Mounts from Desktop Display"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-02-04
Hi.
I successfully edited my fstab to mount 4 nfs shares into a folder I created /media/vault.  They appear there and look like natively existing folders.  However, the nfs folders also appear on my desktop and use a similar icon to SMB shares.  Is there anyway to keep the NFS mounted into my filesystem, but not have the icons appear and clutter up my desktop?  Screenshot attached showing mountpoint and desktop.

---

### Post by neilp85 on 2007-02-08
Open up gconf-editor and go to apps->nautilus->desktop and uncheck volumes_visible.

---

### Post by Coburn on 2007-05-28
Wow.  That is great.  I've been bothered by those NFS folder icons for a long time.  One of those little-known corners of the Menu Maze.  Actually it's the same way on Windows--I had to do some research to find out how to disable icons on the Desktop.

So, this post is valuable.  Hope it remains viewable quite a while.

Thanks,

Coby

---

