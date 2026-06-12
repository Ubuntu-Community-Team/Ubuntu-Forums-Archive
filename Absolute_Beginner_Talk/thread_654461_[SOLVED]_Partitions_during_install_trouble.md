---
title: "[SOLVED] Partitions during install trouble"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by dconstruct on 2007-12-31
Hi.  So, I've decided to install Ubuntu on my HP 530 laptop.  It came with Windows Vista and I'd like to keep it with the partitions it's already made.  There are currently 3 partitions (according to the partition guide during install of Ubuntu).  I've never partitioned before.  In a tutorial I read that there were 3 options to pick and that I should probably pick the first one.  Well, the first option basically says "Guided - use entire disk" and I don't want it to use the entire disk because that will format my Windows Vista.  But, on my install, I only have two options.  And, the other one is "Manual" so I click that.  And, when I get to the partitioner, I see one main root thing like "/dev/sda" and underneath that, i've got three more "/dev/sda1", "/dev/sda2", etc...

Below that, is New partition table (which just seems to erase these and start fresh, which I don't want to do) and Undo changes to partitions which isn't what I'm looking for.

What are my options and what do I do?  The tutorial I was looking at doesn't seem to talk about that.  Please let me know.

Thanks again,

Adam

---

### Post by forestpixie on 2007-12-31
can you open aterminal - applications >accessories - paste this into the terminal

```
sudo fdisk -l
```

paste the output here

---

### Post by dconstruct on 2007-12-31
I'm running it off the live session CD.  Would that still be applicable?

---

### Post by forestpixie on 2007-12-31
yep - the command lists the drives and partitions

---

### Post by dconstruct on 2007-12-31
Okay, I'll give it a go.  I also found this link which seems like it might work or be helpful, just through googling around.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")

---

### Post by forestpixie on 2007-12-31
that's a good link - seen that one 

I'm off out now for a bit - I'll check up later 

if in doubt - post and wait :)

good luck

---

