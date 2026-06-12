---
title: "Sharing an SD card between Mac &amp; Ubuntu"
date: 2012-05-30
forum: Apple Hardware Users
---

### Post by Linux BASHer on 2012-05-30
I'm trying to figure out how to share an SD card between my Mac and Linux netbook. The catch is that it has to be HFS+ formatted.

I installed the hfsplus and hfsprogs packages in Ubuntu. I can read and write to the card  after forcing a remount using the command "sudo mount -o remount,force /dev/sdx". However, after unmounting subsequent mounts will give me read-only access.

Curiously, using the card on my Mac (even just mounting and unmounting) and then in Ubuntu remedies the issue. It seems that OS X is doing something to the card to enable read/write access in Linux. That's fine, but this misses the point, as I won't have my Mac around all the time. What is going on and, most importantly, how I do keep read/write access to the card in Ubuntu?

---

### Post by MisterGaribaldi on 2012-05-30
Why does it have to be HFS+ formatted? It's not like Mac OS X doesn't r/w FAT32.

---

### Post by Linux BASHer on 2012-05-30
> **MisterGaribaldi said:**
> Why does it have to be HFS+ formatted? It's not like Mac OS X doesn't r/w FAT32.

I need to get past FAT32's 4GB limit, and I need compatibility with Time Machine. In addition, HFS+ is far more efficient than FAT32.

---

### Post by Linux BASHer on 2012-06-02
Anyone?

---

### Post by Lars Noodén on 2012-06-02
I share hard drives all the time.  The only thing I can guess at is that journalling should be turned off.  If you create the partition with Linux, it should be that way from the beginning.  On OS X, you need to explicitly turn it off after formatting -- at least on the newer systems.  On the older ones, the option to format without journalling still remains.  

One way of turning it on/off is using the Disk Utility graphical interface, the option is in the File menu.  Another way is via the shell:
```

diskutil disableJournal /Volumes/SomeVolume

```

---

