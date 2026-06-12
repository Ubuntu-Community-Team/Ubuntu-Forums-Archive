---
title: "kubuntu won't detect mp3 player"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by ecoppel on 2007-12-23
The player is an IS-Music player, aka cheap, no-name brand I got on eBay a few years ago.  I was using Debian before I switched to Kubuntu, and it worked with Debian.

I don't get a message when I plug it in: it just doesn't detect it.  (I tried my thumb drive, and it detected that OK, so it's just the player.)

dmesg |tail didn't give me anything about USB devices at all.

lsusb gave me the same three devices whether it was plugged in or not (and I only *have* one device plugged in apart from the mp3 player.)

I tried plugging it in a different usb port, same results.

What else can I try?

---

### Post by benerivo on 2007-12-23
You could try going to media:/ in konqueror, to see if there is an icon there. I had a similar problem and ended up creating an entry for my mp3 player in /etc/fstab so that i was able to mount it. Try plugging it in and using ```
blkid
``` in a terminal to see if it picks it up at all.

---

### Post by ecoppel on 2007-12-23
> **benerivo said:**
> You could try going to media:/ in konqueror, to see if there is an icon there. I had a similar problem and ended up creating an entry for my mp3 player in /etc/fstab so that i was able to mount it. Try plugging it in and using ```
blkid
``` in a terminal to see if it picks it up at all.

That gave me

```
/dev/sda1: UUID="85a853f1-695d-4e45-8108-980fb3d5c782" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="7739b3c3-f992-42f5-9fc7-69c66d9acf66" TYPE="swap"
```

The same whether or not it's plugged in.

media:/ just has CD and floppy drives.

---

### Post by benerivo on 2007-12-23
Have you been able to try it in a a windows or mac machine to see if it is picked up there? I think blkid should pick up all local hard and usb drives whether they are mounted or not, so as it has returned nothing it seems as if it has not been noticed. Also the dmesg | tail command should pick up any new usb connections. Try running ```
dmesg
``` and scrolling to the bottom of the list (the 'tail') to take a quick glance at what it looks like. Then plug in the mp3 player and run dmesg again. Is there anything new at the bottom of the list?

---

