---
title: "Network tar file size limit"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-10-22
Hi there!

Please can someone reply to this! PLEASE! This is the 2nd time I'm posting about this! When tar'ing on my local drives i can make a tar file as big as I'd like. when tar'ing over a samba mounted drive I can only get up to 2 gigs!

Why!!!!!! I need to backup my entire system to a windows box! copying all the data accross won't be ideal as I'll loose my permisions ect. 

if tarring is not the way to go, can some one suggest an app that lets you back up only certain folders, all at once and will save them in a file format that will preserve their original status, ie, zip, bak, tar.

here is what I'm talking about:

sudo tar cvpzf /nwdrives/backup.tgz[COLOR="Red"](Backup to this[/COLOR]) [COLOR="Blue"]--exclude=/proc --exclude=/lost+found --exclude=/stuff --exclude=/mnt --exclude=/sys --exclude=/windrives --exclude=/nwdrives[/COLOR]([COLOR="Blue"]excluding all this[/COLOR]) /([COLOR="Lime"]staring at root and archiving everything beyond this piont except the excluded folfers[/COLOR])



I can't backup to my own drive and then copy the backup over because i only have 8 gigs out of 40 free! 

I would really appreciate some help and advice,

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2006-10-22
OKAY!

Did a 3.5 gig backup on my pc! NOW I CAN'T EVEN COPY THE BLOODY THING OVER THE NETWORK! ](*,) 

I need to make an offsite backup....

PLEASE! SOMEBODY! ANYBODY.... HELP!!!!!

If you have a windows machine and a Ubuntu box could someone just check of they can copy a file bigger then 2.0 GB over the network! Not a folder, a single avi or mpg or zip file.

I need to know wheter this is just me or the windows box or Samba!

thanks,

Rudolf

---

### Post by dmizer on 2006-10-22
you can't copy the file over the network using samba.  samba file size limit is 2 gig.  that's it.  there is no more.

alternatively, you can use ssh, ntfs, ftp or any number of the other file transfer options open to you in windows and linux.

---

### Post by DaveBorealis on 2006-10-22
> **RudolfMDLT said:**
> Did a 3.5 gig backup on my pc! NOW I CAN'T EVEN COPY THE BLOODY THING OVER THE NETWORK! ](*,) 

Hello Rudolf,

One option is to use '/usr/bin/split' to divide the backup into managable pieces.  Then '/bin/cat' them back together.

split -b 1000m reallybigfile.tar

cat x* >> reallybigfilebacktogether.tar

I'm guessing that the '1000m' argument should divide your 3.5 gig into four pieces.  (1000 Meg = 1 Gig, no?)  'man split' and 'man cat' for more info.

Also, another consideration, I find that when I'm bumping against system limitations it's often because I'm doing something inefficiently.  Do a Google and you might find better ways to save a backup snapshot of your system.

Best regards,
Dave

---

### Post by RudolfMDLT on 2006-10-24
Dave.

THanks a lot! this will be a great help! thanks!

---

