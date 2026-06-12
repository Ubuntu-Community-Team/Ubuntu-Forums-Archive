---
title: "[SOLVED] Using secure file erase on ext2 drive from windows"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Arthur Archnix on 2007-08-18
I've installed the extfs driver to read/write files on my ext2 partition with all my files. I only log in to windows for three reasons: chat with video on skype, run some numbers in spss, and run office 2003 (for instance when I need to edit documents and track changes, or view powerpoint files). 

Ideally, I'd like to be running /dev/sda2 (ubuntu) and my /dev/sda4 (my files) on encrypted partitions, but I'm going to wait for Gutsy before trying to set that up using the inbuilt encryption stuff. Until then, I do feel the need to erase some files securely (as this is a laptop that travels, and that ext2 partition could be easily read).

My question is whether it is safe to use eraser to securely erase files on the ext2 partition with my files? Eraser is windows program, and I know of now native program to do this under Ubuntu. I've been browsing the web, and some eraser forums, but haven't come to any conclusions. Eraser says it only supports "FAT32 and NTFS Files Systems", but since I have the ext2fs driver I don't see why it wouldn't *appear* to work. Whether or not it actually does is another thing altogether.

Oh and by safe I mean, I don't want to corrupt the partition or lose other files.

---

### Post by dreadie on 2007-08-18
It sounds like you might find [this thread]("http://ubuntuforums.org/showthread.php?t=525134") relevant.

No it doesn't answer your question directly, but it does address your problem.

---

### Post by Arthur Archnix on 2007-08-18
Actually, that did answer my question. It made my original intent moot. I have to enable encryption!

I can get rid of my other files after a low level wipe.

Thanks.

---

