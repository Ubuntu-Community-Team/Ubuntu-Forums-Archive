---
title: "USB cannot empty hidden trash, URGENT HELP NEEDED!"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by annazack on 2006-05-09
Hi,
I get this message when I try to delete the files in the hidden trash folder on my usb-stick:

Error while deleting
"/media/usb...tex.backup" cannot be deleted because it is on a read-only disk.

Please help me with this since I'm writing on my thesis and I need daily backups! However, since I am not the most experienced Ubuntu-user any advice should be idiot-proof (actually, the terminal and command lines freak me out), but I try and every time I run into problems I learn some more.

//Anna

PS. Hints about a GOOD cd-burn program are also welcome, got myself a writable disc but it doesn't work with K3B...DS.

---

### Post by Sef on 2006-05-09
Try right clicking and changing the properitiees.

---

### Post by annazack on 2006-05-09
Hi, 
I tried that prior to posting this, but then I get this message: 


The permissions could not be changed
Couldn't change the permissions of ".Trash-annazack" because it is on a read-only disk

and I do have write, read and execute permissons already as owner?

Do I need to be logged in as sudo?

//Anna

---

### Post by hito1 on 2006-05-09
omg, do you know it there are hidden trash folders in digital cameras too??

---

### Post by trent dillman on 2006-05-09
...

---

### Post by annazack on 2006-05-15
[QUOTE=trent dillman]Sounds to me like your disk is mounted read only. Is it formatted FAT, EXT, or NTFS? What is the output of 'mount'?[/QUOTE]

Your absolutely right! The file system (vfat) is mounted read only. Mount gives the following output

/dev/sda1 on /media/usbdisk type vfat (ro,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

So my next question is how to fix this?

---

### Post by easyease on 2006-05-15
for the cd burner i can vouch for "GnomeBaker",.

---

### Post by easyease on 2006-05-15
and im no expert but sounds like you need to edit yor fstab......
 take a read of this it may help. I'll look into it further.  :) 
 [http://www.ubuntuforums.org/showthread.php?t=140807&highlight=fstab](http://www.ubuntuforums.org/showthread.php?t=140807&highlight=fstab)

---

### Post by easyease on 2006-05-15
here we go. this should be of help.
 [http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS](http://gentoo-wiki.com/HOWTO_Mount_Windows_partitions_(DOS,_FAT,NTFS))

---

### Post by easyease on 2006-05-15
and if that doesnt work you could try "sudo apt-get install gparted"  from a terminal and use that to format your removable drive to ext3.....thats probably the easiest option actually.lol

---

### Post by Lord Illidan on 2006-05-15
[quote=easyease]and if that doesnt work you could try "sudo apt-get install gparted"  from a terminal and use that to format your removable drive to ext3.....thats probably the easiest option actually.lol[/quote]

I wouldn't do that. The whole advantage of usb disks is portability, and by using ext3, you are limiting your usage to only Linux machines.

Edit your fstab as people have told you before.

About the disk, how come k3b doesn't do it? What kind of brand is it, and what speed did you try writing it?

---

### Post by nocturn on 2006-05-15
Does the stick have a write protection (hardware switch)?

My mp3 player has one, and I accidently trip it when inserting it into the USB port quite often.

---

### Post by easyease on 2006-05-15
yes i told the original poster to edit the fstab, and as a last resort use gparted. good point about it limiting the use of the device to linux machines though. maybe i should stick to keeping quiet rather than offering dubious advice.

---

### Post by Lord Illidan on 2006-05-15
[quote=easyease]yes i told the original poster to edit the fstab, and as a last resort use gparted. good point about it limiting the use of the device to linux machines though. maybe i should stick to keeping quiet rather than offering dubious advice.[/quote]

Don't take me wrong. I don't mean to offend you. Editing the fstab was a good point of yours. And of course, if the OP only has linux computers, then ext3 is a valid suggestion.

Don't keep quiet...research! We all make mistakes!

---

### Post by easyease on 2006-05-15
No worries mate. Ive not made much of an effort to help others on the forum before, 
 I'll try and think and be more precise in future. :-D

---

### Post by annazack on 2006-05-18
What can I say, thanks so much for all the help!!! 

Now it's working again...even though I'm almost to ashamed to admit this (but I thought it might help someone else) I will:

It turns out that my usb-stick had a read-only-button and it was switched to its r-o-position without my knowledge...well before that was concluded we tried a lot of the advice given here on the forum.

There you go...I hope I didn't cause anyone any problems with my stupidity.

Sincerely 
Anna

---

### Post by Lord Illidan on 2006-05-18
No problem, we all make mistakes. Better a problem like that then a fubared usb stick.

---

