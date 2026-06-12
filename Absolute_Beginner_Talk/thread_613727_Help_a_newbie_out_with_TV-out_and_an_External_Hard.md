---
title: "Help a newbie out with TV-out and an External Hard drive"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by palbuddy on 2007-11-15
Hello!

I have Gutsy Gibbon installed, and for the most part.  If I can get these 2 issues resolved, it would make me even more happy. 

I have a laptop Evo N600c with a ATI Mobility Radeon 16MB Video card inside.  How to I enable the TV-Out?  Please!  Be nice, I don't know command line stuff, so if you have a solution keep that in mind. 

I also have a 200 gig external hard drive.  How do I format it, and let it be used for Ubuntu?!  I would like it to contain my .mp3s and movies hopefully.  How can I set it up so I can delete the windows NTFS and add a linux file server?

Thank you in advance,  Linux is great!  I'll check back tomorrow for anyone to help me out!

later!

---

### Post by Inxsible on 2007-11-15
Where are you going to use the External drive? If you plan to use it solely with Linux, format it to EXT3, or if you plan to use it with both, you can format it as NTFS or EXT3.

EXT3 is a better filesystem than NTFS, because of journaling capabilities. and you can always install fs-driver in Windows to access EXT3 drives. It will also help you when you add a linux file server and use it as a drive. altho, since its an external drive (probably connected with USB) it won't give you speeds better than 480 Mbps

---

