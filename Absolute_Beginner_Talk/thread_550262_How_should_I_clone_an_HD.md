---
title: "How should I clone an HD?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by abacate on 2007-09-13
Lately I've been having some trouble with my old HD, so I thought I'd get myself a new one before the old one breaks down. The old HD is a 200gb seagate barracuda and the new one a 500gb seagate.

Now what I'd like to do is I'd want to copy all my files, installed programmes and my installation of feisty - that is to say, everything - from the old HD to the new one. Then I'd erase the old HD and just mount it as extra space in some custom location.

How would you recommend I go about doing this?

---

### Post by CaptainInsaneO on 2007-09-13
Try Partimage. If you search around on the forums you can find a load of ways to do it.

---

### Post by tgalati4 on 2007-09-13
Boot a Live Feisty cd.

Assuming your original drive is /dev/sda and your new drive is /dev/sdb

>sudo umount /dev/sda
>sudo umount /dev/sdb
>sudo cp /dev/sda /dev/sdb

Make sure that your new drive is as large as the existing drive.


Otherwise you can copy partition by partition: (But you need to create partitions first on the new drive.)

>sudo cp /dev/sda1 /dev/sdb1

Swap drives and test your copy.

---

### Post by KevinD_Atl on 2007-09-13
If it's a straight disk to disk copy, I think you can download a Norton Ghost 'Trial'.  Find an older version, like 2003 as it's more stable.  Make a boot disk, and ghost it on out. I'm pretty sure it'll do the file system, I have done it before with a Fedora Core 6 disk just to have a backup.

Make sure you still have a floppy somewhere, you simple make a boot disk and go right into it.

---

### Post by sloggerkhan on 2007-09-13
maybe look into the dd command? (Much better than cp for large files, I hear.)
also, clonezilla maybe?

---

### Post by chrome307 on 2007-09-13
**Are you sure about using Norton Ghost 2003 ? **

I still have this on a floppy disk lying around gathering dust and it's labelled v8.3.

I've only ever used it for Windows.

---

### Post by ddrichardson on 2007-09-13
You needn't download anything, dd from the command line in Live CD: [here]("http://blog.lynxworks.eu/?p=12").

---

### Post by Wynne G Oldman on 2007-09-13
Don't use GHOST 2003 on ext3 partitions. It will clone, but unless you''re doing a sector to sector copy between identical HDD's, it will corrupt your data. You could download the trial version of Acronis TI. That will do the job. It's easy to use as well! Just install it, and create the bootable media, boot off it, and the rest is self explanatory. It'll resize your partitions for you as well.

---

