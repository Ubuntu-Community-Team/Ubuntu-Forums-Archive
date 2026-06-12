---
title: "Slew of Problems"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Salomonis on 2007-10-26
I have many things wrong with my computer if anyone has the patience to help me through them.  Firstly I upgraded 7.04 to 7.10, which seemed good since it allowed Geany to work, but other things that I thought would be fixed or already worked remained problematic and new things were added to the list.  I can't download anything from my hard drive to  my CD-RW not that big a deal since I don't generally use CD's to store info but after I upgraded, my flash drive couldn't be mounted; it worked earlier.  It says: mount: wrong fs type, bad option, bad superblock on /dev/sda,  missing codepage or helper program, or other error   In some cases useful info is found in syslog -try   dmesg|tail or so.  I have no idea what this means and I have no experience using a terminal command line.  I don't want to "Read all of the tax code to be my own accountant".  I will eventually learn everything about command lines but not for this immediate problem.  
Just to let you all know I did research the problem with the CD-RW.  It was the time period where CD-RWs broke the 4x write speed and weren't made backwards compatible with the older versions.  Theoretically I can buy new CD-RWs and not have the lock down problem writing to them.  As you can tell I haven't spent a dime since flash drives are a superior means of storage.  If I still have that problem I will probably let it go, but if anyone knows another means of getting this to work with 4x max speed CD-RWs I'm open to that.
Lastly I noticed that when I upgraded 7.04 to 7.10 it made 3 kernels each 7.10 but are numbered 14,15,16.  I use 16 when I boot, but I don't notice any difference when I used 15.  Is this Normal?  I'm using 6.4 GB on this hard drive which seems reasonable since I have a fair number of media programs, but I'm not sure how much space a kernel takes.  I would prefer to have only one for storage. Not that it does me any good for the only way I can transfer data is through networking(sigh... I wish computers would be a blessing).
Another aspect of this computer is that I'm dual booting it with xp home, but it's on a different hard drive and sata is not being used, so it shouldn't affect what is on this hard drive(theoretically, I'm finding that some computer problems are not rational, for instance it took me and a friend of mine 5 hours to set up this computer to where it could dual boot and the problem was that xp home was deleting the grub file on the OTHER hard drive that it didn't need.  I'm glad that Microsoft ideology still includes genocide of competition even when you don't need the resources of that competition)
I've thought about deleting everything and starting over, but that would nullify all the work my friend and I did in order to run both OS.  
Can someone mentor me for a week.  I'm thrilled I just got a C++ IDE to work on here.  This means I might not fail CS 121.  But not being able to transfer my programs to disk or flash prevents me from turning in assignments(restricted email attachments).  Any help appreciated

---

### Post by amaroKer on 2007-10-26
I really don't mean to be rude, but it's generally a good idea to post your support questions one, possibly two at a time.  More people can help without having to pick through a large article to find a shred of information useful to them.  

Sorry, though.  I don't really know much about hard drive interfaces...

Logan

---

### Post by Maestro23 on 2007-10-26
I'm here to try and help, but you've got to break that up into paragraphs so I can sift thru it.

---

### Post by Salomonis on 2007-10-28
Ok the main problem is the flash drive.  Whenever I attach it says could not mount volume and the details are:
mount: wrong fs type, bad option, bad superblock on /dev/sda,  missing codepage or helper program, or other error   In some cases useful info is found in syslog -try   dmesg|tail or so
What does this mean?

---

