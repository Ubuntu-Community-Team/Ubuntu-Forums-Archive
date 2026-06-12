---
title: "What I'm sure is a stupid backup question"
date: 2008-06-29
forum: Apple Hardware Users
---

### Post by ubrgeek on 2008-06-29
I built a headless Ubuntu server that I'd like to use for backup. I've RAID 5'd it and the drives are formated with an ext3 filesystem,  My question - and I'm sure it's stupid - is if anyone has any suggestions on backup software that will let me backup a Leopard laptop to the server? It works for copying individual files (i.e. I can drag-and-drop individual files) but Carbon Copy Cloner - which is what I use for regular, mac fs-formatted external drives - doesn't seem to want to work. Any suggestions on software/solutions would be really appreciated.

---

### Post by owlgorithm on 2008-06-29
You could use the terminal and commands like cp and ditto if you can mount your ext3 filesystem (you will need [ext2fsx]("http://ubuntuforums.org/showthread.php?t=841913") for that). Using the terminal and a direct connection to the other machine like USB or FireWire has the fastest transfer speed, which can be good if you have a lot of files.

The easiest way would be to use rsync if you can, because although transfer over a network is slower in overall speed, rsync will tend to be quicker for nightly backups because it only updates changes instead of re-copying the whole thing over.

---

### Post by ubrgeek on 2008-06-29
If I can connect to it and transfer files via drag-and-drop, would that suffice? ext2fsx hasn't been updated in 2+ years, so I don't know if it's entirely Leopard-friendly.

---

### Post by cyberdork33 on 2008-06-29
why don't you just setup Time Machine with a share from the Ubuntu machine?

---

### Post by owlgorithm on 2008-06-29
ext2fsx definitely works with Leopard -- you have to use the developer copy, which is 1.4x. Others have recently accomplished this same task on these forums using ext2fsx.

Then, you will be able to mount ext3 filesystems but will still need a way to connect to the server. One possibility which would enable the use of Time Machine is to set up a samba share on the RAID which you can mount from your Mac. Then, set up your Mac to use that share (when mounted) as a Time Machine backup disk.

---

### Post by ubrgeek on 2008-06-30
Truth-to-tell, I had never thought of Time Machine. I was stuck in the mindset that it's not really good for a bootable backup ... not really thinking that I have no desire to boot from what I'm trying to do ...#-o I'll give that a shot tonight. Thanks all :)

---

### Post by ubrgeek on 2008-06-30
Hmm, using ext2fsx and I can't connect to the remote machine. Uninstall it, reboot, and I can connect again. Going to see if Time Machine works without it. Will post the results.

EDIT:
So, ext2fsx keeps from being able to connect to the server and without it, I can't mount the drive with Time Machine ... Gotta love it :) Time to keep trying.

---

### Post by cyberdork33 on 2008-06-30
> **ubrgeek said:**
> Hmm, using ext2fsx and I can't connect to the remote machine. Uninstall it, reboot, and I can connect again. Going to see if Time Machine works without it. Will post the results.

EDIT:
So, ext2fsx keeps from being able to connect to the server and without it, I can't mount the drive with Time Machine ... Gotta love it :) Time to keep trying.
if you are using samba, the filesystem shouldn't matter. the remote machine sees it as a samba share, period. the server handles the writing to the particular filesystem.

Browse the net for a few tips on getting started with the Time Machine on a Samba share. It can be a pain to get working initially, but after that it works very well. I use a similar system myself.

---

