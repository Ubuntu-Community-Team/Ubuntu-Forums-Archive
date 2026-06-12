---
title: "Did Brasero just KILL my home dir :confused:"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by RavanH on 2008-01-08
Hi all,

This forum is maybe not the right one but I chose Absolute Beginner Talk because I feel like an ABSOLUTE beginner! :(

This is what happened:
I am using Ubuntu Gutsy AMD64 on a laptop with only one CD/DVD-player/burner and wanted to copy a DVD. After loading the DVD and starting Brasero Disk Burning Application (installed through Synaptic), I chose the option 'Disk Copy'. Then I chose under 'Select a drive to write to' the option 'File image'. The status/info message below reported 'The image will be saved to /home/ravan/brasero.toc' (where /ravan is my home folder).

All seemed well untill I hit 'Copy' and Brasero reported the disk not having enough space for the full DVD image. So I went back to change the file location via the button 'Properties' and selected another partition (on the same harddisk). After I found that that partition also lacked space, I decided to clean up the partition where my /home/ravan is located. 

After creating the space needed on my /home partition, I hit 'Properties' in Brasero again so I could change the file image location back to my home folder again. I did NOT fill in a name for the file, thinking that Brasero would just use 'brasero.roc' again and selected the folder /home/ravan and hit 'Apply'. Then I hit 'Copy' and noticed that Brasero rendered a partially empty dialog screen. Getting worried, I broke of the process but it was too late! 

Almost all files and folders in my home folder /home/ravan had been DELETED!!! AAARGH!!!!

Days later, after creating a new user and restoring a (two months old :( ) backup, I tried to find out what happened. This time I noticed (repeating the whole process) that the final status/info text just before the deadly run was '**The image will be saved to /home/ravan**' instead of the original '**The image will be saved to /home/ravan/brasero.toc**'... 

Notice the difference? 

Brrrrr.....

Is this a typical beginner mistake? Thinking Linux would be able to make the distinction beween a FILE and a FOLDER with the same name?

---

### Post by Fixman on 2008-01-08
Some programs, like Brasiero, still need some bug fixes. I reccommend you to use K3B to burn DVDs, or DeVeDe to burn video DVDs. The problem with UNIX like systems is that a folder is a file with special permissions (+d).

---

### Post by RavanH on 2008-01-14
> **Fixman said:**
> ... The problem with UNIX like systems is that a folder is a file with special permissions (+d).

Ok, so I *am* a n00b in this respect! 

This means that when trying to save a file with the same name as an existing folder (and no extension), the folder will be overwritten??? I would indeed describe this situation as a PROBLEM... 

Why was this setup ever chosen? Are there any benefits that come with treating folders as files with special permissions?

---

### Post by malty on 2008-01-22
Brasero killed my music folder (thousands of tracks) luckily I still have the originall CDs for the majority of them.
I normally use Sound Juicer, which is excellent, never fails to identify the music, a lot of it obscure (1950s Irmgard Seefried).
However, I do like to research what is out there, and decided to give Brasero a try.
So...
disc copy
select drive to write to
file image
properties
save in folder.........media/disc/music2007 ( the folder is on a separate partion.)
copy
copying CD
What had been my music folder is now 2 files.....
1 = .bin file 503meg
2 = Cdrdao 1.6kb

The partion accessed from WINXP shows...
1 = Apple mac icon 503meg 
2 = zip file 1.6kb
The bug has been reported
Who knows it may have been me ?

Either way in future I will stick to Sound Juicer, Brasero is in the skip.

Odd that, my missus used to have a Corrado (mind you, that I did trash.)
                                              
                                                  Malty

---

### Post by malty on 2008-01-22
Below is the answer to the problem from Brasero

I've got bad news. This is a bug in the 0.6.0 series. Brasero shouldn't let the
user do this operation as it can't rip an audio CD. What brasero did in your
case was make an image of the disc (the *.toc and *.bin files). Unfortunately
this image replaced your directory and its contents. I'm really sorry about
that.
I made some googling and found some tools to recover deleted data. You may not
recover everything but at least part of it. Only one advice I have is to use
the partition on which your files are written as little as possible.

For recovering deleted data, see

-http://www.diskinternals.com/linux-recovery/ (that seem the best option even
though it is closed source and works from windows though ... (means probably to
unscrew your drive and screw it back in windows machine)

- [http://e2undel.sourceforge.net/recovery-howto.html](http://e2undel.sourceforge.net/recovery-howto.html) (apparently a long process
and may not work on ext3)

- [http://www.nucleustechnologies.com/Linux-Data-Recovery-Software.html](http://www.nucleustechnologies.com/Linux-Data-Recovery-Software.html)
(commercial but with free tries apparently)

This bug has been fixed in 0.7.0 but ubuntu didn't update the version it ships.

HMMMM...what do you think he means by "use the partition as little as possible", its 158 GiG !
From WINXP I will use disc director to nuke it ( after copying over all of the other folders to a safe place then re copy back to the refreshed partion.
                            Life can become tiresome.
                                                                              Malty

---

### Post by RavanH on 2008-01-29
Ok, so I am not the only one... I was getting very insecure about myself here ;)

malty, did you manage to get your music back? ("use the disk a little as possible" means that when writing to it, it could well mean overwriting a deleted but potentially recoverable file...)

---

### Post by malty on 2008-01-31
No, I did not recover the lost files, I felt that this seemed to be a hit & miss solution and what I did, as I had most of the original CDs, was as follows........
In WINXP I used Acronis DiscDirector to completely delete the partition, using  4 passes, this took 3 hours.
I then reinstated the partition with DiscDirector.
I then ripped all of the CDs to a new folder using Sound Juicer, during the course of this I can say that Sound Juicer is the best CD ripper I have ever used !, it found 99% of the album information. I know it uses the same sources as other rippers,CDDB I think, but in reality it does that job much better than any other ripper I have ever used, putting even EAC into the shade.

So, Sound Juicer team...10/10

There are, however, some salutory lessons to be learnt from this debacle.

1/ do not experiment with "work in progress" software, be patient, wait until its officially released.

2/ and ( I bet this ruffles feathers ), if you have migrated to Linux from Windows, via duel boot, then why not keep windows. You then have the best of both worlds, in case of accidents, I only followed the above course of action because I had Disc Director. I know and trust this programme.

3/ allways have 2 hard drives, they are now so inexpensive, I have one drive (160G ) for WINXP, the other ( 500G ) with 3 partitions, more or less the same size, Ubuntu, files, backup ( with room for a second Distro. )

                           Keep taking the tablets, 
                                                                   Malty

---

