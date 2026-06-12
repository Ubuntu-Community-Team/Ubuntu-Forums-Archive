---
title: "Windows-esque Hidden Files?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-27
Here's my dilemma:

I've got a bunch of folder on a fat32 drive. I need to make certain ones (named folder.jpg) hidden. But it needs to be hidden as in "Windows hidden," not "dot hidden". :)

Does that make any sense? In other words, I don't want:

.folder.jpg

I want the filename to remain the same, but it should act as a hidden file when viewed under Windows.

Is it possible under Linux? I'm not even sure where to begin searching...

---

### Post by Ecthelion on 2007-01-28
Lol

Put them in a "dot-hidden" folder ?

I wouldn't know how otherwise...

---

### Post by IanW on 2007-01-28
> **Ecthelion said:**
> Lol

Put them in a "dot-hidden" folder ?

I wouldn't know how otherwise...

That wouldn't work. "Folder.jpg" is what Windows calls its folder thumbnail (if you're not using the default pic).
It's often used to provide album art to a ripped CD.

---

### Post by finer recliner on 2007-01-28
since its a fat32 drive, i assume you should be able to do it from linux. however i have no ideas either. the folder obviously has certain characteristics that you can edit somewhere (registry?)

---

### Post by Ecthelion on 2007-01-28
Well I really wouldn't know...

Searching in Synaptic for "hide file" gives as most interesting result a "steganography program".
But that's probably not what you are looking for. :D

---

### Post by kidders on 2007-01-28
Hi there,

I think mtools may be what you're after. Among other things, it contains **mattrib**, which emulates the MSDOS "attrib" command.

---

