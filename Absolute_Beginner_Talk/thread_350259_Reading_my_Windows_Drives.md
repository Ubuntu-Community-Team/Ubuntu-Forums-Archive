---
title: "Reading my Windows Drives"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by sketchone on 2007-01-31
Iv just installed Kubuntu i want to know one thing - where can i find my hard drives

like when you go to my computer on windows you can access which ever drive you choose.

maybe im just not getting this today, someone please put me out of my misery thankyou :confused:

---

### Post by TotalRetard on 2007-01-31
> **sketchone said:**
> Iv just installed Kubuntu i want to know one thing - where can i find my hard drives

like when you go to my computer on windows you can access which ever drive you choose.

maybe im just not getting this today, someone please put me out of my misery thankyou :confused:

On the bar up there ^ is a text that says "Places". In the drop down menu there's the button "Computer". When you click it, it shows you your Filesystem. :)

---

### Post by podunk on 2007-01-31
You're not stupid, you're new. :-) You're also slightly wrong - you can't read or write to a Linux drive from Windows without some non free software.

In Linux you can read your Windows drive - and if you install a free program write to it - but I don't recommend writing to Windows from Linux.

Before you can do anything you need to "mount" a drive. For a step by step see this page:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

Since you're new to Linux I'd suggest copying and pasting the commands to start.

Leaving hard drive unmounted unless you explicitly mount them is sort of a security thing - it prevents those little uh-oh moments we all have. :-)

By the way, Kubuntu has a very nice friendly forum here:
[http://kubuntuforums.net/forums/index.php](http://kubuntuforums.net/forums/index.php)

The community is not as large, but real friendly.

---

### Post by vigleik on 2007-01-31
You want to use konqueror as your file browser. I always create a shortcut for starting konqueror on the taskbar after a new install. Your other hard drives (or partitions) should be accessible under /media. If they appear empty, you need to mount them. That involves typing something like "mount /media/hda4" in console. You can have them mount automatically on startup (if they aren't already), search the forum for how to do that.

Also, right click on the desktop, select configure desktop, then behavior --> device icons, check mounted and unmounted hard disk volume to see the hard drives on your desktop. Then clicking on one of them should open up konqueror showing the content.

---

### Post by Brunellus on 2007-01-31
thread title changed the better to reflect nature of support question.  

We're here to help (if we can).  Use the thread title to tell us (succintly) about your problem.  Don't tell us how stupid you are--that is unlikely to solve your problem.

---

### Post by Pugwash on 2007-01-31
So its not safe to write to your windows ntfs partition using ntfs-3g? I'm also seeding around 30 torrents on my windows partition through azureus (running in ubuntu), is that safe?

---

### Post by Brunellus on 2007-01-31
> **Pugwash said:**
> So its not safe to write to your windows ntfs partition using ntfs-3g? I'm also seeding around 30 torrents on my windows partition through azureus (running in ubuntu), is that safe?
ntfs support in Linux is EXPERIMENTAL ONLY.  do NOT attempt it if you have any data on that ntfs partition that you would like to keep.  If it fails, it fails SPECTACULARLY:  irrecoverable filesystem corruption.

---

### Post by Pugwash on 2007-01-31
> **Brunellus said:**
> ntfs support in Linux is EXPERIMENTAL ONLY.  do NOT attempt it if you have any data on that ntfs partition that you would like to keep.  If it fails, it fails SPECTACULARLY:  irrecoverable filesystem corruption.

Oh dear, thanks for the warning. :( Is there any way I can check for filesystem corruption?

---

### Post by Brunellus on 2007-01-31
> **Pugwash said:**
> Oh dear, thanks for the warning. :( Is there any way I can check for filesystem corruption?
sorry if I was a bit harsh.  you can READ ntfs just fine.  just don't WRITE to it.

---

### Post by Pugwash on 2007-01-31
> **Brunellus said:**
> sorry if I was a bit harsh.  you can READ ntfs just fine.  just don't WRITE to it.

No, its fine. If I'm doing something monumentally stupid, I'd like to be informed. Are there any apps that can check for any filesystem damage btw? Thanks again.

Cheers

---

### Post by Brunellus on 2007-01-31
> **Pugwash said:**
> No, its fine. If I'm doing something monumentally stupid, I'd like to be informed. Are there any apps that can check for any filesystem damage btw? Thanks again.

Cheers
fs damage will be pretty clear iffenwhen you boot Windows again. . .

---

### Post by Pugwash on 2007-01-31
> **Brunellus said:**
> fs damage will be pretty clear iffenwhen you boot Windows again. . .

Ok, thanks for the info.

---

### Post by podunk on 2007-02-01
When I said "I don't recommend writing to a windows drive from Linux" I should have said "I don't recommend writing to a *NTFS* drive in Linux." The software to write NTFS is alph as Brunellus pointed out.

It is perfectly safe to write to a fat32 (vfat) drive/partition with Linux. I keep a partition on my drive just for that to share files safely with windows.

To check your windows file system
Boot windows
Chose the recovery option.
At the prompt type 
chkdisk
fix coffee. Have breakfast, wash dishes. :-D

---

