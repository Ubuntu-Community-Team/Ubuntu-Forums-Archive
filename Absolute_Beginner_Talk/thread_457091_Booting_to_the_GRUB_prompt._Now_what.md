---
title: "Booting to the GRUB prompt. Now what?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by gobrien on 2007-05-28
I'm just booting to the GRUB prompt after todays updates. How do I get back into the OS?

---

### Post by justifier on 2007-05-28
select ubuntu with the up and down keys and press enter

---

### Post by gobrien on 2007-05-28
I've no OS selection options just this,

grub>

and this,

 [ Minimal BASH-like line editing is supported.   For
the   first   word,  TAB  lists  possible  command
completions.  Anywhere else TAB lists the possible
completions of a device/filename. ]

---

### Post by taurus on 2007-05-28
Looks like you may have to reinstall GRUB again.

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by gobrien on 2007-05-28
I did some reading on the forum and thought that might be it, I'll follow the guide and post back here. Thanks for the help so far, I really don't want to do an fresh install I just had everything running nicely.

---

### Post by gobrien on 2007-05-28
I have no idea if this is the right thing to do here, but following the guide I get this.

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

and no change on boot still going to grub> I'm assuming this two failed lines have something to do with it.

---

