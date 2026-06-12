---
title: "I've lost my files {literally}"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by Quinch on 2006-02-12
Let me say, first off, that you're free to laugh at me. I know I would if it happened to you.

This is the situation. I've got three HDs; 

HDD#1 for my Windows system {4GB}, which doesn't really matter in this case, but just in case.

HDD#2 for my files {pictures, programs, logs, so on and so forth}, 80 gigs, FAT32, two partitions 40 GB each.

And HDD#3 for Ubuntu, installed about two days ago, 60 gigs.

So, today I came to an idea; since HDD#2 stared acted rather funky some time back, and I got hints from various programs that the filesystem had some problems, I figured this was as good as time as any to reformat the thing. So, I copied both partitions onto the Linux disk, installed and fired up Gparted, nuked both partitions, remade and formatted them as FAT32 rebooted and went to put the files back on.

Half of which weren't there.

The folder in which I put the first partition, the meat of the matter, as it were, was empty. Void. All that disturbed the silence was the rustling of Trash.Root and .windows-label. The files, which I copied for about half an hour, were gone.

Panicked, I checked the folder with the other partition. It's there. Everything in place, looks like. I desperately checked the folder size in case, maybe, I copied the first partition into there. I didn't. Ten gigs and that's all.

A brief bout of hyperventilating later, I checked the disks. To my great relief, HDD#3 had barely four gigabytes of disk space left, which meant that *something* was taking up a whole lot of space somewhere on the disk. To the tune of twenty-four gigabytes, but that may be just wishful thinking on my behalf. 

But the thing is... I can't find the files. Anywhere. At all. "Search for Files" doesn't seem to search very hard {I've looked for files I knew were there, and it still drew a blank}, I've checked the size of each folder under "File System", and I can't find anything.

Can anyone please give me a hand with this? I feel like a retard.

Regards,

Quinch

---

### Post by Jimmey on 2006-02-12
Damnit. That's harsh.

Ehrm, these maybe the dumbest solutions ever, but if I where you, here's what I'd do.

Whip open the terminal. To check the contents of the folder that you moved all your files to ( including hidden files ), try

>  sudo ls /name/of/the/folder -a 

To make sure that you're files aren't being hidden by permissions, or whatever. 

With the "search files", try looking for just a specific extension, like jpeg, or mp3. 

Let's know the solution.

---

### Post by newuser111 on 2006-02-12
are you using ext3 or reiserfs for the linux partition?

and the suggestion by jimmey was a good one, login in to a root shell with sudo -i and search all directories with ls -a

---

### Post by Jimmey on 2006-02-12
Anyone that laughs, will get personally beat upon be me, and newuser111.

---

### Post by kombipom on 2006-02-12
I don't know why this would work when GUI Search doesn't but you could try using locate or find in the terminal to search for the files that you know are there (somewhere).

In a terminal:
sudo locate *filename*
or
sudo find / -name "*filename*"

Worth a try.

---

### Post by Quinch on 2006-02-12
Well, after.... many an hour spent in the #ubuntu channel, I've found out {with plenty of help from several people there} a few things.

Neither Find or Locate can locate the files. They seem to not exist anywhere. But this is the odd thing; 

```
root@Computer:/# ls
bin          dev     initrd.img      media  root  tmp      vmlinuz.old
boot         etc     initrd.img.old  mnt    sbin  usr
cdrom        home    lib             opt    srv   var
debootstrap  initrd  lost+found      proc   sys   vmlinuz
root@Computer:/# du -hs
24G     .

root@Computer:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdd2              54G   47G  4.2G  92% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-k7/volatile
/dev/hdd1             243M   24M  207M  11% /boot
/dev/hda1              39G   16K   39G   1% /media/hda1
/dev/hda2              38G   16K   38G   1% /media/hda2
/dev/hdb1             4.0G 1011M  3.1G  25% /media/hdb1
```

The results from "du" and "df" are completely different - "du", counting directories, says only 24 gigabytes of disk space are in use, but "df", counting disk usage, says it's 47 gigs.

And the difference between the two is twenty-three gigabytes, roughly the combined size of the files I can't find.

I've tried running fsck on /dev/hdd2 {and that was an Oddysey by itself}, but it didn't report any errors.

Can someone tell me what in blazes is going on on my computer? 

Thanks in advance,

Quinch
PS: Worse comes to worse, can someone recommend me a disk recovery tool?

---

### Post by Minyaliel on 2006-02-12
I remember having troubles like this, too... but that was when I first installed Ubuntu. (Never let a newbie install their own OS.... :P) I know the space on my laptop's disc was 62 gigs, but well, I too lost all my files but the space on my harddisc was suddenly reduced with 12 gigs but none could tell me why. Ubuntu certainly doesn't take up 12 gigs by itself... I still haven't been able to relocate the files/ find out why the space is missing, so if anyone knows what could've happened and how to fix it, I'm sure there are a couple of people around here who're going to be thanking you on their knees ;)

---

### Post by newuser111 on 2006-02-12
afaik there are no undelete programs for ext3 partitions because of the way the file system stores data

it may be possible with reiserfs, but i have never tried it, see url below

[http://www.antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments](http://www.antrix.net/journal/techtalk/reiserfs_data_recovery_howto.comments)

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/) no clue how to use this

quinch you should look into a program called spinrite, commercial but its supposed to be really good for detecting hard drive failures or correcting them

---

### Post by Zeroangel on 2006-02-16
Have you people tried this command?

du | sort -n

The largest files should show up right at the bottom.

---

### Post by newbie2 on 2006-11-19
> **Jimmey said:**
> Anyone that laughs, will get personally beat upon be me, and newuser111.
[here]("http://www.ontrack.com/special/data-disasters-2006.aspx?hp=Top10_2006") are some 10 examples of SERIOUS disasters :rolleyes:

---

### Post by jaboua on 2006-11-19
> **newbie2 said:**
> [here]("http://www.ontrack.com/special/data-disasters-2006.aspx?hp=Top10_2006") are some 10 examples of SERIOUS disasters :rolleyes:

Thanks man, that really made my day. Now I'll know what to do if I drop my computer from a helicopter...

Back to the original problem, I have no idea what could have happened - but you should still be able to rescue your data. I think your best shot would be to try to recover the original fat32 partition - it will be a lot easier if you haven't started storing data on it yet. If you have, I'm not sure that it can be done outside professional laboratories.

---

