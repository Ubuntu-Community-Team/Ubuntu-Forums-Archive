---
title: "delete hardrive... TOTALLY"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by ephman on 2006-02-24
hi,

i have to totally wipe a hard drive clean.  how do i do that so that nothing on the drive is recoverable?  i have to send it back to dell.

thanks,
ephman

---

### Post by earobinson on 2006-02-24
you could use a live cd and just format over and over

Or just reinstall ubuntu and make sure it wipes the drive.... comeon it would be fun to send dell back a ubuntu computer :)

---

### Post by pinkpanther01010 on 2006-02-24
I don't see why rm'ing it to death wouldn't work ?

---

### Post by rharris on 2006-02-24
You might go to the following link and see if it can be of any help:

[http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/06/linux-how-to-delete-file-securely.php](http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/06/linux-how-to-delete-file-securely.php)

Take care.................

Rob

---

### Post by jvolkman on 2006-02-24
try:

dd if=/dev/zero of=/dev/hdX

where X is the identifier of your HDD device.

e.g.: dd if=/dev/zero of=/dev/hda

This will "zero" the drive.  It will overwrite everything with null bytes.

---

### Post by pbaehr on 2006-02-24
I believe if you're extremely paranoid the only way to render a disc entirely unrecoverable is to wipe and write over every sector 7 times (or some other magic number but for some reason 7 sticks in my head).

That may be a bit excessive, though. At this point you should ask yourself if there's really anything on there of so much interest that Dell would hire a computer forensics team to recover it.

I'm assuming you need to send the drive back to Dell in semi-working form so this is just for laughs but I've heard stories about data recovery companies that consider the only truly effective means of disposing of a hard drive with sensitive data is making several large holes in it with a power drill.

I guess it all depends on your level of paranoia.

---

### Post by ajgreeny on 2006-02-24
Get hold of a copy of Nuke Boot Disk from [http://dban.sourceforge.net/](http://dban.sourceforge.net/) which will wipe the disk so nothing is recoverable.  You can get floppy or CD versions.

---

### Post by WebScud on 2006-02-24
[quote=ajgreeny]Get hold of a copy of Nuke Boot Disk from [http://dban.sourceforge.net/]("http://dban.sourceforge.net/") which will wipe the disk so nothing is recoverable.  You can get floppy or CD versions.[/quote]

That's a cool app.  I downloaded it for future use.  Thanks.

---

### Post by uopjohnson on 2006-02-24
[QUOTE=ajgreeny]Get hold of a copy of Nuke Boot Disk [/QUOTE]
This is what I generally use as well, it can take a while, but it gets the job done.
You might also want to look at the manufacturer web site for your hard drive, they often have tools to do this as well.

[QUOTE=jvolkman]dd if=/dev/zero of=/dev/hdX[/QUOTE]
will work, but you really want to do a 
dd if=/dev/urandom of=/dev/hdx a bunch of times to write random data to the drive.

---

### Post by Sp@z on 2006-02-24
[QUOTE=ajgreeny]Get hold of a copy of Nuke Boot Disk from [http://dban.sourceforge.net/](http://dban.sourceforge.net/) which will wipe the disk so nothing is recoverable.  You can get floppy or CD versions.[/QUOTE]
This is so much better than the oldschool method involving a hammer and FIRE!!!!!!!!!!! I still believe the only way to TRULY erase a HDD is to beat it to death with a 3 lb sledge then throw it in a fire.

---

### Post by Kurt` on 2006-02-24
[QUOTE=Sp@z]This is so much better than the oldschool method involving a hammer and FIRE!!!!!!!!!!! I still believe the only way to TRULY erase a HDD is to beat it to death with a 3 lb sledge then throw it in a fire.[/QUOTE]
Drilling holes through the platters helps too ;)

And yes, overwriting it with random junk multiple times works as well. If I recall, simply "zeroing" a drive is not adequate, because it's possible to detect the "residue" of what was written there before. (At least, that's how it was explained in the doc I read, in over-simplified terms)

---

### Post by ecto on 2006-02-24
You can Low Format the drive. Low formatting entails that the hard drive will be restored to factory setting because everything gets written over with zeros thus all the inodes are unlinks. There is no real way to TOTALLY DELETE THE HARDRIVE unless you beleive that smashing it with a hammer counts as deleting :D

---

### Post by ecto on 2006-02-24
You could LOW FORMAT the hard drive. Low formatting entails writing over the harddrive with zeroes therefore unlinking all the inodes. Two peices of software that does this job nicely is Dukes Boot and Nuke and Seagates Hard drive tools. I dont have the links handy but you should google it. You must remember that nothing is ever deleted on a hard drive, simply compressed, unlinked inode, and stored away. The only way to truly delete the hard drive is probably smashing it with a hammer then obliterating it with a nuclear bomb... But even then you'll still have atoms left behind :).

---

### Post by ecto on 2006-02-24
You can Low Format the drive. Low formatting entails that the hard drive will be restored to factory setting because everything gets written over with zeros thus all the inodes are unlinks. There is no real way to TOTALLY DELETE THE HARDRIVE unless you beleive that smashing it with a hammer counts as deleting :D

---

### Post by jimmer on 2006-02-24
Try this program [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm) also found on ultimate boot CD found here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by ephman on 2006-03-25
[QUOTE=ajgreeny]Get hold of a copy of Nuke Boot Disk from [http://dban.sourceforge.net/](http://dban.sourceforge.net/) which will wipe the disk so nothing is recoverable.  You can get floppy or CD versions.[/QUOTE]


great program.  i ended up using this program.  i used the PRNG Stream Wipe with 8 passes.  i can't imagine anything now is recoverable on the drive.

thanks for the info,

ephman

---

