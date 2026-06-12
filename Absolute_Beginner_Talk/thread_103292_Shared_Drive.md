---
title: "Shared Drive"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Maupertus on 2005-12-13
This is the first time I'm Dual-booting, and I was wondering:

When I was only using WindowsXP, I had a C: and a D:, the C: was where I dumped Windows and programs and the D was where all my films and mp3's were located.

Now I still have the same structure, there's a C, D and Ubuntu partition on my computer. But is there a possibility for Ubuntu to 'see' that D: and hence use the mp3's and (and I'll just come out and say it) avi's on there? I'm asking because Unix has it's own file-system, so I don't know if there are big problems, or just small ones that are to be overcome.

Both C and D are now NTFS partitions.

---

### Post by myha on 2005-12-14
Hi!

Yes, you can see windows partitions, but you cannot write to them yet....
please take a look at the following link:
```
http://ubuntuguide.squarecows.com/doku.php#windows
```

br,
Miha

---

### Post by griz on 2005-12-14
Hi,
Linux will read NTFS but won't write to it (I will accept correction on this if the situation has changed.)  What you need to do is mount the d drive with:

sudo mount -t ntfs /dev/hda2 /mnt/ddrive

Prior to this, you would have used:

sudo mkdir /mnt/ddrive

Additionally, I'm assuming that your d drive is on /dev/hda2.  You should be able to determine what partitions you have by using System -> Administration -> Disks.  Let me know how it works out.

Griz.

---

### Post by Maupertus on 2005-12-14
It gives /dev/sda5, is this a problem?

When I subsitute hda2 for sda5, I get this result:

matthijs@CC137648-B:~$ sudo mount -t ntfs /dev/sda5 /mnt/ddrive
mount: mount point /mnt/ddrive does not exist

---

### Post by kaamos on 2005-12-14
Did you do this as griz mentioned
> 
Prior to this, you would have used:

sudo mkdir /mnt/ddrive

This creates the ddrive folder.

---

### Post by Maupertus on 2005-12-14
DOH! Completly read over that line. 
Sorry.

*is now annoyed with himself*

---

### Post by Sokraates on 2005-12-14
Just an explaination to what you just did:

In linux you can mount a partition as a folder of your choice. If the desired folder does not exist, you will have to create it first, since this is not done automatically, when mounting a drive (I'll leave USB-devices aside for now).

---

### Post by Maupertus on 2005-12-14
Thank you for clarifying, when learning something new, it's great to understand 'what'  you are actually learning.

Okay, next step/problem, it is mounted, but: "You do not have the permissions necessary to view the contents of "ddrive"." 

Now I don't recall having altered the permissions for my D partition in windows. So what can be the reason for this prompt (besides the obvious). 

[edit] If I use the terminal to **sudo nautilus** then I can acces everything perfectly, but starting Nautilus from the panel or desktop doesn't work.

---

### Post by Sokraates on 2005-12-14
[QUOTE=Maupertus]Thank you for clarifying, when learning something new, it's great to understand 'what'  you are actually learning.

Okay, next step/problem, it is mounted, but: "You do not have the permissions necessary to view the contents of "ddrive"." 

Now I don't recall having altered the permissions for my D partition in windows. So what can be the reason for this prompt (besides the obvious). 

[edit] If I use the terminal to **sudo nautilus** then I can acces everything perfectly, but starting Nautilus from the panel or desktop doesn't work.[/QUOTE]

Right. You need to be superuser to access all files on the drive. That's why starting nautilus with "sudo" in front will grand you acces: "sudo" will start any app (in this case nautilus) as superuser.

So next we'll want to mount the drive with some options, so that it allows acces to regular users, too.

First execute

```
sudo umount /mnt/ddrive
```

This will unmount ddrive.

Then take a look [here](http://www.ubuntuguide.org/#automountntfs), on how to mount it correctly.

Good luck. :D

---

### Post by Maupertus on 2005-12-14
And everything is working!

Sokraates? Is this the moment where I tell you how much I love you ;)

---

### Post by Sokraates on 2005-12-14
*sniff*

On a sidenote: ubuntuguide.org (the links I gave you) is for Hoary only. So the basics still apply, but some settings won't work or even conflict with Breezy. I keep using it, though, since I can easily remeber the URL. ;) 

For Breezy I suggest these guides:

[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

[http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)

Have fun!

---

