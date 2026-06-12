---
title: "Formatting, Dual-Boot and FAT32 help needed."
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by Chibi Mei on 2005-06-23
Greetings, I would be deeply thankfull towards anyone who couldst aid me with my dilemma, and in best-case-scenario indulge me with a solution to my little problem.
(Also, please note that I have no clue whatsoever how to format. :? )

I have three HDDs:
1. C: internal 80GB IDE (ReiserFS) which is the drive with Ubuntu currently installed on.
2. D: internal 200GB IDE (NTFS)
3. An external 250GB (FAT32)

Now, what I had planned is to format drive D: and make it into FAT32 and install Ubuntu there, since it is currently read-only (Had alot of stuff on it from when I used Windows (Either XP Professional or 2003 Server), which I finally got copied to the external HDD which I bought recently.)
And after that I was thinking of formatting drive C: and if possible make it FAT32 aswell and install Windows on it.

(The reason for why I want it like this is because I want to be able to reach media (Videos, music, images, documents etcetera.) from both OS.)

And, how should I proceed to get it done like that and preferably have as many discs as possible read/writeable from Ubuntu as well as Windows, and having dual boot functioning O.K ?

Also, are there any con's with using FAT32 for either Windows or Ubuntu?
(The main reason I wanted to have a Windows-drive is for gaming, because Cedega isn't satisfiable enough. And, please excuse me if I got something mixed up.. I'm not very knowledgable about computers.)

Please feel free to propose any ideas for filesystems and so that might be better than above-mentioned to suit my needs aswell. :)

Thanks a lot in advance!
-Vicky.   :smile:

---

### Post by desdinova on 2005-06-23
You cannot install Linux on NTFS or FAT/FAT32 - much the same way why you cannot install Windows on EXT3/EXT2 etc

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=desdinova]You cannot install Linux on NTFS or FAT/FAT32 - much the same way why you cannot install Windows on EXT3/EXT2 etc[/QUOTE]


This is true. The best solution is to allow one of your drives to be split- 10 gigs or 20 gigs of NtFS to install XP, and the rest fat32. Then reinstall ubuntu on the first drive using a ext3 (or reiser, whatever) partition.

---

### Post by Chibi Mei on 2005-06-24
Ah, okay. Thanks alot! :]

---

### Post by Omnios on 2005-07-01
Im trying to do something sililar. I have a 120G main drive with Xp on it and a 40G Linux drive. I resised my 120G ntfs to 60G and left about 50G which im trying to figure out how to format as XP will only format a disk up to 32G. 

 The hole point of this is to have more room than ill ever use for XP main and use the fat 32 partition for My Documents that I will be able to share with Linux. 
Actualy I had a XP on the main and My Documents "incuding music" on the 40G drive which worked real well. This also allows for many options when you run into problems both in XP and Linux. Hopefully this will work out real well as it will also allow for a essential tarball collection lol.

---

### Post by bpilgrim1979 on 2005-07-13
Be very attentive to filename case-sensitivity issues if you have a shared FAT32/VFAT partition.

Linux is case sensitive but VFAT is only case preserving.  The VFAT filesystem doesn't know the difference between File.TXT and file.txt, but Ubuntu does!

---

