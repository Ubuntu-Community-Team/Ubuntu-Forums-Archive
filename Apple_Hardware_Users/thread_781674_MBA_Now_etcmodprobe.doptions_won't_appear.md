---
title: "MBA: Now /etc/modprobe.d/options won't appear"
date: 2008-05-04
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-04
Hi,
Simply put, I'm getting almost all the MBA set up. But now, to set the sound, I'm doing what all the threads suggest which is to put this:

```
options snd_hda_intel model=mbp3
```

into the /etc/modprobe.d/options file. But everytime I try to bring that file up, the terminal says 'no such command'. I'm typing this:

```
sudo /etc/modprobe.d/options
```

And I get a response that no such command exists. I have no idea why this is happening. I do appreciate any help on this.

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-04
> **Brightbelt said:**
> ```
sudo /etc/modprobe.d/options
```
You are saying to execute the file that you want to modify. you need to open the file with an editor and edit the file...

```
sudo gedit /etc/modprobe.d/options
```

---

### Post by Brightbelt on 2008-05-04
Wow, Thanks Cyber. I forgot the 'Sudo Gedit' part. It's been a while and I'm rusty...

I had a long absence and so I'm back after a year or so of doing other things. 

Many Thanks, Frank B.

---

