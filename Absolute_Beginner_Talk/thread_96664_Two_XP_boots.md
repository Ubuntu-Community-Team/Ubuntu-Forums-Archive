---
title: "Two XP boots"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-11-29
I've got another PC I'm wanting to put ubuntu on.  What bothers me about this PC is that there is only one partition (NTFS of course), yet there are 2 options on the windows boot screen for XP.  The top one leads to the 'healthy' installation while the other...well...let's just say it leads to a very dark and scary place.  I'm not sure what happeded for this to take place, but at any rate I want this other boot option gone.  How do I do this?

Also, can I use a windows install disk to resize the NTFS partition?  I tried using the ubuntu install disk in the past, but it loops back whenever I try to resize.

---

### Post by rooster on 2005-11-29
> **Griff]I've got another PC I'm wanting to put ubuntu on.  What bothers me about this PC is that there is only one partition (NTFS of course), yet there are 2 options on the windows boot screen for XP.  The top one leads to the 'healthy' installation while the other...well...let's just say it leads to a very dark and scary place.  I'm not sure what happeded for this to take place, but at any rate I want this other boot option gone.  How do I do this?[/QUOTE]

You can install Ubuntu and and format the whole disk - the wrong entry is magically gone away  said:**
> Also, can I use a windows install disk to resize the NTFS partition?  I tried using the ubuntu install disk in the past, but it loops back whenever I try to resize.
NTF resizing on windows is possible with special software like Partition Magic (very good but expensive). Resizing with linux tools - I have heard that this is working, but I think it is dangerous - there are tools for it in some distros, but you are strongly encouraged to do a backup first (everybody tells you so, but it is so, really!!!). Do you want a link? [here]("http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html")

Rooster

---

### Post by Griff on 2005-11-29
Knoppix.  Excellent.  I couldn't remember which distro had ntfsresize.  As for your first suggestion (format the whole thing), it is tempting, but alas I cannot.  What I will do is give linux a bigger partition.  :) Take THAT microsoft.

---

### Post by Brunellus on 2005-11-29
the second lurking partiton may be a 'recovery' partition. 

I've had zero problems using the ubuntu installer to resize ntfs partitions;  what happens when you try doing it with ubuntu?

---

### Post by Griff on 2005-11-29
[QUOTE=Brunellus]...what happens when you try doing it with ubuntu?[/QUOTE]
Absolutely nothing happens.  If I use the install disk and try to change the file system to NTFS and hit 'next' it will simply loop back a few screens and nothing changes.  I heard that not defragging a sufficient number of times can lead to this loop, but I did that enough that it shouldn't be the issue.

I should note that I havn't actually tried this again on this PC.  When I was working on a laptop of mine I know it didn't work so maybe there was a hardware issue I wasn't aware of.  I will try using an ubuntu disk on this comp and will post my results.

---

### Post by Griff on 2005-11-29
I've got qtparted up in knoppix.  It warns me that I need to unmount all partitions.  I thought they were unmounted to begin with in a live cd.  For hda1 it tells me that it is active.  Should I make make it unactive?  I just want to make sure all is well before I hit 'commit'.

---

### Post by Brunellus on 2005-11-29
As I recall, Knoppix automounts your NTFS partitions, so you'd have to unmount them.

---

### Post by zaphod_es on 2005-11-29
[QUOTE=Griff]I've got another PC I'm wanting to put ubuntu on.  What bothers me about this PC is that there is only one partition (NTFS of course), yet there are 2 options on the windows boot screen for XP.  The top one leads to the 'healthy' installation while the other...well...let's just say it leads to a very dark and scary place.  I'm not sure what happeded for this to take place, but at any rate I want this other boot option gone.  How do I do this?

Also, can I use a windows install disk to resize the NTFS partition?  I tried using the ubuntu install disk in the past, but it loops back whenever I try to resize.[/QUOTE]

The Windows boot options are in a file callled boot.ini. It is either in the root of C or in the Windir. You need to change your settings so that system files are not hidden. Back up the file and open boot ini in notepad and remove the second line of the boot options. Save, restore the options to hide system files and reboot.


I would not touch an NTFS partition with Linux. If you need to non-destructively resize a Windows partition try something like Partition Magic. When you have a lump of empty disk space you can safely install Ubuntu using the "use empty disk space" option.

If anything is not clear (apart from the last sentence) I suggest you take it up in a Windows forum.

ZB

---

### Post by Brunellus on 2005-11-29
[QUOTE=zaphod_es]The Windows boot options are in a file callled boot.ini. It is either in the root of C or in the Windir. You need to change your settings so that system files are not hidden. Back up the file and open boot ini in notepad and remove the second line of the boot options. Save, restore the options to hide system files and reboot.


I would not touch an NTFS partition with Linux. If you need to non-destructively resize a Windows partition try something like Partition Magic. When you have a lump of empty disk space you can safely install Ubuntu using the "use empty disk space" option.

If anything is not clear (apart from the last sentence) I suggest you take it up in a Windows forum.

ZB[/QUOTE]
non-destructive resizing of NTFS partitions is possible under linux, with the proviso that the filesystem to be resized is not (too?) fragmented before the resize operation takes place.

---

### Post by Griff on 2005-11-29
Anyway, did some research on ntfsresize under linux and appartently it is integrated into qtparted.  Burned a copy of Knoppix and got to work and everything is fine.  Now all I got left is the install of ubuntu.  Woo.
Thanks for the quick responses guys.

Also, I can't seem to find the link that outlined the dual boot installtion with windows.  I am particulaly interested in the parts about what needs to be mounted where and how to install the grub at the end.  Does anyone have this?  It used to be in a lot of people's sigs and I tried a search as well, but I can't seem to find it.

---

### Post by Griff on 2005-11-29
Did what I thought was right and it ended up working out.  XP and ubuntu are dual booting and the shared partition is working in both systems.  Oh happy days. :p

---

### Post by zaphod_es on 2005-11-29
Well done.  Now your questions will really start.

ZB

---

### Post by jimrz on 2005-11-29
Hi ... I'm brand new to ubuntu (and to linux) have not yet even intalled, but have been checking out these forums. Saw the link you asked about:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by rooster on 2005-11-30
[QUOTE=jimrz]Hi ... I'm brand new to ubuntu (and to linux) have not yet even intalled, but have been checking out these forums. Saw the link you asked about:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)[/QUOTE]

Thank you!

This was a very good first post! Welcome to the board!

---

