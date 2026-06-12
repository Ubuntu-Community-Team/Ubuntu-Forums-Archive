---
title: "Gparted not working - Segmentation Error"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-05-04
Hi, i have a Fat32 partition which I want to resize. I have been reading around and I heard that Gparted is the best for this kind of problems.
So i installed Gparted with synaptic, and wanted to run it.
First it asked for the root password and then it runs.
I get the program starting scanning, and then suddenly it vanishes. :confused: 

Since this is not normal I tried to run it in the command line, and there it says "Segmentation error" when it closes.

I 've been looking for a way to get that error go away, and i tried what ktogias says:
[HTML]http://www.ubuntuforums.org/archive/index.php/t-53320.html[/HTML]
But I get a problem saying that i need a newer version of libparted :( 

```
checking whether PED_DEVICE_UBD is declared... no
configure: error: *** Requires libparted >= 1.6.25
```

I have looked for a newer version ( I have version 1.6.21 ) but the version I have seems to be the most recent.
Is this normal or do I have to add more backports? Where can i get the asked version?

If there is a another (more easy) way to get Gparted working, or if there is a better (working?) similar program for ubuntu, please let me know.
Thanks,
Ecthelion

---

### Post by Dogmeat on 2006-05-04
Gparted stopped working some time ago (last year) for me too. The quick and dirty alternative is to use parted. It is a command line program though, so it can be complicated to people who are used to GUI programs. 

If this is your case, then I recommend qtparted, it's like gparted but it's KDE based so if you don't have any KDE apps installed it will download and install a lot of libraries you may not want to have just to run one program. 

It's very likely that you already have parted installed, and qtparted is available in Synaptic.

---

### Post by Ecthelion on 2006-05-05
Yes, i saw qparted in the synaptic but since it was for kde, i didn't installed it.
So it is possible to run KDE programs even when u are using gnome?
I don't care about having to run a lot of stuff as long as i can change that partition.
I could have done it with partition magic in windows, but since it is a partition of 200Gb, and that windows only wants partitions in fat32 of max 32 Gb or something, it didn't seemed safe to me. Especially since windows isn't able to explore the contense of that disk.
I'll try qparted,
thanks!

---

### Post by Sef on 2006-05-05
Download GParted from its website.  Works great.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Ecthelion on 2006-05-10
I downloaded the live cd,
but there's an problem:
When it starts up it asks al your drivers etc
it also asks which video card you are using... but i don't have any.
I mean, my video card is 8mb of my processor or something.
So i don't know what to choose there and i think I take the wrong one, cause after that I can't read anything on my screen anymore.

So I used qtparted.
It works great, except that it don't seems to be able to resize a partition by using empty, unpartitioned bloks that are before the start blok.
I mean, you can expand to the right (wherever that is on a hard disk) but you can't expand to the left...
Is this normal? Because if it is I better start looking for another alternative, otherwise it's going to be a real trick to get my partitions right.

Ps. The partition I want to resize is ext2
I know there is an option to resize and that i should (i think) be possible to resize to the left, because there is a case that says how many bloks it can expand, but it is grey and i can't change it. :mad:

---

### Post by Omnios on 2006-05-10
Persoanly I used qtparted with the ntfs plug ins to resize my partitions found it to work better than qparted which could not resize my partitions at the time.

---

### Post by Ecthelion on 2006-05-12
But I can resize my disks...
The problem is that i cannot change the left border of the partition.
The start blok is like impossible to change...? Is there someone who knows how to change that? The program does see that it is possible to do it, but doesn't seem to be able to pass the change... I don't get any error, I just can't change it since it is grey.
Do I need to install some other package to enable that?

---

