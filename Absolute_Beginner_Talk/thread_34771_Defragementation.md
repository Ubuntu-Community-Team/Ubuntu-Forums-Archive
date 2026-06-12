---
title: "Defragementation"
date: 2005-05-16
forum: Absolute Beginner Talk
---

### Post by shador on 2005-05-16
How do i defragement the HD? What program do i need

---

### Post by ChrisTheGeek on 2005-05-16
If you are running a journalled file system such as EXT3 then I don't think there is any need or real advantage to defragmenting the disk - unlike on Windows.  

Is there a specific reason you wanted to defrag the disk?

---

### Post by Stormy Eyes on 2005-05-16
[QUOTE=shador]How do i defragement the HD? What program do i need[/QUOTE]

You don't need to defragment Linux filesystems. Not ext3, not ReiserFS. Defragmentation is only a concern when dealing with Windows filesystems like FAT32 and NTFS.

---

### Post by ssam on 2005-05-16
even ext2 (which isnt journled) is good at preventing fragmentation.

basically files dont really get fragmented under linux (or mac os X) in the same way as they do in windows, so defragmentation is not neccissary.

sam

---

### Post by shof2k on 2005-05-16
All the linux file systems prevent fragmentation more than windows.  I've upgraded my distro, installed KDE, removed KDE, and installed a whole heap of other stuff, but my drive is less than 4% fragmented.  

Defragmentation isn't really required, unless you want to for a specific reason.  The easiest way to do so is to copy your filesystem to backup then reload it.

---

### Post by shador on 2005-05-16
Hey cool  :)  So i'ts just that stupid windows that gets fragemented huh. :wink:

---

### Post by Sam on 2005-05-16
[QUOTE=shador]Hey cool  :)  So i'ts just that stupid windows that gets fragemented huh. :wink:[/QUOTE]
One thing you have to know, that's an almost-full disc may get fragmented.

---

### Post by N'Jal on 2005-05-17
What about fsck (file-system check). Sorry, I'm not exactally a complete beginer but i have to learn some stuff along my way, so i figure i start at the begining so all the power-users don't confuse me :$.

Anyway i know that fsck has to be run on an unmounted file system. But what does it do? I have used it to repair a file system manually once before and just followed the golden rule "Defaults are a good thing". But i had bad blocks/cloned blocks. Or that was my understanding of it. What exactally was i doing?

NOTE: Any beginers wanting to use fsck DO NOT just open up the terminal and start it, this can break your computer.

Off-topic

Hey shof2k nice pic of the Roxx

---

### Post by Stormy Eyes on 2005-05-17
[QUOTE=N'Jal]What about fsck (file-system check). Sorry, I'm not exactally a complete beginer but i have to learn some stuff along my way, so i figure i start at the begining so all the power-users don't confuse me :$.[/QUOTE]

If you *have* to use **fsck** manually, then you're in deep trouble. There's a reason some geeks use "fsck" as a euphemism for f---. Having said this, I'd start by reading fsck's man page (**man fsck**).

---

### Post by N'Jal on 2005-05-17
No you misunderstood me i HAD to fix my disc manually and it seem's to have worked, in that it runs better than it did before i repaired it. I just want to know is fsck like a defrag only far deeper and what might i have done?

I probibly should have mentioned that i FIXED the bad blocks/super blocks(?) And my system is fine i just really wonder what i was doing.

---

