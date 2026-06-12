---
title: "Enabling WINE to save documents?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Theros123 on 2008-01-29
Hi all!

Hopefully this is a silly stupid question.  I've got Microsoft Office 2003 working on the latest version of WINE on my Ubuntu 7.10.  The way my harddrive is set up right now is that I have a 10 gig Partition for Vista, 30 gigs for Ubuntu, and the rest is shared.  I created a new NTFS partition from Vista and mounted in Ubuntu, I can put files in there manually from Ubuntu and Vista will read then, vice versa.  However, when trying to save a Word document from within WINE to that shared partition, it tells me that I haven't set up the right permissions...but in Vista, I enabled all users to be able to read/write/delete...  What do I have to do to get WINE to be able to save documents in that partition?

Thanks,
Eric Huang

---

### Post by Theros123 on 2008-01-29
anyone know?

---

### Post by Presto123 on 2008-01-29
With my Ubuntu/Vista setup, I save files on both OS's so I can access it easily on both. All I do is copy and paste into the NTFS system by accessing the drive. As for doing it automatically like you want, I don't know. I usually get on Vista for my Office 2007 stuff.

---

### Post by Luke771 on 2008-01-29
Weird.
NTFS doesn't support permissions under Linux AFAIK.
I have a XP Pro x64 that I use to play games only, and I can save documents directly from Ubuntu in the two NTFS partitions.

---

### Post by Luke771 on 2008-01-29
double post. sorry (edited)

---

### Post by Theros123 on 2008-01-29
Damn.. that's annoying!  Are you saying I have to save the document from Word in Ubuntu first... then manually copy it over?  Jeez, not a deal-breaker, but annoying nonetheless

---

### Post by Luke771 on 2008-05-16
No I'm not.
I'm saying that you can save your files in NTFS partitions just you would do on Ext2/3 partitions (or reiserfs, for that matter)

[edit] Oh. Was that post so old?

---

### Post by Xfcn on 2008-05-17
> **Theros123 said:**
> Hi all!

Hopefully this is a silly stupid question.  I've got Microsoft Office 2003 working on the latest version of WINE on my Ubuntu 7.10.  The way my harddrive is set up right now is that I have a 10 gig Partition for Vista, 30 gigs for Ubuntu, and the rest is shared.  I created a new NTFS partition from Vista and mounted in Ubuntu, I can put files in there manually from Ubuntu and Vista will read then, vice versa.  However, when trying to save a Word document from within WINE to that shared partition, it tells me that I haven't set up the right permissions...but in Vista, I enabled all users to be able to read/write/delete...  What do I have to do to get WINE to be able to save documents in that partition?

Thanks,
Eric Huang

Have you tried the following:

Applications > Wine > Configure Wine > Drives

1) Press the button "Add...", it'll create a new drive, most likely it'll be "E:" if you haven't created others.

2) Highlight "E:" in the list on the screen. **Very Important that you choose the correct drive letter here or you could mess up Wine!** You should see something like:
C: ../drive_c
D: /cdrom/
E: /
Z: /

etc etc things like that.

3) In the field below that, where it says "Path:", hit "Browse" and locate under "/mnt" your Vista's drive. Highlight that and press "OK". You should now have something along the lines of:

E: /mnt/sdb1

Or something of that nature. Click "OK" to close and save Wine's configuration.

Try it again, see if it'll let you save by going to the "My Computer" in the drop-down of your save dialog in your application and choosing the "E" drive or whatever drive you just made into the Vista drive.

I've had success with that in the past. Lemme know  if that doesn't work...

---

