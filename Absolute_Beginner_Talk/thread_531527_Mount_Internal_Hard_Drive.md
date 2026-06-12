---
title: "Mount Internal Hard Drive"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-08-21
Hi All

From what I can tell, this is an extrememly simple question with an extrememly simple answer. So, please excuse my ignorance. I have searched to formums for 1/2 an hour (done my due deligence I think) and have not found an answer I can use. Rather than waste your time I'll get right to my question so you can answer that if you choose and save some of my ranting for afterwards.

Question:
I am running off the Live CD. I am fortunate enough to have a new computer that I don't need yet so I am spending time learning, installing, formating, and figuring things out. As I have figured out Linux doesn't like NTFS so I have formated the internal hard drive with FAT32. I now have a totally clean hard drive partitioned into 20GB for OS, 4GB for swap, and the rest for user files. I have done the same on an external hard drive because I want to play around with installing Linux on an external hard drive. When I boot from the cd it recognizes the external (usb) hard drive and puts short cuts on the desktop but does not recognize the internal hard drive. At times when I have booted from the cd it has shown the internal hard drive but when I go to open it I get that common error of not  being able to mount the volume (I have visions of the computer mounting the hard drive similiar to my dog mounting my leg). Anyway, for now I can see the external hard drive but not the internal one. Does this mean the hard drive is not supported even though I was able to instal on it or do I need to modify a file in order to see it? Do I need to go ahead and instal with blind faith and then make that change since I would assume you can't make these changes while running from cd?

That is my question so if you are in a rush or don't wish to read further you don't need to.

When running XP I got into a bit of programming. It started with a program called Autohotkey ([www.autohotkey.com](www.autohotkey.com)) and then progressed to programming Flash, PHP, and very little C+. Is there anything similiar to Autohotkey for Linux. I.E. I'm looking for a programming for dummies to learn from. Autohotkey was great becuase you simply put commands into a text document and it came with a great help file. The help file had the command, the syntax, the options, and an example much like a dictionary and I found this the easiest way to learn.

Now, a few things I've noticed so far. Firefox doesn't spell check like it does in Windows and when you click on the url in the address bar it doesn't highlight the entire thing. These are two things I would love to see changed or I will as soon as I can figure out this programming thing. Also, when you click the time and the calander appears you double click to show Evelution Mail but it opens the calendar to the day before the one you clicked on. I.E. I open the small calendar on the clock, double click on Monday, August 31, and the program opens to August 30. Finally, in the instal when you pick your time and place it shows Pacific Standard Time as GMT-7, unless I'm mistaken it's GMT-8. I could be wrong I don't keep up with daylight savings and all that jazz.

Thanks for listening to my rant and I hope someone can explain this whole mounting hard drives thing. Thanks.

---

### Post by benerivo on 2007-08-21
I'd definitely try to install it if you have formatted the drives and have nothing to lose. Linux will not be able to install itself to ntfs, although it can now read/write to ntfs partitions/drives perfectly (using hre ntfs-3g package). Ideally all drives/partitions should be formatted to ext3, using the gparted program on the Ubuntu CD before installing, unless they contain data you don't want to lose such as existing windows (ntfs) formatted partitions.

I'm sure once you install it will recognize your hard drive. The live CD should give you access to your internal drive although it won't display it on the desktop (this is just the nature of live cd's).


Don't worry too much about the fiineries of the default installation, and how the little things operate. There are many programs to choose to use in linux, and the new things you find will outweigh the small missed things in the long run. As for programming, there are a few IDE's in the package manager, that may be similar to what you've seen - suich as anjuta or eclipse.

---

### Post by High Camp on 2007-08-25
Hey benerivo ,

Thanks very much for the reply and sorry for the delayed response. I played with Linux a lot but decided not to install it on this computer becuase ultimately it's going to my Mum who doesn't know computers well.

Thanks again,

EDIT: I am installing Xubuntu right now on my own computer. Already I am looking at the development and ways I can contribute and learn and learn about programming.

---

