---
title: "Problems Burning CDs with Serpentine and k3b"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by kmir on 2007-08-14
Hello!

I am obviously new to this and this past weekend I have been trying to burn CDs. I have tried different brands of blank CDs and found some that work fine with my drive under Windows - so now I try burning with ubuntu.

I have tried burning audio CDs with Serpentine, it does not work. When it comes to "preparing recorder", my drive makes funny noises ("tuck krrrrrrrrrt"). 

Next, I tried burning audio CDs with k3b. It started burning and burned the first 2 minutes of the first track, then it stopped, producing the following error message (original message was a little longer, but I think this is the relevant part):



Track 01:   17 of   66 MB written (fifo   9%) [buf  99%]   8.5x.
Track 01:   18 of   66 MB written (fifo   3%) [buf  91%]  14.7x.
Track 01:   19 of   66 MB written (fifo   3%) [buf  36%]   9.7x.
Track 01:   20 of   66 MB written (fifo   1%) [buf  87%]  10.1x.
/usr/bin/X11/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 23 1F 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63504
cmd finished after 23.421s timeout 200s
/usr/bin/X11/cdrecord: A write error occured.
/usr/bin/X11/cdrecord: Please properly read the error message above.
write track data: error after 21146832 bytes
Writing  time:  103.726s
Average write speed  66.8x.
Min drive buffer fill was 31%
Fixating...
Fixating time:    0.002s
BURN-Free was never needed.
/usr/bin/X11/cdrecord: fifo had 397 puts and 334 gets.
/usr/bin/X11/cdrecord: fifo was 54 times empty and 3 times full, min fill was 0%.




What do I have to look for here? Is "Medium Error" supposed to mean that there was a problem with the CD? As I said, my drives seems to love these CDs under Windows.

Well, then I tried burning data CDs with k3b. The process starts, but then it does not write anything (I can use these CDs under Windows afterwards to burn something on them). The error message looks like this (original message was a little longer, but I think this is the relevant part):



Starting to write CD/DVD at speed 16 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
/usr/bin/X11/cdrecord: Success. send opc: scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x4 (CONDITION MET/GOOD)
cmd finished after 63.740s timeout 60s
/usr/bin/X11/cdrecord: OPC failed.
Writing  time:   64.954s
/usr/bin/X11/cdrecord: fifo had 64 puts and 0 gets.
/usr/bin/X11/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
BURN-Free was never needed.



What do I have to look for here?
I wanted to try different programs for burning data CDs, but I found in a few posts that X-CD-Roast was a somewhat outdated program. So I went to brasero. I could not find it in the Add/Remove Applications thing or in Synaptec (I checked all the boxes in Settings - Repositories - Ubuntu... - Edit), so I went online and downloaded what I found here: [http://sourceforge.net/project/showfiles.php?group_id=156415]("http://sourceforge.net/project/showfiles.php?group_id=156415")
I was not able to install it ( :confused: ). 
What can I do now?

I am using the 6.06 LTS version and my CD drive is a LITE-ON LTR-48327S.

Thanks for any help!

---

