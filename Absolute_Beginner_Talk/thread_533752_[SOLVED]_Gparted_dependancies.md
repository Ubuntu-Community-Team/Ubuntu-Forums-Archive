---
title: "[SOLVED] Gparted dependancies"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Bethrine on 2007-08-24
I wanted to install Gparted but there are so many dependancies. And then it suggests adding ntfsprogs which has another list of dependancies. Not to mention the 'sugested' ones. Will these automatically download or am I looking at a long involved process?

---

### Post by r4ik on 2007-08-24
It is in Synaptic.

---

### Post by Bethrine on 2007-08-24
That's where I clicked on properties, opened the dependancies tab and found the long, scrollable list.

---

### Post by compmodder26 on 2007-08-24
They download automatically

---

### Post by Bethrine on 2007-08-24
how about the 'suggested' ones?  (ntfsprogs)

---

### Post by compmodder26 on 2007-08-24
Yes they will as well, as long as you check to install ntfsprogs

---

### Post by por100pre1 on 2007-08-24
> **Bethrine said:**
> That's where I clicked on properties, opened the dependancies tab and found the long, scrollable list.

Don't worry about it. Just go ahead or use this command to install it:

```
sudo aptitude install gparted
```

Hope this helps. :)

---

### Post by Bethrine on 2007-08-24
how about the suggesteds for ntfsprogs? are these advisable?

---

### Post by Bethrine on 2007-08-24
Wow, that was fast. Thanks!

---

### Post by por100pre1 on 2007-08-24
> **Bethrine said:**
> how about the suggesteds for ntfsprogs? are these advisable?

ntfsprogs is needed only if you want gparted to touch Vista partition or to write in Vista partition. My suggestion to you is NOT to install it. Don't use gparted to handle the Vista's partition, use Vista's Disk Manager instead. Linux NTFS write support doesn't always work as intended. You already have NTFS read capability that IMHO is all you really need. :)

---

### Post by Bethrine on 2007-08-24
I ran that and it automatically installed ntfsprogs too. 

I can't get Vista to start up, it freezes and I am admittedly ignorant of any way to fix it.
I want to pull my photos and addresses from Vista, but I thought of that as another subject. I was reading around and trying to figure out exactly how I have partioned my disk and adjust for any corrections. Experimenting here and learning at the same time :) Am definately open to suggestions!

---

### Post by Aishiko on 2007-08-24
> **por100pre1 said:**
> ntfsprogs is needed only if you want gparted to touch Vista partition or to write in Vista partition. My suggestion to you is NOT to install it. Don't use gparted to handle the Vista's partition, use Vista's Disk Manager instead. Linux NTFS write support doesn't always work as intended. You already have NTFS read capability that IMHO is all you really need. :)
and what if he has XP on a NTFS partation? that OS doesn have any internal way of modifying the partation sizes.

NTFS=Vista Only
NTFS=XP Only
NTFS=Microsoft closed sourse file system

Which of the 3 above statements is true? and btw, only one is.

---

### Post by Aishiko on 2007-08-24
> **Bethrine said:**
> I ran that and it automatically installed ntfsprogs too. 

I can't get Vista to start up, it freezes and I am admittedly ignorant of any way to fix it.
I want to pull my photos and addresses from Vista, but I thought of that as another subject. I was reading around and trying to figure out exactly how I have partioned my disk and adjust for any corrections. Experimenting here and learning at the same time :) Am definately open to suggestions!
og ahead and get it and also get the NTFS filesystem readers/writers from the repos.  there is an element of risk to write but so far I'm told just reading the data is safe.

---

### Post by Bethrine on 2007-08-24
> **Aishiko said:**
> 

NTFS=Vista Only
NTFS=XP Only
NTFS=Microsoft closed sourse file system


My pc came with Vista installed, ntfs. I don't know what the last one is? In ubuntu I gound a first partition of about 13GiB (gigabytes?) apparently a backup.

---

### Post by Aishiko on 2007-08-24
NTFS is the a M$ closed sourse fiklesystem which means it's hard to write and develop drivers for it, and it has been used for I beleive NT, Server 2000 and 2003, Media Center, XP, and Vista.  I recommend going with evrything especially if tyou can't get into Vista or don't have it to deal with your problems just read the other tutorials on that here, things like backing up important data, and defraging before you do anything, are important things to do.

---

### Post by Bethrine on 2007-08-24
> **Aishiko said:**
> things like backing up important data, and defraging before you do anything, are important things to do.

yeah, figured that out the hard way ](*,) ](*,) what is IMHO?

---

### Post by r4ik on 2007-08-24
In my humble opinion

---

### Post by Bethrine on 2007-08-24
what is IMHO?

---

### Post by por100pre1 on 2007-08-24
IMHO means in my humble opinion. Try using Vista's disk to check for errors, Linux ntfs write support is not ready for prime time. :(

---

### Post by Bethrine on 2007-08-24
Oh. :)     I'll try that.

---

