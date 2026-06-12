---
title: "Can't Install Ubuntu"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Jim Hill on 2006-04-22
I downloaded PC(Instal X86) install CD, and copied it to a CD-R.
There was a single file: ubuntu-5.10-install-i386.iso    647,129,088 bytes

I started the computer, went to the CD, double clicked the file and received the message “Windows cannot open this file……” I thought of making a bootable CD-R, but don’t have any more CD’s available - and wondered if I would encounter the same problem since I would boot into Windows. I did some searching, but nobody else seems to have listed such a basic problem.

What should I do?  I'm using a Dell Pentium 3, 933 MHz with 384 meg's of RAM.

Thanks, Jim

---

### Post by jpfreely on 2006-04-22
It sounds like you have burned the iso file to the disc as is, not as an image.
You need a program on your windows that has a Burn Image option such as Nero. If the CD you used isn't RW then I'm afraid you'll need another.

---

### Post by x5452 on 2006-04-22
you have to set your bios to boot from the cd first, then the install disk will take off and install through it. I dont think you can install the OS through windows.  Also, make sure the file you copied is an ISO, I dl'd the same thing but i believe i had to burn it as an ISO file to work.

---

### Post by kh4nh on 2006-04-22
[QUOTE=Jim Hill]I downloaded PC(Instal X86) install CD, and copied it to a CD-R.
There was a single file: ubuntu-5.10-install-i386.iso    647,129,088 bytes

I started the computer, went to the CD, double clicked the file and received the message &#8220;Windows cannot open this file&#8230;&#8230;&#8221; I thought of making a bootable CD-R, but don&#8217;t have any more CD&#8217;s available - and wondered if I would encounter the same problem since I would boot into Windows. I did some searching, but nobody else seems to have listed such a basic problem.

What should I do?  I'm using a Dell Pentium 3, 933 MHz with 384 meg's of RAM.

Thanks, Jim[/QUOTE]

keep the CD inside the tray and restart your computer. Make sure your computer  boot order has CD as first. If not, you can change the boot order inside the BIOS

---

### Post by Sef on 2006-04-22
If you have windows, this page has a link to isorecorder (freeware) is real nice for burning isos.  That is all it burns.

[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")

---

### Post by catlett on 2006-04-22
You don't open the disk in windows. If you get into windows with the disk in the drive there is a problem. You may have the disk burned correctly but it sounds like you copied the file as data to a cd.
That file is an image file (ISO) it neads to be burned to a disk (cd)
Once the disc is made correctly you turn off your computer with the cd in the drive. If your Bios are configured correctly your computer will boot from the cd and the install will start.
Your bios are accessable when you first start up. It is very brief. When your computer starts there is a splashscreeen with makers logo on it (usually). This screen will say press F1 or press F12 for setup. Or something like that. Just press the function key it mentions and you will go to a text based menu. From there you wil find the boot options. Change the values by the arrow keys to boot from cdrom.

---

### Post by Jim Hill on 2006-04-23
Thanks for the useful information. I downloaded the install program to a folder on the hard drive, then copied it to a CD-R as a data file. I downloaded the application again, then used Directory Opus (an enhanced Windows Explorer) to see if the three files were duplicates using MD-5 checksum. Directory Opus said they were identical, and the names, extensions, and sizes agreed, too.

The computer is set up to boot from the floppy, then the CD drive, than the hard drive. I eliminated the floppy boot, but it didn't help. 

I used Nero (version that came with the CD drive) with a recent upgrade, and used Help to search for "burn image". The closest topic was "disk image or saved project", defined as "record the disk from disk image previously burned onto the hard drive". Disk image is another record option (others are data, music, videos/pictures, etc.). Are Disk Image and Burn Image the same?  

I ran disk info, and it listed CD-ROM/Session 01 (618MB)/Track 01: 0:02.00 70:15.37 (618MB), ISO 9660/joliet (mode 1)

Jim

---

### Post by mips on 2006-04-23
You need to burn an image.

---

### Post by fyrestrtr on 2006-04-23
From Nero

File --> Open Image
Make sure you select All files from the File Type dropdown
Click the Iso

Then Nero will burn it properly :)

---

### Post by Jim Hill on 2006-04-23
I was successful! Thanks for the tips.

Since someone else may have the same problem, let me summarize.

I downloaded Ubuntu, saved it to a folder on the hard drive, and copied it as a data file to a CD-R.  I couldn’t install using the CD-R; - it would not autostart, and double clicking the file in Windows explorer just opened a window asking what program to use.

I needed to “burn the ISO file to a disk”, which isn’t accomplished by burning it as a data file.  The Nero that came with my CD doesn’t seem to have that feature, so I used the link suggested by Sef [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)  to download a freeware application that allowed me to burn the file properly.

Aside from the thanks, this response may just be extra bandwidth. When I search for my post “Can’t Install Ubuntu” (without quotes) in this forum, I’m unsuccessful. The response is;

 Sorry - no matches. Please try some different terms.  If I just search for install Ubuntu, there are hundreds of responses.

Jim

---

### Post by mips on 2006-04-23
From the search drop-down menu the bottom 2 options will find either all your posts or threads. If you use the Advanced Search from the dropdown you can enter your userid and any keywords and that will narrow things down even further.

---

### Post by catlett on 2006-04-23
You're not wasting bandwidth at all. Someone will see your post and be helped. But if I could suggest, post those directions the next time you see someone having the same problem. You can now give beter advice than I because I don't have Nero experience and many people only have Nero.
So keep Sef's link handy and post your Nero instructions but point out if they have your version they'll need to go to that link and use that program.
In case you weren't aware, after you log in you can click on the "quick links", click on "my profile, when you get into your profile you can click on "find all posts by you" as well as "find all threads started by you".This way you can find your posts when you want to copy and paste some directions or a link. This is how I keep info given me in posts. I leave it there and get to it that way if I want to reply to a forum with a link or directions from a previous thread I was in. 
So, glad to hear it worked.Welcome and pass along your knowledge to the next person in need of it.

P.S. If you're in a post, you can click on your avatar and get to your profile as well.

---

