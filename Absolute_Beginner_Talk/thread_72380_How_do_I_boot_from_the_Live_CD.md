---
title: "How do I boot from the Live CD?"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by Maisha on 2005-10-06
Hi.
I'm totally new to Ubuntu. I dallied with Linux 5 or 6 years ago but never really got off the ground, so I know zero. I like the Linux concept, I love the Ubuntu philosophy. And I'd like to ask for some help (I'm not really very technical, so please excuse some of my expressions).
I decided to get a feel of Ubuntu before making any major decisions so I downloaded and burned the Live CD version of Ubuntu (first 5.10, then 5.04). I set my BIOS to boot from the CD-ROM but the Ubuntu Live CD doesn't boot. It goes straight to the Windows XP startup screen. XP, on the other hand, DOES boot from the CD-ROM, so the problem can't be there (can it?)
I thought there might be a problem because I burned the .iso image onto the CD, so I downloaded a program called IsoBuster (which I used for the first time) to extract the whatyamacallit from the iso image, burned THAT onto a CD and tried to boot from it. Same story.
So now I'm stuck. Any ideas anyone? My PC specs: Athlon XP 1800+, 512 RAM, Windows XP, NTFS.
I appreciate all and any help. I'm really looking forward to trying this out and becoming part of this community. Thanks

---

### Post by Dayylin on 2005-10-06
Hi Maisha,

It sounds as though the LiveCD was burned as data. I used Deep Burner to burn my iso. The only issue I had was a bad disk which didn't copy it right.

Had another thought, do you have 2 cd drives? If so, try placing the cd in the non-burning one. I had to do that in order to get it to boot.

Brian

---

### Post by davmac on 2005-10-06
I suspect it is a problem with how you burned the original CD, because it sounds like you've done everything else right. In WinXP, when you put the CD in and explore the disk, what do you see?
 
I used a free program called DeepBurner to burn my iso images on Windows. You can get it from [http://www.deepburner.com/download/DeepBurner1.exe]("http://www.deepburner.com/download/DeepBurner1.exe") and it is pretty simple to use.
 
BTW: I don't think the approach you took with isobuster will work because, while all the key data files will be on the CD, it won't be bootable (I think).
 
HTH,
 
Dave Mac

---

### Post by Funseeker on 2005-10-06
I saw in another posting, further down in this forum, about someone having the same or similar problem.  They were advised to burn another ISO copy at a slower speed (i.e. instead of 12x try 8x). Sometimes older CD-ROM's may have a problem reading CD's made a higher speeds.  Hope this is helpful.

---

### Post by Milo on 2005-10-06
I too, had the same problem.  Here is what I discovered after first reading this thread.  You could use the DeepBurn as mentioned in this thread.  However, it most likely is not necessary.  I knew a CD had to have a boot record and/or a boot loader to work.  My problem was, while looking in my Roxio CD app, I mistakenly chose the "create a bootable CD".  If I understand it, this is for creating a bootable CD when you have your own files like a floppy would have, because Roxio simply adds its own boot loader and the file(s) you specify.  It just burns them as is.
What I should have been looking for is a CD copy.  I say you shouldn't have to use the DeepBurn because if you have a CD burner, it came with some kind of software and most likely will have a CD copy feature.  This is what you want.  When you copy a CD, you copy the whole thing.  There is a Source selection, which would show available CD drives, but also there is the source option of an **_image file_**.  This is what you want; navigate to where you downloaded the iso image file.  This file is the exact copy of the bootable CD, so when it is copied (as an image file, not a data file) you end up with the bootable CD.  When you use the CD Copy function with an ISO file as the source, it is the same as copying from another CD, because the ISO file IS an exact image of a CD.
If your burned CD only has the image iso file, it didn't work.  If it has a bunch of folders and files like you would expect a boot or install CD to have, then you got it!
Hope this helps.  It's a shame the Ubuntu download page did not provide this simple information, because I didn't know how to "burn an iso image" either.  There are two kinds of people who would download the Live CD; those who have never used Linux and those who are using another distribution of Linux.  Either way, many people are unfamiliar with creating a boot CD from an image, or anything else.  The Ubunto site seems very lacking in any kind of information that would be helpful to people starting out with Linux.

---

### Post by Maisha on 2005-10-08
Thanks everyone! It worked, I liked it, I installed it.

---

