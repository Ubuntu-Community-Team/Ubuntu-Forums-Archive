---
title: "boot-problem"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by Larsj on 2005-10-14
Hi! 

(btw: I'm dutch so sorry for my bad grammar)
well .. I've downloaded the ISO .. burnt it into a cd ... 
while booting my computer gives the following error: 

"
Searching for bootrecord from cdrom ... not found
Searching for bootrecord from IDE ... not found

NTLDR file missing
"

tell me what to do! :(

---

### Post by ssam on 2005-10-14
you need to burn the image to the cd, rather than just put the iso as a file on the cd.

what cd writing software are you using?

---

### Post by Larsj on 2005-10-14
I'm using nero ... and I've burn the iso as an image (file-> burn image) .. it isn't just a file

---

### Post by ssam on 2005-10-14
ok, that seems right

sounds most like there is a problem with the iso file. can you redownload it? can you check the md5sum?

did you download with bit torrent? that uses checksums so should get the file properly.

are you sure you have the right version. not the powerpc or amd64 versions.

---

### Post by Larsj on 2005-10-14
I have downloaded the iso from the ubuntu-homepage and I'm sure I have the right version .. there's only one thing: .. there was a little error at the end of formatting my c-drive .. could that be the cause of this error?
and what's md5sum?:confused:

---

### Post by ssam on 2005-10-14
so you did get the install to work?

as error during formating the disk during install could easily prevent the install being sucessful.

md5sum is a checksum. it is a number that is (almost) unique to a file. the list of md5sums for breezy cds is at [http://se.releases.ubuntu.com/5.10/MD5SUMS](http://se.releases.ubuntu.com/5.10/MD5SUMS) if there is any error on the iso file, its md5sum would change. i dont know how to check the md5sum for a windows file

---

### Post by Larsj on 2005-10-14
well look .. I first worked with windows ... when I discoverd ubuntu on the net I got interessted .. so I formatted windows planning to install ubuntu instead of windows .. do you know a way to get into MSDOS from the boot .. so I can format the disc again (just to be shure)

---

### Post by ds[de] on 2005-10-14
Larsj, if you want to, I can send you an .nrg (Nero Image) file for a Boot-CD with the files needed to re-format your harddrive. If you have any possibility to burn a CD right now, then just PM me your email adress, and I'll send you the file asap.

Regards,
ds[de]

---

### Post by Larsj on 2005-10-14
[email]lars_woehoew@hotmail.com[/email]

how does it work .. I've just got to burn the files on a cd?

---

### Post by ds[de] on 2005-10-14
I just sent you the file (boot.nrg), just choose file -> burn image in Nero and select the file, then just burn the CD, insert it in your cd-rom drive and reboot the computer, if your BIOS options are correct (your boot sequence should be CDROM, HDD, FLOPPY or similar) you should end up in a "dos shell".

Regards,
ds[de]

---

### Post by xeta on 2005-10-14
[QUOTE=Larsj]Hi! 

(btw: I'm dutch so sorry for my bad grammar)
well .. I've downloaded the ISO .. burnt it into a cd ... 
while booting my computer gives the following error: 

"
Searching for bootrecord from cdrom ... not found
Searching for bootrecord from IDE ... not found

NTLDR file missing
"

tell me what to do! :([/QUOTE]

As stated before, if you got to the point where the MBR was looking for windows (NTLDR is what the master boot record looks for when booting to windows), then chances are your CD is either not burned correctly or your iso is corrupted.

Please let us know if the nero boot img that was sent helps you.

---

