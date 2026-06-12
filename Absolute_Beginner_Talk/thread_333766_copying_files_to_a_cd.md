---
title: "copying files to a cd"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by tekno62 on 2007-01-07
like to know how to copy 2 files to a cd so I can load them on a windows comp

---

### Post by meng on 2007-01-07
Are you using GNOME?
Go to Places > CD/DVD creator
Drag the files from your file browser (nautilus) into the CD/DVD creator window.
Then write to disc.

---

### Post by tekno62 on 2007-01-07
it keeps asking for a name and has name.iso? that right?

---

### Post by meng on 2007-01-07
I'm not sure what it is that you got. Can you explain it again?

---

### Post by chewie124 on 2007-01-10
when I press the write to disc button, a write to disk dialog box pops up, with all of the form controls greyed out.  Then it just sits there, like it crashed.  Any ideas?

TIA

---

### Post by Zzl1xndd on 2007-01-10
I use Brasero myself for burning simple things like data disks. works well. Should do everything your looking for.

---

### Post by itsjustarumour on 2007-01-19
> **chewie124 said:**
> when I press the write to disc button, a write to disk dialog box pops up, with all of the form controls greyed out.  Then it just sits there, like it crashed.  Any ideas?

TIA

I´m getting exactly the same thing...

---

### Post by itsjustarumour on 2007-01-19
Try installing k3b:

```
sudo apt-get install k3b
```

Worked first time for me!  :D

---

### Post by cam_tram on 2007-01-19
Are you writing to your CD burner or to an iso image?

You can try just inserting a blank disc and clicking "Make Data CD", it brings up the CD creator

---

### Post by itsjustarumour on 2007-01-19
> **cam_tram said:**
> Are you writing to your CD burner or to an iso image?

You can try just inserting a blank disc and clicking "Make Data CD", it brings up the CD creator

I was just trying to back up my Home directory in its entirety to a blank DVD.  When using k3b, it told me that some file names were over 64 characters long and that it would have to shorten them.  Perhaps this was the reason that Nautilus (and GnomeBaker) didn´t work - rather than warning me of this and offering a course of action, they just crashed (or ¨failed¨ in the case of GnomeBaker).

---

### Post by bodhi.zazen on 2007-01-19
Off topic:

If you transfer files frm Linux to windows, especially if you downloaded them outside the Ubunt repos, scan them with a windows antivirus before you transfer them to windows.

Linux is not vulnerable to windows viruses, but it can transfer them.

Linux antivirus is not as sophisticated as windows (IMO)

Just urging caution :)

---

